---
title: "MediaTrackSupportedConstraints: aspectRatio property"
short-title: aspectRatio
slug: Web/API/MediaTrackSupportedConstraints/aspectRatio
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.aspectRatio_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`aspectRatio`** در دیکشنری {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط‑خواندنی است که در شیء بازگشتی توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و برابر `true` است) اگر و فقط اگر {{Glossary("user agent")}} از محدودیت `aspectRatio` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در لیست قرار نمی‌گیرد، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` به دیکشنری محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

این ویژگی در دیکشنری وجود دارد (و مقدار آن همیشه `true` است) اگر عامل کاربر از محدودیت `aspectRatio` پشتیبانی کند. اگر ویژگی موجود نباشد، این ویژگی از دیکشنری محدودیت‌های پشتیبانی‌شده غایب است و اگر سعی کنید به مقدار آن نگاه کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

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
const supported = navigator.mediaDevices.getSupportedConstraints().aspectRatio;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{ EmbedLiveSample('Examples', 600, 80) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}