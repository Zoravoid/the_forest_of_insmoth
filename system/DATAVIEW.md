<%*
let script = await tp.file.include("[[git/system/Scirpts/Dataview|Dataview]]");
tR += script
%>
# Last Edits
```dataview
TABLE file.mtime AS "Last Modified"
FROM "git/insmoth"
SORT file.mtime DESC
LIMIT 20
```

# File Query by Tag
```dataview
TABLE file.etags AS "Tags", file.mtime AS "Last Modified"
FROM "git/insmoth"
WHERE contains(file.tags, "#characters/player/campaign/the_blight/beaumont")
SORT file.etags ASC
LIMIT 20
```

# Tag View
```dataview
TABLE file.etags AS "Tags", file.count
FROM "git/system/00_TAG_INDEX.md"
SORT file.tags DESC
```
