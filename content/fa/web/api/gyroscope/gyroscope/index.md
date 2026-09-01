---
title: "Gyroscope: Gyroscope() constructor"
short-title: Gyroscope()
slug: Web/API/Gyroscope/Gyroscope
page-type: web-api-constructor
browser-compat: api.Gyroscope.Gyroscope
---

{{securecontext_header}}{{APIRef("Sensor API")}}

سازندهی **`Gyroscope()`** یک شیء جدید {{domxref("Gyroscope")}} می‌سازد که در هر بار اندازه‌گیری، سرعت زاویه‌ای دستگاه را در هر سه محور فراهم می‌کند.

## سینتکس

```js-nolint
new Gyroscope()
new Gyroscope(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : گزینه‌ها به شرح زیر هستند:
    - `frequency` {{optional_inline}}
      - : تعداد دفعات مطلوب نمونه‌برداری در هر ثانیه؛ یعنی تعداد دفعاتی که رویداد {{domxref('sensor.reading_event', 'reading')}} در هر ثانیه فراخوانی می‌شود. می‌توانید از عدد صحیح یا اعشاری استفاده کنید؛ نوع اعشاری برای فرکانس‌های کمتر از یک ثانیه به کار می‌رود. فرکانس واقعی خواندن به سخت‌افزار دستگاه بستگی دارد و بنابراین ممکن است کمتر از مقدار درخواستی باشد.
    - `referenceFrame` {{optional_inline}}
      - : یا `'device'` یا `'screen'`. مقدار پیش‌فرض `'device'` است.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref('sensor.reading_event', 'reading')}}