---
title: "AudioListener: positionX property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/positionX"
translated_by: "n8n + AI"
---

---
title: "AudioListener: positionX property"
short-title: positionX
slug: Web/API/AudioListener/positionX
page-type: web-api-instance-property
browser-compat: api.AudioListener.positionX
---

{{ APIRef("Web Audio API") }}

ویژگی فقطخواندنی `positionX` در رابط {{ domxref("AudioListener") }} یک {{domxref("AudioParam")}} است که موقعیت x شنونده را در فضای دکارتی سه‌بعدی نشان می‌دهد.

> [!NOTE]
> پارامتر وقتی با یک {{domxref("PannerNode")}} که {{domxref("PannerNode.panningModel", "PannerNode")}} آن روی equalpower تنظیم شده است استفاده می‌شود، [_a-rate_](/en-US/docs/Web/API/AudioParam#a-rate) است، یا در غیر این صورت [_k-rate_](/en-US/docs/Web/API/AudioParam#k-rate).

## مقدار

یک {{domxref("AudioParam")}}. مقدار پیش‌فرض آن ۰ است و می‌تواند در بازه‌ای از بی‌نهایت منفی تا بی‌نهایت مثبت قرار گیرد.

## نمونه‌ها

برای کد مثال، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)