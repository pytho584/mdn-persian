---
title: "CSSFunctionRule"
---

---
title: CSSFunctionRule
slug: Web/API/CSSFunctionRule
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CSSFunctionRule
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

رابط **`CSSFunctionRule`** در [مدل شیءِ CSS](/en-US/docs/Web/API/CSS_Object_Model) نمایانگر [قواعد at](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) مربوط به تابع سفارشی ({{cssxref("@function")}}) در CSS است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از {{domxref("CSSGroupingRule")}} به ارث می‌برد._

- {{domxref("CSSFunctionRule.name")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای را برمی‌گرداند که نام تابع سفارشی را نشان می‌دهد.
- {{domxref("CSSFunctionRule.returnType")}} {{ReadOnlyInline}} {{experimental_inline}}
  - : رشته‌ای را برمی‌گرداند که نوع بازگشتی تابع سفارشی را نشان می‌دهد.

## متدهای نمونه

_این رابط همچنین متدهایی را از {{domxref("CSSGroupingRule")}} به ارث می‌برد._

- {{domxref("CSSFunctionRule.getParameters()")}} {{experimental_inline}}
  - : آرایه‌ای از اشیاء را برمی‌گرداند که پارامترهای تابع سفارشی را نشان می‌دهند.

## مثال‌ها

### استفادهٔ پایه از `CSSFunctionRule`

در این مثال، یک تابع سفارشی CSS تعریف می‌کنیم و سپس با استفاده از CSSOM به آن دسترسی پیدا می‌کنیم.

#### CSS

CSS ما با استفاده از قاعدهٔ at مربوط به {{cssxref("@function")}} یک تابع سفارشی تعریف می‌کند. نام این تابع `--lighter()` است و نسخهٔ روشن‌تری از یک رنگ ورودی را خروجی می‌دهد. `--lighter()` دو پارامتر می‌پذیرد: یک {{cssxref("&lt;color&gt;")}} و یک {{cssxref("&lt;number&gt;")}}. این تابع یک رنگ {{cssxref("color_value/oklch", "oklch()")}} را که با استفاده از [نحو رنگ نسبی](/en-US/docs/Web/CSS/Guides/Colors/Using_relative_colors) ساخته شده است برمی‌گرداند؛ رنگ ورودی به یک رنگ `oklch()` تبدیل می‌شود و کانال روشنایی آن به اندازهٔ عدد ورودی افزایش می‌یابد.

```css live-sample___cssfunctionrule-basics
@function --lighter(--color <color>, --lightness-adjust <number>: 0.2) returns
  <color> {
  result: oklch(from var(--color) calc(l + var(--lightness-adjust)) c h);
}
```

#### جاوااسکریپت

اسکریپت ما ابتدا با استفاده از {{domxref("HTMLStyleElement.sheet")}} ارجاعی به شیوه‌نامهٔ متصل به سند می‌گیرد و سپس از طریق {{domxref("CSSStylesheet.cssRules")}} ارجاعی به تنها قاعدهٔ موجود در شیوه‌نامه، یعنی `CSSFunctionRule`، می‌گیرد. سپس هر یک از اعضای `CSSFunctionRule` را در کنسول ثبت می‌کنیم.

```js live-sample___cssfunctionrule-basics
// Get a CSSFunctionRule
const cssFunc = document.getElementById("css-output").sheet.cssRules[0];

// Accessing CSSFunctionRule members
console.log(cssFunc.name);
console.log(cssFunc.returnType);
console.log(cssFunc.getParameters());
```

- ویژگی `name` برابر با `--lighter` است.
- ویژگی `returnType` برابر با `<color>` است.
- متد `getParameters()` آرایه‌ای برمی‌گرداند که به این شکل است:
  ```js
  [
    { name: "--color", type: "<color>" },
    { defaultValue: "0.2", name: "--lightness-adjust", type: "<number>" },
  ];
  ```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{cssxref("@function")}}
- {{domxref("CSSFunctionDescriptors")}}
- {{domxref("CSSFunctionDeclarations")}}