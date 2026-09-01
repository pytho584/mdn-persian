```markdown
---
title: "HTMLTableElement: cellPadding property"
short-title: cellPadding
slug: Web/API/HTMLTableElement/cellPadding
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableElement.cellPadding
---

{{APIRef("HTML DOM")}} {{Deprecated_Header}}

ویژگی **`HTMLTableElement.cellPadding`** نشان‌دهنده فاصله داخلی (padding) پیرامون سلول‌های جدول است.

## مقدار

یک رشته (string) که پیکسل‌ها (مانند `"10"`) یا یک مقدار درصدی (مانند `"10%"`) را نشان می‌دهد.

وقتی این ویژگی روی مقدار `null` تنظیم شود، مقدار `null` به رشته خالی (`""`) تبدیل می‌شود؛ بنابراین `elt.cellPadding = null` معادل `elt.cellPadding = ""` است.

## نمونه‌ها

```js
// تنظیم فاصله داخلی سلول‌ها روی ۱۰ پیکسل
let t = document.getElementById("TableA");
t.cellPadding = "10";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```