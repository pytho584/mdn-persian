---
title: "AudioEncoder: AudioEncoder() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/AudioEncoder"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: AudioEncoder() constructor"
short-title: AudioEncoder()
slug: Web/API/AudioEncoder/AudioEncoder
page-type: web-api-constructor
browser-compat: api.AudioEncoder.AudioEncoder
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

سازندهٔ **`AudioEncoder()`** یک شیء {{domxref("AudioEncoder")}} جدید با تابع بازخورد `init.output` ارائه‌شده به‌عنوان بازخورد خروجی، تابع بازخورد `init.error` به‌عنوان بازخورد خطا، و با {{domxref("AudioEncoder.state")}} تنظیم‌شده روی `"unconfigured"` ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new AudioEncoder(init)
```

### پارامترها

- `init`
  - : یک شیء شامل دو تابع بازخورد الزامی.
    - `output`
      - : یک تابع بازخورد که یک شیء {{domxref("EncodedAudioChunk")}} را به‌عنوان آرگومان اول و یک شیء فرادادهٔ اختیاری را به‌عنوان آرگومان دوم دریافت می‌کند. شیء فراداده یک عضو به نام `decoderConfig` دارد که مقدار آن یک شیء شامل موارد زیر است:
        - `codec`
          - : یک رشته شامل [یک رشتهٔ کدک معتبر](https://w3c.github.io/webcodecs/codec_registry.html#audio-codec-registry).
        - `sampleRate`
          - : یک عدد صحیح که تعداد نمونه‌های فریم در هر ثانیه را نشان می‌دهد.
        - `numberOfChannels`
          - : یک عدد صحیح که تعداد کانال‌های صوتی را نشان می‌دهد.
        - `description` {{optional_inline}}
          - : یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}} یا یک {{jsxref("DataView")}} شامل دنباله‌ای از بایت‌های مخصوص کدک که معمولاً به‌عنوان extradata شناخته می‌شوند.
    - `error`
      - : یک تابع بازخورد که یک شیء {{jsxref("Error")}} را به‌عنوان تنها آرگومان خود دریافت می‌کند.

## مثال‌ها

در مثال زیر، یک `AudioEncoder` با دو تابع بازخورد الزامی ایجاد می‌شود: یکی برای پردازش فریم خروجی و دیگری برای مدیریت خطاها.

```js
const audioEncoder = new AudioEncoder({
  output: processAudio,
  error: onEncoderError,
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}