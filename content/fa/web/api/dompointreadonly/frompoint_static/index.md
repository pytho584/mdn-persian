---
title: "DOMPointReadOnly: fromPoint() static method"
short-title: fromPoint()
slug: Web/API/DOMPointReadOnly/fromPoint_static
page-type: web-api-static-method
browser-compat: api.DOMPointReadOnly.fromPoint_static
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

متد استاتیک **{{domxref("DOMPointReadOnly")}}** به نام `fromPoint()` یک شیء جدید `DOMPointReadOnly` را بر اساس یک نقطهٔ مبدأ ایجاد و بازمی‌گرداند.

همچنین می‌توانید با استفاده از سازندهٔ {{domxref("DOMPointReadOnly.DOMPointReadOnly", "DOMPointReadOnly()")}} یک شیء جدید `DOMPointReadOnly` ایجاد کنید.

## نحو (Syntax)

```js-nolint
DOMPointReadOnly.fromPoint(sourcePoint)
```

### پارامترها

- `sourcePoint`
  - : یک نمونه از {{domxref("DOMPoint")}} یا {{domxref("DOMPointReadOnly")}}، یا یک شیء حاوی ویژگی‌های زیر که مقادیر ویژگی‌های نقطهٔ جدید از آن گرفته می‌شود:
    - `x`
      - : یک عدد اعشاری بدون محدودیت که مختصات `x` نقطه در فضا را نشان می‌دهد. این معمولاً مختصات افقی است، با مقادیر مثبت به سمت راست و مقادیر منفی به سمت چپ. مقدار پیش‌فرض `0` است.
    - `y`
      - : یک عدد اعشاری بدون محدودیت که مختصات `y` نقطه را فراهم می‌کند. این مختصات عمودی است و مادامی‌که تبدیل‌هایی بر روی سیستم مختصات اعمال نشده باشد، مقادیر مثبت به سمت پایین و مقادیر منفی به سمت بالای صفحه هستند. مقدار پیش‌فرض `0` است.
    - `z`
      - : یک عدد اعشاری بدون محدودیت که مختصات `z` نقطه را می‌دهد. این مختصات (با فرض نبودن تبدیل‌هایی که وضعیت را تغییر دهند) مختصات عمق است؛ مقادیر مثبت به کاربر نزدیک‌تر و مقادیر منفی به سمت داخل صفحه عقب می‌روند. مقدار پیش‌فرض `0` است.
    - `w`
      - : مقدار پرسپکتیو `w` نقطه، به صورت یک عدد اعشاری بدون محدودیت. مقدار پیش‌فرض `1` است.

### مقدار بازگشتی

یک شیء جدید {{domxref("DOMPointReadOnly")}} (که با نقطهٔ مبدأ یکسان است).

## مثال‌ها

### ایجاد یک نقطهٔ دوبعدی

این نمونه یک نقطهٔ دوبعدی ایجاد می‌کند و یک شیء درون‌خطی شامل مقادیر مورد استفاده برای {{domxref("DOMPointReadOnly.x", "x")}} و {{domxref("DOMPointReadOnly.y", "y")}} را مشخص می‌کند. ویژگی‌های `z` و `w` اجازه دارند مقادیر پیش‌فرض خود را حفظ کنند (به ترتیب `0` و `1`).

```js
const point2D = DOMPointReadOnly.fromPoint({ x: 25, y: 25 });
```

### ایجاد یک نقطهٔ سه‌بعدی با استفاده از یک نقطهٔ موجود

این مثال نقطه‌ای به نام `origPoint` از نوع {{domxref("DOMPoint")}} را با استفاده از {{domxref("DOMPoint.DOMPoint", "DOMPoint()")}} ایجاد می‌کند. سپس آن نقطه به عنوان ورودی `fromPoint()` برای ایجاد نقطهٔ جدید، `newPoint`، استفاده می‌شود.

```js
const origPoint = new DOMPoint(25, 25, 100, 0.5);

const newPoint = DOMPointReadOnly.fromPoint(origPoint);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}