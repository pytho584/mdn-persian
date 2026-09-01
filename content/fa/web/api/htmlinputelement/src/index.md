---
title: "HTMLInputElement: src property"
short-title: src
slug: Web/API/HTMLInputElement/src
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.src
---

{{APIRef("HTML DOM")}}

ویژگی **`src`** در رابط {{DOMxRef("HTMLInputElement")}}، منبع تصویری را مشخص می‌کند که به‌عنوان دکمه ارسال گرافیکی نمایش داده می‌شود. این ویژگی، صفت [`src`](/en-US/docs/Web/HTML/Reference/Elements/input#src) عنصر {{htmlelement("input")}} را منعکس می‌کند.

ویژگی `src` فقط برای نوع [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است.

## مقدار

یک رشته (string).

## مثال‌ها

```js
const inputElement = document.getElementById("imageButton");
console.log(input.src);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMXref("HTMLButtonElement")}}
- {{HTMLElement("button")}}
- {{HTMLElement("input")}}
- {{HTMLElement("img")}}