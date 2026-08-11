---
title: "Accelerometer: Accelerometer() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Accelerometer/Accelerometer"
translated_by: "n8n + AI"
---

# Accelerometer: سازنده `Accelerometer()`

سازنده **`Accelerometer()`** یک شیء جدید `Accelerometer` ایجاد می‌کند که شتاب دستگاه را در امتداد هر سه محور در لحظه خواندن برمی‌گرداند.

## نحو

```js-nolint
new Accelerometer()
new Accelerometer(options)
```

### پارامترها

- `options` (اختیاری)
  - : گزینه‌ها به شرح زیر است:
    - `frequency` (اختیاری)
      - : تعداد دفعات درخواستی برای نمونه‌برداری در هر ثانیه، به این معنی که رویداد `reading` چند بار در ثانیه فراخوانی می‌شود. می‌توان از عدد صحیح یا اعشاری استفاده کرد (اعداد اعشاری برای فرکانس‌های کمتر از یک ثانیه). فرکانس واقعی خواندن به سخت‌افزار دستگاه بستگی دارد و ممکن است کمتر از مقدار درخواستی باشد.
    - `referenceFrame` (اختیاری)
      - : یکی از دو مقدار `'device'` یا `'screen'`. پیش‌فرض `'device'` است.

### استثناها

- `SecurityError` (از نوع `DOMException`)
  - : استفاده از این ویژگی توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.

## همچنین ببینید

- رویداد `reading`