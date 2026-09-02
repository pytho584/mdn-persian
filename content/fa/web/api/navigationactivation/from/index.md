---
title: "NavigationActivation: from property"
short-title: from
slug: Web/API/NavigationActivation/from
page-type: web-api-instance-property
browser-compat: api.NavigationActivation.from
---

{{APIRef("Navigation API")}}

ویژگی فقط‌خواندنی **`from`** از رابط {{domxref("NavigationActivation")}} شامل یک شیء {{domxref("NavigationHistoryEntry")}} است که ورودی تاریخچه را برای سندِ در حال خروج («from») در ناوبری نمایش می‌دهد.

## مقدار

یک شیء {{domxref("NavigationHistoryEntry")}}، یا `null` اگر سند خروجی:

- هم‌مبدأ با سند ورودی نباشد.
- سند اولیهٔ `about:blank` باشد.

## مثال‌ها

به صفحهٔ اصلی {{domxref("NavigationActivation")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Navigation API](/en-US/docs/Web/API/Navigation_API)
- [View Transition API](/en-US/docs/Web/API/View_Transition_API)