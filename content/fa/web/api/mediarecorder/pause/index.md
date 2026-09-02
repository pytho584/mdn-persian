---
title: "MediaRecorder: pause() method"
short-title: pause()
slug: Web/API/MediaRecorder/pause
page-type: web-api-instance-method
browser-compat: api.MediaRecorder.pause
---

{{APIRef("MediaStream Recording")}}

متد **`pause()`** در رابط {{domxref("MediaRecorder")}} برای توقف موقت ضبط جریان‌های رسانه‌ای استفاده می‌شود.

هنگامی که متد `pause()` روی یک شیء `MediaRecorder` فراخوانی می‌شود، مرورگر یک وظیفه (task) در صف قرار می‌دهد که مراحل زیر را اجرا می‌کند:

1. اگر {{domxref("MediaRecorder.state")}} برابر با `"inactive"` باشد، یک خطای DOM از نوع `InvalidState` صادر کرده و این مراحل پایان می‌یابد. در غیر این صورت، به مرحله بعد بروید.
2. {{domxref("MediaRecorder.state")}} را روی `"paused"` قرار دهید.
3. جمع‌آوری داده‌ها در {{domxref("Blob")}} فعلی را متوقف کنید، اما آن را حفظ کنید تا بتوانید بعداً ضبط را از سر بگیرید.
4. یک رویداد {{domxref("MediaRecorder/pause_event", "pause")}} صادر کنید.

## نحو (Syntax)

```js-nolint
pause()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `MediaRecorder` در حالت `"inactive"` باشد پرتاب می‌شود؛ اگر `MediaRecorder` فعال نباشد نمی‌توانید ضبط را متوقف کنید. اگر در حالی که قبلاً متوقف شده است `pause()` را فراخوانی کنید، متد به‌صورت بی‌صدا هیچ کاری انجام نمی‌دهد.

## مثال‌ها

```js
pause.onclick = () => {
  mediaRecorder.pause();
  console.log("recording paused");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط جریان رسانه‌ای (MediaStream Recording API)](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [وب دیکتافون (Web Dictaphone)](https://mdn.github.io/dom-examples/media/web-dictaphone/): نمایش MediaRecorder + getUserMedia + تجسم Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([سورس در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [نمایش ساده ضبط MediaStream](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton).
- {{domxref("Navigator.getUserMedia")}}