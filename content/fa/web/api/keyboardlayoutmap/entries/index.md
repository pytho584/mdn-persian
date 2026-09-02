---
title: "KeyboardLayoutMap: entries() method"
short-title: entries()
slug: Web/API/KeyboardLayoutMap/entries
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.KeyboardLayoutMap.entries
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.entries
---

{{SeeCompatTable}}{{APIRef("Keyboard API")}}

متد **`entries()`** در رابط {{domxref("KeyboardLayoutMap")}} یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید برمی‌گرداند که شامل جفت‌های کلید/مقدار است، به همان ترتیبی که توسط یک حلقه {{jsxref("Statements/for...in", "for...in")}} ارائه می‌شود (تفاوت در این است که حلقه `for-in` ویژگی‌های زنجیره prototype را نیز شمارش می‌کند).

این متد در غیر این صورت همانند {{jsxref("Map.prototype.entries()")}} است.

## Syntax

```js-nolint
entries()
```

### Parameters

بدون پارامتر.

### Return value

یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید.

## Examples

مثال زیر هر رشته مربوط به مکان یا چیدمان (location- or layout-specific) و کد صفحه‌کلید مرتبط با آن را روی یک صفحه‌کلید انگلیسی QWERTY پیمایش می‌کند.

```js
navigator.keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  for (const [code, key] of keyboardLayoutMap.entries()) {
    console.log(`${code} keyboard code represents ${key} key`);
  }
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("Map.prototype.entries()")}}