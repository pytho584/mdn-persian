---
title: "HTMLFieldSetElement: name property"
short-title: name
slug: Web/API/HTMLFieldSetElement/name
page-type: web-api-instance-property
browser-compat: api.HTMLFieldSetElement.name
---

{{ApiRef("HTML DOM")}}

ویژگی **`name`** در رابط {{domxref("HTMLFieldSetElement")}} نشان‌دهنده نام عنصر {{HTMLElement("fieldset")}} است. این ویژگی، صفت [`name`](/en-US/docs/Web/HTML/Reference/Elements/fieldset#name) عنصر را منعکس می‌کند.

## Value

یک رشته که نام عنصر را نشان می‌دهد.

## Example

```js
const fs = document.querySelector("fieldset");
console.log(`Element's name: ${fs.name}`);
fs.name = "billing"; // sets or updates the element's name
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLFieldSetElement.elements")}}
- {{domxref("HTMLFieldSetElement.disabled")}}
- {{domxref("HTMLLegendElement")}}
- {{domxref("HTMLFormElement")}}
- {{HTMLElement("fieldset")}}
- {{HTMLElement("legend")}}
- {{HTMLElement("form")}}