# Public timetable

## !!! TOHLE NEJSOU API KTERÁ BY VRACELA JSON, POUZE HTML API, JE NUTNÉ PARSOVÁNÍ

### Požadavek
```
GET
/timetable/Public/Next/(Teacher, Class, Room)/id
/Timetable/Public/Actual/(Teacher, Class, Room)/id
/Timetable/Public/Permanent/(Teacher, Class, Room)/id
```

[Příklad pro HTML pro výběr filtrace](../priklady/options.html)

[Příklad pro HTML pro den v rozvrhu](../priklady/day.html)

[Dokumentace pro osobní rozvrh](./timetable.md)

Není potřeba žádná autorizace nebo speciální headers. Při testování jsem nedostával ani žádné chyby.

Parser v JS, je potřeba stáhnout cheerio a node-fetch pomocí správce balíčků (npm, yarn, ...)

App.js
```js
import fetch from "node-fetch";
import * as cheerio from "cheerio";

fetch("https://truhla.bakalari.cz/Timetable/Public/Next/Room/G0")
.then((res) => res.text())
.then((html) => {
    const $ = cheerio.load(html);
    var classes = [];
    $('#selectedClass option').each((i, el) => {
        if (i >= 1) {
            classes.push($(el).val());
        }
    });
    console.log("Classes:");
    console.log(classes);

    var teachers = [];
    $('#selectedTeacher option').each((i, el) => {
        if (i >= 1) {
            teachers.push($(el).val());
        }
    });
    console.log("Teachers:");
    console.log(teachers);

    var rooms = [];
    $('#selectedRoom option').each((i, el) => {
        if (i >= 1) {
            rooms.push($(el).val(), $(el).text);
        }
    });
    console.log("Rooms:");
    console.log(rooms);

    //.bk-timetable-row -> one day -> 5 rows
    //  .bk-timetable-day
    //      .bk-day-day
    //      .bk-day-date
    //  .bk-timetable-cell -> max 10 school classes -> 10 cells
    //   If the cell is empty, skip it, else
    //      .day-item-hover -> get data-detail attribute -> it contains json -> parse it -> i need subjecttext (convert escaped chars like &#256 into normal ones), teacher, room and changeinfo
    
    var timetable = [];
    $('.bk-timetable-row').each((i, el) => {
        var day = {};
        day.day = $(el).find('.bk-timetable-day .bk-day-day').text().trim();
        day.date = $(el).find('.bk-timetable-day .bk-day-date').text().trim();
        day.classes = [];
        $(el).find('.bk-timetable-cell').each((j, cell) => {
            var detail = $(cell).find('.day-item-hover').attr('data-detail');
            if (detail) {
                var detailJson = JSON.parse(detail);
                day.classes.push({
                    subject: detailJson.subjecttext.replace(/&#(\d+);/g, (match, dec) => String.fromCharCode(dec)),
                    teacher: detailJson.teacher,
                    room: detailJson.room,
                    changeInfo: detailJson.changeinfo
                });
            }
        });
        timetable.push(day);
    });
    console.log("Timetable:");
    console.log(timetable);

    //Display classes in a readable format
    timetable.forEach((day) => {
        console.log(`${day.day} (${day.date}):`);
        day.classes.forEach((cls) => {
            console.log(` - ${cls.subject} | Teacher: ${cls.teacher} | Room: ${cls.room} | Change Info: ${cls.changeInfo}`);
        });
    });
});
```

a přidat do package.json

```json
{
    "type": "module"
}
```

Parser v C#, je potřeba stáhnout balíček HtmlAgilityPack

```bash
dotnet add package HtmlAgilityPack
```

```csharp
using System.Net;
using System.Text.Json;
using System.Text.Json.Serialization;
using HtmlAgilityPack;

class Timetable
{
    public List<Day> days { get; } = new();

    public void AddDay(Day day)
    {
        days.Add(day);
    }
}

class Day
{
    public string day {get; set;}
    public string date {get; set;}
    public List<Subject> subjects { get; } = new();

    public void AddSubject(Subject subject)
    {
        subjects.Add(subject);
    }
}

class Subject
{
    [JsonPropertyName("subjecttext")]
    public string subject {get; set;}
        
    [JsonPropertyName("teacher")]
    public string teacher {get; set;}
        
    [JsonPropertyName("room")]
    public string room {get; set;}
        
    [JsonPropertyName("changeinfo")]
    public string changeInfo {get; set;}
}

class Parser
{

    public static void Main()
    {
        string url = "https://<schoo>.bakalari.cz/Timetable/Public/Actual/Class/<id>";
        HtmlWeb web = new HtmlWeb();
        var htmlDoc = web.Load(url);

        void PrintSelectMenu(string type, string nodeId)
        {
            var selectNode = htmlDoc.DocumentNode.SelectNodes($"//select[@id='{nodeId}']");

            if (selectNode.Count > 0)
            {
                Console.WriteLine($"{type}:");

                var options = selectNode[0].SelectNodes(".//option");
                foreach (var option in options)
                {
                    if (option.GetAttributeValue("value", null) != null)
                    {
                        var value = option.GetAttributeValue("value", "default");
                        var text = option.InnerText.Trim();
                        Console.WriteLine($"{value} - {WebUtility.HtmlDecode(text)}");
                    }
                }
            }    
            Console.WriteLine();
        }

        PrintSelectMenu("Classes", "selectedClass");
        PrintSelectMenu("Teachers", "selectedTeacher");
        PrintSelectMenu("Rooms", "selectedRoom");
        
        Console.WriteLine();
        
        
        var timetable = new Timetable();
        
        var selectNode = htmlDoc.DocumentNode.SelectNodes("//div[contains(@class,'bk-timetable-row')]");
        if (selectNode.Count > 0)
        {
            foreach (var row in selectNode)
            {
                Day day = new Day();
                day.day = WebUtility.HtmlDecode(row.SelectNodes(".//span[contains(@class,'bk-day-day')]")[0].InnerText.Trim());
                day.date = row.SelectNodes(".//span[contains(@class,'bk-day-date')]")[0].InnerText.Trim();

                var cells = row.SelectNodes(".//div[contains(@class,'bk-timetable-cell')]");
                foreach (var cell in cells)
                {
                    var nodes = cell.SelectNodes(".//div[contains(@class,'day-item-hover')]");

                    if (nodes != null)
                    {
                        foreach (var node in nodes)
                        {
                            string detail = node.GetAttributeValue("data-detail", null);

                            if (!string.IsNullOrEmpty(detail))
                            {
                                detail = WebUtility.HtmlDecode(detail);
                                var subject = JsonSerializer.Deserialize<Subject>(detail);
                                day.AddSubject(subject!);       
                            }
                        }
                    }
                }
                
                timetable.AddDay(day);
            }
        }

        foreach (var day in timetable.days)
        {
            Console.WriteLine($"{day.day} - {day.date}");
            foreach (var subject in day.subjects)
            {
                Console.WriteLine($" - {subject.subject} | Teacher: {subject.teacher} | Room {subject.room} | Change Info: {subject.changeInfo}");
            }
        }
    }
```

Parser v python, je potřeba doinstalovat requests a beautifulsoup4 pomocí pip

```bash
#Pokud ještě nejste ve virtual env, je potřeba ho nejprve vytvořit a poté vstoupit
python3 -m venv venv #Vytvoři venv složku v aktuálním adresáři
source venv/bin/activate #Aktivuje venv

pip install requests beautifulsoup4
```

```python
import requests
import html
import json
from bs4 import BeautifulSoup


class Subject:
    def __init__(self, subjecttext, teacher, room, changeinfo):
        self.subject = html.unescape(subjecttext)
        self.teacher = teacher
        self.room = room
        self.changeInfo = changeinfo


class Day:
    def __init__(self, day, date):
        self.day = day
        self.date = date
        self.subjects = []

    def add_subject(self, subject):
        self.subjects.append(subject)


class Timetable:
    def __init__(self):
        self.days = []

    def add_day(self, day):
        self.days.append(day)


def print_select_menu(soup, label, select_id):
    select = soup.find("select", {"id": select_id})
    if select:
        print(f"{label}:")
        for option in select.find_all("option"):
            value = option.get("value")
            if value:
                text = html.unescape(option.text.strip())
                print(f"{value} - {text}")
        print()


def main():
    url = "https://<school>.bakalari.cz/Timetable/Public/Actual/Class/<id>"
    response = requests.get(url)
    soup = BeautifulSoup(response.text, "html.parser")

    print_select_menu(soup, "Classes", "selectedClass")
    print_select_menu(soup, "Teachers", "selectedTeacher")
    print_select_menu(soup, "Rooms", "selectedRoom")

    timetable = Timetable()

    rows = soup.find_all("div", class_="bk-timetable-row")
    for row in rows:
        day_text = row.find("span", class_="bk-day-day")
        date_text = row.find("span", class_="bk-day-date")

        if day_text and date_text:
            day = Day(html.unescape(day_text.text.strip()), date_text.text.strip())

            cells = row.find_all("div", class_="bk-timetable-cell")
            for cell in cells:
                hover_nodes = cell.find_all("div", class_="day-item-hover")
                for node in hover_nodes:
                    detail = node.get("data-detail")
                    if detail:
                        try:
                            data = json.loads(html.unescape(detail))
                            subject = Subject(
                                data.get("subjecttext", ""),
                                data.get("teacher", ""),
                                data.get("room", ""),
                                data.get("changeinfo", "")
                            )
                            day.add_subject(subject)
                        except json.JSONDecodeError as e:
                            print(f"Chyba při deserializaci: {e}")

            timetable.add_day(day)

    for day in timetable.days:
        print(f"{day.day} - {day.date}")
        for subject in day.subjects:
            print(f" - {subject.subject} | Teacher: {subject.teacher} | Room {subject.room} | Change Info: {subject.changeInfo}")


if __name__ == "__main__":
    main()

```
