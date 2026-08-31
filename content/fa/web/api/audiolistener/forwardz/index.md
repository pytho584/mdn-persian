---
title: "AudioListener: forwardZ property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/forwardZ"
translated_by: "n8n + AI"
---

---
title: "AudioListener: forwardZ property"
short-title: forwardZ
slug: Web/API/AudioListener/forwardZ
page-type: web-api-instance-property
browser-compat: api.AudioListener.forwardZ
---

{{ APIRef("Web Audio API") }}

ویژگی فقطخواندنی `forwardZ` از رابط {{ domxref("AudioListener") }} یک {{domxref("AudioParam")}} است که مقدار z بردار جهت را نشان می‌دهد و جهت رو به جلویی که شنونده به آن اشاره می‌کند را تعریف می‌کند.

> [!NOTE]
> پارامتر زمانی که با {{domxref("PannerNode")}} استفاده می‌شود که {{domxref("PannerNode.panningModel", "panningModel")}} آن روی equalpower تنظیم شده، به صورت _a-rate_ است، در غیر این صورت _k-rate_ است.

## مقدار

یک {{domxref("AudioParam")}}. مقدار پیش‌فرض آن -1 است و می‌تواند بین مثبت و منفی بی‌نهایت تغییر کند.

## مثال‌ها

برای کد مثال، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)