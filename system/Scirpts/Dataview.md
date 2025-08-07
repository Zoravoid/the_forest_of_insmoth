
```JavaScript
let tagsMap = new Map();

for (let page of dv.pages())
{
	if (!page.file?.tags) continue;
	for (let tag of page.file.tags)
	{
		if (!tagsMap.has(tag))
		{
			tagsMap.set(tag, {count: 0, files: []});
		}
		let tagEntry = tagsMap.get(tag);
		tagEntry.count += 1;
		tagEntry.files.push(page.file.name);
	}
}

let sortedTags = Array.from(tagsMap.entries()).sort((a, b) => b[1].count - a[1].count);

dv.table(["Tag", "Used In", "Files"], sortedTags.map(([tag, info]) => [tag, info.count, info.files.join(", ")]));
```
