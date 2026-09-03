---
title: "PannerNode: positionZ property"
short-title: positionZ
slug: Web/API/PannerNode/positionZ
page-type: web-api-instance-property
browser-compat: api.PannerNode.positionZ
---

{{ APIRef("Web Audio API") }}

ویژگی **`positionZ`** در رابط {{ domxref("PannerNode") }} مختصات Z موقعیت منبع صدا را در مختصات دکارتی سه‌بعدی مشخص می‌کند که با محور _عمق_ (عقب و جلوی شنونده) متناظر است. بردار کامل توسط موقعیت منبع صدا، که به صورت ({{domxref("PannerNode.positionX", "positionX")}}، {{domxref("PannerNode.positionY", "positionY")}}، `positionZ`) داده می‌شود، و جهت‌گیری منبع صدا (یعنی جهتی که منبع به آن سمت قرار دارد)، که به صورت ({{domxref("PannerNode.orientationX", "orientationX")}}، {{domxref("PannerNode.orientationY", "orientationY")}}، {{domxref("PannerNode.orientationZ", "orientationZ")}}) تعریف می‌شود، مشخص می‌گردد.

بسته به جهت‌داری صدا (که با استفاده از ویژگی‌های {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}}، {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} و {{domxref("PannerNode.coneOuterGain", "codeOuterGain")}} تنظیم می‌شود)، جهت‌گیری صدا ممکن است بلندی درک‌شده صدا را هنگام پخش تغییر دهد. اگر صدا به سمت شنونده باشد، بلندتر از حالتی خواهد بود که صدا از شنونده دور شود.

{{domxref("AudioParam")}} موجود در این ویژگی فقط خواندنی است؛ با این حال، همچنان می‌توانید مقدار این پارامتر را با اختصاص یک مقدار جدید به ویژگی {{domxref("AudioParam.value")}} آن تغییر دهید.

## مقدار

یک {{domxref("AudioParam")}} که `value` آن مختصات Z موقعیت منبع صدا را در مختصات دکارتی سه‌بعدی نشان می‌دهد.

## مثال‌ها

مثال زیر یک نوسان‌ساز را شروع می‌کند و آن را پس از ۱ ثانیه جلوی شنونده، پس از ۲ ثانیه پشت شنونده و پس از ۳ ثانیه به موقعیت شنونده بازمی‌گرداند. توجه داشته باشید که در این حالت، تغییر عمدتاً بر رنگ صدا (تیمبر) و بلندی درک‌شده صدا تأثیر می‌گذارد.

```js
const context = new AudioContext();

const osc = new OscillatorNode(context);
const panner = new PannerNode(context);
panner.panningModel = "HRTF";

panner.positionZ.setValueAtTime(1, context.currentTime + 1);
panner.positionZ.setValueAtTime(-1, context.currentTime + 2);
panner.positionZ.setValueAtTime(0, context.currentTime + 3);

osc.connect(panner).connect(context.destination);

osc.start(0);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضاسازی صدا در Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)
- {{domxref("PannerNode")}}