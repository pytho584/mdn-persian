---
title: "Document: referrer property"
short-title: referrer
slug: Web/API/Document/referrer
page-type: web-api-instance-property
browser-compat: api.Document.referrer
---

{{APIRef("DOM")}}

ویژگی **`Document.referrer`**، [URI](https://www.w3.org/Addressing/#background) صفحه‌ای را که به این صفحه لینک داده است، برمی‌گرداند.

## مقدار

اگر کاربر مستقیماً به صفحه رفته باشد (نه از طریق یک لینک، بلکه مثلاً با استفاده از یک نشانک)، مقدار یک رشته خالی است. از آنجا که این ویژگی فقط یک رشته برمی‌گرداند، به شما دسترسی به مدل شیء سند (DOM) صفحه مرجع نمی‌دهد.

درون یک {{HTMLElement("iframe")}}، `Document.referrer` در ابتدا در درخواست‌های هم‌ریشه (same-origin) به {{domxref("HTMLAnchorElement/href", "href")}} از {{domxref("Window/location", "Window.location")}} والد تنظیم می‌شود. در درخواست‌های بین‌ریشه (cross-origin)، به‌طور پیش‌فرض {{domxref("HTMLAnchorElement/origin", "origin")}} از `Window.location` والد است. برای اطلاعات بیشتر، به مستندات [Referrer-Policy: strict-origin-when-cross-origin](/en-US/docs/Web/HTTP/Reference/Headers/Referrer-Policy#strict-origin-when-cross-origin) مراجعه کنید.

## مثال‌ها

مثال زیر یک رشته شامل مرجع سند را ثبت می‌کند.

```js
console.log(document.referrer);
```

اگر کاربر از طریق یک لینک مانند `<a href="https://www.w3.org/">W3</a>` به صفحه رفته باشد، دامنه قبلی مانند `developer.mozilla.org` را خروجی می‌دهد. اگر کاربر مستقیماً به صفحه رفته باشد، یک رشته خالی خروجی می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}