---
title: "Document: getAnimations() method"
short-title: getAnimations()
slug: Web/API/Document/getAnimations
page-type: web-api-instance-method
browser-compat: api.Document.getAnimations
---

{{APIRef("Web Animations")}}

متد `getAnimations()` در رابط {{domxref("Document")}} آرایه‌ای از تمام اشیاء {{domxref("Animation")}} را برمی‌گرداند که در حال حاضر فعال هستند و عناصر هدف آن‌ها از نوادگان سند (document) هستند. این آرایه شامل [انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations)، [ترنزیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Transitions) و [انیمیشن‌های وب](/en-US/docs/Web/API/Web_Animations_API) می‌شود.

## نحو (Syntax)

```js-nolint
getAnimations()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Array")}} از اشیاء {{domxref("Animation")}} که هر کدام نشان‌دهنده یک انیمیشن است که در حال حاضر با عناصری مرتبط است که نوادگان همان {{domxref("Document")}} هستند که متد روی آن فراخوانی شده است.

## مثال‌ها

قطعه کد زیر سرعت همه انیمیشن‌های یک صفحه را با نصف کردن {{domxref("Animation.playbackRate")}} کاهش می‌دهد.

```js
document.getAnimations().forEach((animation) => {
  animation.playbackRate *= 0.5;
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- [انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations)
- [ترنزیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Transitions)
- {{domxref("Element.getAnimations()")}} — دریافت فقط انیمیشن‌های مربوط به یک {{domxref("Element")}} و نوادگان آن.
- {{domxref("Animation")}}