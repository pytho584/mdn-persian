---
title: "DOMQuad: p2 property"
short-title: p2
slug: Web/API/DOMQuad/p2
page-type: web-api-instance-property
browser-compat: api.DOMQuad.p2
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی **`p2`** در رابط **`DOMQuad`**، شیء {{domxref("DOMPoint")}} را نگهداری می‌کند که نمایانگر یکی از چهار گوشهٔ `DOMQuad` است. هنگام ایجاد با استفاده از {{domxref("DOMQuad.fromRect_static", "DOMQuad.fromRect()")}}، این نقطه برابر با (x + width, y) است.

## مقدار

شیء {{domxref("DOMPoint")}} شامل مقادیر ممیز شناور با دقت دوبرابر زیر است:

- {{domxref("DOMPoint.x")}}: مختصات افقی.
- {{domxref("DOMPoint.y")}}: مختصات عمودی.
- {{domxref("DOMPoint.z")}}: مختصات عمق.
- {{domxref("DOMPoint.w")}}: مقدار پرسپکتیو. مقدار پیش‌فرض ۱٫۰ است.

هر یک از این مقادیر **بدون محدودیت** است؛ یعنی می‌تواند بی‌نهایت یا نامعتبر باشد (به عبارت دیگر، مقدار آن ممکن است {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سایر ویژگی‌های `DOMPoint`: {{domxref("DOMQuad.p1", "p1")}}، {{domxref("DOMQuad.p3", "p3")}} و {{domxref("DOMQuad.p4", "p4")}}.