---
title: "AudioBuffer: AudioBuffer() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBuffer/AudioBuffer"
translated_by: "n8n + AI"
---

---
title: "AudioBuffer: AudioBuffer() constructor"
short-title: AudioBuffer()
slug: Web/API/AudioBuffer/AudioBuffer
page-type: web-api-constructor
browser-compat: api.AudioBuffer.AudioBuffer
---

{{APIRef("Web Audio API")}}

سازنده **`AudioBuffer`** از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) یک شیء جدید {{domxref("AudioBuffer")}} ایجاد می‌کند.

## سینتکس

```js-nolint
new AudioBuffer(options)
```

### پارامترها

- `options`
  - : گزینه‌ها به شرح زیر هستند:
    - `length`
      - : اندازه بافر صوتی در فریم‌های نمونه. برای تعیین `length` مورد استفاده برای تعداد مشخصی ثانیه صدا، از `numSeconds * sampleRate` استفاده کنید.
    - `numberOfChannels`
      - : تعداد کانال‌های بافر. پیش‌فرض ۱ است و همه عوامل کاربر موظف‌اند حداقل ۳۲ کانال را پشتیبانی کنند.
    - `sampleRate`
      - : نرخ نمونه‌برداری بر حسب هرتز برای بافر. پیش‌فرض، نرخ نمونه‌برداری `context` مورد استفاده در ساخت این شیء است. عوامل کاربر موظف‌اند نرخ‌های نمونه‌برداری از ۸۰۰۰ هرتز تا ۹۶۰۰۰ هرتز را پشتیبانی کنند (اما مجازند فراتر از این محدوده نیز بروند).

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که یک یا چند گزینه منفی باشند یا به شکل دیگری مقدار نامعتبر داشته باشند (مانند `numberOfChannels` بالاتر از حد پشتیبانی‌شده، یا `sampleRate` خارج از محدوده اسمی).
- {{jsxref("RangeError")}}
  - : در صورتی پرتاب می‌شود که حافظه کافی برای تخصیص بافر موجود نباشد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}