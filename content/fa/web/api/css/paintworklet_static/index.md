---
title: "CSS: paintWorklet static property"
short-title: paintWorklet
slug: Web/API/CSS/paintWorklet_static
page-type: web-api-static-property
status:
  - experimental
browser-compat: api.CSS.paintWorklet_static
---

{{APIRef("CSSOM")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی ایستا و فقط‌خواندنی **`paintWorklet`** در رابط {{DOMxRef("CSS")}}، دسترسی به paint [worklet](/en-US/docs/Web/API/Worklet) را فراهم می‌کند که به‌صورت برنامه‌نویسی‌شده، تصویری را در جایی تولید می‌کند که یک ویژگی CSS انتظار یک فایل را دارد.

## مقدار

شیء مرتبط با {{DOMxRef('Worklet')}}.

## مثال‌ها

مثال زیر، بارگذاری یک paint [worklet](/en-US/docs/Web/API/Worklet) از فایل js آن را نشان می‌دهد و این کار را با تشخیص ویژگی (feature detection) انجام می‌دهد.

```js
if ("paintWorklet" in CSS) {
  CSS.paintWorklet.addModule("checkerboard.js");
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [CSS Painting API](/en-US/docs/Web/API/CSS_Painting_API)
- [Houdini APIs](/en-US/docs/Web/API/Houdini_APIs)