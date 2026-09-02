---
title: "MediaTrackSupportedConstraints: sampleSize property"
short-title: sampleSize
slug: Web/API/MediaTrackSupportedConstraints/sampleSize
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.sampleSize_constraint
---

{{APIRef("Media Capture and Streams")}}

در واژه‌نامهٔ {{domxref("MediaTrackSupportedConstraints")}}، ویژگی **`sampleSize`** یک مقدار بولی فقط‌خواندنی است که در شیء برگشت‌داده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و روی `true` تنظیم شده) اگر و فقط اگر {{Glossary("user agent")}} از محدودیت `sampleSize` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست گنجانده نمی‌شود؛ بنابراین مقدار آن هرگز `false` نخواهد بود.

می‌توانید واژه‌نامهٔ محدودیت‌های پشتیبانی‌شده را با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` دریافت کنید.

## مقدار

اگر {{Glossary("user agent")}} از محدودیت `sampleSize` پشتیبانی کند، این ویژگی در واژه‌نامه وجود دارد (و مقدار آن همیشه `true` است). اگر این ویژگی وجود نداشته باشد، یعنی در واژه‌نامهٔ محدودیت‌های پشتیبانی‌شده غایب است و اگر تلاش کنید مقدار آن را بخوانید، {{jsxref("undefined")}} دریافت می‌کنید.

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
const supported = navigator.mediaDevices.getSupportedConstraints().sampleSize;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{ EmbedLiveSample('Examples', 600, 80) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}