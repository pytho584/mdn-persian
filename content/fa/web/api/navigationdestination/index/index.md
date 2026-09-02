---
title: "NavigationDestination: index property"
short-title: index
slug: Web/API/NavigationDestination/index
page-type: web-api-instance-property
browser-compat: api.NavigationDestination.index
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`index`** از رابط {{domxref("NavigationDestination")}} مقدار {{domxref("NavigationHistoryEntry.index", "index")}} مربوط به {{domxref("NavigationHistoryEntry")}} مقصد را برمی‌گرداند اگر {{domxref("NavigateEvent.navigationType")}} برابر با `traverse` باشد، در غیر این صورت `1-` را برمی‌گرداند.

## مقدار

عددی که نشان‌دهنده `index` مربوط به {{domxref("NavigationHistoryEntry")}} مقصد است، یا `1-`.

## مثال‌ها

```js
navigation.addEventListener("navigate", (event) => {
  console.log(event.destination.index);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)