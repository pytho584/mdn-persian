---
title: "KeyboardLayoutMap: size property"
short-title: size
slug: Web/API/KeyboardLayoutMap/size
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.KeyboardLayoutMap.size
spec-urls: https://tc39.es/ecma262/multipage/keyed-collections.html#sec-get-map.prototype.size
---

{{SeeCompatTable}}{{APIRef("Keyboard API")}}

ویژگی فقط‌خواندنی **`size`** از رابط {{domxref("KeyboardLayoutMap")}} تعداد عناصر موجود در این نگاشت را برمی‌گرداند.

این ویژگی در سایر جنبه‌ها دقیقاً مشابه {{jsxref("Map.prototype.size")}} است.

## مقدار

یک عدد.

## مثال‌ها

مثال زیر تعداد رشته‌های مختص مکان یا چیدمان و کد صفحه‌کلید مرتبط با آن‌ها را روی یک صفحه‌کلید انگلیسی QWERTY به دست می‌آورد.

```js
navigator.keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  console.log(keyboardLayoutMap.size);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{jsxref("Map.prototype.size")}}