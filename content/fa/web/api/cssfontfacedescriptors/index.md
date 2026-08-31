---
title: CSSFontFaceDescriptors
slug: Web/API/CSSFontFaceDescriptors
page-type: web-api-interface
browser-compat: api.CSSFontFaceDescriptors
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSFontFaceDescriptors`** نمایانگر یک بلوک اعلان‌های CSS برای یک [at-rule](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) با نام {{cssxref("@font-face")}} است.

هر توصیفگر در بدنهٔ قانون {{cssxref("@font-face")}} مربوطه را می‌توان با استفاده از نام ویژگی kebab-case آن در [نماد براکتی](/en-US/docs/Learn_web_development/Core/Scripting/Object_basics#bracket_notation) یا با استفاده از نسخهٔ camel-case نام ویژگی در [نماد نقطه‌ای](/en-US/docs/Learn_web_development/Core/Scripting/Object_basics#dot_notation) مورد دسترسی قرار داد. برای مثال، می‌توانید به توصیفگر CSS با نام `font-family` به‌صورت `style["font-family"]` یا `style.fontFamily` دسترسی داشته باشید، که در آن `style` نمونه‌ای از `CSSFontFaceDescriptors` است.

> [!NOTE]
> رابطهٔ {{domxref("CSSFontFaceRule")}} نمایانگر یک at-rule با نام {{cssxref("@font-face")}} است و ویژگی {{domxref("CSSFontFaceRule.style")}} نمونه‌ای از این شیء است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های نمونه را از نیای خود، {{domxref("CSSStyleDeclaration")}}، به ارث می‌برد._

نام‌های ویژگی زیر، به‌صورت kebab-case (دسترسی با نماد براکتی) و camel-case (دسترسی با نماد نقطه‌ای)، هر کدام نمایانگر مقدار یک توصیفگر در قانون `@font-face` مربوطه هستند:

- `font-display` یا `fontDisplay`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/font-display", "font-display")}} را نشان می‌دهد.
- `font-family` یا `fontFamily`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/font-family", "font-family")}} را نشان می‌دهد.
- `font-feature-settings` یا `fontFeatureSettings`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/font-feature-settings", "font-feature-settings")}} را نشان می‌دهد.
- `font-stretch` یا `fontStretch`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/font-stretch", "font-stretch")}} را نشان می‌دهد.
- `font-style` یا `fontStyle`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/font-style", "font-style")}} را نشان می‌دهد.
- `font-weight` یا `fontWeight`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/font-weight", "font-weight")}} را نشان می‌دهد.
- `font-width` یا `fontWidth` {{experimental_inline}}
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/font-width", "font-width")}} را نشان می‌دهد.
- `size-adjust` یا `sizeAdjust`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/size-adjust", "size-adjust")}} را نشان می‌دهد.
- `src`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/src", "src")}} را نشان می‌دهد.
- `unicode-range` یا `unicodeRange`
  - : رشته‌ای که مقدار توصیفگر {{cssxref("@font-face/unicode-range", "unicode-range")}} را نشان می‌دهد.

## متدهای نمونه

_متد خاصی ندارد؛ متدهای نیای خود {{domxref("CSSStyleDeclaration")}} را به ارث می‌برد._

## مثال‌ها

### دسترسی به مقادیر توصیفگرهای @font-face

این مثال یک قانون {{cssxref("@font-face")}} تعریف می‌کند و سپس با استفاده از `CSSFontFaceDescriptors` مقادیر توصیفگرها را بازخوانی می‌کند.

#### CSS

```css
@font-face {
  font-family: "MyHelvetica";
  src:
    local("Helvetica Neue Bold"),
    local("HelveticaNeue-Bold"),
    url("MgOpenModernaBold.woff2") format("woff2");
  font-weight: bold;
  font-style: normal;
  font-display: swap;
}
```

```css hidden
#log {
  height: 200px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### JavaScript

```js
const myRules = document.getElementById("css-output").sheet.cssRules;
for (const rule of myRules) {
  if (rule instanceof CSSFontFaceRule) {
    const style = rule.style; // a CSSFontFaceDescriptors
    log(`font-family: ${style.fontFamily}`);
    log(`src: ${style.src}`);
    log(`font-weight: ${style["font-weight"]}`);
    log(`font-style: ${style.fontStyle}`);
    log(`font-display: ${style["font-display"]}`);
  }
}
```

#### نتیجه

{{EmbedLiveSample("Accessing @font-face descriptor values", "100%", "250px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSFontFaceRule")}}
- {{domxref("CSSFontFaceRule.style")}}
- {{cssxref("@font-face")}}