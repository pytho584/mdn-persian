---
title: "Magnetometer: Magnetometer() constructor"
---

---
title: "Magnetometer: Magnetometer() constructor"
short-title: Magnetometer()
slug: Web/API/Magnetometer/Magnetometer
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.Magnetometer.Magnetometer
---

{{securecontext_header}}{{APIRef("Sensor API")}}{{SeeCompatTable}}

سازندهٔ **`Magnetometer()`** یک شیء جدید از {{domxref("Magnetometer")}} می‌سازد که اطلاعات میدان مغناطیسیِ شناسایی‌شده توسط حسگر اصلی مغناطیس‌سنج دستگاه را ارائه می‌دهد.

## نحو

```js-nolint
new Magnetometer()
new Magnetometer(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : گزینه‌ها به شرح زیر هستند.
    - `frequency` {{optional_inline}}
      - : تعداد دفعات موردنظر برای نمونه‌برداری در هر ثانیه، یعنی تعداد دفعاتی در هر
        ثانیه که رویداد {{domxref('sensor.reading_event', 'reading')}} فراخوانی می‌شود. می‌توان
        از عدد صحیح یا اعشاری استفاده کرد؛ مورد دوم برای فرکانس‌های کمتر از یک ثانیه
        به کار می‌رود. فرکانس واقعی خواندن به سخت‌افزار دستگاه بستگی دارد و در نتیجه
        ممکن است کمتر از مقدار درخواستی باشد.
    - `referenceFrame` {{optional_inline}}
      - : یکی از مقادیر `'device'` یا
        `'screen'`. مقدار پیش‌فرض `'device'` است.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) (سیاست مجوزها) مسدود شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رویداد {{domxref('sensor.reading_event', 'reading')}}