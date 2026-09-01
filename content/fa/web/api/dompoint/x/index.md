---
title: "DOMPoint: x property"
---

---
title: "DOMPoint: x property"
short-title: x
slug: Web/API/DOMPoint/x
page-type: web-api-instance-property
browser-compat: api.DOMPoint.x
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی **`x`** در رابط **`DOMPoint`** مختصات افقی (x) یک نقطه در فضا را نگهداری می‌کند.

به‌طور کلی، مقادیر مثبت `x` به معنای حرکت به راست و مقادیر منفی `x` به معنای حرکت به چپ هستند، مگر اینکه تبدیل‌هایی (transforms) اعمال شده باشند که جهت محورها را تغییر داده باشند.

## مقدار

یک عدد اعشاری با دقت دوگانه (double-precision floating-point) که مقدار مختصات x را برای نقطه نشان می‌دهد. این مقدار **محدودیت ندارد**، به این معنی که می‌تواند بی‌نهایت یا نامعتبر باشد (یعنی مقدار آن ممکن است {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سایر ویژگی‌های مختصات: {{domxref("DOMPoint.y", "y")}}،
  {{domxref("DOMPoint.z", "z")}} و مقدار پرسپکتیو، {{domxref("DOMPoint.w", "w")}}.