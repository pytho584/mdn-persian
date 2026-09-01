---
title: "DOMQuad: p4 property"
short-title: p4
slug: Web/API/DOMQuad/p4
page-type: web-api-instance-property
browser-compat: api.DOMQuad.p4
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی **`p4`** در رابط **`DOMQuad`**، شیء {{domxref("DOMPoint")}} را نگه می‌دارد که یکی از چهار گوشهٔ `DOMQuad` را نشان می‌دهد. وقتی که با {{domxref("DOMQuad.fromRect_static", "DOMQuad.fromRect()")}} ساخته شود، این نقطه برابر با (x, y + height) است.

## مقدار

شیء {{domxref("DOMPoint")}} شامل مقادیر اعشاری با دقت دوگانهٔ زیر است:

- {{domxref("DOMPoint.x")}}: مختصات افقی.
- {{domxref("DOMPoint.y")}}: مختصات عمودی.
- {{domxref("DOMPoint.z")}}: مختصات عمق.
- {{domxref("DOMPoint.w")}}: مقدار پرسپکتیو. مقدار پیش‌فرض 1.0 است.

هر یک از این مقادیر **نامحدود** هستند، به این معنی که می‌توانند بی‌نهایت یا نامعتبر باشند (یعنی مقدار آن‌ها ممکن است {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سایر ویژگی‌های `DOMPoint`: {{domxref("DOMQuad.p1", "p1")}}،
  {{domxref("DOMQuad.p2", "p2")}} و {{domxref("DOMQuad.p3", "p3")}}.