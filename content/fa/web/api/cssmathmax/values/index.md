---
title: "CSSMathMax: values property"
short-title: values
slug: Web/API/CSSMathMax/values
page-type: web-api-instance-property
browser-compat: api.CSSMathMax.values
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`values`** در رابط {{domxref("CSSMathMax")}} یک {{domxref("CSSNumericArray")}} برمی‌گرداند که شامل اشیاء {{domxref("CSSNumericValue")}} است که برای یافتن بیشینه با هم مقایسه می‌شوند.

## مقدار

یک {{domxref('CSSNumericArray')}}.

## مثال‌ها

### استفاده پایه

کد زیر یک شیء `CSSMathMax` می‌سازد و `values` و طول آن را در کنسول ثبت می‌کند.

```js
const max = new CSSMathMax(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(max.values);
// CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(max.values.length); // 3
```

سپس روی `values` پیمایش می‌کنیم و نوع، مقدار، واحد و متن رشته‌ای آن‌ها را ثبت می‌کنیم.
هر یک از این‌ها با اشیاء {{domxref("CSSNumericValue")}} که به سازنده ارسال شده‌اند (یا عملوندهای تابع CSS {{cssxref("max", "max()")}} که آن را نشان می‌دهد) مطابقت دارد، به همان ترتیب.

```js
for (const value of max.values) {
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