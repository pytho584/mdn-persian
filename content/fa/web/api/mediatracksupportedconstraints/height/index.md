---
title: "MediaTrackSupportedConstraints: height property"
short-title: height
slug: Web/API/MediaTrackSupportedConstraints/height
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.height_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`height`** در فرهنگ لغت {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولین فقط‌خواندنی است که در شیء بازگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و برابر با `true` است) اگر و فقط اگر {{Glossary("user agent")}} از محدودیت `height` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست گنجانده نمی‌شود، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` به فرهنگ لغت محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

این ویژگی در فرهنگ لغت وجود دارد (و مقدار آن همیشه `true` است) اگر user agent از محدودیت `height` پشتیبانی کند. اگر این ویژگی وجود نداشته باشد، در فرهنگ لغت محدودیت‌های پشتیبانی‌شده غایب است و اگر بخواهید مقدار آن را بررسی کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

## نمونه‌ها

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
const supported = navigator.mediaDevices.getSupportedConstraints().height;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{ EmbedLiveSample('Examples', 600, 80) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [API ضبط و جریان رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}