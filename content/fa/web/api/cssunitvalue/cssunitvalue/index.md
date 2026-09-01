---
title: "CSSUnitValue: CSSUnitValue() constructor"
---

---
title: "CSSUnitValue: CSSUnitValue() constructor"
short-title: CSSUnitValue()
slug: Web/API/CSSUnitValue/CSSUnitValue
page-type: web-api-constructor
browser-compat: api.CSSUnitValue.CSSUnitValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازندهٔ **`CSSUnitValue()`** یک شیء جدید از نوع {{domxref("CSSUnitValue")}} می‌سازد که نمایانگر مقادیر دارای یک نوع واحد است. برای مثال، «42px» با یک `CSSNumericValue` نمایش داده می‌شود.

## Syntax

```js-nolint
new CSSUnitValue(value, unit)
```

### Parameters

- `value`
  - : عددی که تعداد واحدها را مشخص می‌کند.
- `unit`
  - : رشته‌ای که نوع واحد را مشخص می‌کند.

## Examples

### Basic usage

مثال زیر روش ایجاد یک {{domxref('CSSPositionValue')}} را با استفاده از سازنده‌های جداگانهٔ `CSSUnitValue` نشان می‌دهد.

```js
let pos = new CSSPositionValue(
  new CSSUnitValue(5, "px"),
  new CSSUnitValue(10, "px"),
);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref('CSSUnitValue.unit')}}
- {{domxref('CSSUnitValue.value')}}
- [Using the CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)