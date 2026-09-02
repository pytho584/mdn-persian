---
title: "KeyboardLayoutMap: keys() method"
short-title: keys()
slug: Web/API/KeyboardLayoutMap/keys
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.KeyboardLayoutMap.keys
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.keys
---

{{SeeCompatTable}}{{APIRef("Keyboard API")}}

متد **`keys()`** از رابط {{domxref("KeyboardLayoutMap")}} یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید برمی‌گرداند که کلیدهای هر اندیس در شیء `KeyboardLayoutMap` را شامل می‌شود.

این متد در غیر این صورت مشابه {{jsxref("Map.prototype.keys()")}} است.

## نحو (Syntax)

```js-nolint
keys()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید.

## مثال‌ها

مثال زیر تمام کدهای صفحه‌کلید روی یک صفحه‌کلید انگلیسی QWERTY را پیمایش می‌کند.

```js
navigator.keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  for (const code of keyboardLayoutMap.keys()) {
    console.log(`${code} keyboard code`);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{jsxref("Map.prototype.keys()")}}