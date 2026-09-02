---
title: "KeyboardLayoutMap: forEach() method"
---

---
title: "KeyboardLayoutMap: forEach() method"
short-title: forEach()
slug: Web/API/KeyboardLayoutMap/forEach
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.KeyboardLayoutMap.forEach
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-map.prototype.foreach
---

{{APIRef("Keyboard API")}}{{SeeCompatTable}}

متد **`forEach()`** از رابط {{domxref('KeyboardLayoutMap')}} یک تابع ارائه‌شده را یک بار برای هر عنصر از نقشه اجرا می‌کند.

این متد در سایر موارد مشابه {{jsxref("Map.prototype.forEach()")}} است.

## نحو (Syntax)

```js-nolint
forEach(callbackFn)
forEach(callbackFn, thisArg)
```

### پارامترها

- `callbackFn`
  - : تابعی که برای هر عنصر اجرا می‌شود و سه آرگومان می‌گیرد:
    - `currentValue`
      - : مقدار عنصر جاری در حال پردازش.
    - `index` {{optional_inline}}
      - : شاخص عنصر جاری در حال پردازش.
    - `array` {{optional_inline}}
      - : `KeyboardLayoutMap`ای که `forEach()` روی آن فراخوانی شده است.

- `thisArg` {{Optional_inline}}
  - : مقداری که در هنگام اجرای `callback` به عنوان **`this`** (یعنی ارجاع `Object`) استفاده شود.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

مثال زیر هر رشته مختص مکان یا طرح (layout) و کد صفحه کلید مرتبط با آن را روی یک صفحه کلید انگلیسی QWERTY پیمایش می‌کند.

```js
navigator.keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  keyboardLayoutMap.forEach((key, code) => {
    console.log(`${code} keyboard code represents ${key} key`);
  });
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("Map.prototype.forEach()")}}