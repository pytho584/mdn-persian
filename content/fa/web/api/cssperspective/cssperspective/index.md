---
title: "CSSPerspective: CSSPerspective() constructor"
short-title: CSSPerspective()
slug: Web/API/CSSPerspective/CSSPerspective
page-type: web-api-constructor
browser-compat: api.CSSPerspective.CSSPerspective
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازندهٔ **`CSSPerspective()`** یک شیء جدید {{domxref("CSSPerspective")}} می‌سازد که مقدار {{cssxref("transform-function/perspective", "perspective()")}} پراپرتی {{CSSXref('transform')}} را در CSS نشان می‌دهد.

## نحو (Syntax)

```js-nolint
new CSSPerspective(length)
```

### پارامترها

- {{domxref('CSSPerspective.length','length')}}
  - : مقداری برای فاصله از صفحهٔ z=0 در شیء {{domxref('CSSPerspective')}} که قرار است ساخته شود. این مقدار باید یک {{cssxref('length')}} باشد.

### استثناها

- [`TypeError`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError)
  - : اگر مقدار `CSSPerspective.length` وجود داشته باشد اما یک {{cssxref('length')}} نباشد، پرتاب می‌شود.

## مثال‌ها

待補充

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
