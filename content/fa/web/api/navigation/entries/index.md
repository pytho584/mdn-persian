---
title: "Navigation: entries() method"
short-title: entries()
slug: Web/API/Navigation/entries
page-type: web-api-instance-method
browser-compat: api.Navigation.entries
---

{{APIRef("Navigation API")}}

متد **`entries()`** از رابط {{domxref("Navigation")}} آرایه‌ای از آبجکت‌های {{domxref("NavigationHistoryEntry")}} برمی‌گرداند که نمایانگر تمام ورودی‌های موجود در تاریخچه هستند.

## سینتکس

```js-nolint
entries()
```

### پارامترها

هیچ.

### مقدار بازگشتی

آرایه‌ای از آبجکت‌های {{domxref("NavigationHistoryEntry")}}.

### استثناها

هیچ.

## مثال‌ها

### برگرداندن تعداد ورودی‌های تاریخچه

```js
let numOfEntries = navigation.entries().length - 1;
```

### یک دکمه بازگشت هوشمند

یک دکمه «بازگشت» که در صفحه قرار داده شده باشد، می‌تواند با بررسی ورودی‌های قبلی تاریخچه، شما را حتی پس از بارگذاری مجدد صفحه به عقب بازگرداند:

```js
backButtonEl.addEventListener("click", () => {
  if (
    navigation.entries()[navigation.currentEntry.index - 1]?.url ===
    "/product-listing"
  ) {
    navigation.back();
  } else {
    // If the user arrived here in some other way
    // e.g. by typing the URL directly:
    navigation.navigate("/product-listing", { history: "replace" });
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)