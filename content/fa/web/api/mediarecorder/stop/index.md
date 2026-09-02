```markdown
---
title: "MediaRecorder: stop() method"
short-title: stop()
slug: Web/API/MediaRecorder/stop
page-type: web-api-instance-method
browser-compat: api.MediaRecorder.stop
---

{{APIRef("MediaStream Recording")}}

متد **`stop()`** از رابط {{domxref("MediaRecorder")}} برای توقف ضبط رسانه استفاده می‌شود.

هنگامی که متد `stop()` فراخوانی می‌شود، عامل کاربر (UA) یک وظیفه (task) در صف قرار می‌دهد که مراحل زیر را اجرا می‌کند:

1. اگر {{domxref("MediaRecorder.state")}} برابر `"inactive"` باشد، یک خطای `InvalidState` از نوع DOM ایجاد کرده و این مراحل را خاتمه می‌دهد. در غیر این صورت (اگر state برابر `"inactive"` نباشد) به مرحله بعد بروید.
2. {{domxref("MediaRecorder.state")}} را به `"inactive"` تنظیم کرده و ضبط رسانه را متوقف کنید.
3. یک رویداد `dataavailable` حاوی شیء Blob از داده‌های جمع‌آوری‌شده ایجاد کنید.
4. یک رویداد `stop` ایجاد کنید.

## Syntax

```js-nolint
stop()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی که `MediaRecorder` در حال حاضر `"inactive"` باشد پرتاب می‌شود؛ اگر `MediaRecorder` فعال نباشد نمی‌توانید ضبط را متوقف کنید.

## مثال‌ها

```js
stop.onclick = () => {
  mediaRecorder.stop();
  console.log("recorder stopped, data available");
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): یک دموی تصویری از MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([کد منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone))
- [دموی ساده‌شده ضبط MediaStream](https://simpl.info/mediarecorder/) توسط [Sam Dutton](https://github.com/samdutton)
- {{domxref("Navigator.getUserMedia")}}
```