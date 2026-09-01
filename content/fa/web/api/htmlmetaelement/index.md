---
title: HTMLMetaElement
slug: Web/API/HTMLMetaElement
page-type: web-api-interface
browser-compat: api.HTMLMetaElement
---

{{ APIRef("HTML DOM") }}

رابط **`HTMLMetaElement`**، فراداده‌های توصیفی درباره سند را که در HTML به صورت عنصرهای [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) ارائه می‌شوند، در بر می‌گیرد. این رابط تمام ویژگی‌ها و روش‌های شرح‌داده‌شده در رابط {{domxref("HTMLElement")}} را به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{HTMLElement("meta#charset")}}
  - : رمزگذاری نویسه‌ها برای یک سند HTML.
- {{domxref("HTMLMetaElement.content")}}
  - : بخش «مقدار» از جفت‌های نام-مقدار فراداده‌های سند.
- {{domxref("HTMLMetaElement.httpEquiv")}}
  - : نام دستور pragma (هدایت پردازش)، که همان هدر پاسخ HTTP برای یک سند است.
- {{domxref("HTMLMetaElement.media")}}
  - : بافتار رسانه‌ای برای ویژگی فراداده‌ای `theme-color`.
- {{domxref("HTMLMetaElement.name")}}
  - : بخش «نام» از جفت‌های نام-مقدار که فراداده‌های نام‌دار یک سند را تعریف می‌کنند.
- {{domxref("HTMLMetaElement.scheme")}} {{deprecated_inline}}
  - : طرح (scheme) مقدار موجود در ویژگی {{domxref("HTMLMetaElement.content")}} را تعریف می‌کند.
    این ویژگی منسوخ شده است و نباید در صفحات وب جدید استفاده شود.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

## مثال‌ها

دو مثال زیر رویکرد کلی استفاده از رابط `HTMLMetaElement` را نشان می‌دهند. برای مثال‌های خاص، به صفحه‌های مربوط به هر ویژگی که در بخش [ویژگی‌های نمونه](#instance_properties) در بالا شرح داده شد مراجعه کنید.

### تنظیم فرادادهٔ توضیح صفحه

مثال زیر یک عنصر `<meta>` جدید با ویژگی `name` تنظیم‌شده بر روی [`description`](/en-US/docs/Web/HTML/Reference/Elements/meta/name#meta_names_defined_in_the_html_specification) ایجاد می‌کند. ویژگی `content` یک توضیح برای سند تعیین می‌کند و به `<head>` سند اضافه می‌شود:

```js
const meta = document.createElement("meta");
meta.name = "description";
meta.content =
  "The <meta> element can be used to provide document metadata in terms of name-value pairs, with the name attribute giving the metadata name, and the content attribute giving the value.";
document.head.appendChild(meta);
```

### تنظیم فرادادهٔ viewport

مثال زیر نحوه ایجاد یک عنصر `<meta>` جدید با ویژگی `name` تنظیم‌شده بر روی [`viewport`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/viewport) را نشان می‌دهد. ویژگی `content` اندازه viewport را تعیین کرده و به `<head>` سند اضافه می‌شود:

```js
const meta = document.createElement("meta");
meta.name = "viewport";
meta.content = "width=device-width, initial-scale=1";
document.head.appendChild(meta);
```

برای اطلاعات بیشتر درباره تنظیم viewport، به [`<meta name="viewport">`](/en-US/docs/Web/HTML/Reference/Elements/meta/name/viewport) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("meta")}}