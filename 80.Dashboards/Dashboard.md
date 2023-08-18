
```dataviewjs
dv.span("** Activities **") /* optional ⏹️💤⚡⚠🧩↑↓⏳📔💾📁📝🔄📝🔀⌨️🕸️📅🔍✨ */

const calendarData = {
	colors: { // (optional) defaults to green
		blue: ["#8cb9ff", "#69a3ff", "#428bff", "#1872ff", "#0058e2"],
		green: ["#c6e48b", "#7bc96f", "#49af5d", "#2e8840", "#196127"],
		red: ["#ff9e82", "#ff7b55", "#ff4d1a", "#e73400", "#bd2a00"],
		orange: ["#ffa244", "#fd7f00", "#dd6f00", "#bf6000", "#9b4e00"],
		pink: ["#ff96cb", "#ff70b8", "#ff3a9d", "#ee0077", "#c30062"],
		orangeToRed: ["#ffdf04", "#ffbe04", "#ff9a03", "#ff6d02", "#ff2c01"]
	},
	showCurrentDayBorder: true,
	defaultEntryIntensity: 4,
	intensityScaleStart: 10,
	intensityScaleEnd: 100,
	entries: []
}

const map = {}
dv.pages().map(it => new Date(it.file.ctime)).map(it => formatDate(it)).forEach(it => {
	if(!map[it]) map[it] = 1
	else map[it] += 1
})

for(let k in map){
	calendarData.entries.push({
		date: k,
		intensity: map[k],
		color: "green"
	})
}

function formatDate(date) {
    var d = new Date(date),
        month = '' + (d.getMonth() + 1),
        day = '' + d.getDate(),
        year = d.getFullYear();

    if (month.length < 2) 
        month = '0' + month;
    if (day.length < 2) 
        day = '0' + day;

    return [year, month, day].join('-');
}

renderHeatmapCalendar(this.container, calendarData)

```


```dataview
table file.name, file.mtime
from #unknow
```

