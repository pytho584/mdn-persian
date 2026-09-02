---
title: "NavigationActivation: entry property"
short-title: entry
slug: Web/API/NavigationActivation/entry
page-type: web-api-instance-property
browser-compat: api.NavigationActivation.entry
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`entry`** در رابط {{domxref("NavigationActivation")}} شامل یک شیء {{domxref("NavigationHistoryEntry")}} است که ورودیِ تاریخچهٔ سندِ ورودی («مقصد») را در آن پیمایش نشان می‌دهد. این ویژگی معادل خاصیت {{domxref("Navigation.currentEntry")}} در لحظه‌ای است که سند ورودی فعال شده است.

در برخی موارد، شیء `from` یا `entry` از نوع {{domxref("NavigationHistoryEntry")}} ممکن است هدف مناسبی برای متد `traverseTo()` نباشد؛ زیرا ممکن است در تاریخچه نگهداری نشده باشد. برای مثال، سند می‌تواند با استفاده از `location.replace()` فعال شود، یا ورودی اولیهٔ آن با `history.replaceState()` جایگزین شود. با این حال، خاصیت `url` و متد `getState()` مربوط به آن ورودی‌ها همچنان قابل دسترسی هستند.

## مقدار

یک شیء {{domxref("NavigationHistoryEntry")}}.

## مثال‌ها

به صفحهٔ اصلی {{domxref("NavigationActivation")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Navigation API](/en-US/docs/Web/API/Navigation_API)
- [View Transition API](/en-US/docs/Web/API/View_Transition_API)