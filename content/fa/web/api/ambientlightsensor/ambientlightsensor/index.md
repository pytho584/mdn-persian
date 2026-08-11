---
title: "AmbientLightSensor: AmbientLightSensor() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AmbientLightSensor/AmbientLightSensor"
translated_by: "n8n + AI"
---

> **توجه:** این API فقط در یک بستر امن (Secure Context) در دسترس است و در مرحله آزمایشی قرار دارد.

سازنده `AmbientLightSensor()` یک شیء جدید `AmbientLightSensor` می‌سازد که میزان نور فعلی یا شدت روشنایی نور محیطی اطراف دستگاه میزبان را برمی‌گرداند.

## سینتکس

```js-nolint
new AmbientLightSensor()
new AmbientLightSensor(options)
```

### پارامترها

- `options` (اختیاری)
  - : در حال حاضر تنها یک گزینه پشتیبانی می‌شود:
    - `frequency` (اختیاری)
      - : تعداد دفعات مورد نظر در هر ثانیه که یک نمونه باید گرفته شود؛ به عبارت دیگر، تعداد دفعاتی که رویداد `reading` در هر ثانیه فراخوانی می‌شود. می‌توان از یک عدد صحیح یا اعشاری استفاده کرد که مورد دوم برای فرکانس‌های کمتر از یک ثانیه کاربرد دارد. فرکانس واقعی خواندن به سخت‌افزار دستگاه بستگی دارد و ممکن است کمتر از مقدار درخواستی باشد.

### استثناها

- `SecurityError` (از نوع `DOMException`)
  - : استفاده از این ویژگی توسط خط‌مشی مجوزها ([Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)) مسدود شده است.

## همچنین ببینید

- رویداد `reading`