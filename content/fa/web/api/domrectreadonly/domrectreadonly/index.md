---
title: "DOMRectReadOnly: DOMRectReadOnly() constructor"
short-title: DOMRectReadOnly()
slug: Web/API/DOMRectReadOnly/DOMRectReadOnly
page-type: web-api-constructor
browser-compat: api.DOMRectReadOnly.DOMRectReadOnly
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

سازنده **`DOMRectReadOnly()`** یک شیء جدید {{domxref("DOMRectReadOnly")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new DOMRectReadOnly(x, y, width, height)
```

### پارامترها

- `x`
  - : مختصات `x` مبدأ `DOMRectReadOnly`.
- `y`
  - : مختصات `y` مبدأ `DOMRectReadOnly`.
- `width`
  - : عرض `DOMRectReadOnly`.
- `height`
  - : ارتفاع `DOMRectReadOnly`.

## مثال‌ها

برای ایجاد یک `DOMRectReadOnly` جدید، می‌توانید خط کدی مانند زیر اجرا کنید:

```js
const myDOMRect = new DOMRectReadOnly(0, 0, 100, 100);
// running 'myDOMRect' in the console would then return
// DOMRectReadOnly { x: 0, y: 0, width: 100, height: 100, top: 0, right: 100, bottom: 100, left: 0 }
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMPoint")}}
- {{domxref("DOMRect")}}