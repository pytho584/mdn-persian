---
title: "CSSTransformValue: forEach() method"
short-title: forEach()
slug: Web/API/CSSTransformValue/forEach
page-type: web-api-instance-method
browser-compat: api.CSSTransformValue.forEach
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`CSSTransformValue.forEach()`** یک تابع داده‌شده را یک‌بار برای هر عنصر از `CSSTransformValue` اجرا می‌کند.

## Syntax

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### Parameters

- `callbackFn`
  - : تابعی که برای هر عنصر اجرا می‌شود و سه آرگومان می‌گیرد:
    - `currentValue`
      - : مقدار عنصر فعلی در حال پردازش.
    - `index` {{optional_inline}}
      - : اندیس عنصر فعلی در حال پردازش.
    - `array` {{optional_inline}}
      - : شیء `CSSTransformValue` که `forEach()` روی آن فراخوانی شده است.

- `thisArg` {{Optional_inline}}
  - : مقداری که هنگام اجرای `callback` به‌عنوان **`this`** (یعنی `Object` مرجع) استفاده می‌شود.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

To Do

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}