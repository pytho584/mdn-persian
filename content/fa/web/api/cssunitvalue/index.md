---
title: CSSUnitValue
slug: Web/API/CSSUnitValue
page-type: web-api-interface
browser-compat: api.CSSUnitValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابط **`CSSUnitValue`** از [CSS Typed Object Model API](/en-US/docs/Web/API/CSS_Typed_OM_API) مقادیری را نشان می‌دهد که شامل یک [نوع واحد](/en-US/docs/Web/CSS/Guides/Values_and_units#units) هستند.

برای مثال، مقدار `42px` (یک {{cssxref("&lt;dimension&gt;")}}) توسط یک `CSSNumericValue` نمایش داده می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSUnitValue.CSSUnitValue", "CSSUnitValue()")}}
  - : یک شیء جدید `CSSUnitValue` ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref('CSSUnitValue.value')}}
  - : یک عدد که تعداد واحدها را نشان می‌دهد.
    برای یک `CSSNumericValue` که `42px` را نمایش می‌دهد، این مقدار `42` خواهد بود.
- {{domxref('CSSUnitValue.unit')}} {{ReadOnlyInline}}
  - : یک رشته که نوع واحد را نشان می‌دهد. برای یک `CSSNumericValue` که `42px` را نمایش می‌دهد، این مقدار `"px"` خواهد بود.

## روش‌های ایستا

_همچنین روش‌هایی را از رابط والد خود، {{DOMxRef("CSSNumericValue")}}، به ارث می‌برد._

## روش‌های نمونه

_همچنین روش‌هایی را از رابط والد خود، {{DOMxRef("CSSNumericValue")}}، به ارث می‌برد._

## نمونه‌ها

### استفاده پایه

نمونه زیر روش ایجاد یک {{domxref('CSSPositionValue')}} از سازنده‌های جداگانه `CSSUnitValue` را نشان می‌دهد.

```js
let pos = new CSSPositionValue(
  new CSSUnitValue(5, "px"),
  new CSSUnitValue(10, "px"),
);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [انواع داده عددی CSS](/en-US/docs/Web/CSS/Guides/Values_and_units/Numeric_data_types)
- [مقادیر و واحدهای CSS](/en-US/docs/Web/CSS/Guides/Values_and_units)، فهرستی از تمام واحدها و انواع داده ممکن