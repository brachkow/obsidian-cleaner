This is [obsidian cleaner](https://github.com/brachkow/obsidian-cleaner). If you are in reading view and have everything installed correctly you will see lists of potentially rubbish notes bellow.

## Notes with no title
```dataview
TABLE
FROM "/"
WHERE contains(file.name, "Untitled")
```

## Empty notes
```dataview
TABLE
FROM "/"
WHERE file.size = 0
```
