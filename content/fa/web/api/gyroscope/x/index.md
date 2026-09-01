---
title: "Gyroscope: x property"
short-title: x
slug: Web/API/Gyroscope/x
page-type: web-api-instance-property
browser-compat: api.Gyroscope.x
---

{{securecontext_header}}{{APIRef("Sensor API")}}

خاصیت فقط‌خواندنی **`x`** در رابط {{domxref("Gyroscope")}} عددی را برمی‌گرداند که سرعت زاویه‌ای دستگاه را حول محور x آن مشخص می‌کند.

## مقدار

یک {{jsxref('Number')}}.

## مثال‌ها

معمولاً ژیروسکوپ در تابع بازخوانی رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر این کار شصت بار در ثانیه انجام می‌شود.

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
