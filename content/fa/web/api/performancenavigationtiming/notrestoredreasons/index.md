---
title: "PerformanceNavigationTiming: notRestoredReasons property"
short-title: notRestoredReasons
slug: Web/API/PerformanceNavigationTiming/notRestoredReasons
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceNavigationTiming.notRestoredReasons
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

ویژگی فقط خواندنی **`notRestoredReasons`** از رابط {{domxref("PerformanceNavigationTiming")}} یک شیء {{domxref("NotRestoredReasons")}} را برمی‌گرداند که داده‌های گزارش‌دهی درباره دلایل مسدود شدن سند فعلی از استفاده از حافظه نهان عقب/جلو ({{Glossary("bfcache")}}) در هنگام ناوبری را فراهم می‌کند.

## مقدار

زمانی که شیء `PerformanceNavigationTiming` مرتبط، یک ناوبری تاریخچه‌ای را نشان می‌دهد، `notRestoredReasons` یک شیء {{domxref("NotRestoredReasons")}} برمی‌گرداند.

زمانی که شیء `PerformanceNavigationTiming` یک ناوبری تاریخچه‌ای را نشان نمی‌دهد، `notRestoredReasons` مقدار `null` را برمی‌گرداند. این برای تعیین اینکه آیا bfcache برای یک ناوبری خاص مرتبط است یا خیر مفید است (در مقابل حالتی که `notRestoredReasons` پشتیبانی نمی‌شود، که در آن صورت `undefined` برمی‌گرداند).

> [!NOTE]
> ممکن است `notRestoredReasons` با وجود اینکه نوع ناوبری به عنوان ناوبری عقب/جلو گزارش شده است، `null` برگرداند. این شرایط شامل تکرار یک ناوبری عقب/جلو در یک برگه جدید و بازیابی یک برگه ناوبری عقب/جلو پس از راه‌اندازی مجدد مرورگر است. در چنین مواردی، برخی مرورگرها نوع ناوبری را از برگه اصلی کپی می‌کنند، اما از آنجایی که این‌ها در واقع ناوبری عقب/جلو نیستند، `notRestoredReasons` مقدار `null` را برمی‌گرداند.

## مثال‌ها

داده‌های [`PerformanceNavigationTiming`](/en-US/docs/Web/API/PerformanceNavigationTiming) را می‌توان از خط زمانی عملکرد با استفاده از [`Performance.getEntriesByType()`](/en-US/docs/Web/API/Performance/getEntriesByType) یا [`PerformanceObserver`](/en-US/docs/Web/API/PerformanceObserver) به دست آورد.

به عنوان مثال، می‌توانید تابع زیر را فراخوانی کنید تا تمام اشیاء `PerformanceNavigationTiming` که در حال حاضر در خط زمانی عملکرد وجود دارند را برگردانده و `notRestoredReasons` آن‌ها را ثبت کند:

```js
function returnNRR() {
  const navEntries = performance.getEntriesByType("navigation");
  for (let i = 0; i < navEntries.length; i++) {
    console.log(`Navigation entry ${i}`);
    let navEntry = navEntries[i];
    console.log(navEntry.notRestoredReasons);
  }
}
```

ویژگی `PerformanceNavigationTiming.notRestoredReasons` یک شیء با ساختار زیر برمی‌گرداند که دلایل مسدود شدن سند فعلی از استفاده از bfcache را ارائه می‌دهد. در این مثال، فریم سطح بالا هیچ `<iframe>` فرزندی ندارد:

```json
{
  "children": [],
  "id": null,
  "name": null,
  "reasons": [{ "reason": "unload-listener" }],
  "src": "",
  "url": "example.com"
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [نظارت بر دلایل مسدودسازی bfcache](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceResourceTiming")}}