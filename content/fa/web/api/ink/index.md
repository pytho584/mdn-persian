---
title: Ink
slug: Web/API/Ink
page-type: web-api-interface
status:
  - experimental
browser-compat: api.Ink
---

{{APIRef("Ink API")}}{{SeeCompatTable}}

اینترفیس **`Ink`** در [Ink API](/en-US/docs/Web/API/Ink_API) دسترسی به اشیاء {{domxref("DelegatedInkTrailPresenter")}} را فراهم می‌کند تا برنامه بتواند از آن‌ها برای ترسیم ضربه‌های جوهر استفاده کند.

{{InheritanceDiagram}}

## متدهای نمونه

- {{domxref("Ink.requestPresenter", "requestPresenter()")}} {{Experimental_Inline}}
  - یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("DelegatedInkTrailPresenter")}} برای مدیریت ترسیم ضربه‌ها تحقق می‌یابد.

## مثال

```js
async function inkInit() {
  const ink = navigator.ink;
  let presenter = await ink.requestPresenter({ presentationArea: canvas });

  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}