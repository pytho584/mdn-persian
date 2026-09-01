---
title: "CSSMathSum: values property"
short-title: values
slug: Web/API/CSSMathSum/values
page-type: web-api-instance-property
browser-compat: api.CSSMathSum.values
---

{{APIRef("CSS Typed Object Model API")}}{{AvailableInWorkers}}

ویژگی فقط-خواندنی **`values`** از رابط {{domxref("CSSMathSum")}} یک {{domxref("CSSNumericArray")}} شامل اشیاء {{domxref("CSSNumericValue")}} که با هم جمع شده‌اند را بازمی‌گرداند.

## مقدار

یک {{domxref('CSSNumericArray')}}.

## مثال‌ها

### استفاده پایه

کد زیر یک شیء `CSSMathSum` ایجاد می‌کند و `values` و طول آن را در کنسول ثبت می‌کند.

```js
const sum = new CSSMathSum(CSS.px(10), CSS.em(5), CSS.percent(50));

console.log(sum.values);
// CSSNumericArray {0: CSSUnitValue, 1: CSSUnitValue, 2: CSSUnitValue, length: 3}
console.log(sum.values.length); // 3
```

سپس روی `values` پیمایش می‌کنیم و نوع، مقدار، واحد و متن رشته‌ای آن‌ها را ثبت می‌کنیم. هر یک از این موارد با اشیاء {{domxref("CSSNumericValue")}} که به سازنده ارسال شده‌اند (یا عبارت‌های جمع/تفریقی که نشان می‌دهد) مطابقت دارد، به همان ترتیب.

```js
for (const value of sum.values) {
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

## سازگاری با مرورگر

{{Compat}}