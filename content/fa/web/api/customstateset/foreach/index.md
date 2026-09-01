---
title: "CustomStateSet: forEach() method"
short-title: forEach()
slug: Web/API/CustomStateSet/forEach
page-type: web-api-instance-method
browser-compat: api.CustomStateSet.forEach
---

{{APIRef("Web Components")}}

متد **`forEach()`** از رابط {{domxref("CustomStateSet")}} یک تابع ارائه‌شده را برای هر مقدار در شیء `CustomStateSet` اجرا می‌کند.

## نحو (Syntax)

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که برای هر عنصر اجرا می‌شود و سه آرگومان می‌گیرد:
    - `value`, `key`
      - : عنصر فعلی که در `CustomStateSet` پردازش می‌شود. از آنجا که در `CustomStateSet` کلیدی وجود ندارد، مقدار برای هر دو آرگومان ارسال می‌شود.
    - `set`
      - : شیء `CustomStateSet` که متد `forEach()` روی آن فراخوانی شده است.
- `thisArg`
  - : مقداری که هنگام اجرای `callbackFn` به عنوان `this` استفاده می‌شود.

### مقدار بازگشتی

undefined.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}