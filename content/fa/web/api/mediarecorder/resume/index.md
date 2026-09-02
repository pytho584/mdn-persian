---
title: "MediaRecorder: resume() method"
---

---
title: "MediaRecorder: resume() method"
short-title: resume()
slug: Web/API/MediaRecorder/resume
page-type: web-api-instance-method
browser-compat: api.MediaRecorder.resume
---

{{APIRef("MediaStream Recording")}}

متد **`resume()`** از رابط {{domxref("MediaRecorder")}} برای از سرگیری ضبط رسانه زمانی که قبلاً مکث شده است استفاده می‌شود.

اگر {{domxref("MediaRecorder.state")}} از قبل «recording» باشد، فراخوانی `resume()` هیچ اثری ندارد.

هنگامی که متد `resume()` فراخوانی می‌شود، مرورگر یک کار (task) را در صف قرار می‌دهد که مراحل زیر را اجرا می‌کند:

1. اگر {{domxref("MediaRecorder.state")}} برابر «inactive» باشد، یک استثنای DOM از نوع `InvalidStateError` صادر می‌کند و این مراحل خاتمه می‌یابد. اگر {{domxref("MediaRecorder.state")}} برابر «inactive» نباشد، به مرحله بعد ادامه دهید.
2. {{domxref("MediaRecorder.state")}} را روی «recording» تنظیم کنید.
3. به جمع‌آوری داده‌ها در {{domxref("Blob")}} فعلی ادامه دهید.
4. یک رویداد `resume` صادر کنید.

## سینتکس

```js-nolint
resume()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `MediaRecorder` در حال حاضر «inactive» باشد، پرتاب می‌شود.

## مثال‌ها

```js
pause.onclick = () => {
  if (MediaRecorder.state === "recording") {
    mediaRecorder.pause();
    // recording paused
  } else if (MediaRecorder.state === "paused") {
    mediaRecorder.resume();
    // resume recording
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [وب دیکتافون](https://mdn.github.io/dom-examples/media/web-dictaphone/): دموی نمایشی MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([سورس در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [دموی MediaStream Recording در simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton).
- {{domxref("Navigator.getUserMedia")}}