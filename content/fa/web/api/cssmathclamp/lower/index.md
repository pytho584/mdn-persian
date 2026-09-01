---
title: "CSSMathClamp: lower property"
short-title: lower
slug: Web/API/CSSMathClamp/lower
page-type: web-api-instance-property
browser-compat: api.CSSMathClamp.lower
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`lower`** در رابط {{domxref("CSSMathClamp")}} یک شیء {{domxref("CSSNumericValue")}} برمی‌گرداند که مقدار حداقل آن را نشان می‌دهد.

## مقدار

یک {{domxref("CSSNumericValue")}}.

## مثال‌ها

### استفاده پایه

کد زیر یک شیء `CSSMathClamp` می‌سازد و سپس مقدار `lower` آن را می‌خواند.

```js
const clamp = new CSSMathClamp(CSS.px(10), CSS.percent(50), CSS.px(500));

console.log(clamp.lower); // CSSUnitValue {value: 10, unit: "px"}
console.log(clamp.lower.value); // 10
console.log(clamp.lower.unit); // "px"
```

`lower` به سادگی هر {{domxref("CSSNumericValue")}} که به سازنده داده شده است را برمی‌گرداند — در اینجا یک {{domxref("CSSUnitValue")}} است، زیرا `CSS.px(10)` یک `CSSUnitValue` است.
اگر یک عبارت پیچیده‌تر مانند `CSS.px(10).add(CSS.em(2))` (یک {{domxref("CSSMathSum")}}) منتقل کنید، `lower` همان `CSSMathSum` را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSMathClamp.value")}}
- {{domxref("CSSMathClamp.upper")}}