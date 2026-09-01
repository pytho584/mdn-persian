---
title: CSSScopeRule
slug: Web/API/CSSScopeRule
page-type: web-api-interface
browser-compat: api.CSSScopeRule
---

{{ APIRef("CSSOM") }}

رابطه‌ی **`CSSScopeRule`** در [مدل شیء CSS](/en-US/docs/Web/API/CSS_Object_Model) نمایانگر یک قاعده‌ی at-rule در CSS، یعنی {{CSSxRef("@scope")}} است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از اجداد خود، یعنی {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSScopeRule.end", "end")}}
  - : رشته‌ای برمی‌گرداند که مقدار محدودیت scope در قاعده‌ی `@scope` را شامل می‌شود.
- {{domxref("CSSScopeRule.start", "start")}}
  - : رشته‌ای برمی‌گرداند که مقدار ریشه‌ی scope در قاعده‌ی `@scope` را شامل می‌شود.

## روش‌های نمونه

_روش‌ها را از اجداد خود، یعنی {{domxref("CSSGroupingRule")}} و {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

### دسترسی به اطلاعات @scope در جاوااسکریپت

با فرض اینکه تنها stylesheet متصل به سند به صورت زیر باشد:

```css
@scope (.outer) to (.inner) {
  :scope {
    background: yellow;
  }
}
```

جاوااسکریپت زیر می‌تواند برای دسترسی به اطلاعات بلوک `@scope` استفاده شود:

```js
const scopeBlock = document.styleSheets[0].cssRules[0];

console.log(scopeBlock.start); // Returns ".outer"
console.log(scopeBlock.end); // Returns ".inner"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{CSSxRef("@scope")}}
- {{CSSxRef(":scope")}}