---
title: "DOMPointReadOnly: DOMPointReadOnly() constructor"
short-title: DOMPointReadOnly()
slug: Web/API/DOMPointReadOnly/DOMPointReadOnly
page-type: web-api-constructor
browser-compat: api.DOMPointReadOnly.DOMPointReadOnly
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

سازنده **`DOMPointReadOnly()`** یک شیء جدید {{domxref("DOMPointReadOnly")}} برمی‌گرداند که یک نقطه را در فضای دوبعدی یا سه‌بعدی، به‌صورت اختیاری با پرسپکتیو، نشان می‌دهد و مقادیر آن را نمی‌توان توسط کد اسکریپت تغییر داد.

## نحو (Syntax)

```js-nolint
new DOMPointReadOnly()
new DOMPointReadOnly(x)
new DOMPointReadOnly(x, y)
new DOMPointReadOnly(x, y, z)
new DOMPointReadOnly(x, y, z, w)
```

### پارامترها

- `x` {{optional_inline}}
  - : مقدار مختصات افقی، x، به‌صورت یک عدد اعشاری. مقدار پیش‌فرض 0 است.
- `y` {{optional_inline}}
  - : مقدار مختصات عمودی، y، به‌صورت یک عدد اعشاری. مقدار پیش‌فرض 0 است.
- `z` {{optional_inline}}
  - : مقدار مختصات عمق، z، به‌صورت یک عدد اعشاری. مقدار پیش‌فرض 0 است.
- `w` {{optional_inline}}
  - : مقدار پرسپکتیو، w، به‌صورت یک عدد اعشاری. مقدار پیش‌فرض 1 است.

> [!NOTE]
> هر یک از این مقادیر چیزی است که به آن عدد _نامحدود_ (unrestricted number) گفته می‌شود. علاوه بر هر مقدار اعشاری متناهی، می‌توانید از مقادیر ویژه مانند ±{{jsxref("Infinity")}} و {{jsxref("NaN")}} نیز استفاده کنید.

### مقدار بازگشتی

یک شیء جدید {{domxref("DOMPointReadOnly")}} که مکان مشخص‌شده در فضا را نشان می‌دهد.

## مثال‌ها

کد زیر ساخت نقاط دوبعدی و سه‌بعدی را نشان می‌دهد.

```js
const point2D = new DOMPointReadOnly(50, 25);
const point3D = new DOMPointReadOnly(50, 0, 10);
const perspectivePoint3D = new DOMPointReadOnly(50, 50, 25, 0.5);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}