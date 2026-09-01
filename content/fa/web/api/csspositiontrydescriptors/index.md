---
title: CSSPositionTryDescriptors
slug: Web/API/CSSPositionTryDescriptors
page-type: web-api-interface
browser-compat: api.CSSPositionTryDescriptors
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSPositionTryDescriptors`** ویژگی‌هایی را تعریف می‌کند که فهرست توصیفگرهای (descriptorهای) CSS قابل تنظیم در بدنهٔ یک [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) از نوع {{cssxref("@position-try")}} را نشان می‌دهند.

هر توصیفگر در بدنهٔ at-rule مربوط به {{cssxref("@position-try")}} را می‌توان یا با نام ویژگی آن در [نشانه‌گذاری کروشه‌ای (bracket notation)](/en-US/docs/Learn_web_development/Core/Scripting/Object_basics#bracket_notation) یا با نسخهٔ camel-case نام ویژگی «propertyName» در [نشانه‌گذاری نقطه‌ای (dot notation)](/en-US/docs/Learn_web_development/Core/Scripting/Object_basics#dot_notation) دسترسی پیدا کرد.
برای مثال، می‌توانید به ویژگی CSS «property-name» به صورت `style["property-name"]` یا `style.propertyName` دسترسی داشته باشید، که در آن `style` یک نمونه از `CSSPositionTryDescriptors` است.
ویژگی‌ای با نام تک‌کلمه‌ای مانند {{cssxref("height")}} را می‌توان با هر دو نشانه‌گذاری به کار برد: `style["height"]` یا `style.height`.

> [!NOTE]
> رابط {{domxref("CSSPositionTryRule")}} یک at-rule از نوع {{cssxref("@position-try")}} را نشان می‌دهد و ویژگی {{domxref("CSSPositionTryRule.style")}} نمونه‌ای از این شیء است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از ancestor خود، یعنی {{domxref("CSSStyleDeclaration")}}، به ارث می‌برد._

نام‌های ویژگی زیر، هم به صورت snake-case (دسترسی با نشانه‌گذاری کروشه‌ای) و هم به صورت camel-case (دسترسی با نشانه‌گذاری نقطه‌ای)، هر کدام مقدار یک توصیفگر را در at-rule مربوط به `@position-try` نشان می‌دهند:

- `align-self` یا `alignSelf`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("align-self")}} را نشان می‌دهد.
- `block-size` یا `blockSize`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("block-size")}} را نشان می‌دهد.
- `bottom`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("bottom")}} را نشان می‌دهد.
- `height`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("height")}} را نشان می‌دهد.
- `inline-size` یا `inlineSize`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("inline-size")}} را نشان می‌دهد.
- `inset`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("inset")}} را نشان می‌دهد.
- `position-area` یا `positionArea`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("position-area")}} را نشان می‌دهد.
- `inset-block` یا `insetBlock`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("inset-block")}} را نشان می‌دهد.
- `inset-block-end` یا `insetBlockEnd`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("inset-block-end")}} را نشان می‌دهد.
- `inset-block-start` یا `insetBlockStart`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("inset-block-start")}} را نشان می‌دهد.
- `inset-inline` یا `insetInline`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("inset-inline")}} را نشان می‌دهد.
- `inset-inline-end` یا `insetInlineEnd`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("inset-inline-end")}} را نشان می‌دهد.
- `inset-inline-start` یا `insetInlineStart`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("inset-inline-start")}} را نشان می‌دهد.
- `justify-self` یا `justifySelf`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("justify-self")}} را نشان می‌دهد.
- `left`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("left")}} را نشان می‌دهد.
- `margin`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin")}} را نشان می‌دهد.
- `margin-block` یا `marginBlock`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-block")}} را نشان می‌دهد.
- `margin-block-end` یا `marginBlockEnd`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-block-end")}} را نشان می‌دهد.
- `margin-block-start` یا `marginBlockStart`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-block-start")}} را نشان می‌دهد.
- `margin-bottom` یا `marginBottom`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-bottom")}} را نشان می‌دهد.
- `margin-inline` یا `marginInline`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-inline")}} را نشان می‌دهد.
- `margin-inline-end` یا `marginInlineEnd`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-inline-end")}} را نشان می‌دهد.
- `margin-inline-start` یا `marginInlineStart`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-inline-start")}} را نشان می‌دهد.
- `margin-left` یا `marginLeft`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-left")}} را نشان می‌دهد.
- `margin-right` یا `marginRight`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-right")}} را نشان می‌دهد.
- `margin-top` یا `marginTop`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("margin-top")}} را نشان می‌دهد.
- `max-block-size` یا `maxBlockSize`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("max-block-size")}} را نشان می‌دهد.
- `max-height` یا `maxHeight`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("max-height")}} را نشان می‌دهد.
- `max-inline-size` یا `maxInlineSize`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("max-inline-size")}} را نشان می‌دهد.
- `max-width` یا `maxWidth`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("max-width")}} را نشان می‌دهد.
- `min-block-size` یا `minBlockSize`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("min-block-size")}} را نشان می‌دهد.
- `min-height` یا `minHeight`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("min-height")}} را نشان می‌دهد.
- `min-inline-size` یا `minInlineSize`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("min-inline-size")}} را نشان می‌دهد.
- `min-width` یا `minWidth`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("min-width")}} را نشان می‌دهد.
- `place-self` یا `placeSelf`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("place-self")}} را نشان می‌دهد.
- `position-anchor` یا `positionAnchor`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("position-anchor")}} را نشان می‌دهد.
- `right`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("right")}} را نشان می‌دهد.
- `top`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("top")}} را نشان می‌دهد.
- `width`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("width")}} را نشان می‌دهد.

## روش‌های نمونه

_روش خاصی ندارد؛ روش‌ها را از ancestor خود، یعنی {{domxref("CSSStyleDeclaration")}}، به ارث می‌برد._

## مثال‌ها

CSS شامل یک at-rule از نوع `@position-try` با نام `--custom-right` و سه توصیفگر است.

```css
@position-try --custom-right {
  position-area: right;
  width: 100px;
  margin-left: 10px;
}
```

```js
const myRules = document.styleSheets[0].cssRules;
const tryOption = myRules[0]; // a CSSPositionTryRule
console.log(tryOption.style); // "[object CSSPositionTryDescriptors]"
console.log(tryOption.style.margin); // "0 0 0 10px"
console.log(tryOption.style["position-area"]); // "right"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{DOMxRef("CSSPositionTryRule")}}
- {{cssxref("@position-try")}}
- {{cssxref("position-try-fallbacks")}}
- [ماژول CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning)
- [استفاده از CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using)
- [مدیریت سرریز: گزینه‌های try و پنهان‌سازی شرطی](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding)