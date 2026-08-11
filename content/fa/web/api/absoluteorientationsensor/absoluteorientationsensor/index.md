---
title: "AbsoluteOrientationSensor: AbsoluteOrientationSensor() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbsoluteOrientationSensor/AbsoluteOrientationSensor"
translated_by: "n8n + AI"
---

سازنده‌ی **`AbsoluteOrientationSensor()`** یک شیء جدید `AbsoluteOrientationSensor` ایجاد می‌کند که جهت فیزیکی دستگاه را نسبت به سیستم مختصات مرجع زمین توصیف می‌کند.

## Syntax

```js-nolint
new AbsoluteOrientationSensor()
new AbsoluteOrientationSensor(options)
```

### Parameters

- `options` (اختیاری)
  - : گزینه‌ها به صورت زیر هستند:
    - `frequency` (اختیاری)
      - : تعداد دفعات نمونه‌برداری در هر ثانیه که مطلوب است؛ به عبارتی تعداد فراخوانی رویداد `reading` در هر ثانیه. می‌توان از یک عدد صحیح یا اعشاری استفاده کرد؛ اعداد اعشاری برای فرکانس‌های کمتر از یک ثانیه به کار می‌روند. فرکانس واقعی خواندن وابسته به سخت‌افزار دستگاه است و ممکن است کمتر از مقدار درخواستی باشد.
    - `referenceFrame` (اختیاری)
      - : می‌تواند `'device'` یا `'screen'` باشد. مقدار پیش‌فرض `'device'` است.

## Specifications

## Browser compatibility

## همچنین ببینید

- رویداد `reading`