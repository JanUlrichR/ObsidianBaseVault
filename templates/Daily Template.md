# [[ 📆 Dailys/<% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %> |⬅]] | <% tp.file.title %> ([[ 📆 Dailys/<% tp.date.now("YYYY-[KW]WW", 0, tp.file.title, "YYYY-MM-DD") %> |<% tp.date.now("[KW]WW", 0, tp.file.title, "YYYY-MM-DD") %>]]) | [[ 📆 Dailys/<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %> |➡]]
___
## Startup
<% tp.file.include("[[templates/Daily Template Startup]]") %>

```dataview
TABLE status AS Status
FROM "✅ Tasks"
WHERE status = "Open" OR status = "In Progress"
SORT status DESC
```

## Day Planner
- [ ] <% tp.file.cursor(1) %>

## Shutdown
<% tp.file.include("[[templates/Daily Template Shutdown]]") %>
___
## Random

<% tp.web.daily_quote() %>
<% tp.web.random_picture("400x400", "tech, code") %>


