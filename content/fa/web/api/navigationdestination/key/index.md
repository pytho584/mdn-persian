---
title: "NavigationDestination: key property"
---

---
title: "NavigationDestination: key property"
short-title: key
slug: Web/API/NavigationDestination/key
page-type: web-api-instance-property
browser-compat: api.NavigationDestination.key
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`key`** از رابط {{domxref("NavigationDestination")}}، در صورتی که {{domxref("NavigateEvent.navigationType")}} برابر با `traverse` باشد، مقدار {{domxref("NavigationHistoryEntry.key", "key")}} مربوط به {{domxref("NavigationHistoryEntry")}} مقصد را برمی‌گرداند؛ در غیر این صورت یک رشتهٔ خالی برمی‌گرداند.

مقدار `key` یک مقدار یکتاست که توسط عامل کاربر (user agent) تولید می‌شود و جایگاهِ آن ورودیِ تاریخچه را در فهرست ورودی‌های تاریخچه نشان می‌دهد؛ این مقدار برای پیمایش به همان نقطهٔ تاریخچه از طریق {{domxref("Navigation.traverseTo()")}} استفاده می‌شود. اگر ورودی دیگری جایگزین این ورودی در فهرست شود (یعنی اگر {{domxref("NavigateEvent.navigationType")}} برابر با `replace` باشد)، این مقدار دوباره استفاده خواهد شد.

## مقدار

رشته‌ای که مقدار `key` مقصد {{domxref("NavigationHistoryEntry")}} را نشان می‌دهد، یا یک رشتهٔ خالی.

## مثال‌ها

```js
navigation.addEventListener("navigate", (event) => {
  console.log(event.destination.key);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)