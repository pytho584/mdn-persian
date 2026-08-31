---
title: "BaseAudioContext: listener property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/listener"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: listener property"
short-title: listener
slug: Web/API/BaseAudioContext/listener
page-type: web-api-instance-property
browser-compat: api.BaseAudioContext.listener
---

{{ APIRef("Web Audio API") }}

ویژگی `listener` از رابط {{ domxref("BaseAudioContext") }} یک شیء {{ domxref("AudioListener") }} را برمی‌گرداند که سپس می‌تواند برای پیاده‌سازی فضایی‌سازی صوتی سه‌بعدی استفاده شود.

## مقدار

یک شیء {{ domxref("AudioListener") }}.

## مثال‌ها

> [!NOTE]
> برای یک مثال کامل از فضایی‌سازی صوتی Web Audio، دموی [panner-node](https://github.com/mdn/webaudio-examples/tree/main/panner-node) ما را ببینید.

```js
const audioCtx = new AudioContext();
// Older webkit/blink browsers require a prefix

// …

const myListener = audioCtx.listener;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)