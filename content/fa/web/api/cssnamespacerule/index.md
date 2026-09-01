---
title: CSSNamespaceRule
slug: Web/API/CSSNamespaceRule
page-type: web-api-interface
browser-compat: api.CSSNamespaceRule
---

{{APIRef("CSSOM")}}

رابطه **`CSSNamespaceRule`** یک شیء را توصیف می‌کند که نماینده یک قاعده CSS {{ cssxref("@namespace") }} (یک at-rule) است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از جد خود {{domxref("CSSRule")}} به ارث می‌برد._

- {{domxref("CSSNamespaceRule.namespaceURI")}}
  - : یک رشته شامل متن URI فضای نام داده شده را برمی‌گرداند.
- {{domxref("CSSNamespaceRule.prefix")}}
  - : یک رشته با نام پیشوند مرتبط با این فضای نام را برمی‌گرداند. اگر چنین پیشوندی وجود نداشته باشد، یک رشته خالی برمی‌گرداند.

## روش‌های نمونه

_روش‌ها را از جد خود {{domxref("CSSRule")}} به ارث می‌برد._

## مثال‌ها

صفحه‌سبک (stylesheet) شامل یک فضای نام به عنوان تنها قاعده است. بنابراین اولین {{domxref("CSSRule")}} برگردانده شده یک `CSSNamespaceRule` خواهد بود.

```css
@namespace url("http://www.w3.org/1999/xhtml");
```

```js
const myRules = document.styleSheets[0].cssRules;
console.log(myRules[0]); // A CSSNamespaceRule
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}