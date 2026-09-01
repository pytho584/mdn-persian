---
title: "HTMLSelectElement: autocomplete property"
short-title: autocomplete
slug: Web/API/HTMLSelectElement/autocomplete
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.autocomplete
---

{{ APIRef("HTML DOM") }}

ویژگی **`autocomplete`** در رابط {{DOMxRef("HTMLSelectElement")}} نشان می‌دهد که آیا مقدار کنترول می‌تواند به‌طور خودکار توسط مرورگر تکمیل شود یا خیر. این ویژگی منعکس‌کننده صفت [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/select#autocomplete) عنصر `<select>` است.

## مقدار

یک رشته که مقدار صفت `autocomplete` را نشان می‌دهد (`"on"`، `"off"` یا یک [`<token-list>`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete#token_list_tokens)) یا رشته خالی (`""`) اگر مشخص نشده باشد.

## مثال‌ها

```js
const selectElement = document.getElementById("favorite-fruit");
console.log(textArea.autocomplete);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("select")}}
- {{HTMLElement("option")}}
- صفت HTML [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
- صفت ARIA [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete)
- [غیرفعال کردن تکمیل خودکار فرم‌ها](/en-US/docs/Web/Security/Practical_implementation_guides/Turning_off_form_autocompletion)