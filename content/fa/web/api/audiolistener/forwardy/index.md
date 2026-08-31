---
title: "AudioListener: forwardY property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/forwardY"
translated_by: "n8n + AI"
short-title: forwardY
slug: Web/API/AudioListener/forwardY
page-type: web-api-instance-property
browser-compat: api.AudioListener.forwardY
---

{{ APIRef("Web Audio API") }}

ویژگی فقط خواندنی `forwardY` از رابط {{ domxref("AudioListener") }} یک {{domxref("AudioParam")}} است که مقدار y بردار جهت تعریف‌کننده جهت رو به جلویی که شنونده به آن اشاره می‌کند را نشان می‌دهد.

> [!NOTE]
> زمانی که این پارامتر با یک {{domxref("PannerNode")}} که {{domxref("PannerNode.panningModel", "panningModel")}} آن روی equalpower تنظیم شده استفاده شود، _a-rate_ است، در غیر این صورت _k-rate_ است.

## مقدار

یک {{domxref("AudioParam")}}. مقدار پیش‌فرض آن 0 است، و می‌تواند بین مثبت و منفی بی‌نهایت متغیر باشد.

## مثال‌ها

برای کد مثال به [BaseAudioContext.createPanner()](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)