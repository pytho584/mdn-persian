---
title: "CSSScale: CSSScale() constructor"
short-title: CSSScale()
slug: Web/API/CSSScale/CSSScale
page-type: web-api-constructor
browser-compat: api.CSSScale.CSSScale
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازندهٔ **`CSSScale()`** یک شیء جدید {{domxref("CSSScale")}} می‌سازد که مقادیر {{cssxref("transform-function/scale", "scale()")}} و {{cssxref("transform-function/scale3d", "scale3d()")}} ویژگی مستقل {{CSSXref('transform')}} را در CSS نمایش می‌دهد.

## نحو

```js-nolint
new CSSScale(x, y)
new CSSScale(x, y, z)
```

### پارامترها

- {{domxref('CSSScale.x','x')}}
  - : مقداری برای محور x از شیء {{domxref('CSSScale')}} که قرار است ساخته شود.
    این مقدار باید یا یک عدد باشد (که به یک {{domxref("CSSUnitValue")}} با `unit: "number"` تبدیل می‌شود) یا یک {{domxref("CSSNumericValue")}}.
- {{domxref('CSSScale.y','y')}}
  - : مقداری برای محور y از شیء {{domxref('CSSScale')}} که قرار است ساخته شود.
    این مقدار باید یا یک عدد باشد (که به یک {{domxref("CSSUnitValue")}} با `unit: "number"` تبدیل می‌شود) یا یک {{domxref("CSSNumericValue")}}.
- {{domxref('CSSScale.z','z')}} {{optional_inline}}
  - : مقداری برای محور z از شیء {{domxref('CSSScale')}} که قرار است ساخته شود.
    این مقدار باید یا یک عدد باشد (که به یک {{domxref("CSSUnitValue")}} با `unit: "number"` تبدیل می‌شود) یا یک {{domxref("CSSNumericValue")}}. اگر مقداری ارسال شود، مقدار `is2D` روی `false` تنظیم خواهد شد.

## مثال‌ها

در دست انجام.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}