This is [obsidian cleaner](https://github.com/brachkow/obsidian-cleaner). If you are in reading view and have everything installed correctly you will see lists of notes that potentially need your attention.

## Notes with no title
```dataview
TABLE
FROM ""
WHERE contains(file.name, "Untitled")
```

## Empty notes
```dataview
TABLE
FROM ""
WHERE file.size = 0
```

## Tags by usage
```dataview
TABLE WITHOUT ID (tag + "(" + length(rows.file.link) + ")") AS Tags, link(sort(rows.file.name)) AS Files
FROM ""
WHERE file.tags 
FLATTEN file.tags AS tag 
GROUP BY tag
SORT length(rows.file.link) ASC
```

## Not modified for a long time

```dataview
TABLE file.mtime as "Last modified"
FROM ""
SORT file.mtime ASC
```