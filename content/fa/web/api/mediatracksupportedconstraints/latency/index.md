---
title: "MediaTrackSupportedConstraints: latency property"
short-title: latency
slug: Web/API/MediaTrackSupportedConstraints/latency
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.latency_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`latency`** در دیکشنری (dictionary) {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقطخواندنی است که در شیء بازگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و روی `true` تنظیم شده است) اگر و تنها اگر {{Glossary("user agent")}} از محدودیت `latency` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست گنجانده نمی‌شود، بنابراین این مقدار هرگز `false` نخواهد بود.

با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` می‌توانید به دیکشنری محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

اگر user agent از محدودیت `latency` پشتیبانی کند، این ویژگی در دیکشنری حاضر است (و مقدار آن همیشه `true` است). در غیر این صورت، این ویژگی در دیکشنری محدودیت‌های پشتیبانی‌شده وجود نخواهد داشت و اگر تلاش کنید مقدار آن را بررسی کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

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
const supported = navigator.mediaDevices.getSupportedConstraints().latency;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{ EmbedLiveSample('Examples', 600, 80) }}

## توصیفات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}