---
title: "CSSUnitValue: value property"
short-title: value
slug: Web/API/CSSUnitValue/value
page-type: web-api-instance-property
browser-compat: api.CSSUnitValue.value
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

ویژگی **`value`** از رابط {{domxref("CSSUnitValue")}} تعداد واحدها را نشان می‌دهد.

## مقدار

یک عدد.

## مثال‌ها

### استفاده پایه

کد زیر یک {{domxref('CSSPositionValue')}} از سازنده‌های مجزای `CSSUnitValue` ایجاد می‌کند و سپس `CSSUnitValue.value` را پرس‌وجو می‌کند.

```js
const pos = new CSSPositionValue(
  new CSSUnitValue(5, "px"),
  new CSSUnitValue(10, "px"),
);

console.log(pos.x.value); // 5
console.log(pos.y.value); // 10
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('CSSUnitValue.unit')}}
- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)