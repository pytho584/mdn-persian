---
title: "AudioScheduledSourceNode: stop() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioScheduledSourceNode/stop"
translated_by: "n8n + AI"
---

---
title: "AudioScheduledSourceNode: stop() method"
short-title: stop()
slug: Web/API/AudioScheduledSourceNode/stop
page-type: web-api-instance-method
browser-compat: api.AudioScheduledSourceNode.stop
---

{{ APIRef("Web Audio API") }}

متد `stop()` روی {{domxref("AudioScheduledSourceNode")}} توقف پخش یک صدا را در زمان مشخص‌شده زمان‌بندی می‌کند. اگر زمانی مشخص نشود، پخش صدا بلافاصله متوقف می‌شود.

هر بار که `stop()` را روی همان نود صدا بزنید، زمان مشخص‌شده جایگزین هر زمان توقف قبلی می‌شود که هنوز رخ نداده است. اگر نود قبلاً متوقف شده باشد، این متد هیچ اثری ندارد.

> [!NOTE]
> اگر زمان توقف زمان‌بندی‌شده قبل از زمان شروع زمان‌بندی‌شده نود رخ دهد، نود هرگز شروع به پخش نمی‌کند.

## نحو

```js-nolint
stop()
stop(when)
```

### پارامترها

- `when` {{optional_inline}}
  - : زمان بر حسب ثانیه که صدا باید پخش آن متوقف شود. این مقدار در همان سیستم مختصات زمانی مشخص می‌شود که {{domxref("AudioContext")}} برای ویژگی {{domxref("BaseAudioContext/currentTime", "currentTime")}} خود استفاده می‌کند. حذف این پارامتر، تعیین مقدار ۰، یا عبور دادن یک مقدار منفی باعث می‌شود پخش صدا بلافاصله متوقف شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateNode` {{domxref("DOMException")}}
  - : اگر نود با فراخوانی {{domxref("AudioScheduledSourceNode.start", "start()")}} شروع نشده باشد، پرتاب می‌شود.
- {{jsxref("RangeError")}}
  - : اگر مقدار مشخص‌شده برای `when` منفی باشد، پرتاب می‌شود.

## مثال‌ها

این مثال نحوه شروع یک نود نوسان‌ساز را نشان می‌دهد که زمان‌بندی شده است بلافاصله شروع به پخش کند و پس از یک ثانیه پخش آن متوقف شود. زمان توقف با گرفتن زمان فعلی زمینه صوتی از {{domxref("BaseAudioContext/currentTime", "AudioContext.currentTime")}} و اضافه کردن ۱ ثانیه تعیین می‌شود.

```js
context = new AudioContext();
osc = context.createOscillator();
osc.connect(context.destination);

/* Let's play a sine wave for one second. */

osc.start();
osc.stop(context.currentTime + 1);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("AudioScheduledSourceNode.start", "start()")}}
- {{domxref("AudioScheduledSourceNode")}}
- {{domxref("AudioBufferSourceNode")}}
- {{domxref("ConstantSourceNode")}}
- {{domxref("OscillatorNode")}}