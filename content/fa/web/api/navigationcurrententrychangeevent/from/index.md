---
title: "NavigationCurrentEntryChangeEvent: from property"
short-title: from
slug: Web/API/NavigationCurrentEntryChangeEvent/from
page-type: web-api-instance-property
browser-compat: api.NavigationCurrentEntryChangeEvent.from
---

{{APIRef("Navigation API")}}

خاصیت فقط خواندنی **`from`** از رابط {{domxref("NavigationCurrentEntryChangeEvent")}}، شیء {{domxref("NavigationHistoryEntry")}}ای را برمی‌گرداند که از آن ناوبری صورت گرفته است.

## مقدار

یک شیء {{domxref("NavigationHistoryEntry")}}.

## مثال‌ها

```js
navigation.addEventListener("currententrychange", (event) => {
  console.log(event.from);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)