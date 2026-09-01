---
title: "GainNode: gain property"
short-title: gain
slug: Web/API/GainNode/gain
page-type: web-api-instance-property
browser-compat: api.GainNode.gain
---

{{ APIRef("Web Audio API") }}

ویژگی `gain` از رابط {{ domxref("GainNode") }} یک {{domxref("AudioParam")}} با نرخ [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) است که میزان بهره (gain) اعمال‌شده را نشان می‌دهد.

## مقدار

یک {{domxref("AudioParam")}}.

> [!NOTE]
> اگرچه `AudioParam` بازگشتی فقط‌خواندنی است، مقداری که نشان می‌دهد فقط‌خواندنی نیست.

## مثال‌ها

برای نمونه‌کد نحوه استفاده از `AudioContext` برای ایجاد یک `GainNode` که سپس با تغییر مقدار ویژگی gain برای قطع و وصل کردن صدا استفاده می‌شود، به [`BaseAudioContext.createGain()`](/en-US/docs/Web/API/BaseAudioContext/createGain#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)