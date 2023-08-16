---
cssclass: dashboard
obsidianUIMode: preview
---
## Go to
- `="[[ 📆 Dailys/" + dateformat(date(today), "yyyy-MM-dd") + " |Todays Daily Note]]"`
- `="[[ 📅 Weeklys/" + dateformat(date(today), "yyyy")+"-KW"+dateformat(date(today), "WW") + " | This Weeks Note]]"`
- [[Tasks |Taskoverview]]
- 

## Links
- 
- 
- 
- File Count: `$=dv.pages().length`

## Create
```button
name ✅ Tasks
type note(function(){return this.inputEl.value}) template
action Task Template
```
```button
name 💡 Idea
type note(function(){return this.inputEl.value}) template
action Idea Template
```
```button
name 🛠️ Project
type note(function(){return this.inputEl.value}) template
action Project Template
```

## Recent Updates
 `$=await dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(8).file.link)`

## Task Distribution

```dataviewjs
const groupBy = (arr) => arr.reduce(
    (entryMap, e) => entryMap.set(e, [...entryMap.get(e)||[], e]),
    new Map())
// Use golden Angle to generate distinct colors
const selectColor = (number) => `hsla(${number * 137.508},75%,75%, 0.5)`;

const tasks = await dv.pages('"✅ Tasks"')

const taskStatus = tasks
	.filter(t => t.category !== "Inbox")
	.map(t => t.status).values
const taskCategory = tasks
	.filter(t => t.status !== "Closed")
	.map(t => t.category).values

const taskStatusLengths = groupBy(taskStatus)
const taskCategoryLengths = groupBy(taskCategory)

const statusLabels = [...taskStatusLengths.keys()].sort();
const statusValues = statusLabels.map(label => taskStatusLengths.get(label)).map(it => it.length)
const categoryLabels = [...taskCategoryLengths.keys()].sort();
const categoryValues = categoryLabels.map(label => taskCategoryLengths.get(label)).map(it => it.length);

const labels = [...statusLabels, ...categoryLabels]
const label2color = {
	"Open": "hsla(0, 100%, 50%, 0.5)",
	"In Progress": "hsla(22, 100%, 50%, 0.5)",
	"Closed": "hsla(145, 100%, 50%, 0.5)",
	"Blocked": "hsla(46, 100%, 50%, 0.5)", 
	"Delegated": "hsla(177, 100%, 50%, 0.5)",

	Inbox: "hsla(207, 100%, 50%, 0.5)",
	ASAP: "hsla(315, 100%, 50%, 0.5)",
	Maybe: "hsla(269, 100%, 50%, 0.5)",
	Reference: "hsla(226, 100%, 50%, 0.5)",
}

const colors = labels.map((it, index) => label2color[it] || selectColor(index))

const statusFilledValues = [...statusValues, ...new Array(categoryLabels.length).fill(0)]
const categoryFilledValues = [...new Array(statusLabels.length).fill(0), ...categoryValues]


const chartData = {
    type: 'doughnut',
    data: {
        labels: labels,
        datasets: [{
            label: 'Status',
            data: statusFilledValues,
            backgroundColor: colors,
            borderColor: colors,
            borderWidth: 1
        },{
            label: 'Category',
            data: categoryFilledValues,
            backgroundColor: colors,
            borderColor: colors,
            borderWidth: 1
        }]
    },
    width: '300px',
    labelColors: true
}

window.renderChart(chartData, this.container);
```


## Current Tasks
```dataview
TABLE status AS Status
FROM "✅ Tasks"
WHERE status != "Open" and status != "Closed"
SORT status DESC
```