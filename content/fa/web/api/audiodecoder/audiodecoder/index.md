---
title: "AudioDecoder: AudioDecoder() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/AudioDecoder"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: AudioDecoder() constructor"
short-title: AudioDecoder()
slug: Web/API/AudioDecoder/AudioDecoder
page-type: web-api-constructor
browser-compat: api.AudioDecoder.AudioDecoder
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

سازنده **`AudioDecoder()`** یک شیء جدید {{domxref("AudioDecoder")}} ایجاد می‌کند که در آن callback `init.output` به عنوان callback خروجی، callback `init.error` به عنوان callback خطا، و {{domxref("AudioDecoder.state")}} به `"unconfigured"` تنظیم شده است.

## نحو

```js-nolint
new AudioDecoder(init)
```

### پارامترها

- `init`
  - : یک شیء دیکشنری که شامل دو callback الزامی است.
    - `output`
      - : یک callback که یک آرگومان از نوع {{domxref("AudioData")}} به آن ارسال می‌شود.
    - `error`
      - : یک callback که یک آرگومان از خطای پرتاب شده به آن ارسال می‌شود.

## مثال‌ها

در مثال زیر، یک `AudioDecoder` با دو تابع callback الزامی ایجاد می‌شود، یکی برای پردازش قطعه رمزگشایی شده و دیگری برای مدیریت خطاها.

```js
const audioDecoder = new AudioDecoder({
  output: processAudio,
  error: onEncoderError,
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}