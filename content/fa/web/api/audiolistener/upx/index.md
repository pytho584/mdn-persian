---
title: "AudioListener: upX property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/upX"
translated_by: "n8n + AI"
---

---
title: "AudioListener: upX property"
short-title: upX
slug: Web/API/AudioListener/upX
page-type: web-api-instance-property
browser-compat: api.AudioListener.upX
---

{{ APIRef("Web Audio API") }}

ویژگی فقط‌خواندنی `upX` از رابط {{ domxref("AudioListener") }} یک {{domxref("AudioParam")}} است که مقدار x بردار جهت تعیین‌کننده جهت بالا بودن شنونده را نشان می‌دهد.

> [!NOTE]
> این پارامتر زمانی که با یک {{domxref("PannerNode")}} استفاده می‌شود که {{domxref("PannerNode.panningModel", "PannerNode")}} آن روی `equalpower` تنظیم شده است، به صورت _a-rate_ است، در غیر این صورت به صورت _k-rate_ است.

## مقدار

یک {{domxref("AudioParam")}}. مقدار پیش‌فرض آن 0 است و می‌تواند بین مثبت و منفی بی‌نهایت باشد.

## مثال‌ها

برای کد مثال دقیق‌تر به [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)