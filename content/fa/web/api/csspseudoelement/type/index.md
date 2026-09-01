---
title: "CSSPseudoElement: type property"
short-title: type
slug: Web/API/CSSPseudoElement/type
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSPseudoElement.type
---

{{APIRef}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`type`** در رابط {{DOMxRef("CSSPseudoElement")}} نوع شبه‌عنصر را به صورت یک رشته برمی‌گرداند که در قالب یک [سلکتور CSS](/en-US/docs/Web/CSS/Guides/Pseudo-elements#selectors) بیان می‌شود.

## مقدار

رشته‌ای که نوع شبه‌عنصر نمایش‌داده‌شده توسط `CSSPseudoElement` را نشان می‌دهد. مقادیر ممکن عبارت‌اند از:

- {{cssxref("::after")}}
- {{cssxref("::before")}}
- {{cssxref("::marker")}}

## مثال‌ها

### استفاده پایه

مثال زیر رابطه بین `CSSPseudoElement.type` و {{DOMxRef("Element.pseudo()")}} را نشان می‌دهد:

```js
const myElement = document.querySelector("q");
const mySelector = "::after";
const cssPseudoElement = myElement.pseudo(mySelector);
const typeOfPseudoElement = cssPseudoElement.type;

console.log(mySelector === typeOfPseudoElement); // خروجی: true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("Element.pseudo()")}}
- {{DOMxRef("CSSPseudoElement.pseudo()")}}
- [فهرست شبه‌عنصرها](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements#alphabetical_index)