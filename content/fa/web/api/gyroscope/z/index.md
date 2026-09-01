---
title: "Gyroscope: z property"
short-title: z
slug: Web/API/Gyroscope/z
page-type: web-api-instance-property
browser-compat: api.Gyroscope.z
---

{{securecontext_header}}{{APIRef("Sensor API")}}

خاصیت فقطخواندنی **`z`** در رابط {{domxref("Gyroscope")}} عددی را برمی‌گرداند که سرعت زاویه‌ای دستگاه را در امتداد محور z آن مشخص می‌کند.

## مقدار

یک {{jsxref('Number')}}.

## مثال‌ها

ژیروسکوپ معمولاً در فراخوانی رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر این کار شصت بار در ثانیه انجام می‌شود.

```js
let gyroscope = new Gyroscope({ frequency: 60 });

gyroscope.addEventListener("reading", (e) => {
  console.log(`Angular velocity along the X-axis ${gyroscope.x}`);
  console.log(`Angular velocity along the Y-axis ${gyroscope.y}`);
  console.log(`Angular velocity along the Z-axis ${gyroscope.z}`);
});
gyroscope.start();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}