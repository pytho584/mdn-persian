---
title: "AudioContext: sinkId property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/sinkId"
translated_by: "n8n + AI"
---

---
title: "AudioContext: sinkId property"
short-title: sinkId
slug: Web/API/AudioContext/sinkId
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.AudioContext.sinkId
---

{{APIRef("Web Audio API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی فقط خواندنی **`sinkId`** در رابط {{domxref("AudioContext")}} شناسه خروجی دستگاه صوتی فعلی را برمی‌گرداند.

## مقدار

این ویژگی بسته به نحوه تنظیم شناسه خروجی صدا، یکی از مقادیر زیر را برمی‌گرداند:

- یک رشته خالی
  - : اگر شناسه خروجی صدا به طور صریح تنظیم نشده باشد، از دستگاه خروجی صوتی پیش‌فرض سیستم استفاده می‌شود و `sinkId` یک رشته خالی برمی‌گرداند.
- یک رشته
  - : اگر شناسه خروجی صدا به عنوان یک مقدار رشته (با استفاده از {{domxref("AudioContext.setSinkId", "setSinkId()")}} یا گزینه سازنده `sinkId` در {{domxref("AudioContext.AudioContext", "AudioContext()")}}) تنظیم شده باشد، `sinkId` همان مقدار رشته را برمی‌گرداند.
- یک شیء {{domxref("AudioSinkInfo")}}
  - : اگر شناسه خروجی صدا به عنوان یک شیء گزینه (با استفاده از {{domxref("AudioContext.setSinkId", "setSinkId()")}} یا گزینه سازنده `sinkId` در {{domxref("AudioContext.AudioContext", "AudioContext()")}}) تنظیم شده باشد، `sinkId` یک شیء {{domxref("AudioSinkInfo")}} برمی‌گرداند که مقادیر تنظیم شده در شیء گزینه اولیه را منعکس می‌کند.

## مثال‌ها

در [مثال آزمایشی SetSinkId](https://mdn.github.io/dom-examples/audiocontext-setsinkid/) ما (کد منبع را [اینجا](https://github.com/mdn/dom-examples/tree/main/audiocontext-setsinkid) ببینید)، یک گراف صوتی ایجاد می‌کنیم که یک انفجار سه ثانیه‌ای نویز سفید را از طریق {{domxref("AudioBufferSourceNode")}} تولید می‌کند. ما همچنین این نویز را از طریق {{domxref("GainNode")}} عبور می‌دهیم تا صدا کمی کاهش یابد. علاوه بر این، یک منوی کشویی برای کاربر فراهم می‌کنیم تا بتواند دستگاه خروجی صوتی را تغییر دهد.

هنگامی که دکمه پخش کلیک می‌شود، گراف صوتی را تشکیل می‌دهیم و شروع به پخش می‌کنیم. همچنین اطلاعات مربوط به دستگاه فعلی را بر اساس مقدار `sinkId` در کنسول ثبت می‌کنیم:

- یک رشته خالی به این معنی است که هنوز از دستگاه پیش‌فرض استفاده می‌شود.
- اگر مقدار یک شیء باشد، صدا روی هیچ دستگاهی پخش نمی‌شود زیرا ما یک شیء گزینه حاوی `type: 'none'` تنظیم کرده‌ایم.
- در غیر این صورت مقدار یک رشته شناسه خروجی صدا خواهد بود، بنابراین آن را ثبت می‌کنیم.

```js
playBtn.addEventListener("click", () => {
  const source = audioCtx.createBufferSource();
  source.buffer = myArrayBuffer;
  source.connect(gain);
  gain.connect(audioCtx.destination);
  source.start();

  if (audioCtx.sinkId === "") {
    console.log("Audio playing on default device");
  } else if (
    typeof audioCtx.sinkId === "object" &&
    audioCtx.sinkId.type === "none"
  ) {
    console.log("Audio not playing on any device");
  } else {
    console.log(`Audio playing on device ${audioCtx.sinkId}`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [تغییر دستگاه خروجی مقصد در Web Audio](https://developer.chrome.com/blog/audiocontext-setsinkid/)
- {{domxref("AudioContext.setSinkId()")}}
- {{domxref("AudioContext/sinkchange_event", "sinkchange")}}