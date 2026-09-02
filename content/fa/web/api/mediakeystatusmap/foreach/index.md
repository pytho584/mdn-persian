---
title: "MediaKeyStatusMap: forEach() method"
short-title: forEach()
slug: Web/API/MediaKeyStatusMap/forEach
page-type: web-api-instance-method
browser-compat: api.MediaKeyStatusMap.forEach
---

{{APIRef("Encrypted Media Extensions")}}

متد **`forEach()`** از رابط {{domxref("MediaKeyStatusMap")}} برای هر جفت کلید-مقدار در نقشه وضعیت، به ترتیب درج، یک بار تابع callback را فراخوانی می‌کند. اگر آرگومانی ارائه شود، به تابع callback منتقل خواهد شد.

## نحو

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که برای هر عنصر اجرا می‌شود و سه آرگومان می‌گیرد:
    - `currentValue`
      - : عنصر جاری که در آرایه پردازش می‌شود.
    - `index` {{optional_inline}}
      - : شاخص عنصر جاری که در آرایه پردازش می‌شود.
    - `array` {{optional_inline}}
      - : آرایه‌ای که `forEach()` روی آن اعمال می‌شود.

- `thisArg` {{optional_inline}}
  - : مقداری که در هنگام اجرای `callback` به عنوان `this` استفاده می‌شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}