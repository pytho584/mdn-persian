---
title: "CSSFunctionDeclarations: style property"
short-title: style
slug: Web/API/CSSFunctionDeclarations/style
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.CSSFunctionDeclarations.style
---

{{ APIRef("CSSOM") }}{{SeeCompatTable}}

ویژگی فقط‑خواندنی **`style`** از رابط {{domxref("CSSFunctionDeclarations")}} شامل یک شیء {{domxref("CSSFunctionDescriptors")}} است که توصیف‌گرهای موجود در بدنهٔ قانون {{cssxref("@function")}} را نشان می‌دهد.

## مقدار

یک شیء {{domxref("CSSFunctionDescriptors")}}.

اگرچه ویژگی `style` خود به این معنا فقط‑خواندنی است که نمی‌توانید شیء `CSSFunctionDescriptors` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `style` مقداردهی کنید که معادل با مقداردهی به ویژگی {{domxref("CSSStyleDeclaration/cssText", "cssText")}} آن است. همچنین می‌توانید شیء `CSSFunctionDescriptors` را با استفاده از روش‌های {{domxref("CSSStyleDeclaration/setProperty", "setProperty()")}} و {{domxref("CSSStyleDeclaration/removeProperty", "removeProperty()")}} تغییر دهید.

## مثال‌ها

برای مثال‌ها به صفحهٔ مرجع اصلی {{domxref("CSSFunctionDeclarations")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{cssxref("@function")}}