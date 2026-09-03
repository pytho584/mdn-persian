---
title: PerformanceLongTaskTiming
slug: Web/API/PerformanceLongTaskTiming
page-type: web-api-interface
browser-compat: api.PerformanceLongTaskTiming
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

رابط **`PerformanceLongTaskTiming`** اطلاعاتی درباره وظایفی (tasks) ارائه می‌دهد که نخ UI (واسط کاربری) را به مدت ۵۰ میلی‌ثانیه یا بیشتر اشغال می‌کنند.

## توضیحات

وظایف طولانی که نخ اصلی را به مدت ۵۰ میلی‌ثانیه یا بیشتر مسدود می‌کنند، علاوه بر مشکلات دیگر، موارد زیر را به همراه دارند:

- تأخیر در {{glossary("Time to interactive")}} (زمان تا تعاملی شدن) (TTI).
- تأخیر ورودی بالا/متغیر.
- تأخیر بالای/متغیر در مدیریت رویدادها.
- انیمیشن‌ها و اسکرول‌های ناپایدار (janky).

یک وظیفه طولانی هر دوره بدون وقفه‌ای است که نخ اصلی UI به مدت ۵۰ میلی‌ثانیه یا بیشتر مشغول باشد. نمونه‌های رایج عبارتند از:

- مدیریت‌کننده‌های رویداد طولانی‌مدت.
- reflowهای پرهزینه و سایر رندرگیری‌های مجدد.
- کارهایی که مرورگر بین نوبت‌های مختلف حلقه رویداد انجام می‌دهد و بیش از ۵۰ میلی‌ثانیه طول می‌کشند.

وظایف طولانی به «ظرف زمینه مرورگر مقصر» (culprit browsing context container) یا به اختصار «ظرف» (container) اشاره دارد که همان صفحه سطح بالا، {{HTMLElement("iframe")}}، {{HTMLElement("embed")}} یا {{HTMLElement("object")}} است که وظیفه در آن رخ داده است.

برای وظایفی که درون صفحه سطح بالا رخ نمی‌دهند و برای تشخیص اینکه کدام ظرف مسئول وظیفه طولانی است، رابط {{domxref("TaskAttributionTiming")}} ویژگی‌های `containerId`، `containerName` و `containerSrc` را ارائه می‌دهد که ممکن است اطلاعات بیشتری درباره منبع وظیفه فراهم کند.

`PerformanceLongTaskTiming` از {{domxref("PerformanceEntry")}} به ارث می‌برد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط ویژگی‌های زیر را از {{domxref("PerformanceEntry")}} برای انواع ورودی زمان‌بندی وظیفه طولانی با شرایط زیر گسترش می‌دهد:

- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که زمان سپری شده بین شروع و پایان وظیفه را با دقت ۱ میلی‌ثانیه نشان می‌دهد.
- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : همیشه `"longtask"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یکی از رشته‌های زیر را برمی‌گرداند که به زمینه مرورگر یا فریمی اشاره دارد که می‌تواند به وظیفه طولانی نسبت داده شود:
    - `"cross-origin-ancestor"`
    - `"cross-origin-descendant"`
    - `"cross-origin-unreachable"`
    - `"multiple-contexts"`
    - `"same-origin-ancestor"`
    - `"same-origin-descendant"`
    - `"same-origin"`
    - `"self"`
    - `"unknown"`
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را برمی‌گرداند که زمان شروع وظیفه را نشان می‌دهد.

این رابط همچنین از ویژگی‌های زیر پشتیبانی می‌کند:

- {{domxref("PerformanceLongTaskTiming.attribution")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک دنباله از نمونه‌های {{domxref('TaskAttributionTiming')}} را برمی‌گرداند.

## روش‌های نمونه

- {{domxref("PerformanceLongTaskTiming.toJSON()")}} {{Experimental_Inline}}
  - : یک نمایش JSON از شیء `PerformanceLongTaskTiming` را برمی‌گرداند.

## مثال‌ها

### دریافت وظایف طولانی

برای دریافت اطلاعات زمان‌بندی وظیفه طولانی، یک نمونه {{domxref("PerformanceObserver")}} ایجاد کنید و سپس متد [`observe()`](/en-US/docs/Web/API/PerformanceObserver/observe) آن را فراخوانی کنید، و `"longtask"` را به عنوان مقدار گزینه [`type`](/en-US/docs/Web/API/PerformanceEntry/entryType) وارد کنید. همچنین باید `buffered` را روی `true` تنظیم کنید تا به وظایف طولانی که عامل کاربر در حین ساخت سند بافر کرده است دسترسی داشته باشید. سپس callback شیء `PerformanceObserver` با لیستی از اشیاء `PerformanceLongTaskTiming` فراخوانی می‌شود که می‌توانید آن‌ها را تحلیل کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry);
  });
});

observer.observe({ type: "longtask", buffered: true });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("TaskAttributionTiming")}}