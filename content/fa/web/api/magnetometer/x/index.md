---
title: "Magnetometer: x property"
short-title: x
slug: Web/API/Magnetometer/x
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Magnetometer.x
---

{{securecontext_header}}{{APIRef("Sensor API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`x`** از رابط {{domxref("Magnetometer")}} عددی را برمی‌گرداند که میدان مغناطیسی اطراف محور x دستگاه را مشخص می‌کند.

## مقدار

یک {{jsxref('Number')}}.

## مثال‌ها

مغناطیس‌سنج معمولاً در callback رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر این کار شصت بار در ثانیه انجام می‌شود.

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

## سازگاری با مرورگر

{{Compat}}