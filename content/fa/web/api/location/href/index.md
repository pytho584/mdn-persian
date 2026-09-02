---
title: "Location: href property"
short-title: href
slug: Web/API/Location/href
page-type: web-api-instance-property
browser-compat: api.Location.href
---

{{ApiRef("Location")}}

خاصیت **`href`** در رابط {{domxref("Location")}} یک {{Glossary("stringifier")}} است که رشته‌ای شامل کل URL را برمی‌گرداند و امکان به‌روزرسانی href را فراهم می‌کند.

تنظیم مقدارِ `href` به URL داده‌شده _هدایت_ می‌کند. اگر _تغییر مسیر_ (redirection) می‌خواهید، از {{domxref("Location/replace","location.replace()")}} استفاده کنید. تفاوت آن با تنظیم مقدار خاصیت `href` این است که هنگام استفاده از روش `location.replace()`، پس از هدایت به URL داده‌شده، صفحه فعلی در [تاریخچه](/en-US/docs/Web/API/History_API) جلسه ذخیره نمی‌شود — یعنی کاربر نمی‌تواند با دکمه بازگشت به آن صفحه برگردد.

## مقدار

یک رشته.

## مثال‌ها

```js
// فرض کنید یک عنصر <a id="myAnchor" href="https://developer.mozilla.org/en-US/Location/href"> در سند وجود دارد
const anchor = document.getElementById("myAnchor");
const result = anchor.href; // برمی‌گرداند: 'https://developer.mozilla.org/en-US/Location/href'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}