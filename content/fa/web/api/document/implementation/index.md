---
title: "Document: implementation property"
short-title: implementation
slug: Web/API/Document/implementation
page-type: web-api-instance-property
browser-compat: api.Document.implementation
---

{{ ApiRef("DOM") }}

ویژگی **`Document.implementation`** یک شیء {{domxref("DOMImplementation")}} مرتبط با سند فعلی را بازمی‌گرداند.

## مقدار

یک شیء {{domxref("DOMImplementation")}}.

## مثال‌ها

```js
const modName = "HTML";
const modVer = "2.0";
const conformTest = document.implementation.hasFeature(modName, modVer);

console.log(`DOM ${modName} ${modVer} supported?: ${conformTest}`);

// Log: "DOM HTML 2.0 supported?: true" (hasFeature always returns true)
```

> [!WARNING]
> از این ویژگی برای تشخیص قابلیت‌ها استفاده نکنید. متد `hasFeature()` همیشه `true` برمی‌گرداند.

## نکات

توصیه‌نامه سطح ۱ DOM کنسرسیوم جهانی وب فقط متد `hasFeature` را مشخص کرده بود؛ این متد یکی از راه‌های تعیین این است که آیا یک ماژول DOM توسط مرورگر پشتیبانی می‌شود یا خیر (به مثال بالا و [What does your user agent claim to support?](https://www.w3.org/2003/02/06-dom-support.html) مراجعه کنید). در صورت در دسترس بودن، سایر متدهای `DOMImplementation` خدماتی برای کنترل موارد خارج از یک سند واحد فراهم می‌کنند. برای مثال، رابط `DOMImplementation` شامل متد `createDocumentType` است که با آن می‌توان DTDها را برای یک یا چند سند مدیریت‌شده توسط آن پیاده‌سازی ایجاد کرد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}