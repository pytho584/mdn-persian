---
title: "MediaTrackSupportedConstraints: volume property"
short-title: volume
slug: Web/API/MediaTrackSupportedConstraints/volume
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MediaStreamTrack.applyConstraints.volume_constraint
---

{{APIRef("Media Capture and Streams")}}{{Deprecated_Header}}{{Non-standard_Header}}

خصوصیت **`volume`** در فرهنگ لغت {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط‌خواندنی است که در شیء برگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و روی `true` تنظیم شده است) اگر و فقط اگر {{Glossary("user agent")}} از محدودیت `volume` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست گنجانده نمی‌شود، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` به فرهنگ لغت محدودیت‌های پشتیبانی‌شده دسترسی پیدا کنید.

## مقدار

این خصوصیت در فرهنگ لغت وجود دارد (و مقدار آن همیشه `true` است) اگر user agent از محدودیت `volume` پشتیبانی کند. اگر خصوصیت وجود نداشته باشد، این خصوصیت در فرهنگ لغت محدودیت‌های پشتیبانی‌شده غایب است و اگر بخواهید مقدار آن را بررسی کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

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
const supported = navigator.mediaDevices.getSupportedConstraints().volume;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{EmbedLiveSample('Examples', 600, 80)}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}