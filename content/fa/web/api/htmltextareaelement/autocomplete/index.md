---
title: "HTMLTextAreaElement: autocomplete property"
---

---
title: "HTMLTextAreaElement: autocomplete property"
short-title: autocomplete
slug: Web/API/HTMLTextAreaElement/autocomplete
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.autocomplete
---

{{ APIRef("HTML DOM") }}

ویژگی **`autocomplete`** در رابط {{DOMxRef("HTMLTextAreaElement")}} مشخص می‌کند که آیا مقدار کنترل می‌تواند به‌طور خودکار توسط مرورگر تکمیل شود یا نه. این ویژگی بازتابی از صفت [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/textarea#autocomplete) عنصر `<textarea>` است.

## مقدار

یک رشته که مقدار صفت `autocomplete` را نشان می‌دهد (`"on"`، `"off"`، یا یک [`<token-list>`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete#token_list_tokens))، یا اگر مقداردهی نشده باشد، رشتهٔ خالی (`""`).

## مثال‌ها

```js
const textareaElement = document.getElementById("comment");
console.log(textArea.autocomplete);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("textarea")}}
- صفت HTML [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
- صفت ARIA [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete)
- [غیرفعال کردن تکمیل خودکار](/en-US/docs/Web/Security/Practical_implementation_guides/Turning_off_form_autocompletion)