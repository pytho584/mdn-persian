---
title: "Accelerometer: y property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Accelerometer/y"
translated_by: "n8n + AI"
---

ویژگی فقط‌خواندنی **`y`** در interface `Accelerometer` عددی را برمی‌گرداند که شتاب دستگاه در راستای محور y را نشان می‌دهد.

## مقدار

یک {{jsxref('Number')}}.

## مثال‌ها

شتاب معمولاً در callback رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر این کار ۶۰ بار در ثانیه انجام می‌شود.

```js
const accelerometer = new Accelerometer({ frequency: 60 });

accelerometer.addEventListener("reading", (e) => {
  console.log(`Acceleration along the X-axis ${accelerometer.x}`);
  console.log(`Acceleration along the Y-axis ${accelerometer.y}`);
  console.log(`Acceleration along the Z-axis ${accelerometer.z}`);
});
accelerometer.start();
```