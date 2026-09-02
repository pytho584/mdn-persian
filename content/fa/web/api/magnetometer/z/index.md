---
title: "Magnetometer: z property"
short-title: z
slug: Web/API/Magnetometer/z
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Magnetometer.z
---

{{securecontext_header}}{{APIRef("Sensor API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`z`** در رابط {{domxref("Magnetometer")}} عددی را برمی‌گرداند که میدان مغناطیسی اطراف محور z دستگاه را مشخص می‌کند.

## مقدار

یک {{jsxref('Number')}}.

## مثال‌ها

مغناطیس‌سنج معمولاً در رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر این کار شصت بار در ثانیه انجام می‌شود.

```js
let magSensor = new Magnetometer({ frequency: 60 });

magSensor.addEventListener("reading", (e) => {
  console.log(`Magnetic field along the X-axis ${magSensor.x}`);
  console.log(`Magnetic field along the Y-axis ${magSensor.y}`);
  console.log(`Magnetic field along the Z-axis ${magSensor.z}`);
});
magSensor.start();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}