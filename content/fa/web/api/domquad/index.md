---
title: "DOMQuad"
---

---
title: DOMQuad
slug: Web/API/DOMQuad
page-type: web-api-interface
browser-compat: api.DOMQuad
---

{{APIRef("Geometry Interfaces")}}{{AvailableInWorkers}}

یک `DOMQuad` مجموعه‌ای از چهار `DOMPoint` است که گوشه‌های یک چهارضلعی دلخواه را تعریف می‌کند. بازگرداندن `DOMQuad`ها به `getBoxQuads()` امکان می‌دهد تا حتی در صورت وجود تبدیل‌های دلخواه دو بعدی یا سه بعدی، اطلاعات دقیقی را بازگرداند. دارای یک ویژگی مفید به نام `bounds` است که یک `DOMRectReadOnly` را برای مواردی که فقط یک مستطیل محصور هم‌محور (axis-aligned) می‌خواهید، بازمی‌گرداند.

## سازنده

- {{domxref("DOMQuad.DOMQuad", "DOMQuad()")}}
  - : یک شیء `DOMQuad` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref("DOMQuad.p1")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMPoint")}} که یک گوشه از `DOMQuad` را نشان می‌دهد.
- {{domxref("DOMQuad.p2")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMPoint")}} که یک گوشه از `DOMQuad` را نشان می‌دهد.
- {{domxref("DOMQuad.p3")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMPoint")}} که یک گوشه از `DOMQuad` را نشان می‌دهد.
- {{domxref("DOMQuad.p4")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMPoint")}} که یک گوشه از `DOMQuad` را نشان می‌دهد.

## روش‌های نمونه

- {{domxref("DOMQuad.getBounds()")}}
  - : یک شیء {{domxref("DOMRect")}} با مختصات و ابعاد شیء `DOMQuad` بازمی‌گرداند.
- {{domxref("DOMQuad.toJSON()")}}
  - : یک نمایش JSON از شیء `DOMQuad` بازمی‌گرداند.

## روش‌های ایستا

- {{domxref("DOMQuad.fromQuad_static", "DOMQuad.fromQuad()")}}
  - : یک شیء `DOMQuad` جدید بر اساس مجموعه مختصات ارائه‌شده به شکل یک شیء `DOMQuad` دیگر بازمی‌گرداند.
- {{domxref("DOMQuad.fromRect_static", "DOMQuad.fromRect()")}}
  - : یک شیء `DOMQuad` جدید بر اساس مجموعه مختصات ارائه‌شده به شکل یک شیء {{domxref("DOMRect")}} بازمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}