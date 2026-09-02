---
title: "MouseEvent: getModifierState() method"
short-title: getModifierState()
slug: Web/API/MouseEvent/getModifierState
page-type: web-api-instance-method
browser-compat: api.MouseEvent.getModifierState
---

{{APIRef("Pointer Events")}}

متد **`MouseEvent.getModifierState()`** وضعیت فعلی کلید اصلاح‌کننده (modifier key) مشخص‌شده را برمی‌گرداند: اگر آن کلید اصلاح‌کننده فعال باشد (یعنی کلید فشرده شده یا قفل باشد)، مقدار `true` و در غیر این صورت مقدار `false` بازگردانده می‌شود.

برای جزئیات بیشتر، {{domxref("KeyboardEvent.getModifierState","KeyboardEvent.getModifierState()")}} را ببینید.

## نحو (Syntax)

```js-nolint
getModifierState(key)
```

### پارامترها

- `key`
  - : یک مقدار کلید اصلاح‌کننده.
    این مقدار باید یکی از مقادیر {{domxref("KeyboardEvent.key")}} باشد که کلیدهای اصلاح‌کننده را نشان می‌دهد، یا `"Accel"` {{deprecated_inline}}.
    این پارامتر به حروف بزرگ و کوچک حساس است.

### مقدار بازگشتی

یک مقدار بولی.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MouseEvent")}} که این متد به آن تعلق دارد.
- {{domxref("KeyboardEvent.getModifierState")}}