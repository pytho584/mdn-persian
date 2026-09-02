---
title: "MediaTrackSupportedConstraints: deviceId property"
short-title: deviceId
slug: Web/API/MediaTrackSupportedConstraints/deviceId
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.deviceId_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`deviceId`** در دیکشنری {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط خواندنی است که در شیء بازگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و مقدار آن `true` تنظیم شده است) اگر و فقط اگر {{Glossary("user agent", "عامل کاربر")}} از محدودیت `deviceId` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در لیست گنجانده نمی‌شود، بنابراین این ویژگی هرگز مقدار `false` نخواهد داشت.

می‌توانید با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` به دیکشنری محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

این ویژگی در دیکشنری وجود دارد (و مقدار آن همیشه `true` است) اگر عامل کاربر از محدودیت `deviceId` پشتیبانی کند. اگر ویژگی وجود نداشته باشد، این ویژگی در دیکشنری محدودیت‌های پشتیبانی‌شده غایب است و اگر سعی کنید به مقدار آن نگاه کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

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
const supported = navigator.mediaDevices.getSupportedConstraints().deviceId;
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