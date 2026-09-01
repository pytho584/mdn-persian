---
title: "HTMLOptionElement: value property"
short-title: value
slug: Web/API/HTMLOptionElement/value
page-type: web-api-instance-property
browser-compat: api.HTMLOptionElement.value
---

{{ APIRef("HTML DOM") }}

ویژگی **`value`** در رابط {{DOMxRef("HTMLOptionElement")}} مقدار عنصر {{htmlelement("option")}} را به‌صورت یک رشته نمایش می‌دهد؛ یا اگر مقداری تنظیم نشده باشد، رشتهٔ خالی. این ویژگی، صفت [`value`](/en-US/docs/Web/HTML/Reference/Elements/option#value) عنصر را در صورت وجود منعکس می‌کند. در غیر این صورت، محتویات عنصر را برمی‌گرداند یا تنظیم می‌کند، مشابه ویژگی {{domxref("Node.textContent","textContent")}}.

## مقدار

رشته‌ای شامل مقدار صفت `value` در صورت وجود، یا محتویات عنصر.

## نمونه‌ها

```js
const optionElement = document.querySelector("datalist option:first-of-type");
const oldValue = optionElement.value;
optionElement.value = oldValue.toUpperCase();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("option")}}
- {{DOMXref("HTMLOptionElement.selected")}}
- {{DOMXref("HTMLOptionElement.defaultSelected")}}
- {{DOMXref("HTMLOptionElement.label")}}