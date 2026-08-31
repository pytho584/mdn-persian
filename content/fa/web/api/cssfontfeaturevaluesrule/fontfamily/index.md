---
title: "CSSFontFeatureValuesRule: fontFamily property"
---

---
title: "CSSFontFeatureValuesRule: fontFamily property"
short-title: fontFamily
slug: Web/API/CSSFontFeatureValuesRule/fontFamily
page-type: web-api-instance-property
browser-compat: api.CSSFontFeatureValuesRule.fontFamily
---

{{ APIRef("CSSOM") }}

ویژگی **`fontFamily`** از رابط {{domxref("CSSFontFeatureValuesRule")}} نام خانواده فونتی را که این قاعده روی آن اعمال می‌شود، نشان می‌دهد.

## مقدار

یک رشته.

## مثال‌ها

### خواندن خانواده فونت

در این مثال، دو {{cssxref("@font-feature-values")}} تعریف می‌کنیم؛ یکی برای خانواده فونت _Font One_ و دیگری برای _Font Two_. سپس با استفاده از CSSOM این خانواده فونت‌ها را می‌خوانیم و آن‌ها را در لاگ نمایش می‌دهیم.

```html
<pre id="log"></pre>
```

#### CSS

```css
/* At-rule for "nice-style" in Font One */
@font-feature-values Font One {
  @styleset {
    nice-style: 12;
  }
}

/* At-rule for "nice-style" in Font Two */
@font-feature-values Font Two {
  @styleset {
    nice-style: 4;
  }
}

/* Apply the at-rules with a single declaration */
.nice-look {
  font-variant-alternates: styleset(nice-style);
}
```

#### JavaScript

```js
const log = document.getElementById("log");
const rules = document.getElementById("css-output").sheet.cssRules;

const fontOne = rules[0]; // A CSSFontFeatureValuesRule
log.textContent = `The 1st '@font-feature-values' family: "${fontOne.fontFamily}".\n`;

const fontTwo = rules[1]; // Another CSSFontFeatureValuesRule
log.textContent += `The 2nd '@font-feature-values' family: "${fontTwo.fontFamily}".`;
```

{{EmbedLiveSample("read_font_family", "100%", "75px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}