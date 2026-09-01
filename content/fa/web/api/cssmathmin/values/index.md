---
title: "CSSMathMin: values property"
short-title: values
slug: Web/API/CSSMathMin/values
page-type: web-api-instance-property
browser-compat: api.CSSMathMin.values
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`values`** در رابط {{domxref("CSSMathMin")}} یک {{domxref("CSSNumericArray")}} برمی‌گرداند که شامل اشیاء {{domxref("CSSNumericValue")}} است که برای یافتن کمینه با هم مقایسه می‌شوند.

## مقدار

یک {{domxref('CSSNumericArray')}}.

## مثال‌ها

### استفادهٔ پایه

کد زیر یک شیء `CSSMathMin` می‌سازد و `values` و طول آن را در کنسول ثبت می‌کند.

```js
const min = new CSSMathMin(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(min.values);
// CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(min.values.length); // 3
```

سپس روی `values` پیمایش می‌کنیم و نوع، مقدار، واحد و متن تبدیل‌شدهٔ هر کدام را ثبت می‌کنیم.
هر کدام از این‌ها با اشیاء {{domxref("CSSNumericValue")}} که به سازنده (یا عملوندهای تابع CSS {{cssxref("min", "min()")}} که نشان می‌دهد) ارسال شده‌اند، به همان ترتیب مطابقت دارند.

```js
for (const value of min.values) {
  console.log(
    `${value.constructor.name}: ${value.value} ${value.unit} (${value})`,
  );
}

// CSSUnitValue: 10 px (10px)
// CSSUnitValue: 5 em (5em)
// CSSUnitValue: 50 percent (50%)
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}