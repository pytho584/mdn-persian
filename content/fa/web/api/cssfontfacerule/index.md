---
title: CSSFontFaceRule
slug: Web/API/CSSFontFaceRule
page-type: web-api-interface
browser-compat: api.CSSFontFaceRule
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSFontFaceRule`** یک [قانون at](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) از نوع {{cssxref("@font-face")}} را نمایش می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSFontFaceRule.style")}} {{ReadOnlyInline}}
  - : یک شیء {{domxref("CSSFontFaceDescriptors")}} برمی‌گرداند که امکان خواندن و تنظیم توصیف‌گرهای قانون at مربوط به {{cssxref("@font-face")}} را فراهم می‌کند.

## روش‌های نمونه

_روش‌ها را از والد خود {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

### دسترسی به ویژگی‌های @font-face

در این مثال، یک قانون {{cssxref("@font-face")}} تعریف می‌شود و سپس قوانین موجود در صفحه پیمایش می‌شوند تا `CSSFontFaceRule` مربوطه پیدا شود. در ادامه، برخی از ویژگی‌ها در خروجی ثبت می‌شوند.

#### CSS

```css
@font-face {
  font-family: "MyHelvetica";
  src:
    local("Helvetica Neue Bold"), local("HelveticaNeue-Bold"),
    url("MgOpenModernaBold.woff2");
  font-weight: bold;
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

#### JavaScript

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const myRules = document.getElementById("css-output").sheet.cssRules;
for (const rule of myRules) {
  if (rule instanceof CSSFontFaceRule) {
    log(`this: ${rule}`);
    log(` cssText: ${rule.cssText}`);
    log(` parentRule: ${rule.parentRule}`);
    log(` parentStyleSheet: ${rule.parentStyleSheet}`);
    log(` type: ${rule.type}`);
    log(` style: ${rule.style}`);
  }
}
```

#### نتیجه

{{EmbedLiveSample("Accessing @font-face properties", "100%", "250px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}