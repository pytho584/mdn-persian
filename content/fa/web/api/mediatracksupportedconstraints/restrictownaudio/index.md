---
title: "MediaTrackSupportedConstraints: restrictOwnAudio property"
short-title: restrictOwnAudio
slug: Web/API/MediaTrackSupportedConstraints/restrictOwnAudio
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.MediaStreamTrack.applyConstraints.restrictOwnAudio_constraint
---

{{APIRef("Media Capture and Streams")}}{{SeeCompatTable}}

ویژگی **`restrictOwnAudio`** در دیکشنری {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولین فقط‌خواندنی است که در شیء بازگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و مقدار آن `true` است) اگر و تنها اگر عامل کاربر ({{Glossary("user agent")}}) از محدودیت `restrictOwnAudio` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست قرار نمی‌گیرد؛ بنابراین مقدار این ویژگی هرگز `false` نخواهد بود.

می‌توانید با فراخوانی {{domxref("MediaDevices.getSupportedConstraints()", "navigator.mediaDevices.getSupportedConstraints()")}} به دیکشنری محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

این ویژگی در دیکشنری وجود دارد (و مقدار آن همیشه `true` است) اگر عامل کاربر از محدودیت `restrictOwnAudio` پشتیبانی کند. اگر ویژگی موجود نباشد، این ویژگی در دیکشنری محدودیت‌های پشتیبانی‌شده وجود نخواهد داشت و اگر برای دسترسی به مقدار آن تلاش کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

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
const supported =
  navigator.mediaDevices.getSupportedConstraints().restrictOwnAudio;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{EmbedLiveSample('Examples', 600, 80)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}