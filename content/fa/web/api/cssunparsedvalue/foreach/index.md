---
title: "CSSUnparsedValue: forEach() method"
---

---
title: "CSSUnparsedValue: forEach() method"
short-title: forEach()
slug: Web/API/CSSUnparsedValue/forEach
page-type: web-api-instance-method
browser-compat: api.CSSUnparsedValue.forEach
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`CSSUnparsedValue.forEach()`** برای هر عنصر از {{domxref('CSSUnparsedValue')}}، تابع ارائه‌شده را یک‌بار اجرا می‌کند.

## سینتکس

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که باید برای هر عنصر اجرا شود و سه آرگومان می‌گیرد:
    - `currentValue`
      - : مقدار عنصر فعلی در حال پردازش.
    - `index` {{optional_inline}}
      - : ایندکس عنصر فعلی در حال پردازش.
    - `array` {{optional_inline}}
      - : شیء `CSSUnparsedValue` که متد `forEach()` روی آن فراخوانی شده است.

- `thisArg` {{Optional_inline}}
  - : مقداری که هنگام اجرای `callback` به‌عنوان **`this`** (یعنی همان شیء مرجع `Object`) استفاده می‌شود.

### مقدار برگشتی

هیچ ({{jsxref("undefined")}}).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSUnparsedValue.CSSUnparsedValue", "CSSUnparsedValue()")}}
- {{domxref("CSSUnparsedValue.entries")}}
- {{domxref("CSSUnparsedValue.keys")}}
- {{domxref("CSSUnparsedValue.length")}}
- {{domxref("CSSUnparsedValue.values")}}
- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)