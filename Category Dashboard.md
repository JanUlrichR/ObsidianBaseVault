---
obsidianUIMode: preview
---
# Inbox
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Status"], dv.pages('"✅ Tasks"')
	.filter(t => t.category === "Inbox")
	.map(t => [
		t.file.link,
		t['status']
		])
)
```

# ASAP
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Status"], dv.pages('"✅ Tasks"')
	.filter(t => t.category === "ASAP")
	.map(t => [
		t.file.link,
		t['status']
		])
)
```

# Maybe
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Status"], dv.pages('"✅ Tasks"')
	.filter(t => t.category === "Maybe")
	.map(t => [
		t.file.link,
		t['status']
		])
)
```

# Reference
```dataviewjs
const {createButton} = app.plugins.plugins["buttons"]
const {update} = app.plugins.plugins['metaedit'].api

const changeStatus = async (file, value) => {
    await update("status", value, file)
}

dv.table(["Task", "Comp"], dv.pages('"✅ Tasks"')
	.filter(t => t.category === "Reference")
	.map(t => [
		t.file.link,
		t['status']
		])
)
```
