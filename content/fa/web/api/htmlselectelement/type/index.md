---
title: "HTMLSelectElement: type property"
short-title: type
slug: Web/API/HTMLSelectElement/type
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.type
---

{{ APIRef("HTML DOM") }}

ویژگی فقط-خواندنی **`HTMLSelectElement.type`**، نوع کنترل فرم را برمی‌گرداند.

## مقدار

یکی از موارد زیر:

- `"select-multiple"` اگر بتوان چندین مقدار را انتخاب کرد.
- `"select-one"` اگر فقط یک مقدار قابل انتخاب باشد.

## مثال‌ها

```js
switch (select.type) {
  case "select-multiple":
    // Multiple values may be selected
    break;
  case "select-one":
    // Only one value may be selected
    break;
  default:
  // Non-standard value (or this isn't a SELECT element)
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{HTMLElement("select")}} که این رابط را پیاده‌سازی می‌کند.