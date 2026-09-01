---
title: "HTMLMetaElement: scheme property"
short-title: scheme
slug: Web/API/HTMLMetaElement/scheme
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLMetaElement.scheme
---

{{APIRef("HTML DOM")}}{{Deprecated_Header}}

ویژگی **`HTMLMetaElement.scheme`**، طرحواره‌ی مقدار موجود در ویژگی {{domxref("HTMLMetaElement.content")}} را تعریف می‌کند.
ویژگی `scheme` برای فراهم کردن اطلاعات اضافی جهت تفسیر مقدار ویژگی `content` ایجاد شده است. این ویژگی یک قالب طرحواره (مانند `YYYY-MM-DD`) یا نام قالب طرحواره (مانند `ISBN`)، یا یک URI که اطلاعات بیشتری درباره‌ی قالب طرحواره فراهم می‌کند را به‌عنوان مقدار می‌پذیرد. طرحواره، قالب مقدار ویژگی `content` را مشخص می‌کند.
اگر مرورگر یا عامل کاربر (user agent) طرحواره را بشناسد، محتوای `scheme` به‌عنوان توسعه‌ای از ویژگی {{domxref("HTMLMetaElement.name")}} عنصر تفسیر می‌شود.

این ویژگی منسوخ (deprecated) شده است و نباید در صفحات وب جدید استفاده شود.

## مقدار

یک رشته.

## مثال‌ها

مثال زیر یک عنصر `<meta>` را جستجو می‌کند که دارای ویژگی `name` با مقدار `identifier` است. مقدار `scheme` برای نمایش طرحواره‌ی محتوای فراداده در کنسول ثبت می‌شود:

```js
// given <meta name="identifier" content="1580081754" scheme="ISBN">
const meta = document.querySelector("meta[name='identifier']");
console.log(meta.scheme);
// "ISBN"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meta")}}