---
title: "LinearAccelerationSensor: LinearAccelerationSensor() constructor"
short-title: LinearAccelerationSensor()
slug: Web/API/LinearAccelerationSensor/LinearAccelerationSensor
page-type: web-api-constructor
browser-compat: api.LinearAccelerationSensor.LinearAccelerationSensor
---

{{securecontext_header}}{{APIRef("Sensor API")}}

سازندهٔ **`LinearAccelerationSensor()`** یک شیء جدید {{domxref("LinearAccelerationSensor")}} می‌سازد که در هر بار خوانش، شتاب وارد بر دستگاه را در هر سه محور، بدون احتساب گرانش، فراهم می‌کند.

## نحو

```js-nolint
new LinearAccelerationSensor()
new LinearAccelerationSensor(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : گزینه‌ها به شرح زیر هستند:
    - `frequency` {{optional_inline}}
      - : تعداد دفعات مطلوب در هر ثانیه برای نمونه‌برداری، یعنی تعداد دفعاتی در هر ثانیه که رویداد {{domxref('sensor.reading_event', 'reading')}} فراخوانی می‌شود. می‌توان از عدد صحیح یا اعشاری استفاده کرد؛ عدد اعشاری برای فرکانس‌های کمتر از یک ثانیه استفاده می‌شود. فرکانس واقعی خوانش به سخت‌افزار دستگاه بستگی دارد و در نتیجه ممکن است کمتر از مقدار درخواستی باشد.
    - `referenceFrame` {{optional_inline}}
      - : یکی از مقادیر `'device'` یا `'screen'`. مقدار پیش‌فرض `'device'` است.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط [خط‌مشی مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- رویداد {{domxref('sensor.reading_event', 'reading')}}