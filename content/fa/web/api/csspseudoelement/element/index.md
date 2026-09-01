---
title: "CSSPseudoElement: element property"
short-title: element
slug: Web/API/CSSPseudoElement/element
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSPseudoElement.element
---

{{APIRef}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`element`** در رابط {{DOMxRef("CSSPseudoElement")}} ارجاعی به عنصرِ مبدأِ نهاییِ شبه‌عنصر بازمی‌گرداند.

این ویژگی با ویژگی {{DOMxRef("CSSPseudoElement.parent")}} تفاوت دارد؛ ویژگی `parent` ارجاعی به _مبدأ بلافصلِ_ شبه‌عنصر بازمی‌گرداند: این می‌تواند یک {{DOMxRef("Element")}} یا در مورد [شبه‌عنصرهای تودرتو](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements#nesting_pseudo-elements)، یک `CSSPseudoElement` باشد.

## مقدار

یک {{DOMxRef("Element")}} که عنصر مبدأِ نهاییِ شبه‌عنصر را نشان می‌دهد.

## مثال‌ها

### استفادهٔ پایه

مثال زیر رابطه بین `CSSPseudoElement.element` و {{DOMxRef("Element.pseudo()")}} را نشان می‌دهد:

```js
const myElement = document.querySelector("q");
const cssPseudoElement = myElement.pseudo("::after");
const originatingElement = cssPseudoElement.element;

console.log(myElement === originatingElement); // خروجی: true
console.log(myElement.parentElement === originatingElement); // خروجی: false
console.log(myElement.lastElementChild === cssPseudoElement); // خروجی: false
console.log(myElement.lastChild === cssPseudoElement); // خروجی: false
console.log(myElement.nextElementSibling === cssPseudoElement); // خروجی: false
console.log(myElement.nextSibling === cssPseudoElement); // خروجی: false
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("CSSPseudoElement.parent")}}
- {{DOMxRef("CSSPseudoElement.pseudo()")}}
- {{DOMxRef("Element.pseudo()")}}