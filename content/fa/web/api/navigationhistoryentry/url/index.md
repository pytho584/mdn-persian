---
title: "NavigationHistoryEntry: url property"
short-title: url
slug: Web/API/NavigationHistoryEntry/url
page-type: web-api-instance-property
browser-compat: api.NavigationHistoryEntry.url
---

{{APIRef("Navigation API")}}

ویژگی فقطخواندنی **`url`** از رابط {{domxref("NavigationHistoryEntry")}}، نشانی مطلق (absolute URL) این مدخلِ تاریخچه را برمی‌گرداند. اگر این مدخل با سندی غیر از سندِ جاری متناظر باشد (یعنی ویژگی `sameDocument` آن `false` باشد) و آن سند با هدرِ {{httpheader("Referrer-Policy")}} دارای مقدار `no-referrer` یا `origin` واکشی شده باشد، این ویژگی مقدار `null` را برمی‌گرداند. اگر سندِ جاری کاملاً فعال (fully active) نباشد، این ویژگی یک رشتهٔ خالی برمی‌گرداند.

## مقدار

یک رشته که نمایانگر URL است یا `null`.

## مثال‌ها

```js
const current = navigation.currentEntry;
console.log(current.url);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)