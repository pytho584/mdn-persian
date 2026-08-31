---
title: "AudioProcessingEvent: AudioProcessingEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioProcessingEvent/AudioProcessingEvent"
translated_by: "n8n + AI"
---

---
title: "AudioProcessingEvent: AudioProcessingEvent() constructor"
short-title: AudioProcessingEvent()
slug: Web/API/AudioProcessingEvent/AudioProcessingEvent
page-type: web-api-constructor
status:
  - deprecated
browser-compat: api.AudioProcessingEvent.AudioProcessingEvent
---

{{APIRef("Web Audio API")}}{{Deprecated_header}}

سازنده **`AudioProcessingEvent()`** یک شیء جدید {{domxref("AudioProcessingEvent")}} ایجاد می‌کند.

> [!NOTE]
> معمولاً این سازنده مستقیماً توسط کد شما فراخوانی نمی‌شود، زیرا مرورگر خود این اشیاء را ایجاد کرده و آن‌ها را به کنترل‌کننده رویداد ارائه می‌دهد.

## سینتکس

```js-nolint
new AudioProcessingEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته با نام رویداد. این رشته به حروف بزرگ و کوچک حساس است و مرورگرها همیشه آن را روی `audioprocess` تنظیم می‌کنند.
- `options`
  - : یک شیء که دارای ویژگی‌های زیر است:
    - `playbackTime`
      - : یک عدد که نشان‌دهنده زمانی است که صدا پخش خواهد شد.
    - `inputBuffer`
      - : یک {{domxref("AudioBuffer")}} حاوی داده‌های صوتی ورودی.
    - `outputBuffer`
      - : یک {{domxref("AudioBuffer")}} که داده‌های صوتی خروجی در آن نوشته خواهد شد.

### مقدار بازگشتی

یک {{domxref("AudioProcessingEvent")}} جدید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("AudioProcessingEvent")}}
- {{domxref("ScriptProcessorNode")}}