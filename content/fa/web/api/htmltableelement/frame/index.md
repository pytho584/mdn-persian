---
title: "HTMLTableElement: frame property"
---

---
title: "HTMLTableElement: frame property"
short-title: frame
slug: Web/API/HTMLTableElement/frame
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.HTMLTableElement.frame
---

{{APIRef("HTML DOM")}} {{Deprecated_Header}}

مخصوصیت **`frame`** در رابط {{domxref("HTMLTableElement")}} یک رشته است که مشخص می‌کند کدام یک از مرزهای بیرونی جدول باید ترسیم شوند.

## مقدار

یکی از مقادیر زیر:

- `void`
  - : هیچ ضلعی. این مقدار پیش‌فرض است.
- `"above"`
  - : فقط ضلع بالا
- `"below"`
  - : فقط ضلع پایین
- `"hsides"`
  - : فقط بالا و پایین
- `"vsides"`
  - : فقط راست و چپ
- `"lhs"`
  - : فقط سمت چپ
- `"rhs"`
  - : فقط سمت راست
- `"box"`
  - : هر چهار ضلع
- `"border"`
  - : هر چهار ضلع

## مثال‌ها

```js
// Set the frame of TableA to 'border'
const t = document.getElementById("TableA");
t.frame = "border";
t.border = "2px";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}