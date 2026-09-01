---
title: "CSSLayerStatementRule: nameList property"
---

---
title: "CSSLayerStatementRule: nameList property"
short-title: nameList
slug: Web/API/CSSLayerStatementRule/nameList
page-type: web-api-instance-property
browser-compat: api.CSSLayerStatementRule.nameList
---

{{APIRef("CSSOM")}}

ویژگی فقط‌خواندنی **`nameList`** از رابط {{DOMxRef("CSSLayerStatementRule")}} فهرست نام‌های لایه‌های آبشاری مرتبط را برمی‌گرداند. این نام‌ها قابل تغییر نیستند.

## مقدار

یک {{jsxref("Array")}} از رشته‌ها، که هر کدام نشان‌دهنده یک لایه آبشاری است که توسط قانون بیانیه {{cssxref("@layer")}} تعریف شده است.

## مثال‌ها

### HTML

```html
<div></div>
```

### CSS

```css
@layer layerName, layerName2;

@layer layerName3 {
  div {
    font-family: serif;
  }
}
```

### JavaScript

```js
const item = document.getElementsByTagName("div")[0];
const rules = document.getElementById("css-output").sheet.cssRules;

const layerStatementRule = rules[0]; // A CSSLayerStatementRule
const layerBlockRule = rules[1]; // A CSSLayerBlockRule; no nameList property.

item.textContent = `@layer declares the following layers: ${layerStatementRule.nameList.join(
  ", ",
)}.`;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMXRef("CSSLayerBlockRule.name")}}
- {{CSSXref("@layer")}}
- [قانون بیانیه `@layer` برای لایه‌های نام‌دار](/en-US/docs/Learn_web_development/Core/Styling_basics/Cascade_layers#the_layer_statement_at-rule_for_named_layers)