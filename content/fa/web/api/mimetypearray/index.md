---
title: MimeTypeArray
slug: Web/API/MimeTypeArray
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.MimeTypeArray
---

{{APIRef("HTML DOM")}}{{Deprecated_Header}}

رابط **`MimeTypeArray`** آرایه‌ای از نمونه‌های {{domxref('MimeType')}} را برمی‌گرداند که هر یک حاوی اطلاعاتی درباره یک افزونه مرورگر پشتیبانی‌شده است. این شیء توسط ویژگی منسوخ‌شده {{domxref("Navigator.mimeTypes")}} برگردانده می‌شود.

این رابط یک [تلاش برای ایجاد یک لیست غیرقابل تغییر](https://stackoverflow.com/questions/74630989/why-use-domstringlist-rather-than-an-array/74641156#74641156) بود و تنها برای جلوگیری از شکستن کدهایی که قبلاً از آن استفاده می‌کنند پشتیبانی می‌شود. APIهای مدرن ساختارهای لیستی را با استفاده از انواع مبتنی بر [آرایه‌های](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) جاوااسکریپت نمایش می‌دهند، بنابراین بسیاری از متدهای آرایه در دسترس هستند و در عین حال معناشناسی اضافی را بر استفاده از آنها تحمیل می‌کنند (مانند فقط خواندنی کردن آیتم‌هایشان).

## ویژگی‌های نمونه

- {{domxref("MimeTypeArray.length")}} {{Deprecated_Inline}}
  - : تعداد آیتم‌های موجود در آرایه.

## روش‌های نمونه

- {{domxref("MimeTypeArray.item()")}} {{Deprecated_Inline}}
  - : شیء `MimeType` را با ایندکس مشخص‌شده برمی‌گرداند.
- {{domxref("MimeTypeArray.namedItem()")}} {{Deprecated_Inline}}
  - : شیء `MimeType` را با نام مشخص‌شده برمی‌گرداند.

## مثال

مثال زیر بررسی می‌کند که آیا یک افزونه برای نوع mime 'application/pdf' در دسترس است یا خیر و اگر چنین باشد، توضیحات آن را در کنسول ثبت می‌کند.

```js
const mimeTypes = navigator.mimeTypes;
const pdf = mimeTypes.namedItem("application/pdf");

if (pdf) {
  console.log(pdf.description);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}