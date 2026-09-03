---
title: "Navigator: ink property"
short-title: ink
slug: Web/API/Navigator/ink
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Navigator.ink
---

{{SeeCompatTable}}{{APIRef("Ink API")}}

خاصیت فقط‌خواندنی **`ink`** در رابط {{domxref("Navigator")}}، یک شیء {{domxref("Ink")}} برای سند جاری برمی‌گرداند که دسترسی به قابلیت‌های [Ink API](/en-US/docs/Web/API/Ink_API) را فراهم می‌کند.

## مقدار

یک شیء {{domxref('Ink')}}.

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

## سازگاری با مرورگرها

{{Compat}}