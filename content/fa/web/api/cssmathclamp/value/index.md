---
title: "CSSMathClamp: value property"
short-title: value
slug: Web/API/CSSMathClamp/value
page-type: web-api-instance-property
browser-compat: api.CSSMathClamp.value
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

خاصیت فقط خواندنی **`value`** در رابط {{domxref("CSSMathClamp")}} یک نمونه {{domxref("CSSNumericValue")}} برمی‌گرداند که مقدار ترجیحی (preferred value) آن را نشان می‌دهد.

## مقدار

یک {{domxref("CSSNumericValue")}}.

## مثال‌ها

### استفاده پایه

کد زیر یک شیء `CSSMathClamp` می‌سازد و سپس `value` آن را می‌خواند.

```js
const clamp = new CSSMathClamp(CSS.px(10), CSS.percent(50), CSS.px(500));

console.log(clamp.value); // CSSUnitValue {value: 50, unit: "percent"}
console.log(clamp.value.value); // 50
console.log(clamp.value.unit); // "percent"
```

`value` صرفاً هر {{domxref("CSSNumericValue")}} که به سازنده (constructor) داده شده است را برمی‌گرداند — در اینجا یک {{domxref("CSSUnitValue")}} است، زیرا `CSS.percent(50)` یک `CSSUnitValue` است. اگر یک عبارت پیچیده‌تر مانند `CSS.percent(50).add(CSS.em(2))` (یک {{domxref("CSSMathSum")}}) پاس داده شود، آنگاه `value` آن `CSSMathSum` را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSMathClamp.lower")}}
- {{domxref("CSSMathClamp.upper")}}