---
title: "CSSFontFaceRule: style property"
short-title: style
slug: Web/API/CSSFontFaceRule/style
page-type: web-api-instance-property
browser-compat: api.CSSFontFaceRule.style
---

{{APIRef("CSSOM")}}

ویژگی فقط خواندنی **`style`** در رابط {{domxref("CSSFontFaceRule")}} یک شیء از نوع {{domxref("CSSFontFaceDescriptors")}} را برمی‌گرداند که نشان‌دهندهٔ توصیف‌گرهای (descriptors) موجود در بدنهٔ قانون {{cssxref("@font-face")}} است.

## مقدار

یک شیء {{domxref("CSSFontFaceDescriptors")}}.

اگرچه خود ویژگی `style` به این معنا فقط خواندنی است که نمی‌توانید شیء `CSSFontFaceDescriptors` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به `style` مقداردهی کنید که معادل مقداردهی به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء `CSSFontFaceDescriptors` را با استفاده از روش‌های {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## مثال‌ها

### استفادهٔ پایه

این مثال یک قانون {{cssxref("@font-face")}} تعریف می‌کند و سپس از `CSSFontFaceDescriptors` برای خواندن مقادیر توصیف‌گرها استفاده می‌کند.

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
    const descriptors = rule.style;
    if (descriptors instanceof CSSStyleDeclaration) {
      log(`rule.style is a CSSStyleDeclaration.`);
    } else {
      log(`rule.style is a CSSFontFaceDescriptors.`);
    }
    log("Descriptors:");
    log(` font-family: ${descriptors.fontFamily}`);
    log(` src: ${descriptors.src}`);
    log(` font-weight: ${descriptors["font-weight"]}`);
    log(` font-style: ${descriptors.fontStyle}`);
    log(` font-display: ${descriptors["font-display"]}`);
  }
}
```

#### نتیجه

{{EmbedLiveSample("Basic usage", "100%", "250px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}