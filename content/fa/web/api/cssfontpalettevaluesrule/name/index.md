```yaml
---
title: "CSSFontPaletteValuesRule: name property"
short-title: name
slug: Web/API/CSSFontPaletteValuesRule/name
page-type: web-api-instance-property
browser-compat: api.CSSFontPaletteValuesRule.name
---
```

{{APIRef("CSSOM")}}

ویژگی فقط خواندنی **`name`** در رابط {{domxref("CSSFontPaletteValuesRule")}}، نامی را نشان می‌دهد که قاعده at-rule {{CSSxRef("@font-palette-values")}} مرتبط را شناسایی می‌کند. یک نام معتبر همیشه با دو خط تیره شروع می‌شود، مانند `--Alternate`.

## مقدار

یک رشته که با دو خط تیره شروع می‌شود.

## مثال‌ها

### خواندن نام at-rule

این مثال ابتدا یک قاعده {{cssxref("@import")}} و یک قاعده {{cssxref("@font-palette-values")}} تعریف می‌کند. سپس قاعده {{cssxref("@font-palette-values")}} را خوانده و نام آن را نمایش می‌دهد. زیرساخت [نمونه زنده](/en-US/docs/MDN/Writing_guidelines/Page_structures/Live_samples) MDN تمام بلوک‌های CSS موجود در مثال را در یک استایل درون‌خطی واحد با شناسه `css-output` ترکیب می‌کند، بنابراین ابتدا از {{domxref("document.getElementById()")}} برای پیدا کردن آن شیوه‌نامه استفاده می‌کنیم. پالت، دومین {{domxref("CSSRule")}} در آن شیوه‌نامه خواهد بود. بنابراین، `rules[1]` یک شیء `CSSFontPaletteValuesRule` برمی‌گرداند که از آن می‌توانیم به `name` دسترسی داشته باشیم.

#### HTML

```html
<pre id="log">نام قاعده @font-palette-values:</pre>
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
const fontPaletteValuesRule = rules[1]; // a CSSFontPaletteValuesRule interface
log.textContent += ` ${fontPaletteValuesRule.name}`;
```

#### نتیجه

{{EmbedLiveSample("Read the at-rule's name", "100", "40")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- قاعده at-rule {{cssxref("@font-palette-values")}}