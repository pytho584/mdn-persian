---
title: "HTMLInputElement: defaultChecked property"
short-title: defaultChecked
slug: Web/API/HTMLInputElement/defaultChecked
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.defaultChecked
---

{{ APIRef("HTML DOM") }}

ویژگی **`defaultChecked`** از رابط {{DOMxRef("HTMLInputElement")}} وضعیت پیش‌فرض علامت‌خورده بودن عنصر را مشخص می‌کند. این ویژگی منعکس‌کننده ویژگی [`checked`](/en-US/docs/Web/HTML/Reference/Elements/input#checked) عنصر {{htmlelement("input")}} است.

ویژگی بولی [`checked`](/en-US/docs/Web/HTML/Reference/Elements/input#checked) برای انواع ورودی `radio` ([`<input type="radio">`](/en-US/docs/Web/HTML/Reference/Elements/input/radio)) و `checkbox` ([`<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox)) معتبر است. وجود این ویژگی، ویژگی `defaultChecked` را به `true` تنظیم می‌کند.

## Value

یک مقدار بولی.

## Examples

```js
const inputElement = document.getElementById("contactMail");
console.log(inputElement.defaultChecked);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLElement("input")}}
- {{cssxref(":default")}} pseudo-class
- {{cssxref(":checked")}} pseudo-class