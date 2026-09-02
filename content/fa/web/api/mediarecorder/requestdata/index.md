---
title: "MediaRecorder: requestData() method"
short-title: requestData()
slug: Web/API/MediaRecorder/requestData
page-type: web-api-instance-method
browser-compat: api.MediaRecorder.requestData
---

{{APIRef("MediaStream Recording")}}

متد **`requestData()`** از رابط {{domxref("MediaRecorder")}} برای برانگیختن یک رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} حاوی یک شیء {{domxref("Blob")}} از رسانه‌ی ضبط‌شده به همان صورتی که در زمان فراخوانی متد بوده است، استفاده می‌شود. سپس می‌توانید آن را به دلخواه خود دریافت و دستکاری کنید.

هنگامی که متد `requestData()` فراخوانی می‌شود، مرورگر یک وظیفه (task) را در صف قرار می‌دهد که مراحل زیر را اجرا می‌کند:

1. اگر {{domxref("MediaRecorder.state")}} برابر با "inactive" باشد، یک خطای `InvalidState` از نوع DOM ایجاد کرده و این مراحل را پایان دهید. اگر {{domxref("MediaRecorder.state")}} "inactive" نباشد، به مرحله‌ی بعد بروید.
2. یک رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} حاوی یک {{domxref("Blob")}} از داده‌های ضبط‌شده‌ی فعلی ایجاد کنید (این Blob در ویژگی `data` رویداد در دسترس است).
3. یک Blob جدید ایجاد کرده و داده‌های بعدی ضبط‌شده را در آن قرار دهید.

## Syntax

```js-nolint
requestData()
```

### Parameters

هیچکدام.

### Return value

هیچکدام ({{jsxref("undefined")}}).

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورتی که `MediaRecorder` در وضعیت `"inactive"` باشد، پرتاب می‌شود؛ اگر `MediaRecorder` فعال نباشد، نمی‌توانید ضبط را دریافت کنید.

## Examples

```js
captureMedia.onclick = () => {
  mediaRecorder.requestData();
  // makes snapshot available of data so far
  // ondataavailable fires, then capturing continues
  // in new Blob
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): نمایشی از MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([متن در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone))
- [نسخه‌ی نمایشی ضبط MediaStream از simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton)
- {{domxref("Navigator.getUserMedia()")}}