---
title: "CSSFontPaletteValuesRule: fontFamily property"
short-title: fontFamily
slug: Web/API/CSSFontPaletteValuesRule/fontFamily
page-type: web-api-instance-property
browser-compat: api.CSSFontPaletteValuesRule.fontFamily
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`fontFamily`** از رابط {{domxref("CSSFontPaletteValuesRule")}} فهرستی از خانواده‌های فونت را ارائه می‌دهد که این قاعده می‌تواند روی آن‌ها اعمال شود. خانواده‌های فونت باید خانواده‌های _نام‌دار_ باشند؛ خانواده‌های _عمومی_ مانند `courier` معتبر نیستند.

## مقدار

یک رشته شامل فهرستی از خانواده‌های فونت که با فاصله از هم جدا شده‌اند و قاعده می‌تواند روی آن‌ها اعمال شود.

## مثال‌ها

### خواندن خانواده فونت مرتبط

این مثال ابتدا یک {{cssxref("@import")}} و یک قاعده at-rule به نام {{cssxref("@font-palette-values")}} تعریف می‌کند. سپس قاعده {{cssxref("@font-palette-values")}} را می‌خواند و نام آن را نمایش می‌دهد. زیرساخت [نمونه زنده](/en-US/docs/MDN/Writing_guidelines/Page_structures/Live_samples) MDN همه بلوک‌های CSS موجود در مثال را در یک استایل داخلی با شناسه `css-output` ترکیب می‌کند، بنابراین ابتدا از {{domxref("document.getElementById()")}} برای یافتن آن شیوه‌نامه استفاده می‌کنیم. پالت، دومین {{domxref("CSSRule")}} در آن شیوه‌نامه خواهد بود. بنابراین، `rules[1]` یک شیء `CSSFontPaletteValuesRule` برمی‌گرداند که از آن می‌توانیم به `fontFamily` دسترسی داشته باشیم.

#### HTML

```html
<pre id="log">
قاعده @font-palette-values برای این خانواده‌های فونت اعمال می‌شود:</pre>
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

{{EmbedLiveSample("Read the associated font family", "100", "40")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- قاعده at-rule {{cssxref("@font-palette-values")}}
- توصیفگر {{cssxref("@font-palette-values/font-family", "font-family")}}