---
title: "CSSMathInvert: value property"
---

---
title: "CSSMathInvert: value property"
short-title: value
slug: Web/API/CSSMathInvert/value
page-type: web-api-instance-property
browser-compat: api.CSSMathInvert.value
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

**`value`** یک خاصیت فقطخواندنی در رابط {{domxref("CSSMathInvert")}} است که مقدار {{domxref("CSSNumericValue")}} در حال معکوس شدن را برمیگرداند.

این همان پارامتری است که هنگام ایجاد این شیء به سازنده (constructor) داده شده بود.

## Value

یک {{domxref('CSSNumericValue')}} یا یکی از انواع مشتق‌شده از آن.

## Examples

### استفاده پایه

کد زیر یک شیء `CSSMathInvert` می‌سازد و سپس `value` آن را می‌خواند.

```js
const inverted = new CSSMathInvert(CSS.percent(4));

console.log(inverted.value); // CSSUnitValue {value: 4, unit: "percent"}
```

`value` دقیقاً همان چیزی را برمی‌گرداند که در سازنده به `arg` داده شده است. در این حالت، ما `CSS.percent(4)` را داده‌ایم، بنابراین `value` یک {{domxref('CSSUnitValue')}} است. اگر عبارتی مانند `CSS.percent(4).add(CSS.em(2))` ارسال کنید، `value` یک {{domxref('CSSMathSum')}} برمی‌گرداند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("CSSMathNegate.value")}}
