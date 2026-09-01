---
title: "CSSMathNegate: value property"
short-title: value
slug: Web/API/CSSMathNegate/value
page-type: web-api-instance-property
browser-compat: api.CSSMathNegate.value
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

خاصیتِ فقط‌خواندنی **`value`** در رابط {{domxref("CSSMathNegate")}}، مقدار {{domxref("CSSNumericValue")}}ای را که نفی (negate) شده است بازمی‌گرداند.

این همان مقداری است که به سازنده (constructor) ارسال شده و به یک {{domxref("CSSNumericValue")}} تبدیل شده است (اگر از قبل چنین نبوده باشد). اگر یک عدد ساده به سازنده ارسال شده باشد، مقداری که این خاصیت بازمی‌گرداند، همان مقدار ورودی است که در یک {{domxref("CSSUnitValue")}} با `unit: "number"` قرار گرفته است.

## مقدار

یک {{domxref("CSSNumericValue")}} یا یکی از انواع مشتق‌شده از آن.

## مثال‌ها

### استفاده پایه

کد زیر یک شیء `CSSMathNegate` می‌سازد و سپس `value` آن را می‌خواند.

در این حالت، `CSS.px(10)` را ارسال کرده‌ایم، بنابراین `value` یک {{domxref("CSSUnitValue")}} است. ارسال یک عبارت ترکیبی مانند `CSS.px(10).add(CSS.percent(5))` باعث می‌شود `value` یک {{domxref("CSSMathSum")}} بازگرداند.

```js
const negated = new CSSMathNegate(CSS.px(10));

console.log(negated.value); // CSSUnitValue {value: 10, unit: "px"}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSMathInvert.value")}}