---
title: "Navigation: navigateerror event"
short-title: navigateerror
slug: Web/API/Navigation/navigateerror_event
page-type: web-api-event
browser-compat: api.Navigation.navigateerror_event
---

{{APIRef("Navigation API")}}

رویداد **`navigateerror`** از رابط {{domxref("Navigation")}} زمانی که یک ناوبری (navigation) شکست می‌خورد، فعال می‌شود.

برای مثال، اگر شبکه قطع باشد، هر متد {{domxref("Window/fetch", "fetch()")}} که برای مدیریت یک ناوبری فراخوانی شود، شکست خواهد خورد و خطا به `navigateerror` هدایت می‌شود.

## Syntax

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("navigateerror", (event) => { })

onnavigateerror = (event) => { }
```

## Event type

یک {{domxref("ErrorEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("ErrorEvent")}}

## Examples

ممکن است یک ناوبری موفق را با پنهان کردن یک نشانگر پیشرفت (progress indicator) که قبلاً نمایش داده شده بود، مدیریت کنید، به این صورت:

```js
navigation.addEventListener("navigatesuccess", (event) => {
  loadingIndicator.hidden = true;
});
```

یا ممکن است در صورت شکست، یک پیام خطا نمایش دهید:

```js
navigation.addEventListener("navigateerror", (event) => {
  loadingIndicator.hidden = true; // also hide indicator
  showMessage(`Failed to load page: ${event.message}`);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)