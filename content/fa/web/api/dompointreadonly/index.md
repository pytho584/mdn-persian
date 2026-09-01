---
title: "DOMPointReadOnly"
source: "https://developer.mozilla.org/en-US/docs/Web/API/DOMPointReadOnly"
---

---
title: DOMPointReadOnly
slug: Web/API/DOMPointReadOnly
page-type: web-api-interface
browser-compat: api.DOMPointReadOnly
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

رابطهٔ **`DOMPointReadOnly`** فیلدهای مختصات و پرسپکتیو را مشخص می‌کند که توسط {{domxref("DOMPoint")}} برای تعریف یک نقطهٔ دو‌بعدی یا سه‌بعدی در یک دستگاه مختصات استفاده می‌شوند.

دو راه برای ایجاد یک نمونهٔ جدید `DOMPointReadOnly` وجود دارد. نخست، می‌توانید از سازندهٔ آن استفاده کنید و مقادیر پارامترها را برای هر بعد و به‌صورت اختیاری، مقدار پرسپکتیو را وارد کنید:

```js
/* دو‌بعدی */
const point2D = new DOMPointReadOnly(50, 50);

/* سه‌بعدی */
const point3D = new DOMPointReadOnly(50, 50, 25);

/* سه‌بعدی با پرسپکتیو */
const point3DPerspective = new DOMPointReadOnly(100, 100, 100, 1.0);
```

گزینهٔ دیگر استفاده از روش ایستای {{domxref("DOMPointReadOnly.fromPoint_static", "DOMPointReadOnly.fromPoint()")}} است:

```js
const point = DOMPointReadOnly.fromPoint({ x: 100, y: 100, z: 50, w: 1.0 });
```

## سازنده (Constructor)

- {{domxref("DOMPointReadOnly.DOMPointReadOnly","DOMPointReadOnly()")}}
  - : یک شیء `DOMPointReadOnly` جدید با توجه به مقادیر مختصات و پرسپکتیو آن ایجاد می‌کند. برای ایجاد یک نقطه با استفاده از یک شیء، می‌توانید به‌جای آن از {{domxref("DOMPointReadOnly.fromPoint_static", "DOMPointReadOnly.fromPoint()")}} استفاده کنید.

## ویژگی‌های نمونه (Instance properties)

- {{domxref("DOMPointReadOnly.x")}} {{ReadOnlyInline}}
  - : مختصات افقی نقطه، یعنی `x`.
- {{domxref("DOMPointReadOnly.y")}} {{ReadOnlyInline}}
  - : مختصات عمودی نقطه، یعنی `y`.
- {{domxref("DOMPointReadOnly.z")}} {{ReadOnlyInline}}
  - : مختصات عمق نقطه، یعنی `z`.
- {{domxref("DOMPointReadOnly.w")}} {{ReadOnlyInline}}
  - : مقدار پرسپکتیو نقطه، یعنی `w`.

## روش‌های ایستا (Static methods)

- {{domxref("DOMPointReadOnly.fromPoint_static", "DOMPointReadOnly.fromPoint()")}}
  - : یک روش ایستا که یک شیء `DOMPointReadOnly` جدید با توجه به مختصات ارائه‌شده در شیء مشخص‌شده ایجاد می‌کند.

## روش‌های نمونه (Instance methods)

- {{domxref("DOMPointReadOnly.matrixTransform", "matrixTransform()")}}
  - : یک تبدیل ماتریسی که به‌صورت یک شیء مشخص شده است را روی شیء `DOMPointReadOnly` اعمال می‌کند.
- {{domxref("DOMPointReadOnly.toJSON()", "toJSON()")}}
  - : یک نمایش JSON از شیء `DOMPointReadOnly` برمی‌گرداند.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- {{domxref("DOMPoint")}}
- {{domxref("DOMRect")}}
- {{domxref("DOMMatrix")}}