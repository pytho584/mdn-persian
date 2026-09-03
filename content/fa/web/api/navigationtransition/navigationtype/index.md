---
title: "NavigationTransition: navigationType property"
short-title: navigationType
slug: Web/API/NavigationTransition/navigationType
page-type: web-api-instance-property
browser-compat: api.NavigationTransition.navigationType
---

{{APIRef("Navigation API")}}

ویژگی فقط خواندنی **`navigationType`** از رابط {{domxref("NavigationTransition")}} نوع پیمایش (navigation) در حال انجام را برمی‌گرداند.

## مقدار

یک مقدار شمارشی که نوع پیمایش در حال انجام را نشان می‌دهد.

مقادیر ممکن عبارتند از:

- `push`: یک مکان جدید پیمایش می‌شود و یک ورودی جدید به فهرست تاریخچه اضافه می‌کند.
- `reload`: {{domxref("Navigation.currentEntry")}} دوباره بارگذاری می‌شود.
- `replace`: {{domxref("Navigation.currentEntry")}} با یک ورودی جدید در تاریخچه جایگزین می‌شود. این ورودی جدید از همان {{domxref("NavigationHistoryEntry.key", "key")}} استفاده می‌کند، اما یک {{domxref("NavigationHistoryEntry.id", "id")}} متفاوت به آن اختصاص داده می‌شود.
- `traverse`: مرورگر از یک ورودی تاریخچه موجود به ورودی تاریخچه موجود دیگری پیمایش می‌کند.

## مثال‌ها

```js
console.log(navigation.transition.navigationType);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [مسیریابی مدرن در سمت کلاینت: API پیمایش](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API پیمایش](https://github.com/WICG/navigation-api/blob/main/README.md)