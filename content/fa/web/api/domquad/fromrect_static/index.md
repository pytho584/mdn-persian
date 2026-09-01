---
title: "DOMQuad: fromRect() static method"
---

---
title: "DOMQuad: fromRect() static method"
short-title: fromRect()
slug: Web/API/DOMQuad/fromRect_static
page-type: web-api-static-method
browser-compat: api.DOMQuad.fromRect_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد ایستای **`fromRect()`** در رابط {{domxref("DOMQuad")}} یک شیء `DOMQuad` جدید بر اساس مجموعه مختصات ارائه‌شده به شکل یک شیء {{domxref("DOMRect")}} برمی‌گرداند.

## نحو

```js-nolint
DOMQuad.fromRect()
DOMQuad.fromRect(rect)
```

### پارامترها

- `rect` {{optional_inline}}
  - : یک {{domxref("DOMRect")}}، {{domxref("DOMRectReadOnly")}} یا شیئی با همان ویژگی‌ها. همهٔ ویژگی‌ها به‌طور پیش‌فرض `0` هستند. ویژگی‌ها عبارت‌اند از:
    - {{domxref("DOMRect/x", "x")}} {{optional_inline}}
      - : مختصات x مبدأ مستطیل (گوشهٔ بالا-چپ).
    - {{domxref("DOMRect/y", "y")}} {{optional_inline}}
      - : مختصات y مبدأ مستطیل (گوشهٔ بالا-چپ).
    - {{domxref("DOMRect/width", "width")}} {{optional_inline}}
      - : عرض مستطیل.
    - {{domxref("DOMRect/height", "height")}} {{optional_inline}}
      - : ارتفاع مستطیل.

### مقدار بازگشتی

یک شیء {{domxref("DOMQuad")}}.

## مثال‌ها

### ایجاد یک چهارضلعی مستطیلی

این مثال یک `DOMQuad` را از صفر می‌سازد که اتفاقاً مستطیلی است. استفاده از `fromRect()` راحت‌تر از به‌کارگیری سازندهٔ {{domxref("DOMQuad.DOMQuad", "DOMQuad()")}} است.

```js
const quad = DOMQuad.fromRect({ x: 10, y: 20, width: 100, height: 50 });

console.log(quad.p1); // DOMPoint {x: 10, y: 20, z: 0, w: 1}
console.log(quad.p2); // DOMPoint {x: 110, y: 20, z: 0, w: 1}
console.log(quad.p3); // DOMPoint {x: 110, y: 70, z: 0, w: 1}
console.log(quad.p4); // DOMPoint {x: 10, y: 70, z: 0, w: 1}
```

### ایجاد یک چهارضلعی از روی DOMRect

این مثال نشان می‌دهد که چگونه می‌توان یک `DOMQuad` را از روی یک شیء {{domxref("DOMRect")}} ایجاد کرد.

```js
const domRect = new DOMRect(50, 60, 200, 100);
const quad = DOMQuad.fromRect(domRect);

console.log(quad.p1); // DOMPoint {x: 50, y: 60, z: 0, w: 1}
console.log(quad.p2); // DOMPoint {x: 250, y: 60, z: 0, w: 1}
console.log(quad.p3); // DOMPoint {x: 250, y: 160, z: 0, w: 1}
console.log(quad.p4); // DOMPoint {x: 50, y: 160, z: 0, w: 1}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سازندهٔ {{domxref("DOMQuad.DOMQuad", "DOMQuad()")}}
- {{domxref("DOMRect")}}
- {{domxref("DOMPoint")}}