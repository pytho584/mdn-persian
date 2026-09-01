---
title: "Document: prerenderingchange event"
short-title: prerenderingchange
slug: Web/API/Document/prerenderingchange_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.Document.prerenderingchange_event
---

{{ APIRef("Speculation Rules API") }}{{seecompattable}}

رویداد **`prerenderingchange`** بر روی یک سند از پیش رندر شده (prerendered) هنگامی که فعال می‌شود (یعنی کاربر صفحه را مشاهده می‌کند) رخ می‌دهد.

## نحو (Syntax)

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler) تنظیم نمایید.

```js-nolint
addEventListener("prerenderingchange", (event) => { })

onprerenderingchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### جلوگیری از اجرای کد در حین از پیش رندر کردن

این مثال نشان می‌دهد که چگونه می‌توان کدی را که در غیر این صورت در حین از پیش رندر کردن اجرا می‌شود، تا پس از فعال‌سازی صفحه به تعویق انداخت. این کار برای به تعویق انداختن کدهای تحلیلی (analytics) که فقط زمانی که صفحه واقعاً مشاهده می‌شود مرتبط هستند، مفید است.

کد بررسی می‌کند که آیا از پیش رندر کردن با استفاده از {{domxref("Document.prerendering")}} در حال اجرا است یا خیر، و اگر چنین باشد، یک شنونده رویداد اضافه می‌کند تا پس از فعال‌سازی صفحه، تابع مقداردهی اولیه تحلیلی را اجرا کند. در صفحه‌ای که از پیش رندر نمی‌شود، کد تحلیلی بلافاصله اجرا می‌شود.

```js
if (document.prerendering) {
  document.addEventListener("prerenderingchange", initAnalytics, {
    once: true,
  });
} else {
  initAnalytics();
}
```

توجه داشته باشید که نباید از این نوع کد برای اندازه‌گیری تعداد دفعات فعال‌سازی یک پیش‌رندر استفاده کرد، زیرا ممکن است کد پس از فعال‌شدن یک صفحه از پیش رندر شده اجرا شود.

> [!NOTE]
> صفحه اصلی [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API) و به ویژه بخش [شرایط بارگذاری حدسی ناامن](/en-US/docs/Web/API/Speculation_Rules_API#unsafe_speculative_loading_conditions) را برای اطلاعات بیشتر در مورد انواع فعالیت‌هایی که ممکن است بخواهید تا پایان از پیش رندر کردن به تعویق بیندازید، ببینید.

### اندازه‌گیری فعال‌سازی‌های از پیش رندر کردن

این کد نشان می‌دهد که چگونه می‌توان تعداد دفعات فعال‌سازی یک پیش‌رندر را اندازه‌گیری کرد. از رویداد `prerenderingchange` برای ردیابی رویدادهای فعال‌سازی و از {{domxref("Performance.getEntriesByType()")}} برای ردیابی فعال‌سازی‌های ناوبری استفاده می‌کند.

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Speculation Rules API](/en-US/docs/Web/API/Speculation_Rules_API)
- ویژگی {{domxref("Document.prerendering", "prerendering")}}
- ویژگی {{domxref("PerformanceNavigationTiming.activationStart")}}