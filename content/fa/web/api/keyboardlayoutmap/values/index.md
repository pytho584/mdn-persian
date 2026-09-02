---
title: "KeyboardLayoutMap: values() method"
---

---
title: "KeyboardLayoutMap: values() method"
short-title: values()
slug: Web/API/KeyboardLayoutMap/values
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.KeyboardLayoutMap.values
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.values
---

{{SeeCompatTable}}{{APIRef("Keyboard API")}}

متد **`values()`** از رابط {{domxref("KeyboardLayoutMap")}} یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید برمی‌گرداند که شامل مقادیر مربوط به هر اندیس در شیء `KeyboardLayoutMap` است.

این متد از هر نظر مشابه {{jsxref("Map.prototype.values()")}} است.

## سینتکس

```js-nolint
values()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید.

## مثال‌ها

مثال زیر همه‌ی رشته‌های مختص موقعیت یا چیدمان را روی یک صفحه‌کلید انگلیسی QWERTY پیمایش می‌کند.

```js
navigator.keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  for (const key of keyboardLayoutMap.values()) {
    console.log(`${key} key`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("Map.prototype.values()")}}