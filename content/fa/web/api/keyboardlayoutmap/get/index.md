---
title: "KeyboardLayoutMap: get() method"
short-title: get()
slug: Web/API/KeyboardLayoutMap/get
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.KeyboardLayoutMap.get
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.get
---

{{APIRef("Keyboard API")}}{{SeeCompatTable}}

متد **`get()`** از رابط {{domxref('KeyboardLayoutMap')}}، عنصر مربوط به کلید داده‌شده را بازمی‌گرداند.

فهرست کلیدهای معتبر در مشخصات [UI Events KeyboardEvent code Values](https://w3c.github.io/uievents-code/) موجود است.

این متد در غیر این صورت مشابه {{jsxref("Map.prototype.get()")}} است.

## Syntax

```js-nolint
get(key)
```

### پارامترها

- `key`
  - : کلید آیتمی که از نقشه بازگردانده می‌شود.

### مقدار بازگشتی

مقدار کلید مشخص‌شده.

## مثال‌ها

مثال زیر نحوه دریافت رشته مختص موقعیت یا چیدمان مرتبط با کد صفحه‌کلید که مربوط به کلید 'W' در یک صفحه‌کلید انگلیسی QWERTY است را نشان می‌دهد.

```js
navigator.keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  const upKey = keyboardLayoutMap.get("KeyW");
  window.alert(`Press ${upKey} to move up.`);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("Map.prototype.get()")}}