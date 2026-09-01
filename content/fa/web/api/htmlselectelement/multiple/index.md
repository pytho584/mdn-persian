---
title: "HTMLSelectElement: multiple property"
short-title: multiple
slug: Web/API/HTMLSelectElement/multiple
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.multiple
---

{{ APIRef("HTML DOM") }}

ویژگی **`multiple`** در رابط {{DOMxRef("HTMLSelectElement")}} مشخص میکند که کاربر میتواند بیش از یک گزینه را از فهرست گزینهها انتخاب کند. این ویژگی، صفت [`multiple`](/en-US/docs/Web/HTML/Reference/Elements/select#multiple) عنصر {{htmlelement("select")}} را بازتاب میدهد.

## مقدار

یک مقدار بولی.

## مثالها

```js
const selectElement = document.getElementById("comment");
console.log(selectElement.multiple);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("select")}}
- {{DOMXref("HTMLSelectElement.selectedOptions")}}
- {{DOMXref("HTMLSelectElement.length")}}
- {{DOMXref("HTMLSelectElement.selectedIndex")}}