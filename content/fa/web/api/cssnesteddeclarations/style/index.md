---
title: "CSSNestedDeclarations: style property"
short-title: style
slug: Web/API/CSSNestedDeclarations/style
page-type: web-api-instance-property
browser-compat: api.CSSNestedDeclarations.style
---

{{APIRef("CSSOM")}}

ویژگی فقط‑خواندنی **`style`** از رابط {{domxref("CSSNestedDeclarations")}} نشان‌دهندهٔ سبک‌های مرتبط با قوانین تو در تو است.

## مقدار

یک شیء {{domxref("CSSStyleProperties")}}.

اگرچه خود ویژگی `style` فقط‑خواندنی است به این معنا که نمی‌توانید شیء `CSSStyleProperties` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `style` مقداردهی کنید که معادل مقداردهی به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء `CSSStyleProperties` را با استفاده از متدهای {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## مثال‌ها

این شیوه‌نامه شامل یک {{domxref("cssRule","cssRules")}} تو در تو است.

اولین `console.log` ویژگی `style` سطح بالا را نشان می‌دهد، دومی پرس‌وجوی `@media` تو در تو را با سبک تو در توی آن نشان می‌دهد و سومی سبک تو در توی اعلام‌شده پس از پرس‌وجوی `@media` را نشان می‌دهد.

```css
.foo {
  font-size: 1.2rem;
  @media screen {
    color: tomato;
    background-color: darkgrey;
  }
  color: black;
}
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].style);
// { "0": "font-size" }
console.log(myRules[0].cssRules[0].cssRules[0].style);
// { "0": "color", "1": "background-color" }
console.log(myRules[0].cssRules[1].style);
// { "0": "color" }
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CSSNestedDeclarations")}}
- [قانون اعلام‌های تو در تو](/en-US/docs/Web/CSS/Guides/Nesting/Using#nested_declarations_rule)