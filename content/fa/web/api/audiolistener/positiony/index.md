---
title: "AudioListener: positionY property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/positionY"
short-title: positionY
slug: Web/API/AudioListener/positionY
page-type: web-api-instance-property
browser-compat: api.AudioListener.positionY
translated_by: "n8n + AI"
---

{{ APIRef("Web Audio API") }}

ویژگی فقط‌خواندنی `positionY` از رابط {{ domxref("AudioListener") }} یک {{domxref("AudioParam")}} است که موقعیت y شنونده را در فضای سه‌بعدی دکارتی نشان می‌دهد.

> [!NOTE]
> پارامتر زمانی که با یک {{domxref("PannerNode")}} که {{domxref("PannerNode.panningModel", "PannerNode")}} آن روی equalpower تنظیم شده است، [_a-rate_](/en-US/docs/Web/API/AudioParam#a-rate) است، در غیر این صورت [_k-rate_](/en-US/docs/Web/API/AudioParam#k-rate) است.

## مقدار

یک {{domxref("AudioParam")}}. مقدار پیش‌فرض آن 0 است و می‌تواند بین مثبت و منفی بی‌نهایت متغیر باشد.

## مثال‌ها

برای کد مثال، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)