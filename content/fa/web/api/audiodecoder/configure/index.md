---
title: "AudioDecoder: configure() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDecoder/configure"
translated_by: "n8n + AI"
---

---
title: "AudioDecoder: configure() method"
short-title: configure()
slug: Web/API/AudioDecoder/configure
page-type: web-api-instance-method
browser-compat: api.AudioDecoder.configure
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متود **`configure()`** از رابط {{domxref("AudioDecoder")}} یک پیام کنترلی را برای پیکربندی رمزگشای صوتی جهت رمزگشایی بخش‌ها (chunks) در صف قرار می‌دهد.

## Syntax

```js-nolint
configure(config)
```

### پارامترها

- `config`
  - : یک شیء فرهنگ لغت (dictionary) حاوی اعضای زیر:
    - `codec`
      - : یک رشته شامل یک [رشته کدک معتبر](https://w3c.github.io/webcodecs/codec_registry.html#audio-codec-registry). برای جزئیات ساختار رشته کدک به [پارامتر "codecs"](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter#codec_options_by_container) مراجعه کنید.
    - `sampleRate`
      - : یک عدد صحیح که تعداد نمونه‌های فریم در ثانیه را نشان می‌دهد.
    - `numberOfChannels`
      - : یک عدد صحیح که تعداد کانال‌های صوتی را نشان می‌دهد.
    - `description` {{optional_inline}}
      - : یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}} یا {{jsxref("DataView")}} حاوی دنباله‌ای از بایت‌های خاص کدک که معمولاً به عنوان extradata شناخته می‌شود.

> [!NOTE]
> ثبت‌ها در [ثبت‌نامه کدک‌های WebCodecs](https://w3c.github.io/webcodecs/codec_registry.html#audio-codec-registry) به یک مشخصه (specification) پیوند می‌خورند که جزئیات نحوه و زمان پر کردن عضو اختیاری `description` را توضیح می‌دهد.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر `config` ارائه‌شده نامعتبر باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("AudioDecoder.state","state")}} برابر با `"closed"` باشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر `config` ارائه‌شده معتبر باشد اما عامل کاربر (user agent) نتواند کدکی برای رمزگشایی این پروفایل فراهم کند، پرتاب می‌شود.

## مثال‌ها

مثال زیر `audioDecoder` را با کدک `opus` پیکربندی می‌کند.

```js
audioDecoder.configure({
  codec: "opus",
  sampleRate: 44100,
  numberOfChannels: 2,
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}