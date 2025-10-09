---
company:
location:
title:
email:
website:
aliases:
phone:
---
tags:: [[Business MOC]]

# <% tp.file.title %>
<% await tp.file.move("03_Cards/business/" + tp.file.title) %>

## Notes
-

## People
```dataviewjs
const pages = dv.pages()
    .where(p => {
        // Check for inline tags::[[People MOC]] - it's a single object, not an array
        return p.tags && p.tags.path === "01_Atlas/People MOC.md";
    })
    .where(p => p.file.outlinks.some(link => link.path === dv.current().file.path));

let html = '<table style="border-collapse: collapse; width: 100%;"><!--<thead><tr style="border-bottom: 2px solid #333;"><th style="padding: 8px;">Name</th><th style="padding: 8px;">Photo</th></tr></thead>--><tbody>';

for (let page of pages) {
    const content = await dv.io.load(page.file.path);
    const imageMatch = content.match(/!\[\]\(([^)]+)\)/);
    
    const nameLink = `<a href="obsidian://open?file=${encodeURIComponent(page.file.path)}">${page.file.name}</a>`;
    const image = imageMatch ? `<img src="${imageMatch[1]}" width="50" height="50" style="object-fit: cover;">` : "";
    const title = page.title ? page.title.toString().replace(/^,\s*/, "") : "";
    
    html += `<tr style="border-bottom: 1px solid #ddd;"><td style="padding: 8px;">${nameLink}<br>${title}</td><td style="padding: 8px;">${image}</td></tr>`;
}

html += '</tbody></table>';
dv.paragraph(html);
```

## Meetings
```dataview
TABLE file.cday as Created, summary AS "Summary"
FROM "02_Calendar/Daily/meetings" where contains(file.outlinks, [[<% tp.file.title %>]])
SORT file.cday DESC
```

