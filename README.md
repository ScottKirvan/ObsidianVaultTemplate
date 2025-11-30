

- 🔖 Encounters   
 `$=dv.list(dv.pages('"+ Main"').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`  
- 🗄️ Recent Updates   
`$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`  

- 〽️ Stats
	-  File Count: `$=dv.pages().length`
	-  Personal recipes: `$=dv.pages('"Family/Recipes"').length`
	- [People](03_Cards/People.md):`$=dv.pages('"03_Cards/people"').length`


```dataview
list without id
L.text
from ""
flatten file.lists as L
where contains(L.tags, "#q")
```

