---
title: "MediaTrackSupportedConstraints: channelCount property"
short-title: channelCount
slug: Web/API/MediaTrackSupportedConstraints/channelCount
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.channelCount_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`channelCount`** در دیکشنری {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط‌خواندنی است که در شیء برگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} حضور دارد (و روی `true` تنظیم شده است) اگر و فقط اگر {{Glossary("user agent")}} از محدودیت `channelCount` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست گنجانده نمی‌شود، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` به دیکشنری محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

این ویژگی در دیکشنری حضور دارد (و مقدار آن همیشه `true` است) اگر user agent از محدودیت `channelCount` پشتیبانی کند. اگر ویژگی حضور نداشته باشد، این ویژگی از دیکشنری محدودیت‌های پشتیبانی‌شده غایب است و اگر بخواهید مقدار آن را بررسی کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

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
const supported = navigator.mediaDevices.getSupportedConstraints().channelCount;
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