# Public timetable

## !!! TOHLE NEJSOU API KTERÁ BY VRACELA JSON, POUZE HTML API, JE NUTNÉ PARSOVÁNÍ

### Požadavek
```
GET
/timetable/Public/Next/(Teacher, Class, Room)/id
/Timetable/Public/Actual/(Teacher, Class, Room)/id
/Timetable/Public/Permanent/(Teacher, Class, Room)/id
```

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
