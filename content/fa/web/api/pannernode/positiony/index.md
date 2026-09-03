---
title: "PannerNode: positionY property"
short-title: positionY
slug: Web/API/PannerNode/positionY
page-type: web-api-instance-property
browser-compat: api.PannerNode.positionY
---

{{ APIRef("Web Audio API") }}

ویژگی **`positionY`** از رابط {{ domxref("PannerNode") }} مختصات Y موقعیت منبع صوتی را در فضای سه‌بعدی دکارتی مشخص می‌کند که با محور _عمودی_ (بالا-پایین) متناظر است. بردار کامل توسط موقعیت منبع صوتی، که به صورت ({{domxref("PannerNode.positionX", "positionX")}}, `positionY`, {{domxref("PannerNode.positionZ", "positionZ")}}) تعریف می‌شود، و جهت‌گیری منبع صوتی (یعنی جهتی که به آن سمت نشانه رفته است) که به صورت ({{domxref("PannerNode.orientationX", "orientationX")}}, {{domxref("PannerNode.orientationY", "orientationY")}}, {{domxref("PannerNode.orientationZ", "orientationZ")}}) تعریف می‌شود، مشخص می‌گردد.

بسته به جهت‌دار بودن صدا (که با استفاده از ویژگی‌های {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}}، {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} و {{domxref("PannerNode.coneOuterGain", "codeOuterGain")}} مشخص می‌شود)، جهت‌گیری صدا ممکن است بلندیِ درک‌شده صدا را در حین پخش تغییر دهد. اگر صدا به سمت شنونده نشانه رفته باشد، نسبت به حالتی که از شنونده دور شده باشد، بلندتر خواهد بود.

{{domxref("AudioParam")}} موجود در این ویژگی فقط خواندنی است؛ با این حال، شما می‌توانید با اختصاص یک مقدار جدید به ویژگی {{domxref("AudioParam.value")}} آن، مقدار پارامتر را تغییر دهید.

## مقدار

یک {{domxref("AudioParam")}} که `value` آن مختصات Y موقعیت منبع صوتی را در فضای سه‌بعدی دکارتی نشان می‌دهد.

## مثال‌ها

مثال زیر یک نوسان‌ساز (oscillator) را شروع کرده و آن را پس از ۱ ثانیه به بالای سر شنونده، پس از ۲ ثانیه به زیر پای شنونده و پس از ۳ ثانیه به مرکز برمی‌گرداند. توجه داشته باشید که در این مورد، تغییر عمدتاً بر تُن (timbre) نوسان‌ساز تأثیر می‌گذارد، زیرا یک موج سادهٔ مونو (تک‌کاناله) است.

```js
const context = new AudioContext();

const osc = new OscillatorNode(context);
const panner = new PannerNode(context);
panner.panningModel = "HRTF";

panner.positionY.setValueAtTime(1, context.currentTime + 1);
panner.positionY.setValueAtTime(-1, context.currentTime + 2);
panner.positionY.setValueAtTime(0, context.currentTime + 3);

osc.connect(panner).connect(context.destination);

osc.start(0);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضاسازی صدا در Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)
- {{domxref("PannerNode")}}