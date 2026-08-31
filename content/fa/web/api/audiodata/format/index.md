---
title: "AudioData: format property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioData/format"
translated_by: "n8n + AI"
short-title: format
slug: Web/API/AudioData/format
page-type: web-api-instance-property
browser-compat: api.AudioData.format
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

ویژگی فقط خواندنی **`format`** از رابط {{domxref("AudioData")}} قالب نمونه‌های شیء `AudioData` را برمی‌گرداند.

## مقدار

یک رشته. یکی از موارد زیر:

- `"u8"`
  - : نمونه‌های عدد صحیح بدون علامت 8 بیتی، در قالب درهم‌آمیخته.
- `"s16"`
  - : نمونه‌های عدد صحیح علامت‌دار 16 بیتی، در قالب درهم‌آمیخته.
- `"s32"`
  - : نمونه‌های عدد صحیح علامت‌دار 32 بیتی، در قالب درهم‌آمیخته.
- `"f32"`
  - : نمونه‌های ممیز شناور 32 بیتی، در قالب درهم‌آمیخته.
- `"u8-planar"`
  - : نمونه‌های عدد صحیح بدون علامت 8 بیتی، در قالب صفحه‌ای.
- `"s16-planar"`
  - : نمونه‌های عدد صحیح علامت‌دار 16 بیتی، در قالب صفحه‌ای.
- `"s32-planar"`
  - : نمونه‌های عدد صحیح علامت‌دار 32 بیتی، در قالب صفحه‌ای.
- `"f32-planar"`
  - : نمونه‌های ممیز شناور 32 بیتی، در قالب صفحه‌ای.

## مثال‌ها

مثال زیر مقدار `format` را در کنسول چاپ می‌کند.

```js
console.log(AudioData.format);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}