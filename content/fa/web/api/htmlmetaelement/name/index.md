---
title: "HTMLMetaElement: name property"
short-title: name
slug: Web/API/HTMLMetaElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLMetaElement.name
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMetaElement.name`** در ترکیب با {{domxref("HTMLMetaElement.content")}} برای تعریف جفت‌های نام-مقدار برای فراداده‌های یک سند استفاده می‌شود. صفت `name` نام فراداده و صفت `content` مقدار آن را تعریف می‌کند.

## مقدار

یک رشته.

## مثال‌ها

### خواندن نام فراداده یک عنصر meta

مثال زیر اولین عنصر `<meta>` را در یک سند جستجو می‌کند. مقدار `name` در کنسول ثبت می‌شود و نشان می‌دهد که [کلمات کلیدی](/en-US/docs/Web/HTML/Reference/Elements/meta/name#meta_names_defined_in_the_html_specification) برای سند مشخص شده‌اند:

```js
// given <meta name="keywords" content="documentation, HTML, web technologies">
const meta = document.querySelector("meta");
console.log(meta.name);
// "keywords"
```

### ایجاد یک عنصر meta با فراداده `author`

مثال زیر یک عنصر `<meta>` جدید با صفت `name` تنظیم شده به [`author`](/en-US/docs/Web/HTML/Reference/Elements/meta/name#meta_names_defined_in_the_html_specification) ایجاد می‌کند. صفت `content` نویسنده سند را تنظیم می‌کند و عنصر به `<head>` سند اضافه می‌شود:

```js
let meta = document.createElement("meta");
meta.name = "author";
meta.content = "Franz Kafka";
document.head.appendChild(meta);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- {{HTMLElement("meta")}}
- [مقادیر ممکن برای صفت name](/en-US/docs/Web/HTML/Reference/Elements/meta/name#meta_names_defined_in_the_html_specification)