# [[ 📅 Weeklys/<% tp.date.now("YYYY-[KW]WW", -7, tp.file.title, "YYYY-[KW]WW") %> |⬅]] | <% tp.file.title %> | [[ 📅 Weeklys/<% tp.date.now("YYYY-[KW]WW", 7, tp.file.title, "YYYY-[KW]WW") %> |➡]]
___
## Startup
<% tp.file.include("[[templates/Weekly Template Startup]]") %>

## Planned Tasks
Actions that will ensure I make progress on my goals 
-  <% tp.file.cursor(1) %>

## Week at a Glance

[[📆 Dailys/<% tp.date.weekday("YYYY-MM-DD", 0, tp.file.title, "YYYY-[KW]WW") %>|Monday]]
[[📆 Dailys/<% tp.date.weekday("YYYY-MM-DD", 1, tp.file.title, "YYYY-[KW]WW") %>|Tuesday]]
[[📆 Dailys/<% tp.date.weekday("YYYY-MM-DD", 2, tp.file.title, "YYYY-[KW]WW") %>|Wednesday]]
[[📆 Dailys/<% tp.date.weekday("YYYY-MM-DD", 3, tp.file.title, "YYYY-[KW]WW") %>|Thursday]]
[[📆 Dailys/<% tp.date.weekday("YYYY-MM-DD", 4, tp.file.title, "YYYY-[KW]WW") %>|Friday]]
[[📆 Dailys/<% tp.date.weekday("YYYY-MM-DD", 5, tp.file.title, "YYYY-[KW]WW") %>|Saturday]]
[[📆 Dailys/<% tp.date.weekday("YYYY-MM-DD", 6, tp.file.title, "YYYY-[KW]WW") %>|Sunday]]
___
## End Of Week Review

<% tp.file.include("[[templates/Weekly Template Shutdown]]") %>