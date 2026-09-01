---
title: "DOMPoint: سازنده DOMPoint()"
short-title: DOMPoint()
slug: Web/API/DOMPoint/DOMPoint
page-type: web-api-constructor
browser-compat: api.DOMPoint.DOMPoint
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

سازنده **`DOMPoint()`** یک شیء جدید از نوع {{domxref("DOMPoint")}} ایجاد و برمی‌گرداند، با توجه به مقادیر داده شده برای برخی یا تمام ویژگی‌های آن.

همچنین می‌توانید یک `DOMPoint` را با فراخوانی تابع ایستای {{domxref("DOMPoint.fromPoint_static", "DOMPoint.fromPoint()")}} ایجاد کنید. این تابع هر شیءای که پارامترهای مورد نیاز را داشته باشد، از جمله یک `DOMPoint` یا {{domxref("DOMPointReadOnly")}}، می‌پذیرد.

## نحو

```js-nolint
new DOMPoint()
new DOMPoint(x)
new DOMPoint(x, y)
new DOMPoint(x, y, z)
new DOMPoint(x, y, z, w)
```

### پارامترها

- `x` {{optional_inline}}
  - : مختصات `x` برای `DOMPoint` جدید.
- `y` {{optional_inline}}
  - : مختصات `y` برای `DOMPoint` جدید.
- `z` {{optional_inline}}
  - : مختصات `z` برای `DOMPoint` جدید.
- `w` {{optional_inline}}
  - : مقدار پرسپکتیو برای `DOMPoint` جدید.

## مثال‌ها

این مثال یک `DOMPoint` ایجاد می‌کند که گوشه‌ی بالا-چپ پنجره‌ی جاری را نشان می‌دهد، سپس یک نقطه‌ی دوم بر اساس نقطه‌ی اول ایجاد می‌کند که با ۱۰۰ پیکسل در هر دو جهت عمودی و افقی جابه‌جا شده است.

```js
const windTopLeft = new DOMPoint(window.screenX, window.screenY);
const newTopLeft = DOMPoint.fromPoint(windTopLeft);
newTopLeft.x += 100;
newTopLeft.y += 100;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DOMPointReadOnly.DOMPointReadOnly", "DOMPointReadOnly()")}}
- {{domxref("DOMRect")}}
- {{domxref("DOMMatrix")}}