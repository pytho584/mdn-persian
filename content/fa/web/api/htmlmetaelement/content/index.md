---
title: "HTMLMetaElement: content property"
short-title: content
slug: Web/API/HTMLMetaElement/content
page-type: web-api-instance-property
browser-compat: api.HTMLMetaElement.content
---

{{APIRef("HTML DOM")}}

خاصیت **`HTMLMetaElement.content`** مقدار ویژگی `content` را در دستورالعمل‌های pragma و داده‌های نام‌گذاری شده {{htmlelement("meta")}} به همراه {{domxref("HTMLMetaElement.name")}} یا {{domxref("HTMLMetaElement.httpEquiv")}} دریافت یا تنظیم می‌کند. برای اطلاعات بیشتر، به ویژگی [content](/en-US/docs/Web/HTML/Reference/Elements/meta#content) مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

### خواندن محتوای عنصر meta

مثال زیر یک عنصر `<meta>` را که دارای ویژگی `name` با مقدار `keywords` است، جستجو می‌کند. مقدار `content` در کنسول ثبت می‌شود تا [کلمات کلیدی](/en-US/docs/Web/HTML/Reference/Elements/meta/name#meta_names_defined_in_the_html_specification) سند نمایش داده شود:

```js
// given <meta name="keywords" content="documentation, HTML, web">
const meta = document.querySelector("meta[name='keywords']");
console.log(meta.content);
// "documentation, HTML, web"
```

### ایجاد یک عنصر meta با محتوا

مثال زیر یک عنصر `<meta>` جدید با ویژگی `name` برابر با [`description`](/en-US/docs/Web/HTML/Reference/Elements/meta/name#meta_names_defined_in_the_html_specification) ایجاد می‌کند. ویژگی `content` توضیحی از سند را تنظیم می‌کند و به عنصر `<head>` سند اضافه می‌شود:

```js
const meta = document.createElement("meta");
meta.name = "description";
meta.content =
  "The <meta> element can be used to provide document metadata in terms of name-value pairs, with the name attribute giving the metadata name, and the content attribute giving the value.";
document.head.appendChild(meta);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meta")}}
- {{domxref("HTMLMetaElement.name")}}
- {{domxref("HTMLMetaElement.httpEquiv")}}
- [یادگیری: ابرداده در HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/Webpage_metadata#metadata_the_meta_element)