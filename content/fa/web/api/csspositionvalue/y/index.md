---
title: "CSSPositionValue: y property"
short-title: y
slug: Web/API/CSSPositionValue/y
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPositionValue.y
---

{{deprecated_header}}{{APIRef("CSS Typed Object Model API")}}{{Non-standard_header}}

ویژگی **`y`** در رابط {{domxref("CSSPositionValue")}} موقعیت عنصر را در امتداد محور عمودی بازمی‌گرداند.

## مقدار

یک {{domxref('CSSNumericValue')}}.

## نمونه‌ها

### کاربرد پایه

مثال زیر یک `<div>` ظرف را ۵ پیکسل از بالا و ۱۰ پیکسل از چپ صفحه قرار می‌دهد:

```js
let replaceEl = document.getElementById("container");
let position = new CSSPositionValue(CSS.px(5), CSS.px(10));

replaceEl.attributeStyleMap.set("object-position", position);
console.log(position.x.value, position.y.value);
```

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CSSPositionValue.CSSPositionValue", "CSSPositionValue()")}}
- {{domxref("CSSPositionValue.x")}}
- [Using the CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)