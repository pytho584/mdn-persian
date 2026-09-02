---
title: "NavigationDestination: id property"
short-title: id
slug: Web/API/NavigationDestination/id
page-type: web-api-instance-property
browser-compat: api.NavigationDestination.id
---

{{APIRef("Navigation API")}}

خاصیت فقط خواندنی **`id`** در رابط {{domxref("NavigationDestination")}}، مقدار {{domxref("NavigationHistoryEntry.id", "id")}} ورودی تاریخچه مقصد {{domxref("NavigationHistoryEntry")}} را در صورتی که {{domxref("NavigateEvent.navigationType")}} برابر با `traverse` باشد، برمی‌گرداند، در غیر این صورت یک رشته خالی.

`id` یک مقدار یکتا است که توسط عامل کاربر (UA) تولید می‌شود و همواره نمایانگر ورودی تاریخچه است. این مقدار برای مرتبط کردن یک ورودی تاریخچه با یک منبع خارجی مانند حافظه نهان ذخیره‌سازی مفید است.

## مقدار

یک رشته که نشان‌دهنده `id` ورودی تاریخچه مقصد {{domxref("NavigationHistoryEntry")}} است، یا یک رشته خالی.

## مثال‌ها

```js
navigation.addEventListener("navigate", (event) => {
  console.log(event.destination.id);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)