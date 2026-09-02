---
title: "Navigation: navigatesuccess event"
short-title: navigatesuccess
slug: Web/API/Navigation/navigatesuccess_event
page-type: web-api-event
browser-compat: api.Navigation.navigatesuccess_event
---

{{APIRef("Navigation API")}}

رویداد **`navigatesuccess`** از رابط {{domxref("Navigation")}} زمانی که یک پیمایش موفقیت‌آمیز به پایان رسیده است، فعال می‌شود.

در مورد یک پیمایش رهگیری‌شده، این رویداد پس از تحقق هر قولی که توسط کنترل‌کننده {{domxref("NavigateEvent.intercept", "intercept()")}} شما بازگردانده شده است، رخ می‌دهد. قول {{domxref("NavigationTransition.finished")}} نیز همزمان تحقق می‌یابد.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("navigatesuccess", (event) => { })

onnavigatesuccess = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

می‌توانید با مخفی کردن یک نشانگر پیشرفت که قبلاً نمایش داده شده بود، با یک پیمایش موفقیت‌آمیز برخورد کنید، مانند این:

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

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)