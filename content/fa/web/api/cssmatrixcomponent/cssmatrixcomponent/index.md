---
title: "CSSMatrixComponent: CSSMatrixComponent() constructor"
short-title: CSSMatrixComponent()
slug: Web/API/CSSMatrixComponent/CSSMatrixComponent
page-type: web-api-constructor
browser-compat: api.CSSMatrixComponent.CSSMatrixComponent
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازنده **`CSSMatrixComponent()`** یک شیء جدید از نوع {{domxref("CSSMatrixComponent")}} می‌سازد که مقادیر {{cssxref("transform-function/matrix", "matrix()")}} و {{cssxref("transform-function/matrix3d", "matrix3d()")}} ویژگی {{CSSXRef('transform')}} در CSS را نمایش می‌دهد.

## Syntax

```js-nolint
new CSSMatrixComponent(matrix)
new CSSMatrixComponent(matrix, options)
```

### Parameters

- {{domxref('CSSMatrixComponent.matrix','matrix')}}
  - : یک ماتریس دو بعدی یا سه بعدی.
- `options` {{optional_inline}}
  - : یک شیء با ویژگی زیر:
    - `is2D`
      - : یک مقدار بولین که مشخص می‌کند آیا `CSSMatrixComponent` ساخته شده باید به عنوان یک ماتریس دو بعدی در نظر گرفته شود. اگر حذف شود، این مقدار به طور پیش‌فرض برابر با ویژگی {{domxref("DOMMatrixReadOnly.is2D", "is2D")}} خود `matrix` خواهد بود.

## Examples

در دست تهیه

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}