---
title: "PannerNode: orientationY property"
short-title: orientationY
slug: Web/API/PannerNode/orientationY
page-type: web-api-instance-property
browser-compat: api.PannerNode.orientationY
---

{{ APIRef("Web Audio API") }}

خاصیت **`orientationY`** از رابط {{ domxref("PannerNode") }} مؤلفهٔ Y (عمودی) جهت‌گیری منبع صوتی را در فضای مختصات دکارتی سه‌بعدی نشان می‌دهد.

بردار کامل توسط موقعیت منبع صوتی که به صورت ({{domxref("PannerNode.positionX", "positionX")}}, {{domxref("PannerNode.positionY", "positionY")}}, {{domxref("PannerNode.positionZ", "positionZ")}}) داده شده است، و جهت‌گیری منبع صوتی (یعنی جهتی که به آن سمت قرار دارد) که به صورت ({{domxref("PannerNode.orientationX", "orientationX")}}, `orientationY`, {{domxref("PannerNode.orientationZ", "orientationZ")}}) تعریف می‌شود.

بسته به جهت‌داری صدا (که با استفاده از ویژگی‌های {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}}، {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} و {{domxref("PannerNode.coneOuterGain", "coneOuterGain")}} مشخص می‌شود)، جهت‌گیری صدا ممکن است بلندی صدای در حال پخش را تغییر دهد. اگر صدا به سمت شنونده باشد، بلندتر از زمانی خواهد بود که صدا از شنونده دور شده باشد.

{{domxref("AudioParam")}} موجود در این خاصیت فقط خواندنی است؛ با این حال، می‌توانید با تخصیص یک مقدار جدید به خاصیت {{domxref("AudioParam.value")}} آن، مقدار پارامتر را تغییر دهید.

## مقدار

یک {{domxref("AudioParam")}} که `value` آن مؤلفهٔ Y جهت‌گیری منبع صوتی در فضای مختصات دکارتی سه‌بعدی است.

## مثال‌ها

برای کد نمونه‌ای که تأثیر تغییر پارامترهای جهت‌گیری {{domxref("PannerNode")}} را در ترکیب با {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}} و {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} بر بلندی صدا نشان می‌دهد، به [`PannerNode.orientationX`](/en-US/docs/Web/API/PannerNode/orientationX#example) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضایی‌سازی Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)
- {{domxref("PannerNode")}}