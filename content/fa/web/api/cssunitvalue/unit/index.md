---
title: "CSSUnitValue: unit property"
short-title: unit
slug: Web/API/CSSUnitValue/unit
page-type: web-api-instance-property
browser-compat: api.CSSUnitValue.unit
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

ویژگی فقط-خواندنی **`unit`** از رابط {{domxref("CSSUnitValue")}} یک رشته بازمی‌گرداند که [نوع واحد](/en-US/docs/Web/CSS/Guides/Values_and_units#units) را نشان می‌دهد.

## مقدار

یک رشته که نوع واحد را نشان می‌دهد، مانند `"em"`، `"px"`، `"%"` و غیره.

## مثال‌ها

### استفاده پایه

کد زیر یک {{domxref('CSSPositionValue')}} را از سازنده‌های جداگانه `CSSUnitValue` می‌سازد و سپس `CSSUnitValue.unit` را پرس‌وجو می‌کند.

```js
const pos = new CSSPositionValue(
  new CSSUnitValue(5, "px"),
  new CSSUnitValue(10, "em"),
);

console.log(pos.x.unit); // "px"
console.log(pos.y.unit); // "em"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('CSSUnitValue.value')}}
- [انواع داده‌های عددی CSS](/en-US/docs/Web/CSS/Guides/Values_and_units/Numeric_data_types)
- [مقادیر و واحدهای CSS](/en-US/docs/Web/CSS/Guides/Values_and_units)، یک فهرست از تمام انواع واحدهای ممکن
- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)