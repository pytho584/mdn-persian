---
title: "DOMQuad: p1 property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/DOMQuad/p1"
---

---
title: "DOMQuad: p1 property"
short-title: p1
slug: Web/API/DOMQuad/p1
page-type: web-api-instance-property
browser-compat: api.DOMQuad.p1
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

ویژگی **`p1`** در رابط **`DOMQuad`**، شیء {{domxref("DOMPoint")}} را نگه می‌دارد که یکی از چهار گوشهٔ `DOMQuad` را نشان می‌دهد. وقتی با استفاده از {{domxref("DOMQuad.fromRect_static", "DOMQuad.fromRect()")}} ساخته شود، این نقطه برابر با (x, y) است.

## مقدار

شیء {{domxref("DOMPoint")}} شامل مقادیر اعشاری با دقت دوگانهٔ زیر است:

- {{domxref("DOMPoint.x")}}: مختصات افقی.
- {{domxref("DOMPoint.y")}}: مختصات عمودی.
- {{domxref("DOMPoint.z")}}: مختصات عمق.
- {{domxref("DOMPoint.w")}}: مقدار پرسپکتیو. مقدار پیش‌فرض 1.0 است.

هر یک از این مقادیر **نامحدود** هستند، یعنی می‌توانند بی‌نهایت یا نامعتبر باشند (به عبارت دیگر، مقدارشان می‌تواند {{jsxref("NaN")}} یا {{jsxref("Infinity", "±Infinity")}} باشد).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- سایر ویژگی‌های `DOMPoint`: {{domxref("DOMQuad.p2", "p2")}}،
  {{domxref("DOMQuad.p3", "p3")}} و {{domxref("DOMQuad.p4", "p4")}}.