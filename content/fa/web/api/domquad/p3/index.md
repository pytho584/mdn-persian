---
title: "DOMQuad: p3 property"
short-title: p3
slug: Web/API/DOMQuad/p3
page-type: web-api-instance-property
browser-compat: api.DOMQuad.p3
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی **`p3`** در رابط **`DOMQuad`** شامل شیء {{domxref("DOMPoint")}} است که یکی از چهار گوشه‌ی `DOMQuad` را نشان می‌دهد. هنگامی که از طریق {{domxref("DOMQuad.fromRect_static", "DOMQuad.fromRect()")}} ایجاد می‌شود، این نقطه (x + width, y + height) است.

## مقدار

شیء {{domxref("DOMPoint")}} شامل مقادیر ممیز شناور با دقت مضاعف زیر است:

- {{domxref("DOMPoint.x")}}: مختصات افقی.
- {{domxref("DOMPoint.y")}}: مختصات عمودی.
- {{domxref("DOMPoint.z")}}: مختصات عمق.
- {{domxref("DOMPoint.w")}}: مقدار پرسپکتیو. مقدار پیش‌فرض 1.0 است.

هر یک از این مقادیر **نامحدود** هستند، به این معنی که می‌توانند بی‌نهایت یا نامعتبر باشند (یعنی مقدار آن‌ها ممکن است {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- سایر ویژگی‌های `DOMPoint`: {{domxref("DOMQuad.p1", "p1")}}، {{domxref("DOMQuad.p2", "p2")}} و {{domxref("DOMQuad.p4", "p4")}}.