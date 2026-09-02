---
title: "MediaTrackSupportedConstraints: autoGainControl property"
slug: Web/API/MediaTrackSupportedConstraints/autoGainControl
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.autoGainControl_constraint
---

{{APIRef("Media Capture and Streams")}}

دیکشنری {{domxref("MediaTrackSupportedConstraints")}} شامل ویژگی **`autoGainControl`** است، یک مقدار بولی فقط‌خواندنی که اگر و فقط اگر {{Glossary("user agent")}} از محدودیت **`autoGainControl`** پشتیبانی کند، در شیء برگشتی از {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و مقدار آن `true` است). اگر این محدودیت پشتیبانی نشود، در فهرست قرار نمی‌گیرد، بنابراین این مقدار هرگز `false` نخواهد بود.

می‌توانید دیکشنری محدودیت‌های پشتیبانی‌شده را با فراخوانی `navigator.mediaDevices.getSupportedConstraints()` مشاهده کنید.

محدودیت `autoGainControl` نشان می‌دهد که آیا مرورگر قابلیت کنترل خودکار بهره (حجم صدا) را روی رسانه‌ها ارائه می‌دهد یا نه؛ بدیهی است که این امر به پشتیبانی دستگاه خاص از کنترل خودکار بهره نیز بستگی دارد؛ این قابلیت معمولاً توسط میکروفون‌ها ارائه می‌شود.

## مقدار

این ویژگی در دیکشنری وجود دارد (و مقدار آن همیشه `true` است) اگر user agent از محدودیت `autoGainControl` پشتیبانی کند. اگر ویژگی وجود نداشته باشد، این ویژگی در دیکشنری محدودیت‌های پشتیبانی‌شده غایب است و اگر بخواهید مقدار آن را بررسی کنید، {{jsxref("undefined")}} دریافت می‌کنید.

## مثال‌ها

این مثال نشان می‌دهد که آیا مرورگر شما از محدودیت `autoGainControl` پشتیبانی می‌کند یا خیر.

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
  navigator.mediaDevices.getSupportedConstraints().autoGainControl;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### نتیجه

{{ EmbedLiveSample('Examples', 600, 80) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [API ضبط و جریان رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}