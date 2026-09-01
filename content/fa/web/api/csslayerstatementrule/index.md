---
title: CSSLayerStatementRule
slug: Web/API/CSSLayerStatementRule
page-type: web-api-interface
browser-compat: api.CSSLayerStatementRule
---

{{APIRef("CSSOM")}}

**`CSSLayerStatementRule`** نمایانگر یک قانون اعلان {{cssxref("@layer")}} است. برخلاف {{domxref("CSSLayerBlockRule")}}، این قانون شامل قوانین دیگری نیست و صرفاً یک یا چند لایه را با ارائه نام‌های آن‌ها تعریف می‌کند.

این قانون امکان اعلام صریح ترتیب لایه‌ها را به شکلی آشکار در ابتدای یک فایل CSS فراهم می‌کند: ترتیب لایه‌ها بر اساس ترتیب اولین ظهور هر نام لایه تعریف می‌شود. اعلام آن‌ها با یک دستور به خواننده امکان می‌دهد ترتیب لایه‌ها را درک کند. همچنین امکان درهم‌آمیختن لایه‌های درون‌خطی و واردشده را فراهم می‌کند، که با استفاده از نحو `CSSLayerBlockRule` ممکن نیست.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_همچنین ویژگی‌های رابط والد خود، {{DOMxRef("CSSRule")}} را به ارث می‌برد._

- {{DOMxRef("CSSLayerStatementRule.nameList")}} {{ReadOnlyInline}}
  - آرایه‌ای از رشته‌ها که نام هر لایه آبشاری تعریف‌شده توسط قانون را نشان می‌دهد.

## مثال‌ها

### HTML

```html
<p></p>
```

### CSS

```css
@layer layerName, layerName2;
```

### JavaScript

```js
const item = document.getElementsByTagName("p")[0];
const rules = document.getElementById("css-output").sheet.cssRules;

const layer = rules[0]; // یک CSSLayerStatementRule

item.textContent = `قانون @layer در CSS لایه‌های زیر را اعلام می‌کند: ${layer.nameList.join(
  ", ",
)}.`;
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@layer")}}
- [قانون اعلان `@layer` برای لایه‌های نام‌دار](/en-US/docs/Learn_web_development/Core/Styling_basics/Cascade_layers#the_layer_statement_at-rule_for_named_layers)
- {{DOMxRef("CSSLayerBlockRule")}}