---
title: CSSFunctionDeclarations
slug: Web/API/CSSFunctionDeclarations
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CSSFunctionDeclarations
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

رابط **`CSSFunctionDeclarations`** در [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) نمایانگر یک دنباله‌ی متوالی از اعلان‌های CSS است که درون بدنه‌ی یک {{cssxref("@function")}} قرار دارند.

این می‌تواند شامل [ویژگی‌های سفارشی CSS](/en-US/docs/Web/CSS/Guides/Cascading_variables/Using_custom_properties) و مقدار توصیف‌گر `results` درون بدنه‌ی `@function` باشد، اما بلوک‌هایی مانند قوانین-at {{cssxref("@media")}} را که ممکن است گنجانده شوند، شامل نمی‌شود. چنین بلوکی که در میان مجموعه‌ای از اعلان‌ها قرار گیرد، باعث می‌شود محتوای بدنه به اشیاء `CSSFunctionDeclarations` جداگانه‌ای تقسیم شود، همانطور که در نمایش [چندین `CSSFunctionDeclarations`](#multiple_cssfunctiondeclarations) مشاهده می‌کنید.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSFunctionDeclarations.style")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : یک شیء {{domxref("CSSFunctionDescriptors")}} را برمی‌گرداند که نمایانگر توصیف‌گرهای موجود در بدنه‌ی یک {{cssxref("@function")}} است.

## مثال‌ها

### استفاده‌ی پایه از `CSSFunctionDeclarations`

در این مثال، یک تابع سفارشی CSS تعریف می‌کنیم و سپس با استفاده از CSSOM به اعلان‌های آن دسترسی پیدا می‌کنیم.

#### CSS

```css live-sample___cssfunctiondeclarations-basics
@function --lighter(--color <color>, --lightness-adjust <number>: 0.2) returns
  <color> {
  --someVar: 100;
  result: oklch(from var(--color) calc(l + var(--lightness-adjust)) c h);
}
```

#### JavaScript

اسکریپت ما با گرفتن یک ارجاع به شیوه‌نامه‌ی متصل به سند با استفاده از {{domxref("HTMLStyleElement.sheet")}} شروع می‌شود، سپس یک ارجاع به تنها قانون موجود در شیوه‌نامه، یعنی `CSSFunctionRule`، از طریق {{domxref("CSSStylesheet.cssRules")}} به دست می‌آورد.

سپس با استفاده از {{domxref("CSSGroupingRule.cssRules", "cssRules[0]")}} به شیء `CSSFunctionDeclarations` که نمایانگر تنها دنباله‌ی پیوسته‌ی اعلان‌های درون تابع است دسترسی پیدا می‌کنیم، با استفاده از {{domxref("CSSFunctionDeclarations.style")}} به اطلاعات توصیف‌گر آن دسترسی می‌یابیم، و سپس طول توصیف‌گر و اطلاعات سبک را دریافت می‌کنیم. تمام این اطلاعات در کنسول ثبت می‌شوند.

```js live-sample___cssfunctiondeclarations-basics
// Get a CSSFunctionRule
const cssFunc = document.getElementById("css-output").sheet.cssRules[0];

// Accessing CSSFunctionDeclarations and CSSFunctionDescriptors
console.log(cssFunc.cssRules[0]); // CSSFunctionDeclarations
console.log(cssFunc.cssRules[0].style); // CSSFunctionDescriptors
console.log(cssFunc.cssRules[0].style.length);
console.log(cssFunc.cssRules[0].style.result);
```

قابل توجه‌ترین موارد:

- ویژگی `length` برابر با `2` است، زیرا متن توصیف‌گر دو بخش دارد (`--someVar: 100;` و `result: oklch(from var(--color) calc(l + var(--lightness-adjust)) c h);`).
- ویژگی `result` برابر با توصیف‌گر `result` بدنه‌ی `@function` است که `oklch(from var(--color) calc(l + var(--lightness-adjust)) c h)` می‌باشد.

### چندین `CSSFunctionDeclarations`

در این مثال، نشان می‌دهیم که چگونه یک قانون-at `@media` که در میان مجموعه‌ای از اعلان‌ها قرار می‌گیرد باعث تولید دو شیء `CSSFunctionDeclarations` می‌شود.

#### CSS

```css live-sample___multiple-cssfunctiondeclarations
@function --bar() {
  --x: 42;
  result: var(--y);
  @media (width > 1000px) {
    /* ... */
  }
  --y: var(--x);
}
```

#### JavaScript

اسکریپت ما با گرفتن یک ارجاع به شیوه‌نامه‌ی متصل به سند از طریق {{domxref("HTMLStyleElement.sheet")}} شروع می‌شود، سپس یک ارجاع به تنها قانون موجود در شیوه‌نامه، یعنی `CSSFunctionRule`، از طریق {{domxref("CSSStylesheet.cssRules")}} به دست می‌آورد.

سپس به {{domxref("CSSGroupingRule.cssRules")}} دسترسی پیدا می‌کنیم و مقدار آن را در کنسول ثبت می‌کنیم. این یک شیء {{domxref("CSSRuleList")}} شامل سه شیء را برمی‌گرداند:

- یک شیء `CSSFunctionDeclarations` نمایانگر بخش `--x: 42;result: var(--y);`
- یک شیء {{domxref("CSSMediaRule")}} نمایانگر قانون-at `@media`
- یک شیء دوم `CSSFunctionDeclarations` نمایانگر بخش `--y: var(--x);`

سپس چند جزئیات از هر شیء `CSSFunctionDeclarations` را در کنسول ثبت می‌کنیم — خود شیء، شیء {{domxref("CSSFunctionDescriptors")}} موجود در ویژگی `style` آن، و ویژگی {{domxref("CSSFunctionDescriptors.result")}}.

```js live-sample___multiple-cssfunctiondeclarations
console.log(cssFunc.cssRules[0]); // First CSSFunctionDeclarations
console.log(cssFunc.cssRules[0].style); // CSSFunctionDescriptors
console.log(cssFunc.cssRules[0].style.result);

console.log(cssFunc.cssRules[2]); // Second CSSFunctionDeclarations
console.log(cssFunc.cssRules[2].style); // CSSFunctionDescriptors
console.log(cssFunc.cssRules[2].style.result);
```

در حالت دوم، `result` یک رشته‌ی خالی برمی‌گرداند، زیرا بخش دوم اعلان‌ها شامل یک توصیف‌گر `result` نیست.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{cssxref("@function")}}
- {{domxref("CSSFunctionRule")}}
- {{domxref("CSSFunctionDescriptors")}}