---
title: "CSSNumericValue: toSum() method"
---

---
title: "CSSNumericValue: toSum() method"
short-title: toSum()
slug: Web/API/CSSNumericValue/toSum
page-type: web-api-instance-method
browser-compat: api.CSSNumericValue.toSum
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

متد **`toSum()`** از رابط {{domxref("CSSNumericValue")}} مقدار شیء را به یک {{domxref("CSSMathSum")}} متشکل از {{domxref("CSSUnitValue")}}ها تبدیل می‌کند که در صورت امکان فقط از واحدهای مشخص‌شده استفاده می‌کند. اگر بدون واحد فراخوانی شود، به‌جای آن مقدار را به یک مجموعِ حداقلی از `CSSUnitValue`ها ساده‌سازی می‌کند.

## سینتکس

```js-nolint
toSum()
toSum(unit1)
toSum(unit1, unit2)
toSum(unit1, unit2, /* …, */ unitN)
```

### پارامترها

- `unit1`, …, `unitN` {{optional_inline}}
  - : واحدهایی که مقدار باید به آن‌ها تبدیل شود.

### مقدار بازگشتی

یک {{domxref('CSSMathSum')}}.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که هر یک از `unit1`, …, `unitN` یک شناسهٔ واحد معتبر نباشد.
- {{jsxref("TypeError")}}
  - : در شرایط زیر پرتاب می‌شود:
    - مقدار نتواند به صورت مجموع `CSSUnitValue`ها بیان شود — برای مثال، چون یکی از جمله‌های آن واحد ترکیبی (مانند `px * s`) دارد که نمی‌توان آن را با یک `CSSUnitValue` تنها نشان داد.
    - یک یا چند واحد به متد ارسال شده باشد و مقدار شامل جمله‌ای باشد که واحد آن با هیچ‌کدام از آن‌ها سازگار نیست.

## مثال‌ها

### استفادهٔ پایه

```js
let v = CSS.px("23").add(CSS.percent("4")).add(CSS.cm("3")).add(CSS.in("9"));
v.toString(); // => "calc(23px + 4% + 3cm + 9in)"
v.toSum("px", "percent").toString(); // => "calc(1000.39px + 4%)"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}