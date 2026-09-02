---
title: "MediaTrackSupportedConstraints: sampleRate property"
short-title: sampleRate
slug: Web/API/MediaTrackSupportedConstraints/sampleRate
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.sampleRate_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`sampleRate`** در فرهنگ لغت {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولیِ فقط‌خواندنی است که در شیء برگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} فقط زمانی وجود دارد (و برابر با `true` است) که {{Glossary("user agent")}} از محدودیت `sampleRate` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست قرار نمی‌گیرد، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` به فرهنگ لغت محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

این ویژگی در فرهنگ لغت وجود دارد (و مقدار آن همیشه `true` است) اگر user agent از محدودیت `sampleRate` پشتیبانی کند. اگر ویژگی وجود نداشته باشد، این ویژگی در فرهنگ لغت محدودیت‌های پشتیبانی‌شده غایب است و اگر بخواهید به مقدار آن دسترسی پیدا کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

## مثال‌ها

```html hidden
<div id="result"></div>
```

```css hidden
#result {
  font:
    14px "Arial",
    sans-serif;
}
```

```js
const result = document.getElementById("result");
const supported = navigator.mediaDevices.getSupportedConstraints().sampleRate;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{ EmbedLiveSample('Examples', 600, 80) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط و جریان رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}