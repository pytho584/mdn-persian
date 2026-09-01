---
title: "Document: prerendering property"
short-title: prerendering
slug: Web/API/Document/prerendering
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Document.prerendering
---

{{ APIRef("Speculation Rules API") }}{{seecompattable}}

ویژگی فقط خواندنی **`prerendering`** از رابط {{domxref("Document")}} مقدار `true` را برمی‌گرداند اگر سند در حال حاضر در فرآیند پیش‌رندرینگ (prerendering) باشد، همانطور که از طریق [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API) آغاز شده است.

## مقدار

یک مقدار بولی. اگر سند در حال حاضر در فرآیند پیش‌رندرینگ باشد، `true` و در غیر این صورت `false` برمی‌گرداند. `false` برای اسنادی که پیش‌رندرینگ را به پایان رسانده‌اند و اسنادی که پیش‌رندر نشده‌اند، برگردانده می‌شود.

## مثال‌ها

برای اجرای یک فعالیت در حالی که صفحه در حال پیش‌رندرینگ است، می‌توانید ویژگی `prerendering` را بررسی کنید. برای مثال می‌توانید برخی تحلیل‌ها را اجرا کنید:

```js
if (document.prerendering) {
  analytics.sendInfo("got this far during prerendering!");
}
```

هنگامی که یک سند پیش‌رندر شده فعال می‌شود، {{domxref("PerformanceNavigationTiming.activationStart")}} به یک مقدار {{domxref("DOMHighResTimeStamp")}} تنظیم می‌شود که نشان‌دهنده زمان بین شروع پیش‌رندرینگ و فعال شدن واقعی سند است. تابع زیر می‌تواند صفحات در حال پیش‌رندرینگ _و_ پیش‌رندر شده را بررسی کند:

```js
function pagePrerendered() {
  return (
    document.prerendering ||
    performance.getEntriesByType("navigation")[0]?.activationStart > 0
  );
}
```

هنگامی که صفحه پیش‌رندر شده توسط کاربر (با مشاهده صفحه) فعال می‌شود، رویداد {{domxref("Document.prerenderingchange_event", "prerenderingchange")}} فعال می‌شود. این می‌تواند برای فعال‌سازی فعالیت‌هایی استفاده شود که قبلاً به صورت پیش‌فرض در بارگذاری صفحه شروع می‌شدند، اما شما می‌خواهید تا زمانی که کاربر واقعاً صفحه را مشاهده می‌کند، به تأخیر بیفتند. کد زیر یک شنونده رویداد تنظیم می‌کند تا یک تابع را پس از اتمام پیش‌رندرینگ روی یک صفحه پیش‌رندر شده اجرا کند، یا آن را بلافاصله روی یک صفحه غیر پیش‌رندر شده اجرا کند:

```js
if (document.prerendering) {
  document.addEventListener("prerenderingchange", initAnalytics, {
    once: true,
  });
} else {
  initAnalytics();
}
```

> [!NOTE]
> برای اطلاعات بیشتر در مورد انواع فعالیت‌هایی که ممکن است بخواهید به تأخیر بیندازید، به صفحه اصلی [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API) و به ویژه بخش [شرایط بارگذاری گمانه‌زنی ناایمن](/en-US/docs/Web/API/Speculation_Rules_API#unsafe_speculative_loading_conditions) مراجعه کنید.

برای اندازه‌گیری تعداد دفعاتی که یک پیش‌رندر فعال می‌شود، هر سه API را ترکیب کنید: `document.prerendering` برای تشخیص مواردی که صفحه در حال پیش‌رندرینگ است، `prerenderingchange` برای نظارت بر فعال‌سازی‌ها در آن مورد، و `activationStart` برای بررسی مواردی که صفحه در گذشته پیش‌رندر شده است.

```js
if (document.prerendering) {
  document.addEventListener(
    "prerenderingchange",
    () => {
      console.log("Prerender activated after this script ran");
    },
    { once: true },
  );
} else if (performance.getEntriesByType("navigation")[0]?.activationStart > 0) {
  console.log("Prerender activated before this script ran");
} else {
  console.log("This page load was not via prerendering");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API)
- رویداد {{domxref("Document.prerenderingchange_event", "prerenderingchange")}}
- ویژگی {{domxref("PerformanceNavigationTiming.activationStart")}}