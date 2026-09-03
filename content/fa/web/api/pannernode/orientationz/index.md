---
title: "PannerNode: orientationZ property"
---

---
title: "PannerNode: orientationZ property"
short-title: orientationZ
slug: Web/API/PannerNode/orientationZ
page-type: web-api-instance-property
browser-compat: api.PannerNode.orientationZ
---

{{ APIRef("Web Audio API") }}

ویژگی **`orientationZ`** از رابط {{ domxref("PannerNode") }} مؤلفهٔ Z (عمق) جهت‌گیری منبع صوتی را در فضای مختصات دکارتی سه‌بعدی نشان می‌دهد.

بردار کامل توسط موقعیت منبع صوتی، که به صورت ({{domxref("PannerNode.positionX", "positionX")}}, {{domxref("PannerNode.positionY", "positionY")}}, {{domxref("PannerNode.positionZ", "positionZ")}}) داده می‌شود، و جهت‌گیری منبع صوتی (یعنی جهتی که به آن روبرو است)، که به صورت ({{domxref("PannerNode.orientationX", "orientationX")}}, {{domxref("PannerNode.orientationY", "orientationY")}}, `orientationZ`) داده می‌شود، تعریف می‌گردد.

بسته به جهت‌دار بودن صدا (که با استفاده از ویژگی‌های {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}}، {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} و {{domxref("PannerNode.coneOuterGain", "coneOuterGain")}} مشخص می‌شود)، جهت‌گیری صدا ممکن است بلندی درک‌شدهٔ صدا را هنگام پخش تغییر دهد. اگر صدا به سمت شنونده باشد، بلندتر از حالتی خواهد بود که صدا از شنونده دور می‌شود.

{{domxref("AudioParam")}} موجود در این ویژگی فقط‌خواندنی است؛ با این حال، می‌توانید مقدار پارامتر را با اختصاص یک مقدار جدید به ویژگی {{domxref("AudioParam.value")}} تغییر دهید.

## مقدار

یک {{domxref("AudioParam")}} که `value` آن مؤلفهٔ Z جهت‌گیری منبع صوتی در فضای مختصات دکارتی سه‌بعدی است.

## مثال

برای مشاهدهٔ کد مثال که تأثیر تغییر پارامترهای جهت‌گیری {{domxref("PannerNode")}} بر بلندی صدا را در ترکیب با {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}} و {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} نشان می‌دهد، به [`PannerNode.orientationX`](/en-US/docs/Web/API/PannerNode/orientationX#example) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضاسازی Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)
- {{domxref("PannerNode")}}