---
title: "PannerNode: coneOuterAngle property"
short-title: coneOuterAngle
slug: Web/API/PannerNode/coneOuterAngle
page-type: web-api-instance-property
browser-compat: api.PannerNode.coneOuterAngle
---

{{ APIRef("Web Audio API") }}

ویژگی `coneOuterAngle` از رابط {{ domxref("PannerNode") }} یک مقدار double است که زاویه (بر حسب درجه) مخروطی را مشخص می‌کند که خارج از آن، حجم صدا با یک مقدار ثابت (که توسط ویژگی {{domxref("PannerNode.coneOuterGain","coneOuterGain")}} تعریف شده است) کاهش می‌یابد.

مقدار پیش‌فرض ویژگی `coneOuterAngle` برابر `0` است.

## مقدار

یک مقدار double.

## مثال‌ها

برای مشاهدهٔ کد مثالی که تأثیر تغییر پارامترهای جهت‌گیری {{domxref("PannerNode")}} را به همراه {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}} و `coneOuterAngle` بر حجم صدا نشان می‌دهد، به [`PannerNode.orientationX`](/en-US/docs/Web/API/PannerNode/orientationX#example) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضایی‌سازی صدا در Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)