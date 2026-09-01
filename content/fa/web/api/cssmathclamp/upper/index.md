---
title: "CSSMathClamp: upper property"
short-title: upper
slug: Web/API/CSSMathClamp/upper
page-type: web-api-instance-property
browser-compat: api.CSSMathClamp.upper
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

خاصیتِ فقط‌خواندنی **`upper`** در واسط {{domxref("CSSMathClamp")}} یک شیء {{domxref("CSSNumericValue")}} برمی‌گرداند که حداکثر مقدار را نشان می‌دهد.

## مقدار

یک {{domxref("CSSNumericValue")}}.

## مثال‌ها

### استفادهٔ پایه

کد زیر یک شیء `CSSMathClamp` می‌سازد و سپس مقدار `upper` آن را می‌خواند.

```js
const clamp = new CSSMathClamp(CSS.px(10), CSS.percent(50), CSS.px(500));

console.log(clamp.upper); // CSSUnitValue {value: 500, unit: "px"}
console.log(clamp.upper.value); // 500
console.log(clamp.upper.unit); // "px"
```

`upper` صرفاً همان {{domxref("CSSNumericValue")}}ای را برمی‌گرداند که به سازنده (constructor) داده شده بود — در اینجا یک {{domxref("CSSUnitValue")}} است، چون `CSS.px(500)` یک `CSSUnitValue` است. اگر یک عبارت پیچیده‌تر مانند `CSS.px(500).add(CSS.em(2))` (که یک {{domxref("CSSMathSum")}} است) داده شود، آنگاه `upper` همان `CSSMathSum` را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSMathClamp.lower")}}
- {{domxref("CSSMathClamp.value")}}