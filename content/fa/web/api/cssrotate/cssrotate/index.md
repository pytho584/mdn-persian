---
title: "CSSRotate: CSSRotate() constructor"
---

---
title: "CSSRotate: CSSRotate() constructor"
short-title: CSSRotate()
slug: Web/API/CSSRotate/CSSRotate
page-type: web-api-constructor
browser-compat: api.CSSRotate.CSSRotate
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازندهٔ **`CSSRotate()`** یک شیء جدید {{domxref("CSSRotate")}} می‌سازد که مقدار {{cssxref("transform-function/rotate", "rotate()")}} ویژگیِ منفردِ {{CSSXref('transform')}} را در CSS نمایش می‌دهد.

این سازنده می‌تواند به‌صورت یک چرخش دوبعدی با زاویه‌ای مشخص یا یک چرخش سه‌بعدی با زاویه‌ای حول یک محور مشخص تعریف شود.

## سینتکس

```js-nolint
new CSSRotate(angle)
new CSSRotate(x, y, z, angle)
```

### پارامترها

- {{domxref('CSSRotate.angle','angle')}}
  - : مقداری برای زاویهٔ شیء {{domxref('CSSRotate')}} که قرار است ساخته شود. این مقدار باید یک {{domxref('CSSNumericValue')}} باشد.
- {{domxref('CSSRotate.x','x')}} {{optional_inline}}
  - : مقداری برای محور x شیء {{domxref('CSSRotate')}} که قرار است ساخته شود. این مقدار باید یا یک عدد باشد (که در یک {{domxref("CSSUnitValue")}} با `unit: "number"` قرار می‌گیرد) یا یک {{domxref("CSSNumericValue")}}. این پارامتر فقط هنگام ساخت چرخش سه‌بعدی استفاده می‌شود و در آن صورت الزامی است.
- {{domxref('CSSRotate.y','y')}} {{optional_inline}}
  - : مقداری برای محور y شیء {{domxref('CSSRotate')}} که قرار است ساخته شود. این مقدار باید یا یک عدد باشد (که در یک {{domxref("CSSUnitValue")}} با `unit: "number"` قرار می‌گیرد) یا یک {{domxref("CSSNumericValue")}}. این پارامتر فقط هنگام ساخت چرخش سه‌بعدی استفاده می‌شود و در آن صورت الزامی است.
- {{domxref('CSSRotate.z','z')}} {{optional_inline}}
  - : مقداری برای محور z شیء {{domxref('CSSRotate')}} که قرار است ساخته شود. این مقدار باید یا یک عدد باشد (که در یک {{domxref("CSSUnitValue")}} با `unit: "number"` قرار می‌گیرد) یا یک {{domxref("CSSNumericValue")}}. این پارامتر فقط هنگام ساخت چرخش سه‌بعدی استفاده می‌شود و در آن صورت الزامی است.

### استثناها

- [`TypeError`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError)
  - : اگر مقدار `CSSRotate.angle` یک مقدار [\<angle>](/en-US/docs/Web/CSS/Reference/Values/angle) نباشد یا `CSSRotate.x`، `CSSRotate.y`، `CSSRotate.z` مقادیر [\<number>](/en-US/docs/Web/CSS/Reference/Values/number) نباشند، این خطا پرتاب می‌شود.

## مثال‌ها

در دست انجام.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}