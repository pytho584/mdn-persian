---
title: Magnetometer
slug: Web/API/Magnetometer
page-type: web-api-interface
status:
  - experimental
browser-compat: api.Magnetometer
---

{{securecontext_header}}{{APIRef("Sensor API")}}{{SeeCompatTable}}

رابطِ **`Magnetometer`** از [Sensor APIs](/en-US/docs/Web/API/Sensor_APIs) اطلاعاتی دربارهٔ میدان مغناطیسی ارائه می‌دهد که توسط سنسور مغناطیس‌سنج اصلی دستگاه شناسایی می‌شود.

برای استفاده از این سنسور، کاربر باید از طریق [Permissions API](/en-US/docs/Web/API/Permissions_API) به سنسور دستگاهِ `'magnetometer'` دسترسی بدهد. علاوه بر این، ممکن است این قابلیت توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) تنظیم‌شده روی سرور شما مسدود شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("Magnetometer.Magnetometer", "Magnetometer()")}} {{Experimental_Inline}}
  - : یک شیء جدید `Magnetometer` می‌سازد.

## ویژگی‌های نمونه

- {{domxref('Magnetometer.x')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک عدد double شامل میدان مغناطیسی اطراف محور x دستگاه را برمی‌گرداند.
- {{domxref('Magnetometer.y')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک عدد double شامل میدان مغناطیسی اطراف محور y دستگاه را برمی‌گرداند.
- {{domxref('Magnetometer.z')}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک عدد double شامل میدان مغناطیسی اطراف محور z دستگاه را برمی‌گرداند.

## متدهای نمونه

_`Magnetometer` متدهای خاص خود را ندارد؛ با این حال، متدهای رابط‌های والد خود، یعنی {{domxref("Sensor")}} و {{domxref("EventTarget")}}، را به ارث می‌برد._

## رویدادها

_`Magnetometer` رویدادهای خاص خود را ندارد؛ با این حال، رویدادهای رابط والد خود، یعنی {{domxref('Sensor')}}، را به ارث می‌برد._

## مثال

داده‌های سنسور مغناطیس‌سنج معمولاً در callback رویداد {{domxref('Sensor.reading_event', 'reading')}} خوانده می‌شوند. در مثال زیر، این کار شصت بار در ثانیه انجام می‌شود.

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