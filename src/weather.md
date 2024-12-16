# Weather report


## Prints a Promise here as the data loader isn't yet completed until the JS Block execution is complete
```js
const forecast = FileAttachment("./data/forecast.json").json();
display(forecast);
```

## Prints actual values of the forecast as JSON object
```js
display(forecast);
```

## Create a function here to plot the temperature
```js
function temperaturePlot(data, {width} = {}) {
    return Plot.plot({
      title: "Hourly temperature forecast",
      width,
      x: {type: "utc", ticks: "day", label: null},
      y: {grid: true, inset: 10, label: "Degrees (F)"},
      marks: [
        Plot.lineY(data.properties.periods, {
          x: "startTime",
          y: "temperature",
          z: null, // varying color, not series
          stroke: "temperature",
          curve: "step-after"
        })
      ]
    });
  }
```

Display function is called with a function and the data as parameter
```js
display(temperaturePlot(forecast));
```