---
title: "AudioListener: upZ property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/upZ"
translated_by: "n8n + AI"
---

---
title: "AudioListener: upZ property"
short-title: upZ
slug: Web/API/AudioListener/upZ
page-type: web-api-instance-property
browser-compat: api.AudioListener.upZ
---

{{ APIRef("Web Audio API") }}

ویژگی فقط‌خواندنی `upZ` از رابط {{ domxref("AudioListener") }} یک {{domxref("AudioParam")}} است که مقدار z از بردار جهت تعیین‌کننده جهت بالا که شنونده به آن اشاره می‌کند را نشان می‌دهد.

> [!NOTE]
> این پارامتر وقتی با یک {{domxref("PannerNode")}} استفاده می‌شود که {{domxref("PannerNode.panningModel", "PannerNode")}} آن روی equalpower تنظیم شده باشد، _a-rate_ است، در غیر این صورت _k-rate_ است.

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