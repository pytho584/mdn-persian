---
title: "NavigationCurrentEntryChangeEvent: navigationType property"
short-title: navigationType
slug: Web/API/NavigationCurrentEntryChangeEvent/navigationType
page-type: web-api-instance-property
browser-compat: api.NavigationCurrentEntryChangeEvent.navigationType
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`navigationType`** از رابط {{domxref("NavigationCurrentEntryChangeEvent")}} نوع پیمایشی را برمی‌گرداند که منجر به این تغییر شده است. اگر این تغییر در نتیجه‌ی {{domxref("Navigation.updateCurrentEntry()")}} رخ داده باشد، مقدار این ویژگی ممکن است `null` باشد.

## مقدار

یک مقدار شمارشی (enumerated) که نوع پیمایش را نشان می‌دهد.

مقادیر ممکن عبارت‌اند از:

- `push`: به مکان جدیدی پیمایش می‌شود که در نتیجه یک مدخل جدید به فهرست تاریخچه اضافه می‌شود.
- `reload`: {{domxref("Navigation.currentEntry")}} دوباره بارگذاری می‌شود.
- `replace`: {{domxref("Navigation.currentEntry")}} با یک مدخل تاریخچه جدید جایگزین می‌شود. این مدخل جدید همان {{domxref("NavigationHistoryEntry.key", "key")}} را دوباره به کار می‌برد، اما یک {{domxref("NavigationHistoryEntry.id", "id")}} متفاوت به آن اختصاص می‌یابد.
- `traverse`: مرورگر از یک مدخل تاریخچه موجود به مدخل تاریخچه موجود دیگری پیمایش می‌کند.

## نمونه‌ها

```js
navigation.addEventListener("currententrychange", (event) => {
  console.log(event.navigationType);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)