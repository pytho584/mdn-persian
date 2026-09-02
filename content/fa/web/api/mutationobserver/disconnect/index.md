---
title: "MutationObserver: disconnect() method"
short-title: disconnect()
slug: Web/API/MutationObserver/disconnect
page-type: web-api-instance-method
browser-compat: api.MutationObserver.disconnect
---

{{APIRef("DOM WHATWG")}}

متد **`disconnect()`** از {{domxref("MutationObserver")}} به مشاهده‌گر (observer) می‌گوید که تماشای تغییرات (mutations) را متوقف کند.

مشاهده‌گر را می‌توان با فراخوانی دوبارهٔ متد {{domxref("MutationObserver.observe", "observe()")}} دوباره به کار گرفت.

## نحو (Syntax)

```js-nolint
disconnect()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

`undefined`.

> [!NOTE]
> تمام اعلان‌های مربوط به تغییراتی که قبلاً _تشخیص داده شده‌اند_ اما هنوز _به مشاهده‌گر گزارش نشده‌اند_، کنار گذاشته می‌شوند. برای نگه‌داشتن و رسیدگی به تغییراتِ تشخیص‌داده‌شده ولی گزارش‌نشده، از متد {{domxref("MutationObserver.takeRecords()", "takeRecords()")}} استفاده کنید.

## نکات استفاده

اگر عنصرِ در حال مشاهده از DOM حذف و سپس توسط سازوکار جمع‌آوری زباله (garbage collection) مرورگر آزاد شود، `MutationObserver` مشاهدهٔ عنصر حذف‌شده را متوقف خواهد کرد. با این حال، خودِ `MutationObserver` همچنان می‌تواند باقی بماند تا عناصر موجود دیگر را مشاهده کند.

## مثال‌ها

این مثال یک مشاهده‌گر می‌سازد؛ سپس متد `disconnect()` را روی آن فراخوانی می‌کند و آن را برای استفادهٔ احتمالی مجدد در دسترس نگه می‌دارد.

```js
const targetNode = document.querySelector("#someElement");
const observerOptions = {
  childList: true,
  attributes: true,
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, observerOptions);

/* some time later… */

observer.disconnect();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}