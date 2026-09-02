---
title: "MediaTrackSupportedConstraints: facingMode property"
short-title: facingMode
slug: Web/API/MediaTrackSupportedConstraints/facingMode
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.facingMode_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`facingMode`** در فرهنگ لغت {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط خواندنی است که در شیء بازگشتی از {{domxref("MediaDevices.getSupportedConstraints()")}} حضور دارد (و برابر `true` تنظیم شده) اگر و تنها اگر {{Glossary("user agent")}} از محدودیت `facingMode` پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در لیست قرار نمی‌گیرد، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید فرهنگ لغت محدودیت‌های پشتیبانی‌شده را با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` دریافت کنید.

## مقدار

این ویژگی در فرهنگ لغت حضور دارد (و مقدار آن همیشه `true` است) اگر عامل کاربر از محدودیت `facingMode` پشتیبانی کند. اگر ویژگی وجود نداشته باشد، این ویژگی در فرهنگ لغت محدودیت‌های پشتیبانی‌شده غایب است و اگر بخواهید مقدار آن را بررسی کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

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
const supported = navigator.mediaDevices.getSupportedConstraints().facingMode;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{ EmbedLiveSample('Examples', 600, 80) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [API ضبط و جریان‌های رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}