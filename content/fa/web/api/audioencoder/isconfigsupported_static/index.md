---
title: "AudioEncoder: isConfigSupported() static method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/isConfigSupported_static"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: isConfigSupported() static method"
short-title: isConfigSupported()
slug: Web/API/AudioEncoder/isConfigSupported_static
page-type: web-api-static-method
browser-compat: api.AudioEncoder.isConfigSupported_static
---

{{APIRef("WebCodecs API")}}{{SecureContext_Header}}{{AvailableInWorkers("window_and_dedicated")}}

متد استاتیک **`isConfigSupported()`** از رابط {{domxref("AudioEncoder")}} بررسی می‌کند که آیا پیکربندی داده‌شده پشتیبانی می‌شود یا خیر (یعنی آیا اشیاء {{domxref("AudioEncoder")}} می‌توانند با پیکربندی داده‌شده با موفقیت پیکربندی شوند).

## Syntax

```js-nolint
AudioEncoder.isConfigSupported(config)
```

### Parameters

- `config`
  - : شیء دیکشنری که توسط {{domxref("AudioEncoder.configure")}} پذیرفته می‌شود.

### Return value

یک {{jsxref("Promise")}} که با یک شیء حاوی اعضای زیر حل می‌شود:

- `supported`
  - : یک مقدار بولی که در صورت پشتیبانی پیکربندی داده‌شده توسط رمزگذار، `true` است.
- `config`
  - : یک کپی از پیکربندی داده‌شده با تمام فیلدهایی که توسط رمزگذار شناسایی شده‌اند.

### Exceptions

- {{jsxref("TypeError")}}
  - : در صورت نامعتبر بودن `config` ارائه‌شده پرتاب می‌شود؛ یعنی اگر مقادیر مورد نیاز را نداشته باشد (مانند فیلد خالی `codec`) یا مقادیر نامعتبر داشته باشد (مانند `sampleRate` منفی).

## Examples

مثال زیر بررسی می‌کند که آیا مرورگر از چندین کدک صوتی پشتیبانی می‌کند یا خیر.

```js
const codecs = ["mp4a.40.2", "mp3", "alaw", "ulaw"];
const configs = [];
for (const codec of codecs) {
  configs.push({
    codec,
    sampleRate: 48000,
    numberOfChannels: 1,
    not_supported_field: 123,
  });
}
for (const config of configs) {
  const support = await AudioEncoder.isConfigSupported(config);
  console.log(
    `AudioEncoder's config ${JSON.stringify(support.config)} support: ${
      support.supported
    }`,
  );
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}