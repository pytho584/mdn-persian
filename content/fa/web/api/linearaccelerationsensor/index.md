---
title: LinearAccelerationSensor
slug: Web/API/LinearAccelerationSensor
page-type: web-api-interface
browser-compat: api.LinearAccelerationSensor
---

{{securecontext_header}}{{APIRef("Sensor API")}}

رابطهٔ **`LinearAccelerationSensor`** در [Sensor APIs](/en-US/docs/Web/API/Sensor_APIs) در هر بار خواندن، شتابِ واردشده به دستگاه را در هر سه محور ارائه می‌دهد، اما بدون سهم گرانش.

برای استفاده از این سنسور، کاربر باید از طریق [Permissions API](/en-US/docs/Web/API/Permissions_API) به سنسور دستگاه `'accelerometer'` اجازه دهد. همچنین ممکن است این قابلیت توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) تنظیم‌شده روی سرور شما مسدود شده باشد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("LinearAccelerationSensor.LinearAccelerationSensor", "LinearAccelerationSensor()")}}
  - : یک شیء جدید `LinearAccelerationSensor` می‌سازد.

## ویژگی‌های نمونه

_ویژگی‌ها را از اجداد خود، {{domxref('Accelerometer')}}، {{domxref("Sensor")}} و {{domxref("EventTarget")}} به ارث می‌برد._

## روش‌های نمونه

_`LinearAccelerationSensor` روش‌های خاص خود را ندارد. با این حال، روش‌ها را از رابط‌های والد خود، {{domxref("Sensor")}} و {{domxref("EventTarget")}} به ارث می‌برد._

## رویدادها

_`LinearAccelerationSensor` رویدادهای خاص خود را ندارد. با این حال، رویدادها را از رابط والد خود، {{domxref('Sensor')}} به ارث می‌برد._

## مثال

شتاب خطی معمولاً در فراخوان رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر این کار شصت بار در ثانیه انجام می‌شود.

```js
let laSensor = new LinearAccelerationSensor({ frequency: 60 });

laSensor.addEventListener("reading", (e) => {
  console.log(`Linear acceleration along the X-axis ${laSensor.x}`);
  console.log(`Linear acceleration along the Y-axis ${laSensor.y}`);
  console.log(`Linear acceleration along the Z-axis ${laSensor.z}`);
});
laSensor.start();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}