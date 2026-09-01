---
title: GravitySensor
slug: Web/API/GravitySensor
page-type: web-api-interface
browser-compat: api.GravitySensor
---

{{securecontext_header}}{{APIRef("Sensor API")}}

رابط **`GravitySensor`** از [APIهای حسگر](/en-US/docs/Web/API/Sensor_APIs) در هر بار خوانش، گرانش اعمال‌شده به دستگاه را در امتداد هر سه محور ارائه می‌دهد.

برای استفاده از این حسگر، کاربر باید از طریق [API مجوزها](/en-US/docs/Web/API/Permissions_API) به حسگر دستگاه `'accelerometer'` مجوز دهد. همچنین، ممکن است این ویژگی توسط [سیاست مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) تنظیم‌شده روی سرور شما مسدود شود.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("GravitySensor.GravitySensor", "GravitySensor()")}}
  - : یک شیء جدید `GravitySensor` ایجاد می‌کند.

## ویژگی‌های نمونه (Instance properties)

_ویژگی‌ها را از اجداد خود، یعنی {{domxref('Accelerometer')}}، {{domxref('Sensor')}} و {{domxref('EventTarget')}}، به ارث می‌برد._

## روش‌های نمونه (Instance methods)

_`GravitySensor` روش‌های خاص خود را ندارد. با این حال، روش‌ها را از رابط‌های والد خود، یعنی {{domxref("Sensor")}} و {{domxref("EventTarget")}}، به ارث می‌برد._

## رویدادها (Events)

_`GravitySensor` رویدادهای خاص خود را ندارد. با این حال، رویدادها را از رابط والد خود، یعنی {{domxref('Sensor')}}، به ارث می‌برد._

## مثال

گرانش معمولاً در callback رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر، این کار شصت بار در ثانیه انجام می‌شود.

```js
let gravitySensor = new GravitySensor({ frequency: 60 });

gravitySensor.addEventListener("reading", (e) => {
  console.log(`Gravity along the X-axis ${gravitySensor.x}`);
  console.log(`Gravity along the Y-axis ${gravitySensor.y}`);
  console.log(`Gravity along the Z-axis ${gravitySensor.z}`);
});

gravitySensor.start();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}