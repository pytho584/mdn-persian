---
title: "Gyroscope"
---

---
title: Gyroscope
slug: Web/API/Gyroscope
page-type: web-api-interface
browser-compat: api.Gyroscope
---

{{securecontext_header}}{{APIRef("Sensor API")}}

رابط **`Gyroscope`** از [Sensor APIs](/en-US/docs/Web/API/Sensor_APIs) در هر بار خواندن، سرعت زاویه‌ای دستگاه را در هر سه محور فراهم می‌کند.

برای استفاده از این سنسور، کاربر باید از طریق [Permissions API](/en-US/docs/Web/API/Permissions_API) به سنسور دستگاه `'gyroscope'` مجوز بدهد. علاوه بر این، ممکن است این قابلیت توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) تنظیم‌شده روی سرور شما مسدود شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("Gyroscope.Gyroscope", "Gyroscope()")}}
  - : یک شیء `Gyroscope` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref('Gyroscope.x')}} {{ReadOnlyInline}}
  - : یک مقدار double برمی‌گرداند که شامل سرعت زاویه‌ای دستگاه در امتداد محور x دستگاه است.
- {{domxref('Gyroscope.y')}} {{ReadOnlyInline}}
  - : یک مقدار double برمی‌گرداند که شامل سرعت زاویه‌ای دستگاه در امتداد محور y دستگاه است.
- {{domxref('Gyroscope.z')}} {{ReadOnlyInline}}
  - : یک مقدار double برمی‌گرداند که شامل سرعت زاویه‌ای دستگاه در امتداد محور z دستگاه است.

## روش‌های نمونه

_`Gyroscope` روش‌های اختصاصی خود را ندارد. با این حال، روش‌هایی را از رابط‌های والد خود، یعنی {{domxref("Sensor")}} و {{domxref("EventTarget")}} به ارث می‌برد._

## رویدادها

_`Gyroscope` رویدادهای اختصاصی خود را ندارد. با این حال، رویدادهایی را از رابط والد خود، یعنی {{domxref('Sensor')}} به ارث می‌برد._

## مثال

ژیروسکوپ معمولاً در تابع بازخوانی رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شود. در مثال زیر، این کار شصت بار در ثانیه انجام می‌شود.

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