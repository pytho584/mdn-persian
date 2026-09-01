---
title: "HTMLFormElement: autocomplete property"
short-title: autocomplete
slug: Web/API/HTMLFormElement/autocomplete
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.autocomplete
---

{{ APIRef("HTML DOM") }}

خاصیت **`autocomplete`** در رابط {{DOMxRef("HTMLFormElement")}} مشخص می‌کند که آیا مقدار کنترلها‌ی فرم می‌تواند به‌طور خودکار توسط مرورگر تکمیل شود یا نه. این خاصیت، ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) عنصر {{htmlelement("form")}} را منعکس می‌کند.

## مقدار

یک رشته؛ اگر به‌صراحت روی `"off"` تنظیم شده باشد، مقدار `"off"` برمی‌گرداند و در غیر این صورت همیشه `"on"` خواهد بود.

## مثال‌ها

```js
const formElement = document.getElementById("name");
console.log(formElement.autocomplete);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("form")}}
- ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) در HTML
- ویژگی [`aria-autocomplete`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-autocomplete) در ARIA
- [غیرفعال‌کردن تکمیل خودکار فرم](/en-US/docs/Web/Security/Practical_implementation_guides/Turning_off_form_autocompletion)