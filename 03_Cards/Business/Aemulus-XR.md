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

# Aemulus-XR


## Notes
-  [Sam Gebhardt](03_Cards/People/Sam%20Gebhardt.md) - COO
- [James King](03_Cards/People/James%20King.md) - CTO
- [Fredric Gaba](03_Cards/People/Fredric%20Gaba.md) - Lead Framework "SAM" Engineer
- [Mark Fitzpatrick](03_Cards/People/Mark%20Fitzpatrick.md) - Technical Director,  3D
- [Paul Bernal](03_Cards/People/Paul%20Bernal.md) - CEO
- [Walter Engle](03_Cards/People/Walter%20Engle.md) - CMO, Chief Medical Officer
- [Yadira Bernal](03_Cards/People/Yadira%20Bernal.md)- VP Global Sales
- [Lukasz Jurczak](03_Cards/People/Lukasz%20Jurczak.md) - European Medical Consultant
- [Alex Bandar](03_Cards/People/Alex%20Bandar.md) - Senior Director, Hardware Engineering
- [Ibrahim AL Balawi](03_Cards/People/Ibrahim%20AL%20Balawi.md) - Director of Business Development
- 

```dataviewjs
const pages = dv.pages()
    .where(p => {
        // Check for inline tags::[[People MOC]] - it's a single object, not an array
        return p.tags && p.tags.path === "01_Atlas/People MOC.md";
    })
    .where(p => p.file.outlinks.some(link => link.path === dv.current().file.path));

let html = '<table style="border-collapse: collapse; width: 100%;"><thead><tr style="border-bottom: 2px solid #333;"><th style="padding: 8px;">Name</th><th style="padding: 8px;">Photo</th></tr></thead><tbody>';

for (let page of pages) {
    const content = await dv.io.load(page.file.path);
    const imageMatch = content.match(/!\[\]\(([^)]+)\)/);
    
    const nameLink = `<a href="obsidian://open?file=${encodeURIComponent(page.file.path)}">${page.file.name}</a>`;
    const image = imageMatch ? `<img src="${imageMatch[1]}" width="50" height="50" style="object-fit: cover;">` : "";
    
    html += `<tr style="border-bottom: 1px solid #ddd;"><td style="padding: 8px;">${nameLink}</td><td style="padding: 8px;">${image}</td></tr>`;
}

html += '</tbody></table>';
dv.paragraph(html);
```

## Meetings
```dataview
TABLE file.cday as Created, summary AS "Summary"
FROM "02_Calendar/Daily/meetings" where contains(file.outlinks, [[Aemulus XR]])
SORT file.cday DESC
```

