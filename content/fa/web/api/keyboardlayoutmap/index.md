---
title: KeyboardLayoutMap
slug: Web/API/KeyboardLayoutMap
page-type: web-api-interface
status:
  - experimental
browser-compat: api.KeyboardLayoutMap
---

{{SeeCompatTable}}{{APIRef("Keyboard API")}}

رابط **`KeyboardLayoutMap`** از {{domxref("Keyboard API", "", "", "nocode")}} یک شیء فقط‌خواندنی است که توابعی برای بازیابی رشته مرتبط با کلیدهای فیزیکی مشخص ارائه می‌دهد.

یک نمونه `KeyboardLayoutMap` یک [شیء شبیه `Map`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map#map-like_browser_apis) فقط‌خواندنی است که در آن هر کلید یک رشته است که کلید فیزیکی یکتا روی صفحه‌کلید را مشخص می‌کند ("کد کلید")، و مقدار متناظر آن، مقدار ویژگی کلید مرتبط است (که ممکن است تحت تأثیر چیدمان صفحه‌کلید و غیره قرار گیرد).

لیست کلیدهای معتبر در مشخصات [UI Events KeyboardEvent code Values](https://w3c.github.io/uievents-code/) موجود است.

## ویژگی‌های نمونه

- {{domxref('KeyboardLayoutMap.size')}} {{ReadOnlyInline}} {{experimental_inline}}
  - : تعداد عناصر موجود در شیء `KeyboardLayoutMap` را برمی‌گرداند.

## روش‌های نمونه

- `KeyboardLayoutMap[Symbol.iterator]()` {{experimental_inline}}
  - : یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید برمی‌گرداند که شامل جفت‌های کلید/مقدار است.
- {{domxref('KeyboardLayoutMap.entries()')}} {{experimental_inline}}
  - : یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید برمی‌گرداند که شامل جفت‌های کلید/مقدار است.
- {{domxref('KeyboardLayoutMap.forEach()')}} {{experimental_inline}}
  - : یک تابع ارائه‌شده را یک بار برای هر عنصر از `KeyboardLayoutMap` اجرا می‌کند.
- {{domxref('KeyboardLayoutMap.get()')}} {{experimental_inline}}
  - : عنصر با کلید داده‌شده را از شیء `KeyboardLayoutMap` برمی‌گرداند.
- {{domxref('KeyboardLayoutMap.has()')}} {{experimental_inline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا شیء `KeyboardLayoutMap` دارای عنصری با کلید مشخص‌شده است یا خیر.
- {{domxref('KeyboardLayoutMap.keys()')}} {{experimental_inline}}
  - : یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید برمی‌گرداند که شامل کلیدهای هر شاخص در شیء `KeyboardLayoutMap` است.
- {{domxref('KeyboardLayoutMap.values()')}} {{experimental_inline}}
  - : یک شیء [Iterator](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Iterator) جدید برمی‌گرداند که شامل مقادیر هر شاخص در شیء `KeyboardLayoutMap` است.

## مثال‌ها

مثال زیر نحوه به‌دست‌آوردن رشته مخصوص مکان یا چیدمان مرتبط با کد صفحه‌کلید مربوط به کلید 'W' در یک صفحه‌کلید انگلیسی QWERTY را نشان می‌دهد.

```js
navigator.keyboard.getLayoutMap().then((keyboardLayoutMap) => {
  const upKey = keyboardLayoutMap.get("KeyW");
  window.alert(`Press ${upKey} to move up.`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}