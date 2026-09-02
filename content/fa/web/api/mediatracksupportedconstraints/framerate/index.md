---
title: "MediaTrackSupportedConstraints: frameRate property"
short-title: frameRate
slug: Web/API/MediaTrackSupportedConstraints/frameRate
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.frameRate_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`frameRate`** در دیکشنری {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط‌خواندنی است که در شیء بازگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} وجود دارد (و روی `true` تنظیم می‌شود) اگر و تنها اگر عامل کاربر ({{Glossary("user agent")}}) از محدودیت {{domxref("MediaTrackConstraints.frameRate","frameRate")}} پشتیبانی کند.

اگر این محدودیت پشتیبانی نشود، در فهرست قرار نمی‌گیرد، بنابراین این مقدار هرگز `false` نخواهد بود.

محدودیت `frameRate` می‌تواند برای تعیین کران‌های بالا و پایینِ قابل قبول برای نرخ فریم ویدیوی یک track ویدیویی جدید، یا برای مشخص کردن یک نرخ فریم دقیق که برای موفقیت درخواست باید ارائه شود، استفاده شود. بررسی مقدار این ویژگی به شما امکان می‌دهد تعیین کنید که آیا عامل کاربر اجازه محدود کردن پیکربندی track ویدیویی بر اساس نرخ فریم را می‌دهد یا خیر. برای مشاهده نحوه استفاده از آن، به [مثال](#examples) مراجعه کنید.

## Value

این ویژگی در دیکشنری وجود دارد اگر عامل کاربر از محدودیت `frameRate` پشتیبانی کند. اگر ویژگی وجود نداشته باشد، عامل کاربر اجازه تعیین محدودیت‌های نرخ فریم برای track‌های ویدیویی را نمی‌دهد.

> [!NOTE]
> اگر این ویژگی وجود داشته باشد، مقدار آن همیشه `true` است.

## Examples

این مثال ساده بررسی می‌کند که آیا مرورگر شما هنگام درخواست track‌های ویدیویی از محدود کردن نرخ فریم پشتیبانی می‌کند یا خیر.

### JavaScript

```js
const result = document.getElementById("result");
const supported = navigator.mediaDevices.getSupportedConstraints().frameRate;
result.textContent = supported ? "Supported!" : "Not supported!";
```

### HTML

```html
<div id="result"></div>
```

### CSS

```css
#result {
  font:
    14px "Arial",
    sans-serif;
}
```

### Result

خروجی، که نشان می‌دهد آیا مرورگر شما از محدودیت `frameRate` پشتیبانی می‌کند، به صورت زیر است:

{{ EmbedLiveSample('Examples', 600, 80) }}

اگرچه این مثال ساده است، می‌توانید خروجی ساده «Supported» در برابر «Not supported» را با کدی جایگزین کنید که روش‌های جایگزینی برای ارائه اطلاعات سمعی‌وبصری که می‌خواهید با کاربر به اشتراک بگذارید یا به شکل دیگری با آن کار کنید، فراهم کند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}