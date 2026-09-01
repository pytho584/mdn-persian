---
title: "CSSPositionValue: CSSPositionValue() constructor"
short-title: CSSPositionValue()
slug: Web/API/CSSPositionValue/CSSPositionValue
page-type: web-api-constructor
status:
  - deprecated
  - non-standard
browser-compat: api.CSSPositionValue.CSSPositionValue
---

{{APIRef("CSS Typed Object Model API")}}{{deprecated_header}}{{Non-standard_header}}

سازندهٔ **`CSSPositionValue()`** یک شیء جدید {{domxref("CSSPositionValue")}} ایجاد می‌کند که نشان‌دهندهٔ مقادیر ویژگی‌هایی است که یک موقعیت را می‌پذیرند، مانند {{cssxref('object-position')}}.

## نحو

```js-nolint
new CSSPositionValue(x, y)
```

### پارامترها

- `x`
  - : موقعیتی در امتداد محور افقی صفحهٔ وب.
- `y`
  - : موقعیتی در امتداد محور عمودی صفحهٔ وب.

## مثال‌ها

### استفادهٔ پایه

مثال زیر، یک `<div>` کانتینر را در فاصلهٔ ۵ پیکسل از بالا و ۱۰ پیکسل از چپ صفحه قرار می‌دهد.

```js
let someDiv = document.getElementById("container");
let position = new CSSPositionValue(CSS.px(5), CSS.px(10));

someDiv.attributeStyleMap.set("object-position", position);
console.log(position.x.value, position.y.value); // 5 10
```

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CSSPositionValue.x")}}
- {{domxref("CSSPositionValue.y")}}
- [Using the CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)