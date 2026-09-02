---
title: "MediaTrackSupportedConstraints: width property"
short-title: width
slug: Web/API/MediaTrackSupportedConstraints/width
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.width_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`width`** در دیکشنری {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط‌خواندنی است که اگر و فقط اگر {{Glossary("user agent")}} از محدودیت `width` پشتیبانی کند، در شیء بازگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} حضور دارد (و روی `true` تنظیم شده است). اگر این محدودیت پشتیبانی نشود، در فهرست گنجانده نمی‌شود، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` به دیکشنری محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

این ویژگی در دیکشنری حضور دارد (و مقدار آن همیشه `true` است) اگر user agent از محدودیت `width` پشتیبانی کند. اگر ویژگی حضور نداشته باشد، این ویژگی در دیکشنری محدودیت‌های پشتیبانی‌شده وجود ندارد و اگر بخواهید مقدار آن را بررسی کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

## مثال

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
const supported = navigator.mediaDevices.getSupportedConstraints().width;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{ EmbedLiveSample('Example', 600, 80) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API دراپ و جریان رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}