---
title: "CSSFontPaletteValuesRule: overrideColors property"
short-title: overrideColors
slug: Web/API/CSSFontPaletteValuesRule/overrideColors
page-type: web-api-instance-property
browser-compat: api.CSSFontPaletteValuesRule.overrideColors
---

{{APIRef("CSSOM")}}

خاصیت فقط‌خواندنی **`overrideColors`** در رابط {{domxref("CSSFontPaletteValuesRule")}} رشته‌ای است حاوی فهرستی از اندیس‌های رنگ و جفت‌های رنگی که باید به‌جای رنگ‌های پیش‌فرض استفاده شوند. این خاصیت در قالبی مشابه توصیفگر متناظر {{cssxref("@font-palette-values/override-colors", "override-colors")}} تعریف شده است.

## مقدار

رشته‌ای حاوی فهرستی جداشده با ویرگول از اندیس‌های رنگ و جفت‌های رنگ.

## مثال‌ها

### خواندن رنگ جایگزین‌شده

این مثال ابتدا چند at-rule تعریف می‌کند، از جمله دو {{cssxref("@font-palette-values")}}. زیرساخت [نمونهٔ زنده](/en-US/docs/MDN/Writing_guidelines/Page_structures/Live_samples) MDN همهٔ بلوک‌های CSS موجود در مثال را در یک استایل درون‌خطی با شناسهٔ `css-output` ترکیب می‌کند؛ بنابراین ابتدا با استفاده از {{domxref("document.getElementById()")}} آن برگه را پیدا می‌کنیم.

#### HTML

```html
<div class="hat">
  <div class="emoji colored-hat">🎩</div>
</div>
<button>Toggle color</button>
<pre id="log"></pre>
```

#### CSS

```css
@font-face {
  font-family: "Noto Color Emoji";
  font-style: normal;
  font-weight: normal;
  src: url("https://fonts.gstatic.com/l/font?kit=Yq6P-KqIXTD0t4D9z1ESnKM3-HpFabts6diywYkdG3gjD0U&skey=a373f7129eaba270&v=v24")
    format("woff2");
}

.emoji {
  font-family: "Noto Color Emoji", emoji;
  font-size: 3rem;
}

@font-palette-values --blue {
  font-family: "Noto Color Emoji";
  override-colors:
    3 rgb(1 28 193),
    4 rgb(60 124 230);
}

@font-palette-values --green {
  font-family: "Noto Color Emoji";
  override-colors:
    3 rgb(28 193 1),
    4 rgb(34 230 1);
}

.colored-hat {
  font-palette: --blue;
}
```

#### JavaScript

```js
const log = document.getElementById("log");
const button = document.querySelector("button");
const hat = document.querySelector(".colored-hat");
const rules = document.getElementById("css-output").sheet.cssRules;
const greenFontPaletteValuesRule = rules[3];
const blueFontPaletteValuesRule = rules[2];
log.textContent = `Overridden colors: ${blueFontPaletteValuesRule.overrideColors}`;

button.addEventListener("click", (event) => {
  if (hat.style.fontPalette !== "--green") {
    hat.style.fontPalette = "--green";
    log.textContent = `Overridden colors: ${greenFontPaletteValuesRule.overrideColors}`;
  } else {
    hat.style.fontPalette = "--blue";
    log.textContent = `Overridden colors: ${blueFontPaletteValuesRule.overrideColors}`;
  }
});
```

#### نتیجه

{{EmbedLiveSample("Read the overridden colors", "100", "125")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- at-rule {{cssxref("@font-palette-values")}}
- توصیفگر {{cssxref("@font-palette-values/override-colors", "override-colors")}}