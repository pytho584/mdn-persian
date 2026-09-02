---
title: "NavigationActivation: navigationType property"
short-title: navigationType
slug: Web/API/NavigationActivation/navigationType
page-type: web-api-instance-property
browser-compat: api.NavigationActivation.navigationType
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`navigationType`** از رابط {{domxref("NavigationActivation")}} رشته‌ای را نشان می‌دهد که نوع ناوبری را مشخص می‌کند.

## مقدار

رشته‌ای که نوع ناوبری مربوط به {{domxref("NavigationActivation")}} را نشان می‌دهد. مقادیر ممکن عبارت‌اند از:

- `push`: به مکان جدیدی ناوبری شده است که باعث می‌شود یک ورودی جدید به فهرست تاریخچه اضافه شود.
- `reload`: {{domxref("NavigationActivation.entry")}} بارگذاری مجدد شده است.
- `replace`: {{domxref("NavigationActivation.entry")}} با یک ورودی تاریخچه جدید جایگزین شده است. این ورودی جدید همان {{domxref("NavigationHistoryEntry.key", "key")}} را دوباره استفاده می‌کند، اما یک {{domxref("NavigationHistoryEntry.id", "id")}} متفاوت به آن اختصاص داده می‌شود.
- `traverse`: مرورگر از یک ورودی تاریخچه موجود به ورودی تاریخچه موجود دیگری ناوبری کرده است.

## مثال‌ها

```js
window.addEventListener("pageswap", (event) => {
  // For example, the page was hidden, or the navigation is cross-document.
  if (!event.viewTransition) return;

  // Skip the view transition for back/forward navigations.
  if (event.activation.navigationType === "traverse") {
    event.viewTransition.skipTransition();
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Navigation API](/en-US/docs/Web/API/Navigation_API)
- [View Transition API](/en-US/docs/Web/API/View_Transition_API)