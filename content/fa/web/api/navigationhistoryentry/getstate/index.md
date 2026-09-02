---
title: "NavigationHistoryEntry: getState() method"
short-title: getState()
slug: Web/API/NavigationHistoryEntry/getState
page-type: web-api-instance-method
browser-compat: api.NavigationHistoryEntry.getState
---

{{APIRef("Navigation API")}}

متد **`getState()`** در رابط {{domxref("NavigationHistoryEntry")}} یک نسخهٔ کلون‌شده از state (وضعیت) ارائه‌شده توسط توسعه‌دهنده را که به این ورودی تاریخچه مرتبط است، برمی‌گرداند.

## Syntax

```js-nolint
getState()
```

### پارامترها

هیچ.

### مقدار بازگشتی

مقداری که نمایانگر state است. این مقدار می‌تواند هر نوع داده‌ای باشد که قابلیت [structured-cloneable](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) را داشته باشد.

اگر stateای تعریف نشده باشد یا سند فعلی کاملاً فعال (fully active) نباشد، `undefined` برگردانده می‌شود.

### استثناها

هیچ.

## نمونه‌ها

```js
async function handleReload() {
  // به‌روزرسانی state موجود از طریق reload()
  await navigation.reload({
    state: { ...navigation.currentEntry.getState(), newState: 3 },
  });

  // چاپ state فعلی در کنسول
  const current = navigation.currentEntry;
  console.log(current.getState());
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)
- متدهایی که امکان به‌روزرسانی state را فراهم می‌کنند — {{domxref("Navigation.navigate()")}}، {{domxref("Navigation.reload()")}} و {{domxref("Navigation.updateCurrentEntry()")}}