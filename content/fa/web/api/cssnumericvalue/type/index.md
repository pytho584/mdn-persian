---
title: "CSSNumericValue: type() method"
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`type()`** از رابط {{domxref("CSSNumericValue")}} نوع `CSSNumericValue` را بازمی‌گرداند؛ این نوع یکی از موارد `angle`، `flex`، `frequency`، `length`، `resolution`، `percent`، `percentHint` یا `time` است.

## نحو

```js-nolint
type()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک دیکشنری `CSSNumericType` که شامل ویژگی‌های زیر است:

- `length`
- `angle`
- `time`
- `frequency`
- `resolution`
- `flex`
- `percent`
- `percentHint`

برای هر ویژگی به‌جز `percentHint`، مقدار یک عدد صحیح است که توان (power) آن واحد را نشان می‌دهد. برای مثال، یک مقدار عددی مانند `calc(1px * 1em)` خروجی `{ length: 2 }` را برمی‌گرداند.

ویژگی `percentHint` یک رشته است که نوع مقداری را که درصد به آن اعمال می‌شود را نشان می‌دهد. مقدار رشته‌ای آن همانند ویژگی‌های نوع است: `"length"`، `"angle"`، `"time"`، `"frequency"`، `"resolution"`، `"flex"` یا `"percent"`. این ویژگی نشان می‌دهد که نوع موردنظر در واقع یک درصد را نگه می‌دارد، اما آن درصد در نهایت به نوع پایهٔ اشاره‌شده (hinted base type) تبدیل می‌شود و بنابراین در نوع با آن جایگزین شده است.

### استثناها

هیچ.

## مثال‌ها

### استفاده پایه

```js
let mathSum = CSS.px("23")
  .sub(CSS.percent("4"))
  .sub(CSS.cm("3"))
  .sub(CSS.in("9"));
// Returns an object with the structure: {length: 1, percentHint: "length"}
let cssNumericType = mathSum.type();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}