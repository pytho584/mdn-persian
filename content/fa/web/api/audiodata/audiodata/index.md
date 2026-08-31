---
title: "AudioData: AudioData() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioData/AudioData"
translated_by: "n8n + AI"
---

---
title: "AudioData: AudioData() constructor"
short-title: AudioData()
slug: Web/API/AudioData/AudioData
page-type: web-api-constructor
browser-compat: api.AudioData.AudioData
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

سازنده‌ی **`AudioData()`** یک شیء جدید {{domxref("AudioData")}} می‌سازد که یک نمونه صوتی جداگانه را نشان می‌دهد.

## نحو

```js-nolint
new AudioData(init)
```

## پارامترها

- `init`
  - : یک شیء شامل موارد زیر:
    - `format`
      - : یکی از:
        - "u8"
        - "s16"
        - "s32"
        - "f32"
        - "u8-planar"
        - "s16-planar"
        - "s32-planar"
        - "f32-planar"
    - `sampleRate`
      - : یک عدد اعشاری شامل نرخ نمونه‌برداری بر حسب هرتز.
    - `numberOfFrames`
      - : یک عدد صحیح شامل تعداد فریم‌ها در این نمونه.
    - `numberOfChannels`
      - : یک عدد صحیح شامل تعداد کانال‌ها در این نمونه.
    - `timestamp`
      - : یک عدد صحیح که زمان داده را بر حسب میکروثانیه نشان می‌دهد.
    - `data`
      - : یک آرایه تایپ‌شده از داده‌های صوتی برای این نمونه.
    - `transfer`
      - : آرایه‌ای از {{jsxref("ArrayBuffer")}}ها که `AudioData` آن‌ها را جدا کرده و مالکیتشان را بر عهده می‌گیرد. اگر آرایه شامل {{jsxref("ArrayBuffer")}} پشتیبان `data` باشد، `AudioData` مستقیماً از آن بافر استفاده می‌کند به جای کپی کردن از آن.

## استثناها

- {{jsxref("TypeError")}}
  - : در صورتی که `init` در قالبی نادرست باشد پرتاب می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}