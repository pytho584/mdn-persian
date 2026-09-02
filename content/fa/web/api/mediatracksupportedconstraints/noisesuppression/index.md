---
title: "MediaTrackSupportedConstraints: noiseSuppression property"
---

---
title: "MediaTrackSupportedConstraints: noiseSuppression property"
short-title: noiseSuppression
slug: Web/API/MediaTrackSupportedConstraints/noiseSuppression
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.noiseSuppression_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`noiseSuppression`** در دیکشنری {{domxref("MediaTrackSupportedConstraints")}} یک مقدار بولی فقط‌خواندنی است. این ویژگی در شیء بازگردانده‌شده توسط {{domxref("MediaDevices.getSupportedConstraints()")}} حضور دارد (و روی `true` تنظیم می‌شود) اگر و تنها اگر {{Glossary("user agent")}} از محدودیت **`noiseSuppression`** پشتیبانی کند. اگر این محدودیت پشتیبانی نشود، در فهرست گنجانده نمی‌شود؛ بنابراین این مقدار هرگز `false` نخواهد بود.

برای دسترسی به دیکشنری محدودیت‌های پشتیبانی‌شده، می‌توانید `navigator.mediaDevices.getSupportedConstraints()` را فراخوانی کنید.

محدودیت `noiseSuppression` نشان می‌دهد که آیا مرورگر قابلیت کنترل خودکار بهره (حجم صدا) روی تراک‌های رسانه‌ای را ارائه می‌دهد یا نه؛ بدیهی است که این امر به پشتیبانی دستگاه خاص از کنترل خودکار بهره نیز بستگی دارد.

## مقدار

اگر عامل کاربر از محدودیت `noiseSuppression` پشتیبانی کند (و در نتیجه از کاهش نویز روی تراک‌های صوتی پشتیبانی کند)، این ویژگی در دیکشنری حضور دارد (و مقدار آن همیشه `true` است). اگر این ویژگی وجود نداشته باشد، در دیکشنری محدودیت‌های پشتیبانی‌شده غایب است و اگر تلاش کنید به مقدار آن دسترسی پیدا کنید، {{jsxref("undefined")}} دریافت خواهید کرد.

## مثال‌ها

این مثال نمایش می‌دهد که آیا مرورگر شما از محدودیت `noiseSuppression` پشتیبانی می‌کند یا نه.

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
  navigator.mediaDevices.getSupportedConstraints().noiseSuppression;
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