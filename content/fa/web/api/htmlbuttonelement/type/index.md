---
title: "HTMLButtonElement: type property"
---

---
title: "HTMLButtonElement: type property"
short-title: type
slug: Web/API/HTMLButtonElement/type
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.type
---

{{ApiRef("HTML DOM")}}

ویژگی **`type`** از رابط {{domxref("HTMLButtonElement")}} یک رشته است که نوع رفتار عنصر {{HTMLElement("button")}} را مشخص می‌کند.

این ویژگی، ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/button#type) عنصر {{HTMLElement("button")}} را بازتاب می‌دهد.

## مقدار

رشته‌ای که نوع را نشان می‌دهد.

مقادیر ممکن آن در بخشِ [انواع دکمه](/en-US/docs/Web/HTML/Reference/Elements/button#type) فهرست شده‌اند.

## مثال

### HTML

```html
<button id="button" type="reset">type</button>
```

### JavaScript

```js
const buttonElement = document.querySelector("#button");
console.log(buttonElement.type); // "reset"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگیِ {{domxref("HTMLTextAreaElement.type")}}
- ویژگیِ {{domxref("HTMLInputElement.type")}}