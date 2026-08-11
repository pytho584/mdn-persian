---
title: "Accelerometer: x property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Accelerometer/x"
translated_by: "n8n + AI"
---

# Accelerometer: ویژگی x

ویژگی فقط‌خواندنی **`x`** در واسط {{domxref("Accelerometer")}} عددی را برمی‌گرداند که شتاب دستگاه در راستای محور x را مشخص می‌کند.

## مقدار

یک عدد (`Number`).

## مثال

معمولاً شتاب در رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر این کار ۶۰ بار در ثانیه انجام می‌شود.

```js
const accelerometer = new Accelerometer({ frequency: 60 });

accelerometer.addEventListener("reading", (e) => {
  console.log(`Acceleration along the X-axis ${accelerometer.x}`);
  console.log(`Acceleration along the Y-axis ${accelerometer.y}`);
  console.log(`Acceleration along the Z-axis ${accelerometer.z}`);
});
accelerometer.start();
```