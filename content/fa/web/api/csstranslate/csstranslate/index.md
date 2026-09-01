---
title: "CSSTranslate: CSSTranslate() constructor"
---

---
title: "CSSTranslate: CSSTranslate() constructor"
short-title: CSSTranslate()
slug: Web/API/CSSTranslate/CSSTranslate
page-type: web-api-constructor
browser-compat: api.CSSTranslate.CSSTranslate
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازندهٔ **`CSSTranslate()`** یک شیء جدید {{domxref("CSSTranslate")}} می‌سازد که مقدار {{cssxref("transform-function/translate", "translate()")}} ویژگیِ مجزای {{CSSXref('transform')}} را در CSS نشان می‌دهد.

## نحو

```js-nolint
new CSSTranslate(x, y)
new CSSTranslate(x, y, z)
```

### پارامترها

- {{domxref('CSSTranslate.x','x')}}
  - : مقداری برای محور x از شیء {{domxref('CSSTranslate')}} که قرار است ساخته شود. این مقدار باید از نوع {{cssxref('length-percentage')}} باشد.
- {{domxref('CSSTranslate.y','y')}}
  - : مقداری برای محور y از شیء {{domxref('CSSTranslate')}} که قرار است ساخته شود. این مقدار باید از نوع {{cssxref('length-percentage')}} باشد.
- {{domxref('CSSTranslate.z','z')}} {{optional_inline}}
  - : مقداری برای محور z از شیء {{domxref('CSSTranslate')}} که قرار است ساخته شود. این مقدار باید از نوع {{cssxref('length')}} باشد.

    اگر مقداری برای `z-axis` (محور z) ارسال شود، این یک تبدیل سه‌بعدی (3D transform) است و مقدار `is2D` برابر `false` قرار خواهد گرفت.

### استثناها

- [`TypeError`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError)
  - : اگر مقدار `CSSTranslate.x` یا `CSSTranslate.y` از نوع {{cssxref('length-percentage')}} نباشد، پرتاب می‌شود.
- [`TypeError`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError)
  - : اگر مقدار `CSSTranslate.z` وجود داشته باشد اما از نوع {{cssxref('length')}} نباشد، پرتاب می‌شود.

## مثال‌ها

این بخش به‌زودی تکمیل می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}