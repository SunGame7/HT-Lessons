**Important Functions**
Unit 1: `JSON.parse()` & `JSON.stringify()`

New
```js
JSON.parse(fs.readFile(path)) // Gets the JSON data from a file
fs.writeFile(path, JSON.stringify(jsonvar), () => {}) // Writes a file, based on a variable.
```

**How your balance file should look**
```json
  {
    "527524461323485205": 100,
    "811830036481966111": 100
   }
```

**How your updated balance file should look**
```json
  {
    "527524461323485205": {
      "coins": 100,
      "gems": 20
    },
    "811830036481966111": {
      "coins": 100,
      "gems": 20
    }
   }
```
