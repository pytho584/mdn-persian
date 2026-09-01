---
title: "DOMQuad: fromQuad() static method"
short-title: fromQuad()
slug: Web/API/DOMQuad/fromQuad_static
page-type: web-api-static-method
browser-compat: api.DOMQuad.fromQuad_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد ایستای **`fromQuad()`** در رابط {{domxref("DOMQuad")}} یک شیء `DOMQuad` جدید بر اساس مجموعه‌ای از مختصات که به شکل شیء `DOMQuad` دیگری ارائه شده‌اند، برمی‌گرداند.

## نحو (Syntax)

```js-nolint
DOMQuad.fromQuad()
DOMQuad.fromQuad(quad)
```

### پارامترها

- `quad` {{optional_inline}}
  - : یک {{domxref("DOMQuad")}} یا یک شیء با ویژگی‌های مشابه. تمام ویژگی‌ها به صورت پیش‌فرض `(0, 0, 0, 1)` هستند. ویژگی‌ها عبارت‌اند از:
    - {{domxref("DOMQuad/p1", "p1")}} {{optional_inline}}، {{domxref("DOMQuad/p2", "p2")}} {{optional_inline}}، {{domxref("DOMQuad/p3", "p3")}} {{optional_inline}}، {{domxref("DOMQuad/p4", "p4")}} {{optional_inline}}
      - : هر یک یک {{domxref("DOMPoint")}} یا یک شیء با ویژگی‌های مشابه است که یک گوشه از چهارضلعی را نشان می‌دهد.

    این شیء معمولاً باید یک نمونهٔ دیگر از {{domxref("DOMQuad")}} باشد، یا یک شیء موجود که از جایی بازیابی شده است. اگر این شیء را از ابتدا می‌سازید، بهتر است از سازندهٔ {{domxref("DOMQuad.DOMQuad", "DOMQuad()")}} استفاده کنید که چهار نقطه را جداگانه می‌پذیرد و از ایجاد شیء میانی جلوگیری می‌کند.

### مقدار بازگشتی

یک شیء {{domxref("DOMQuad")}}.

## مثال‌ها

### ایجاد یک چهارضلعی از یک DOMQuad موجود

این مثال نشان می‌دهد که چگونه یک `DOMQuad` جدید از یک `DOMQuad` موجود بسازید.

```js
const originalQuad = new DOMQuad(
  { x: 0, y: 0 },
  { x: 50, y: 0 },
  { x: 50, y: 50 },
  { x: 0, y: 50 },
);

const newQuad = DOMQuad.fromQuad(originalQuad);

console.log(newQuad.p1.x, newQuad.p1.y); // 0 0
console.log(newQuad.p2.x, newQuad.p2.y); // 50 0
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سازندهٔ {{domxref("DOMQuad.DOMQuad", "DOMQuad()")}}
- {{domxref("DOMPoint")}}
- {{domxref("DOMRect")}}