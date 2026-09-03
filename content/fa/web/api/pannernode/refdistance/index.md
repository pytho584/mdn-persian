---
title: "PannerNode: refDistance property"
short-title: refDistance
slug: Web/API/PannerNode/refDistance
page-type: web-api-instance-property
browser-compat: api.PannerNode.refDistance
---

{{ APIRef("Web Audio API") }}

ویژگی `refDistance` از رابط {{ domxref("PannerNode") }} یک مقدار اعشاری (double) است که فاصله مرجع برای کاهش حجم صدا را هنگام دور شدن منبع صوتی از شنونده نشان می‌دهد – یعنی فاصله‌ای که کاهش حجم از آن نقطه شروع به اثر می‌کند. این مقدار در تمام مدل‌های فاصله استفاده می‌شود.

مقدار پیش‌فرض ویژگی `refDistance` برابر با `1` است.

## مقدار

یک عدد غیرمنفی. اگر مقدار کمتر از 0 تنظیم شود، یک {{jsxref("RangeError")}} پرتاب می‌شود.

### استثناها

- {{jsxref("RangeError")}}
  - : اگر مقداری به ویژگی داده شود که خارج از محدوده مجاز باشد، پرتاب می‌شود.

## مثال‌ها

این مثال نشان می‌دهد که چگونه مقادیر مختلف `refDistance` بر نحوه کاهش حجم صدا در هنگام دور شدن از شنونده تأثیر می‌گذارند. برخلاف {{ domxref("PannerNode.rolloffFactor", "rolloffFactor") }}، تغییر این مقدار همچنین کاهش حجم را تا زمانی که صدا از نقطه مرجع عبور کند _به تأخیر می‌اندازد_.

```js
const context = new AudioContext();
// all our test tones will last this many seconds
const NOTE_LENGTH = 6;
// this is how far we'll move the sound
const Z_DISTANCE = 20;

// this function creates a graph for the test tone with a given refDistance
// and schedules it to move away from the listener along the Z (depth-wise) axis
// at the given start time, resulting in a decrease in volume (decay)
const scheduleTestTone = (refDistance, startTime) => {
  const osc = new OscillatorNode(context);

  const panner = new PannerNode(context);
  panner.refDistance = refDistance;

  // set the initial Z position, then schedule the ramp
  panner.positionZ.setValueAtTime(0, startTime);
  panner.positionZ.linearRampToValueAtTime(Z_DISTANCE, startTime + NOTE_LENGTH);

  osc.connect(panner).connect(context.destination);

  osc.start(startTime);
  osc.stop(startTime + NOTE_LENGTH);
};

// this tone should decay immediately and fairly quickly
scheduleTestTone(1, context.currentTime);
// this tone should decay slower and later than the previous one
scheduleTestTone(4, context.currentTime + NOTE_LENGTH);
// this tone should decay only slightly, and only start decaying fairly late
scheduleTestTone(7, context.currentTime + NOTE_LENGTH * 2);
```

پس از اجرای این کد، شکل‌موج‌های حاصل باید چیزی شبیه به این باشند:

![تصویری از شکل‌موج سه تُن نوسان‌ساز تولید شده در Web Audio. هر نوسان‌ساز با سرعت یکسان از شنونده دور می‌شود، اما با refDistances مختلف که کاهش حجم حاصل را تحت تأثیر قرار می‌دهد.](screen_shot_2018-10-11_at_23.14.32.png)

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضایی‌سازی Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)