---
title: "خاصیت orientationX از PannerNode"
short-title: orientationX
slug: Web/API/PannerNode/orientationX
page-type: web-api-instance-property
browser-compat: api.PannerNode.orientationX
---

{{ APIRef("Web Audio API") }}

خاصیت **`orientationX`** از رابط {{domxref("PannerNode")}}، مؤلفه X (افقی) جهتی را مشخص می‌کند که منبع صدا به آن سمت است، در یک فضای مختصات دکارتی سه‌بعدی.

بردار کامل با موقعیت منبع صدا، یعنی ({{domxref("PannerNode.positionX", "positionX")}}، {{domxref("PannerNode.positionY", "positionY")}}، {{domxref("PannerNode.positionZ", "positionZ")}}) و جهت منبع صدا (جهتی که به آن سمت است) یعنی (`orientationX`، {{domxref("PannerNode.orientationY", "orientationY")}}، {{domxref("PannerNode.orientationZ", "orientationZ")}}) تعریف می‌شود.

بسته به جهت‌داری صدا (که با استفاده از ویژگی‌های {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}}، {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} و {{domxref("PannerNode.coneOuterGain", "coneOuterGain")}} مشخص می‌شود)، جهت صدا ممکن است بلندی صدای درک شده را در حین پخش تغییر دهد. اگر صدا به سمت شنونده باشد، بلندتر از حالتی خواهد بود که از شنونده دور شود.

{{domxref("AudioParam")}} موجود در این خاصیت فقط خواندنی است؛ اما می‌توانید با اختصاص یک مقدار جدید به خاصیت {{domxref("AudioParam.value")}} آن، مقدار پارامتر را تغییر دهید.

## مقدار

یک {{domxref("AudioParam")}} که `value` آن مؤلفه X جهتی است که منبع صدا به آن سمت است، در فضای مختصات دکارتی سه‌بعدی.

## مثال

در این مثال، نحوه تأثیر تغییر پارامترهای جهت یک {{domxref("PannerNode")}} در ترکیب با {{domxref("PannerNode.coneInnerAngle", "coneInnerAngle")}} و {{domxref("PannerNode.coneOuterAngle", "coneOuterAngle")}} بر بلندی صدا را نشان می‌دهیم. برای کمک به تجسم نحوه تأثیر بردار جهت، می‌توانیم از [قانون دست راست](https://en.wikipedia.org/wiki/Right-hand_rule) استفاده کنیم:

![این نمودار نحوه تأثیر بردارهای جهت PannerNode بر جهت مخروط صدا را نشان می‌دهد.](pannernode-orientation.png)

ابتدا، یک تابع کمکی برای محاسبه _بردار جهت_ خود می‌نویسیم. مؤلفه‌های X و Z همیشه با زاویه ۹۰ درجه نسبت به یکدیگر هستند، بنابراین می‌توانیم از توابع سینوس و کسینوس استفاده کنیم که به همان میزان بر حسب رادیان偏移 دارند. با این حال، معمولاً این بدان معناست که {{ domxref("PannerNode") }} در چرخش ۰ درجه به **سمت چپ** شنونده اشاره می‌کند – زیرا `x = cos(0) = 1` و `z = sin(0) = 0`. مفیدتر است که زاویه را با ۹۰- درجه偏移 دهیم، که باعث می‌شود {{domxref("PannerNode")}} در چرخش ۰ درجه **مستقیماً به سمت شنونده** اشاره کند.

```js
// این تابع مقدار چرخش حول محور Y را
// (یعنی چرخش در 'صفحه افقی') به یک بردار جهت تبدیل می‌کند
const yRotationToVector = (degrees) => {
  // تبدیل درجه به رادیان و offset زاویه به طوری که ۰ به سمت شنونده باشد
  const radians = (degrees - 90) * (Math.PI / 180);
  // استفاده از کسینوس و سینوس در اینجا تضمین می‌کند که خروجی‌ها همیشه نرمال شده هستند
  // یعنی بین ۱- و ۱ قرار دارند
  const x = Math.cos(radians);
  const z = Math.sin(radians);

  // مؤلفه Y را به صورت ثابت ۰ قرار می‌دهیم، زیرا Y محور چرخش است
  return [x, 0, z];
};
```

اکنون می‌توانیم {{ domxref("AudioContext") }}، یک نوسان‌ساز و یک {{domxref("PannerNode")}} ایجاد کنیم:

```js
const context = new AudioContext();

const osc = new OscillatorNode(context);
osc.type = "sawtooth";

const panner = new PannerNode(context);
panner.panningModel = "HRTF";
```

سپس، _مخروط_ صدای فضایی‌سازی شده خود را تنظیم می‌کنیم و ناحیه‌ای که در آن صدا قابل شنیدن است را مشخص می‌کنیم:

```js
// این مقدار اندازه ناحیه‌ای را تعیین می‌کند که در آن بلندی صدا ثابت است
// اگر coneInnerAngle === 30 باشد، به این معنی است که وقتی صدا حداکثر ۱۵ (۳۰/۲) درجه به هر طرف بچرخد، بلندی صدا تغییر نمی‌کند
panner.coneInnerAngle = 30;
// این مقدار اندازه ناحیه‌ای را تعیین می‌کند که در آن بلندی صدا به تدریج کاهش می‌یابد
// اگر coneOuterAngle === 45 و coneInnerAngle === 30 باشد، به این معنی است که وقتی صدا بین ۱۵ (۳۰/۲) و ۲۲٫۵ (۴۵/۲) درجه به هر طرف بچرخد، بلندی صدا به تدریج کاهش می‌یابد
panner.coneOuterAngle = 45;
// این مقدار بلندی صدای خارج از هر دو مخروط داخلی و خارجی را تعیین می‌کند
// تنظیم آن به 0 به این معنی است که هیچ صدایی وجود ندارد، بنابراین می‌توانیم به وضوح بشنویم که از مخروط خارج می‌شویم
// 0 همچنین مقدار پیش‌فرض است
panner.coneOuterGain = 0;
// افزایش موقعیت Z برای اطمینان از تأثیر مخروط
// (در غیر این صورت صدا در همان موقعیت شنونده قرار دارد)
panner.positionZ.setValueAtTime(1, context.currentTime);
```

پس از تنظیم {{ domxref("PannerNode") }}، اکنون می‌توانیم برخی به‌روزرسانی‌ها را برای چرخش حول محور Y آن برنامه‌ریزی کنیم:

```js
// محاسبه بردار برای عدم چرخش
// این بدان معناست که صدا با بلندی کامل پخش می‌شود
const [x1, y1, z1] = yRotationToVector(0);
// برنامه‌ریزی بردار عدم چرخش بلافاصله
panner.orientationX.setValueAtTime(x1, context.currentTime);
panner.orientationY.setValueAtTime(y1, context.currentTime);
panner.orientationZ.setValueAtTime(z1, context.currentTime);

// محاسبه بردار برای ۲۲٫۴- درجه
// از آنجایی که coneOuterAngle ما 45 است، این مقدار تقریباً صدا را قابل شنیدن می‌کند
// اگر آن را روی +/-22.5 تنظیم کنیم، بلندی صدا 0 خواهد بود، زیرا آستانه انحصاری است
const [x2, y2, z2] = yRotationToVector(-22.4);
panner.orientationX.setValueAtTime(x2, context.currentTime + 2);
panner.orientationY.setValueAtTime(y2, context.currentTime + 2);
panner.orientationZ.setValueAtTime(z2, context.currentTime + 2);
```

در نهایت، تمام گره‌های خود را متصل کرده و نوسان‌ساز را شروع می‌کنیم!

```js
osc.connect(panner).connect(context.destination);

osc.start(0);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضایی‌سازی Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)
- {{domxref("PannerNode")}}