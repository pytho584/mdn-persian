---
title: "Element: ariaSelected property"
short-title: ariaSelected
slug: Web/API/Element/ariaSelected
page-type: web-api-instance-property
browser-compat: api.Element.ariaSelected
---

{{APIRef("DOM")}}

ویژگی **`ariaSelected`** در رابط {{domxref("Element")}} منعکس‌کنندهٔ مقدار ویژگی [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) است که وضعیت «انتخاب‌شده» کنونی عناصر دارای حالت انتخاب را نشان می‌دهد.

## مقدار

رشته‌ای با یکی از مقادیر زیر:

- `"true"`
  - : مورد انتخاب شده است.
- `"false"`
  - : مورد انتخاب نشده است.
- `"undefined"`
  - : مورد قابل انتخاب نیست.

## مثال‌ها

در این مثال، ویژگی `aria-selected` روی عنصری با شناسهٔ `tab-id` برابر با `"true"` قرار داده شده است. با استفاده از `ariaSelected`، مقدار را به `"false"` به‌روزرسانی می‌کنیم.

```html
<button role="tab" aria-selected="true" aria-controls="tabpanel-id" id="tab-id">
  Tab label
</button>
```

```js
let el = document.getElementById("tab-id");
console.log(el.ariaSelected); // true
el.ariaSelected = "false";
console.log(el.ariaSelected); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نقش tab در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)