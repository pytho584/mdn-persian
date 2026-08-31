---
title: "AudioListener: positionZ property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/positionZ"
translated_by: "n8n + AI"
short-title: positionZ
slug: Web/API/AudioListener/positionZ
page-type: web-api-instance-property
browser-compat: api.AudioListener.positionZ
---

{{ APIRef("Web Audio API") }}

ویژگی فقط خواندنی `positionZ` از رابط {{ domxref("AudioListener") }} یک {{domxref("AudioParam")}} است که موقعیت z شنونده را در فضای دکارتی سه‌بعدی نشان می‌دهد.

> [!NOTE]
> این پارامتر زمانی که با یک {{domxref("PannerNode")}} که {{domxref("PannerNode.panningModel", "PannerNode")}} آن روی equalpower تنظیم شده است استفاده شود، [_a-rate_](/en-US/docs/Web/API/AudioParam#a-rate) است، در غیر این صورت [_k-rate_](/en-US/docs/Web/API/AudioParam#k-rate) است.

## مقدار

یک {{domxref("AudioParam")}}. مقدار پیش‌فرض آن 0 است و می‌تواند بین مثبت و منفی بی‌نهایت باشد.

## مثال‌ها

برای کد مثال، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)