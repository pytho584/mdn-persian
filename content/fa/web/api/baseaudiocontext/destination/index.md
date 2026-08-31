---
title: "BaseAudioContext: destination property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/destination"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: destination property"
short-title: destination
slug: Web/API/BaseAudioContext/destination
page-type: web-api-instance-property
browser-compat: api.BaseAudioContext.destination
---

{{ APIRef("Web Audio API") }}

ویژگی `destination` از رابط {{ domxref("BaseAudioContext") }} یک {{ domxref("AudioDestinationNode") }} برمی‌گرداند که مقصد نهایی تمام صداها در این زمینه را نشان می‌دهد. این اغلب نمایانگر یک دستگاه واقعی رندر صدا، مانند بلندگوهای دستگاه شما است.

## مقدار

یک {{ domxref("AudioDestinationNode") }}.

## مثال‌ها

> [!NOTE]
> برای مثال‌ها/اطلاعات کاربردی کامل‌تر، دموی [Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) ما را ببینید (برای کد مرتبط، [app.js lines 108–193](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) را ببینید).

```js
const audioCtx = new AudioContext();
// Older webkit/blink browsers require a prefix

const oscillatorNode = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();

oscillatorNode.connect(gainNode);
gainNode.connect(audioCtx.destination);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)