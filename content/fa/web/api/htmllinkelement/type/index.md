---
title: "HTMLLinkElement: type property"
short-title: type
slug: Web/API/HTMLLinkElement/type
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.type
---

{{APIRef("HTML DOM")}}

ویژگی **`type`** در رابط {{domxref("HTMLLinkElement")}} یک رشته است که {{glossary("MIME type","نوع MIME")}} منبع مرتبط‌شده را بازتاب می‌دهد.

این ویژگی، ویژگی `type` عنصر {{HTMLElement("link")}} را بازتاب می‌دهد.

## مقدار

یک رشته که باید یک رشته معتبر از نوع MIME باشد.

## مثال‌ها

```html
<link
  id="el"
  rel="apple-touch-icon"
  sizes="114x114"
  href="apple-icon-114.png"
  type="image/png" />
```

```js
const el = document.getElementById("el");
console.log(el.type); // Output: "image/png"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}