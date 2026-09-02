---
title: "MediaTrackSupportedConstraints: echoCancellation property"
short-title: echoCancellation
slug: Web/API/MediaTrackSupportedConstraints/echoCancellation
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.echoCancellation_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`echoCancellation`** در فرهنگ لغت {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط‌خواندنی است که در شیء بازگشتی از {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و مقدار آن `true` است) اگر و فقط اگر {{Glossary("user agent")}} (عامل کاربر) از محدودیت `echoCancellation` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در لیست وجود ندارد، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید فرهنگ لغت محدودیت‌های پشتیبانی‌شده را با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` دریافت کنید.

## مقدار

این ویژگی در فرهنگ لغت وجود دارد (و مقدار آن همیشه `true` است) اگر عامل کاربر از محدودیت `echoCancellation` پشتیبانی کند. اگر ویژگی وجود نداشته باشد، این ویژگی در فرهنگ لغت محدودیت‌های پشتیبانی‌شده غایب است و اگر تلاش کنید به مقدار آن دسترسی پیدا کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

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
  navigator.mediaDevices.getSupportedConstraints().echoCancellation;
result.textContent = supported ? "پشتیبانی می‌شود!" : "پشتیبانی نمی‌شود!";
```

### نتیجه

{{ EmbedLiveSample('Examples', 600, 80) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}