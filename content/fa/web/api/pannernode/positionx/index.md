---
title: "PannerNode: positionX property"
short-title: positionX
slug: Web/API/PannerNode/positionX
page-type: web-api-instance-property
browser-compat: api.PannerNode.positionX
---

{{ APIRef("Web Audio API") }}

ویژگی **`positionX`** از رابط {{ domxref("PannerNode")}} مختصات X موقعیت منبع صوتی را در مختصات دکارتی سه‌بعدی مشخص می‌کند که با محور *افقی* (چپ-راست) متناظر است.

بردار کامل توسط موقعیت منبع صوتی، که به صورت (`positionX`, {{domxref("PannerNode.positionY", "positionY")}}, {{domxref("PannerNode.positionZ", "positionZ")}}) داده می‌شود، و جهت‌گیری منبع صوتی (یعنی جهتی که به آن رو می‌کند)، که به صورت ({{domxref("PannerNode.orientationX", "orientationX")}}, {{domxref("PannerNode.orientationY", "orientationY")}}, {{domxref("PannerNode.orientationZ", "orientationZ")}}) داده می‌شود، تعریف می‌شود.

بسته به جهت‌داری صدا (همانطور که با استفاده از ویژگی‌های {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}}، {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} و {{domxref("PannerNode.coneOuterGain", "codeOuterGain")}} مشخص می‌شود)، جهت‌گیری صدا ممکن است بلندی درک‌شده صدا را در حین پخش تغییر دهد. اگر صدا به سمت شنونده باشد، بلندتر از حالتی خواهد بود که صدا از شنونده دور باشد.

{{domxref("AudioParam")}} موجود در این ویژگی فقط‌خواندنی است؛ با این حال، همچنان می‌توانید مقدار پارامتر را با تخصیص دادن یک مقدار جدید به ویژگی {{domxref("AudioParam.value")}} تغییر دهید.

## مقدار

یک {{domxref("AudioParam")}} که `value` آن مختصات X موقعیت منبع صوتی در مختصات دکارتی سه‌بعدی است. مقدار پیش‌فرض 0 است.

## مثال‌ها

مثال زیر یک نوسان‌ساز (oscillator) را راه می‌اندازد و آن را پس از ۱ ثانیه به چپ، پس از ۲ ثانیه به راست، و پس از ۳ ثانیه به مرکز می‌برد.

```js
const context = new AudioContext();

const osc = new OscillatorNode(context);
const panner = new PannerNode(context);

panner.positionX.setValueAtTime(-1, context.currentTime + 1);
panner.positionX.setValueAtTime(1, context.currentTime + 2);
panner.positionX.setValueAtTime(0, context.currentTime + 3);

osc.connect(panner).connect(context.destination);

osc.start(0);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضاسازی Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)
- {{domxref("PannerNode")}}