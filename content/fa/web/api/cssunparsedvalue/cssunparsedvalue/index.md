---
title: "CSSUnparsedValue: CSSUnparsedValue() constructor"
short-title: CSSUnparsedValue()
slug: Web/API/CSSUnparsedValue/CSSUnparsedValue
page-type: web-api-constructor
browser-compat: api.CSSUnparsedValue.CSSUnparsedValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازنده‌ی **`CSSUnparsedValue()`** یک شیء {{domxref("CSSUnparsedValue")}} جدید ایجاد می‌کند که مقادیر ویژگی‌هایی را نشان می‌دهد که به ویژگی‌های سفارشی (custom properties) ارجاع می‌دهند.

## Syntax

```js-nolint
new CSSUnparsedValue(members)
```

### Parameters

- `members`
  - : آرایه‌ای که مقادیر آن باید یا یک رشته (string) باشند یا یک {{domxref('CSSVariableReferenceValue')}}.

## Examples

### استفاده‌ی پایه

```js
const value = new CSSUnparsedValue(["4deg"]);
const values = new CSSUnparsedValue(["1em", "#445566", "-45px"]);

console.log(value); // CSSUnparsedValue {0: "4deg", length: 1}
console.log(values); // CSSUnparsedValue {0: "1em", 1: "#445566", 2: "-45px", length: 3}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("CSSUnparsedValue.entries")}}
- {{domxref("CSSUnparsedValue.forEach")}}
- {{domxref("CSSUnparsedValue.keys")}}
- {{domxref("CSSUnparsedValue.length")}}
- {{domxref("CSSUnparsedValue.values")}}
- [Using the CSS Typed OM](/en-US/docs/Web/API/CSS_Typed_OM_API/Guide)
- [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API)