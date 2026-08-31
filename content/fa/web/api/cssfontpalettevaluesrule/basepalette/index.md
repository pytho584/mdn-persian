---
title: "CSSFontPaletteValuesRule: basePalette property"
short-title: basePalette
slug: Web/API/CSSFontPaletteValuesRule/basePalette
page-type: web-api-instance-property
browser-compat: api.CSSFontPaletteValuesRule.basePalette
---

{{APIRef("CSSOM")}}

خاصیت فقط خواندنی **`basePalette`** از رابط {{domxref("CSSFontPaletteValuesRule")}} نشان‌دهندهٔ پالت پایه مرتبط با قانون است.

## مقدار

یک رشته که می‌تواند یکی از مقادیر رنگی زیر باشد:

- `light`
  - : با اولین پالت در فایل فونت که به عنوان مناسب برای پس‌زمینهٔ روشن (نزدیک به سفید) علامت‌گذاری شده است، مطابقت دارد. اگر هیچ پالتی در فونت وجود نداشته باشد یا هیچ پالتی فرادادهٔ مورد نیاز را نداشته باشد، مقدار معادل `"0"` یعنی اولین پالت در فونت است.
- `dark`
  - : با اولین پالت در فایل فونت که به عنوان مناسب برای پس‌زمینهٔ تیره (نزدیک به سیاه) علامت‌گذاری شده است، مطابقت دارد. اگر هیچ پالتی در فونت وجود نداشته باشد یا هیچ پالتی فرادادهٔ مورد نیاز را نداشته باشد، مقدار معادل `"0"` یعنی اولین پالت در فونت است.
- یک رشته شامل یک ایندکس (مانند `"0"`, `"1"`, …)
  - : با پالت متناظر با ایندکس مطابقت دارد. اولین پالت با `"0"` مطابقت دارد.

## مثال‌ها

### خواندن پالت پایهٔ مرتبط

زیرساخت نمونه‌های زندهٔ MDN تمام بلوک‌های CSS موجود در مثال را در یک استایل in-line با شناسهٔ `css-output` ترکیب می‌کند، بنابراین ابتدا از {{domxref("document.getElementById()")}} برای پیدا کردن آن شیوه‌نامه استفاده می‌کنیم. `rules[2]` اولین شیء {{domxref("CSSFontPaletteValuesRule")}} و `rules[3]` دومی را بازمی‌گرداند.

#### HTML

```html
<h2>default base-palette</h2>
<h2 class="two">base-palette at index 2</h2>
<h2 class="five">base-palette at index 5</h2>
<pre id="log"></pre>
```

#### CSS

```css
@import "https://fonts.googleapis.com/css2?family=Nabla&display=swap";

h2 {
  font-family: "Nabla", fantasy;
}

@font-palette-values --two {
  font-family: "Nabla";
  base-palette: 2;
}

@font-palette-values --five {
  font-family: "Nabla";
  base-palette: 5;
}

.two {
  font-palette: --two;
}

.five {
  font-palette: --five;
}
```

#### JavaScript

```js
const log = document.getElementById("log");

const rules = document.getElementById("css-output").sheet.cssRules;
const twoRule = rules[2]; // A CSSFontPaletteValuesRule interface
const fiveRule = rules[3]; // A CSSFontPaletteValuesRule interface

log.textContent = `The ${twoRule.name} @font-palette-values base palette is: ${twoRule.basePalette}\n`;
log.textContent += `The ${fiveRule.name} @font-palette-values base palette is: ${fiveRule.basePalette}`;
```

#### نتیجه

{{EmbedLiveSample("Read the associated base palette", "100", "255")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@font-palette-values")}} قاعدهٔ at-rule
- توصیف‌کنندهٔ {{cssxref("@font-palette-values/base-palette", "base-palette")}}