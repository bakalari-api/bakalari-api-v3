# Označování hotových/nehotových úkolů

## Požadavek

```
PUT /api/3/homeworks/<ID>/student-done/<stav>
```

Stavy: `true` - označit jako hotové, `false` - nehotové.

ID je ID úkolu, nicméně musí být v případě potřeby percent-encoded (`ZSQCVE[IMJ` -> `ZSQCVE%5BIMJ`) - v JavaScriptu funkce [`encodeURIComponent()`][1].

[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent#description
