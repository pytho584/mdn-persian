---
title: "HTMLOptGroupElement: label property"
short-title: label
slug: Web/API/HTMLOptGroupElement/label
page-type: web-api-instance-property
browser-compat: api.HTMLOptGroupElement.label
---

{{ APIRef("HTML DOM") }}

ویژگی **`label`** در رابط {{domxref("HTMLOptGroupElement")}} یک مقدار رشتهای است که صفت [`label`](/en-US/docs/Web/HTML/Reference/Elements/optgroup#label) عنصر {{htmlelement("optgroup")}} را بازتاب می‌دهد؛ این صفت یک برچسب متنی برای گروه گزینه‌ها فراهم می‌کند.

## مقدار

یک رشته.

## مثال‌ها

```js
const optionGroup = document.getElementById("groupB");
console.log(optionGroup.label);
optionGroup.label = `${optionGroup.label} (${optionGroup.children.length})`;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{htmlelement("optgroup")}}
- صفت [`label`](/en-US/docs/Web/HTML/Reference/Elements/optgroup#label) در HTML
