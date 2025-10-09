tags:: #<% tp.date.now("YYYY",0,tp.file.title,"YYYY-MM-DD") %>/<% tp.date.now("YYYY-[Q]Q",0,tp.file.title,"YYYY-MM-DD") %>/<%tp.date.now("YYYY-MM",0,tp.file.title,"YYYY-MM-DD")%>/<%tp.date.now("YYYY-MM-DD",0,tp.file.title,"YYYY-MM-DD")%>  
[<< Prev](02_Calendar/Daily/<% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %>) | <% tp.date.now("dddd, YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %> | [Next >>](02_Calendar/Daily/<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>)

# <% tp.date.now("dddd, YYYY-MM-DD", 0, tp.file.title, "YYYY-MM-DD") %>
{{qotd}}
## Processing
email - texts - discord - linkedin - calendar - slack job board - photos - [[inbox]]
- 
## Journal
- 

## Created Today
```dataview
TABLE string(split(string(file.ctime), " - ")[0]) as "Created", file.mtime as "Last Modified"
WHERE contains(file.path, "{{date:YYYY-MM-DD}}")
  OR (file.cday = date("{{date:YYYY-MM-DD}}") AND !regexmatch("^\d{4}-\d{2}-\d{2}", file.name))
SORT file.name ASC
```

## Last Modified Today
```dataview
TABLE string(split(string(file.mtime), " - ")[0]) as "Last Modified"
WHERE !contains(file.path, "{{date:YYYY-MM-DD}}")
  AND !contains(file.path, "{{date:YYYY-MM-DD}} Daily Note")
  AND file.mday = date("{{date:YYYY-MM-DD}}")
SORT file.mtime DESC
```

## Touched Today
```dataview
TASK WHERE completion = date("{{date:YYYY-MM-DD}}")
  AND due != date("{{date:YYYY-MM-DD}}")
```

## Whiteboard