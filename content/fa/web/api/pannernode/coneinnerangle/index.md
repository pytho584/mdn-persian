---
title: "PannerNode: coneInnerAngle property"
short-title: coneInnerAngle
slug: Web/API/PannerNode/coneInnerAngle
page-type: web-api-instance-property
browser-compat: api.PannerNode.coneInnerAngle
---

{{ APIRef("Web Audio API") }}

خاصیت `coneInnerAngle` از رابط {{ domxref("PannerNode") }} یک مقدار اعشاری (double) است که زاویه (بر حسب درجه) یک مخروط را مشخص می‌کند؛ درون این مخروط هیچ کاهش حجمی رخ نخواهد داد.

مقدار پیش‌فرض خاصیت `coneInnerAngle` برابر `360` است که برای یک منبع غیرجهت‌دار مناسب می‌باشد.

## مقدار

یک عدد اعشاری (double).

## مثال‌ها

برای مشاهده کد نمونه‌ای که تأثیر تغییر پارامترهای جهت‌گیری {{domxref("PannerNode")}} را در ترکیب با `coneInnerAngle` و {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} بر روی حجم صدا نشان می‌دهد، به [`PannerNode.orientationX`](/en-US/docs/Web/API/PannerNode/orientationX#example) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضاسازی صوتی Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)