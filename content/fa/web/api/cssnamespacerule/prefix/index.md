---
title: "CSSNamespaceRule: prefix property"
short-title: prefix
slug: Web/API/CSSNamespaceRule/prefix
page-type: web-api-instance-property
browser-compat: api.CSSNamespaceRule.prefix
---

{{ APIRef("CSSOM") }}

ویژگی فقط‌خواندنی **`prefix`** از {{domxref("CSSNamespaceRule")}} یک رشته شامل نام پیشوند مرتبط با این فضای نام (namespace) را برمی‌گرداند. اگر چنین پیشوندی وجود نداشته باشد، یک رشتهٔ خالی برمی‌گرداند.

## مقدار

یک رشته شامل پیشوند مرتبط با این فضای نام. اگر پیشوندی وجود نداشته باشد، یک رشتهٔ خالی.

## مثال‌ها

شیوه‌نامه (stylesheet) شامل دو قانون فضای نام است. اولی بدون پیشوند و دومی با پیشوند `svg` است. دو شیء `CSSNamespaceRule` برگردانده می‌شود. مقدار ویژگی `prefix` برای اولی یک رشتهٔ خالی و برای دومی `svg` خواهد بود.

```css
@namespace url("http://www.w3.org/1999/xhtml");
@namespace svg url("http://www.w3.org/2000/svg");
```

```js
let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0].prefix); // an empty string ""
console.log(myRules[1].prefix); // "svg"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}