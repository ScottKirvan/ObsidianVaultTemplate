---
company:
location:
title:
email:
website:
aliases:
phone:
---
tags:: [[03_Cards/People]]

# <% tp.file.title %>
<% await tp.file.move("03_Cards/people/" + tp.file.title) %>

## Notes
-

## Meetings
```dataview
TABLE file.cday as Created, summary AS "Summary"
FROM "02_Calendar/Daily/meetings" where contains(file.outlinks, [[<% tp.file.title %>]])
SORT file.cday DESC
```