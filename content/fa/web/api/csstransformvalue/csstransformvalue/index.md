---
title: "CSSTransformValue: CSSTransformValue() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CSSTransformValue/CSSTransformValue"
---

---
title: "CSSTransformValue: CSSTransformValue() constructor"
short-title: CSSTransformValue()
slug: Web/API/CSSTransformValue/CSSTransformValue
page-type: web-api-constructor
browser-compat: api.CSSTransformValue.CSSTransformValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازنده **`CSSTransformValue()`** یک شیء {{domxref("CSSTransformValue")}} جدید ایجاد می‌کند که فهرستی از اشیاء تبدیل (transform) مجزا را نشان می‌دهد.

## Syntax

```js-nolint
new CSSTransformValue(transforms)
```

### Parameters

- `transforms`
  - : فهرستی از اشیاء {{domxref("CSSTransformComponent")}} که باید روی آن‌ها پیمایش شود.

### Return value

یک {{domxref("CSSTransformValue")}} جدید.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر `transforms` خالی باشد پرتاب می‌شود.

## Examples

To do

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}