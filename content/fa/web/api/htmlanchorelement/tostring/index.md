---
title: "HTMLAnchorElement: toString() method"
short-title: toString()
slug: Web/API/HTMLAnchorElement/toString
page-type: web-api-instance-method
browser-compat: api.HTMLAnchorElement.toString
---

{{ApiRef("URL API")}}

متد **`HTMLAnchorElement.toString()`** {{Glossary("stringifier")}} یک رشته حاوی کل URL را برمی‌گرداند. این متد یک نسخهٔ فقط‌خواندنی از {{domxref("HTMLAnchorElement.href")}} است.

## نحو

```js-nolint
toString()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک رشته حاوی URL کامل عنصر.

## مثال‌ها

### فراخوانی toString روی یک عنصر anchor

```js
// An <a id="myAnchor" href="/en-US/docs/HTMLAnchorElement"> element is in the document
const anchor = document.getElementById("myAnchor");
anchor.toString(); // returns 'https://developer.mozilla.org/en-US/docs/HTMLAnchorElement'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این متد به آن تعلق دارد.