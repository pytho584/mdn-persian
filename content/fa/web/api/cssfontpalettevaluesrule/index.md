---
title: CSSFontPaletteValuesRule
slug: Web/API/CSSFontPaletteValuesRule
page-type: web-api-interface
browser-compat: api.CSSFontPaletteValuesRule
---

{{APIRef("CSSOM")}}

رابطهٔ **`CSSFontPaletteValuesRule`** نمایانگر یک [ات-قانون](/en-US/docs/Web/CSS/Guides/Syntax/At-rules) از نوع {{cssxref("@font-palette-values")}} است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("CSSRule")}}، به ارث می‌برد._

- {{domxref("CSSFontPaletteValuesRule.name")}} {{ReadOnlyInline}}
  - : رشته‌ای شامل نام پالت فونت.
- {{domxref("CSSFontPaletteValuesRule.fontFamily")}} {{ReadOnlyInline}}
  - : رشته‌ای که خانواده‌های فونتی را که قانون باید روی آن‌ها اعمال شود، مشخص می‌کند.
- {{domxref("CSSFontPaletteValuesRule.basePalette")}} {{ReadOnlyInline}}
  - : رشته‌ای که پالت پایهٔ مرتبط با قانون را نشان می‌دهد.
- {{domxref("CSSFontPaletteValuesRule.overrideColors")}} {{ReadOnlyInline}}
  - : رشته‌ای که رنگ‌های بازنویسی‌شدهٔ پالت پایه و رنگ‌های جدید را نشان می‌دهد.

## روش‌های نمونه

_روش‌ها را از والد خود، {{domxref("CSSRule")}}، به ارث می‌برد._

## مثال‌ها

### خواندن خانوادهٔ فونت مرتبط با استفاده از CSSOM

در این مثال، ابتدا یک ات-قانون {{cssxref("@import")}} و یک ات-قانون {{cssxref("@font-palette-values")}} تعریف می‌شود. سپس قانون {{cssxref("@font-palette-values")}} خوانده شده و نام آن نمایش داده می‌شود. زیرساخت [نمونهٔ زندهٔ MDN](/en-US/docs/MDN/Writing_guidelines/Page_structures/Live_samples) همهٔ بلوک‌های CSS موجود در مثال را در یک استایل درون‌خطی واحد با شناسهٔ `css-output` ترکیب می‌کند، بنابراین ابتدا از {{domxref("document.getElementById()")}} برای یافتن آن stylesheet استفاده می‌کنیم. پالت، دومین {{domxref("CSSRule")}} در آن stylesheet خواهد بود. بنابراین، `rules[1]` یک شیء `CSSFontPaletteValuesRule` برمی‌گرداند که می‌توانیم از آن به `fontFamily` دسترسی داشته باشیم.

#### HTML

```html
<pre id="log">خانواده‌های فونت در ات-قانون @font-palette-values:</pre>
```

#### CSS

```css
@import "https://fonts.googleapis.com/css2?family=Bungee+Spice";

@font-palette-values --Alternate {
  font-family: "Bungee Spice";
  override-colors:
    0 #00ffbb,
    1 #007744;
}

.alternate {
  font-palette: --Alternate;
}
```

#### JavaScript

```js
const log = document.getElementById("log");

const rules = document.getElementById("css-output").sheet.cssRules;
const fontPaletteValuesRule = rules[1]; // یک رابط CSSFontPaletteValuesRule
log.textContent += ` ${fontPaletteValuesRule.fontFamily}`;
```

#### نتیجه

{{EmbedLiveSample("Read associated font family using CSSOM", "100", "40")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{cssxref("@font-palette-values")}}