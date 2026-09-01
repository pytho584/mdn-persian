---
title: CSSLayerBlockRule
slug: Web/API/CSSLayerBlockRule
page-type: web-api-interface
browser-compat: api.CSSLayerBlockRule
---

{{APIRef("CSSOM")}}

**`CSSLayerBlockRule`** یک قاعده‌ی بلوک {{cssxref("@layer")}} را نشان می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های اجداد خود {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} را به ارث می‌برد._

- {{DOMxRef("CSSLayerBlockRule.name")}} {{ReadOnlyInline}}
  - : یک رشته که نام لایه‌ی آبشاری مرتبط را شامل می‌شود.

## روش‌های نمونه

_روش‌های اجداد خود {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} را به ارث می‌برد._

## مثال‌ها

### HTML

```html
<p>I am displayed in <code>color: rebeccapurple</code>.</p>
```

### CSS

```css
@layer special {
  p {
    color: rebeccapurple;
  }
}
```

### JavaScript

```js
const item = document.getElementsByTagName("p")[0];
const rules = document.getElementById("css-output").sheet.cssRules;

const layer = rules[0]; // A CSSLayerBlockRule

item.textContent = `The CSSLayerBlockRule is for the "${layer.name}" layer`;
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{cssxref("@layer")}}
- {{DOMxRef("CSSLayerStatementRule")}}
- [آشنایی با لایه‌های آبشاری CSS](/en-US/docs/Learn_web_development/Core/Styling_basics/Cascade_layers)