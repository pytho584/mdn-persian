---
title: "HTMLSelectElement: name property"
short-title: name
slug: Web/API/HTMLSelectElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.name
---

{{ApiRef("HTML DOM")}}

ویژگی **`name`** در رابط {{domxref("HTMLSelectElement")}} نام عنصر {{HTMLElement("select")}} را مشخص می‌کند. این ویژگی، صفت [`name`](/en-US/docs/Web/HTML/Reference/Elements/select#name) عنصر را بازتاب می‌دهد.

## مقدار

یک رشته که نشان‌دهندهٔ نام عنصر است.

## مثال

```js
const selectElement = document.querySelector("#planets");
console.log(`Element's name: ${selectElement.name}`);
selectElement.name = "galaxies"; // sets or updates the element's name
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLSelectElement.value")}}
- {{domxref("HTMLSelectElement.selectedIndex")}}
- {{domxref("HTMLSelectElement.options")}}