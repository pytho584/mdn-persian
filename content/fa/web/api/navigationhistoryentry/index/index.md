```yaml
---
title: "NavigationHistoryEntry: index property"
short-title: index
slug: Web/API/NavigationHistoryEntry/index
page-type: web-api-instance-property
browser-compat: api.NavigationHistoryEntry.index
---

{{APIRef("Navigation API")}}

ویژگی فقط-خواندنی **`index`** از رابط {{domxref("NavigationHistoryEntry")}}، اندیس (شاخص) ورودی تاریخچه را در لیست ورودی‌های تاریخچه (یعنی لیستی که توسط {{domxref("Navigation.entries()")}} بازگردانده می‌شود) برمی‌گرداند، یا اگر ورودی در لیست وجود نداشته باشد یا سند جاری به طور کامل فعال نباشد، مقدار `-1` را برمی‌گرداند.

## مقدار

عددی که نشان‌دهنده `index` ورودی در لیست ورودی‌های تاریخچه است، یا `-1` اگر این آیتم در لیست وجود نداشته باشد.

## مثال‌ها

```js
const current = navigation.currentEntry;
console.log(current.index);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: API Navigation](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح API Navigation](https://github.com/WICG/navigation-api/blob/main/README.md)
```