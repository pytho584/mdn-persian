---
title: "Accelerometer: z property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Accelerometer/z"
translated_by: "n8n + AI"
---

ویژگی `z` در شیء `Accelerometer` (فقط خواندنی)

ویژگی فقط خواندنی **`z`** در رابط `Accelerometer` عددی را برمی‌گرداند که شتاب دستگاه در امتداد محور z را مشخص می‌کند.

## مقدار

یک `Number` از نوع {{jsxref('Number')}}.

## مثال‌ها

معمولاً شتاب در رویداد `reading` ({{domxref('Sensor.reading_event', 'reading')}}) خوانده می‌شود. در مثال زیر این کار شصت بار در ثانیه انجام می‌شود.

```js
const accelerometer = new Accelerometer({ frequency: 60 });

accelerometer.addEventListener("reading", (e) => {
  console.log(`Acceleration along the X-axis ${accelerometer.x}`);
  console.log(`Acceleration along the Y-axis ${accelerometer.y}`);
  console.log(`Acceleration along the Z-axis ${accelerometer.z}`);
});
accelerometer.start();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}