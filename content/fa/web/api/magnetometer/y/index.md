---
title: "Magnetometer: y property"
---

---
title: "Magnetometer: y property"
short-title: y
slug: Web/API/Magnetometer/y
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Magnetometer.y
---

{{securecontext_header}}{{APIRef("Sensor API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`y`** در رابط {{domxref("Magnetometer")}} عددی را برمی‌گرداند که میدان مغناطیسی اطراف محور y دستگاه را مشخص می‌کند.

## مقدار

یک مقدار از نوع {{jsxref('Number')}}.

## مثال‌ها

مغناطیس‌سنج معمولاً در تابع callback مربوط به رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر، این کار شصت بار در ثانیه انجام می‌شود.

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