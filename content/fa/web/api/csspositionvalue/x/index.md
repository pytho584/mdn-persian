---
title: "CSSPositionValue: x property"
short-title: x
slug: Web/API/CSSPositionValue/x
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPositionValue.x
---

{{deprecated_header}}{{APIRef("CSS Typed Object Model API")}}{{Non-standard_header}}

ویژگی **`x`** در رابط {{domxref("CSSPositionValue")}} موقعیت آیتم را در محور افقی صفحه وب برمیگرداند.

## مقدار

یک {{domxref('CSSNumericValue')}}.

## مثالها

### استفاده پایه

مثال زیر یک `<div>` ظرف را ۵ پیکسل از بالا و ۱۰ پیکسل از چپ صفحه قرار میدهد.

```js
let someDiv = document.getElementById("container");
let position = new CSSPositionValue(CSS.px(5), CSS.px(10));

someDiv.attributeStyleMap.set("object-position", position);
console.log(position.x.value, position.y.value);
```

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSPositionValue.CSSPositionValue", "CSSPositionValue()")}}
- {{domxref("CSSPositionValue.y")}}
- [استفاده از CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)