---
title: "FontFaceSet: forEach() method"
short-title: forEach()
slug: Web/API/FontFaceSet/forEach
page-type: web-api-instance-method
browser-compat: api.FontFaceSet.forEach
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

متد **`forEach()`** از رابط {{domxref("FontFaceSet")}} یک تابع ارائه‌شده را برای هر مقدار در شیء `FontFaceSet` اجرا می‌کند.

## نحو

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که برای هر عنصر اجرا می‌شود و سه آرگومان می‌گیرد:
    - `value`, `key`
      - : عنصر جاری که در `FontFaceSet` پردازش می‌شود. از آنجا که در `FontFaceSet` کلیدی وجود ندارد، مقدار برای هر دو آرگومان ارسال می‌شود.
    - `set`
      - : شیء `FontFaceSet` که `forEach()` روی آن فراخوانی شده است.
- `thisArg` {{optional_inline}}
  - : مقداری که هنگام اجرای `callbackFn` به عنوان [`this`](/en-US/docs/Web/JavaScript/Reference/Operators/this) استفاده می‌شود. پیش‌فرض `undefined` است.

### مقدار بازگشتی

{{jsxref("undefined")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}