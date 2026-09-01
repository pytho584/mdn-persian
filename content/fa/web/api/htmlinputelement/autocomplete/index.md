---
title: "HTMLInputElement: autocomplete property"
short-title: autocomplete
slug: Web/API/HTMLInputElement/autocomplete
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.autocomplete
---

{{ APIRef("HTML DOM") }}

ویژگی **`autocomplete`** در رابط {{DOMxRef("HTMLInputElement")}} مشخص می‌کند که آیا مقدار کنترل می‌تواند توسط مرورگر به‌طور خودکار تکمیل شود. این ویژگی منعکس‌کننده صفت [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) عنصر {{htmlelement("input")}} است.

## مقدار

یک رشته؛ مقدار صفت `autocomplete` (`"on"`، `"off"`، یک [`<token-list>`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete#token_list_tokens))، یا رشته خالی `""` در صورت عدم تعیین.

## مثال‌ها

```js
const inputElement = document.getElementById("name");
console.log(inputElement.autocomplete);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{HTMLElement("input")}}
- ویژگی {{DOMxRef("HTMLInputElement.value")}}
- صفت HTML [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
- صفت ARIA [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete)
- [غیرفعال‌سازی تکمیل خودکار](/en-US/docs/Web/Security/Practical_implementation_guides/Turning_off_form_autocompletion)