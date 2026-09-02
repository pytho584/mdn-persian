---
title: "KeyboardLayoutMap: has() method"
---

{{APIRef("Keyboard API")}}{{SeeCompatTable}}

متد **`has()`** از رابط {{domxref('KeyboardLayoutMap')}} یک مقدار بولین (boolean) برمی‌گرداند که نشان می‌دهد آیا شیء دارای عنصری با کلید مشخص شده است یا خیر.

فهرست کلیدهای معتبر در مشخصات [UI Events KeyboardEvent code Values](https://w3c.github.io/uievents-code/) موجود است.

این متد در غیر این صورت همانند {{jsxref("Map.prototype.has()")}} است.

## Syntax

```js-nolint
has(key)
```

### Parameters

- `key`
  - : کلید عنصری که باید در نقشه جستجو شود.

### Return value

یک {{jsxref('Boolean')}} که نشان می‌دهد آیا کلید مشخص شده پیدا شده است یا خیر.

## Examples

مثال زیر بررسی می‌کند که آیا رشته مخصوص مکان یا چیدمان مرتبط با کد صفحه‌کلید که با کلید 'W' روی یک صفحه‌کلید انگلیسی QWERTY مطابقت دارد، وجود دارد یا خیر.

```js
navigator.keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  console.log(keyboardLayoutMap.has("KeyW"));
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("Map.prototype.has()")}}