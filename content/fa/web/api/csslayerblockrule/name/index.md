---
title: "CSSLayerBlockRule: name property"
short-title: name
slug: Web/API/CSSLayerBlockRule/name
page-type: web-api-instance-property
browser-compat: api.CSSLayerBlockRule.name
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`name`** در رابط {{domxref("CSSLayerBlockRule")}} نمایانگر نام لایهٔ آبشاریِ مرتبط است.

## مقدار

مقدار آن یک رشته شامل نام لایه است، یا اگر لایه بی‌نام (anonymous) باشد، `""` است.

## مثال‌ها

### HTML

```html
<output></output> <output></output>
```

### CSS

```css
output {
  display: block;
}

@layer special {
  div {
    color: rebeccapurple;
  }
}

@layer {
  div {
    color: black;
  }
}
```

### JavaScript

```js
const item1 = document.getElementsByTagName("output")[0];
const item2 = document.getElementsByTagName("output")[1];
const rules = document.getElementById("css-output").sheet.cssRules;

const layer = rules[1]; // A CSSLayerBlockRule
const anonymous = rules[2]; // An anonymous CSSLayerBlockRule

item1.textContent = `The first CSSLayerBlockRule defines the "${layer.name}" layer.`;
item2.textContent = `A second CSSLayerBlockRule defines a layer with the following name: "${anonymous.name}".`;
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- شکل بیانیه‌ای (statement) قانون {{cssxref("@layer")}} توسط رابط {{domxref("CSSLayerStatementRule")}} بازنمایی می‌شود.
- [ساخت لایه‌های آبشاری نام‌دار](/en-US/docs/Learn_web_development/Core/Styling_basics/Cascade_layers#creating_cascade_layers) در CSS.