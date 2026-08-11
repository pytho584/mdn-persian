---
title: "AmbientLightSensor: illuminance property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AmbientLightSensor/illuminance"
translated_by: "n8n + AI"
---

## ویژگی `illuminance` در `AmbientLightSensor`

ویژگی فقط‌خواندنی `illuminance` از واسط `AmbientLightSensor` سطح روشنایی کنونی نور محیط پیرامون دستگاه میزبان را بر حسب [لوکس](https://en.wikipedia.org/wiki/Lux) برمی‌گرداند.

### مقدار

یک عدد (`Number`) که سطح روشنایی کنونی را بر حسب لوکس نشان می‌دهد.

### مثال‌ها

```js
if ("AmbientLightSensor" in window) {
  const sensor = new AmbientLightSensor();
  sensor.addEventListener("reading", (event) => {
    console.log("Current light level:", sensor.illuminance);
  });
  sensor.addEventListener("error", (event) => {
    console.log(event.error.name, event.error.message);
  });
  sensor.start();
}
```