---
title: "AudioListener: upY property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/upY"
translated_by: "n8n + AI"
---

---
title: "AudioListener: upY property"
short-title: upY
slug: Web/API/AudioListener/upY
page-type: web-api-instance-property
browser-compat: api.AudioListener.upY
---

{{ APIRef("Web Audio API") }}

ویژگی فقط‌خواندنی `upY` از رابط {{ domxref("AudioListener") }} یک {{domxref("AudioParam")}} است که مقدار y بردار جهتِ تعریف‌کنندهٔ جهت بالا را نشان می‌دهد؛ جهتی که شنونده به آن سمت اشاره می‌کند.

> [!NOTE]
> این پارامتر وقتی با {{domxref("PannerNode")}} استفاده شود که {{domxref("PannerNode.panningModel", "PannerNode")}} آن روی equalpower تنظیم شده باشد، از نوع _a-rate_ است، در غیر این صورت _k-rate_ است.

## مقدار

یک {{domxref("AudioParam")}}. مقدار پیش‌فرض آن 1 است و می‌تواند بین مثبت و منفی بی‌نهایت تغییر کند.

## مثال‌ها

برای کد مثال، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)