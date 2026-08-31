---
title: "CSSFunctionDescriptors"
---

---
title: CSSFunctionDescriptors
slug: Web/API/CSSFunctionDescriptors
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CSSFunctionDescriptors
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

رابطهٔ **`CSSFunctionDescriptors`** در [مدل شیءِ CSS](/en-US/docs/Web/API/CSS_Object_Model) توصیف‌گرهای موجود در مجموعه‌ای از اعلان‌های CSS را نشان می‌دهد که توسط شیء {{domxref("CSSFunctionDeclarations")}} بازنمایی می‌شوند.

یک شیء `CSSFunctionDescriptors` از طریق ویژگی {{domxref("CSSFunctionDeclarations.style")}} قابل دسترسی است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های {{domxref("CSSStyleDeclaration")}} را به ارث می‌برد._

- {{domxref("CSSFunctionDescriptors.result")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای را برمی‌گرداند که توصیف‌گر `result` را نشان می‌دهد، در صورتی که در مجموعه‌اعلان‌های مرتبط وجود داشته باشد.

## مثال‌ها

### استفادهٔ پایه از `CSSFunctionDescriptors`

در این مثال، یک تابع سفارشی CSS تعریف می‌کنیم و سپس با استفاده از CSSOM به اعلان‌های آن دسترسی پیدا می‌کنیم.

#### CSS

CSS ما یک تابع سفارشی را با استفاده از قاعدهٔ at-rule {{cssxref("@function")}} تعریف می‌کند. نام تابع `--lighter()` است و نسخهٔ روشن‌تر یک رنگ ورودی را خروجی می‌دهد. `--lighter()` دو پارامتر می‌پذیرد: یک {{cssxref("&lt;color&gt;")}} و یک {{cssxref("&lt;number&gt;")}}. این تابع یک رنگ {{cssxref("color_value/oklch", "oklch()")}} را برمی‌گرداند که با استفاده از [نحو رنگ نسبی](/en-US/docs/Web/CSS/Guides/Colors/Using_relative_colors) ساخته شده است؛ رنگ ورودی به یک رنگ `oklch()` تبدیل می‌شود و کانال روشنایی آن به اندازهٔ عدد ورودی افزایش می‌یابد.

```css live-sample___cssfunctiondescriptors-basics
@function --lighter(--color <color>, --lightness-adjust <number>: 0.2) returns
  <color> {
  result: oklch(from var(--color) calc(l + var(--lightness-adjust)) c h);
}
```

#### JavaScript

اسکریپت ما با به‌دست آوردن ارجاعی به شیوه‌نامهٔ متصل به سند با استفاده از {{domxref("HTMLStyleElement.sheet")}} شروع می‌شود و سپس ارجاعی به تنها قاعدهٔ موجود در شیوه‌نامه، یعنی `CSSFunctionRule`، از طریق {{domxref("CSSStylesheet.cssRules")}} به دست می‌آورد.

سپس با استفاده از {{domxref("CSSGroupingRule.cssRules", "cssRules[0]")}} به شیء `CSSFunctionDeclarations` که تنها مجموعهٔ پیوستهٔ اعلان‌های داخل تابع را نشان می‌دهد دسترسی پیدا می‌کنیم، اطلاعات توصیف‌گر آن را با استفاده از {{domxref("CSSFunctionDeclarations.style")}} می‌خوانیم و سپس به اطلاعات سبک توصیف‌گر دسترسی می‌یابیم. تمام این اطلاعات در کنسول ثبت می‌شوند.

```js live-sample___cssfunctiondescriptors-basics
// دریافت یک CSSFunctionRule
const cssFunc = document.getElementById("css-output").sheet.cssRules[0];

// دسترسی به CSSFunctionDeclarations و CSSFunctionDescriptors
console.log(cssFunc.cssRules[0]); // CSSFunctionDeclarations
console.log(cssFunc.cssRules[0].style); // CSSFunctionDescriptors
console.log(cssFunc.cssRules[0].style.result);
```

قابل توجه‌ترین نکته این است که ویژگی `result` برابر با توصیف‌گر `result` در بدنهٔ `@function` است که عبارت است از `oklch(from var(--color) calc(l + var(--lightness-adjust)) c h)`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{cssxref("@function")}}
- {{domxref("CSSFunctionRule")}}
- {{domxref("CSSFunctionDeclarations")}}