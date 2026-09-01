---
title: "HTMLTableElement: rules property"
short-title: rules
slug: Web/API/HTMLTableElement/rules
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableElement.rules
---

{{APIRef("HTML DOM")}} {{Deprecated_Header}}

ویژگی **`HTMLTableElement.rules`** مشخص می‌کند که کدام مرزهای سلول‌ها در جدول باید نمایش داده شوند.

## مقدار

یکی از موارد زیر:

- `none`
  - : بدون خط جداکننده
- `groups`
  - : فقط خطوط بین گروه‌ها
- `rows`
  - : خطوط بین ردیف‌ها
- `cols`
  - : خطوط بین ستون‌ها
- `all`
  - : خطوط بین همه سلول‌ها

## مثال‌ها

```js
// فعال کردن تمام مرزهای داخلی یک جدول
const t = document.getElementById("TableID");
t.rules = "all";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}