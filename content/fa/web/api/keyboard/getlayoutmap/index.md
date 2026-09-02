---
title: "Keyboard: getLayoutMap() method"
---

---
title: "Keyboard: getLayoutMap() method"
short-title: getLayoutMap()
slug: Web/API/Keyboard/getLayoutMap
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Keyboard.getLayoutMap
---

{{APIRef("Keyboard API")}}{{SeeCompatTable}}{{securecontext_header}}

متد **`getLayoutMap()`** از رابط {{domxref("Keyboard")}} یک {{jsxref('Promise')}} برمی‌گرداند که با یک نمونه از {{domxref('KeyboardLayoutMap')}} حل می‌شود. این یک شیء شبیه به نقشه (map) است که توابعی برای بازیابی رشته‌های مرتبط با کلیدهای فیزیکی خاص دارد.

## Syntax

```js-nolint
getLayoutMap()
```

### Parameters

هیچکدام.

### Return value

یک {{jsxref('Promise')}} که با یک نمونه از {{domxref('KeyboardLayoutMap')}} حل می‌شود.

### Exceptions

- `SecurityError` {{domxref("DOMException")}}
  - : در صورتی که فراخوانی توسط یک [خط‌مشی مجوز](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شود، پرتاب می‌شود.

## Examples

مثال زیر نحوه دریافت رشته مرتبط با مکان یا طرح (layout) کلید متناظر با کلید 'W' در یک صفحه‌کلید انگلیسی QWERTY را نشان می‌دهد.

```js
const keyboard = navigator.keyboard;
keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  const upKey = keyboardLayoutMap.get("KeyW");
  window.alert(`Press ${upKey} to move up.`);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("Intl")}}