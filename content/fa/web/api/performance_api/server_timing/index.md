---
title: "Server timing"
---

---
title: Server timing
slug: Web/API/Performance_API/Server_timing
page-type: guide
---

{{DefaultAPISidebar("Performance API")}}

Server-Timing بخشی از Performance API است و به سرورها امکان می‌دهد معیارهای چرخه‌ی درخواست-پاسخ را به عامل کاربر (user agent) منتقل کنند. می‌توانید این اطلاعات را جمع‌آوری کنید و دقیقاً مانند سایر معیارهایی که با Performance API پردازش می‌شوند، بر اساس معیارهای سمت سرور عمل کنید.

## ارسال معیارهای سرور

هدر HTTP {{HTTPHeader("Server-Timing")}} برای نمایش معیارهای زمان‌بندی سمت سرور (backend) استفاده می‌شود. برای مثال، ممکن است بخواهید زمان عملیات خواندن/نوشتن پایگاه داده، زمان CPU و دسترسی به سیستم فایل را ارسال کنید.

می‌توانید معیارها را همراه با مقدار یا بدون مقدار ارسال کنید. معیارها به‌صورت اختیاری می‌توانند توضیحاتی داشته باشند. توصیه می‌شود نام‌ها، توضیحات و داده‌ها را تا حد امکان کوتاه نگه دارید تا سربار HTTP کاهش یابد.

نمونه‌هایی از هدرهای `Server-Timing`:

```http
// Single metric without value
Server-Timing: missedCache

// Single metric with value
Server-Timing: cpu;dur=2.4

// Single metric with description and value
Server-Timing: cache;desc="Cache Read";dur=23.2

// Two metrics with values
Server-Timing: db;dur=53, app;dur=47.2

// Server-Timing as trailer
Trailer: Server-Timing
--- response body ---
Server-Timing: total;dur=123.4
```

برای محاسبه‌ی معیارهای واقعی سمت سرور، به مستندات CMS، فریمورک یا زبان برنامه‌نویسی سمت سرور خود مراجعه کنید تا نحوه‌ی اندازه‌گیری کارایی در برنامه‌ی backend را بیاموزید. اگر سرور شما از Node.js استفاده می‌کند، APIهای اندازه‌گیری کارایی آن بسیار شبیه به Performance API در مرورگرها خواهند بود؛ زیرا ماژول performance در Node.js زیرمجموعه‌ای از W3C Web Performance APIs به‌همراه APIهای اضافی برای اندازه‌گیری‌های مخصوص Node.js است. برای اطلاعات بیشتر، [مستندات performance در Node.js](https://nodejs.org/api/perf_hooks.html#performance-measurement-apis) را ببینید.

توجه داشته باشید که هیچ همگام‌سازی ساعتی بین سرور، کلاینت و هر پروکسی میانی وجود ندارد. این بدان معناست که اگر سرور شما برچسب‌های زمانی (timestamp) یا `startTime` ارسال کند، ممکن است مقدار آن به‌طور معناداری با `startTime` در خط زمانی کلاینت مطابقت نداشته باشد.

هنگامی که معیارهای مورد نظر خود را محاسبه کردید، سرور باید هدر `Server-Timing` را در پاسخ خود ارسال کند. برای نمونه‌ی نحوه‌ی ارسال این هدر در Node.js، به صفحه‌ی مرجع {{HTTPHeader("Server-Timing")}} مراجعه کنید.

## بازیابی معیارهای سرور

معیارهای زمان‌بندی سرور معمولاً در ابزار توسعه‌دهنده‌ی مرورگر ظاهر می‌شوند، اما به‌صورت ورودی‌های کارایی (performance entries) از نوع {{domxref("PerformanceServerTiming")}} نیز ذخیره می‌شوند و می‌توانید مانند سایر [داده‌های کارایی](/en-US/docs/Web/API/Performance_API/Performance_data) به آن‌ها دسترسی داشته باشید. با این حال، هیچ ورودی مستقلی با نام `"server-timing"` وجود ندارد. اشیاء `PerformanceServerTiming` از طریق ورودی‌های کارایی `"navigation"` و `"resource"` قابل مشاهده هستند. شما می‌توانید معیارهای سرور را از خاصیت {{domxref("PerformanceResourceTiming.serverTiming")}} که آرایه‌ای از اشیاء `PerformanceServerTiming` است، به‌دست آورید.

با یک {{HTTPHeader("Server-Timing")}} مانند این:

```http
Server-Timing: cache;desc="Cache Read";dur=23.2,db;dur=53,app;dur=47.2
```

یک `PerformanceObserver` می‌تواند ورودی‌ها را در سمت کلاینت با کد زیر ثبت کند:

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    entry.serverTiming.forEach((serverEntry) => {
      console.log(
        `${serverEntry.name} (${serverEntry.description}) duration: ${serverEntry.duration}`,
      );
      // Logs "cache (Cache Read) duration: 23.2"
      // Logs "db () duration: 53"
      // Logs "app () duration: 47.2"
    });
  });
});

["navigation", "resource"].forEach((type) =>
  observer.observe({ type, buffered: true }),
);
```

## ملاحظات حریم خصوصی و امنیت

هدر `Server-Timing` ممکن است اطلاعات حساس بالقوه‌ای درباره‌ی برنامه و زیرساخت افشا کند. بنابراین، باید در سمت سرور کنترل کنید که معیارها چه زمانی و به چه کسانی بازگردانده شوند. برای مثال، می‌توانید معیارها را فقط به کاربران احرازهویتشده نشان دهید و هیچ داده‌ای را در دسترس عموم قرار ندهید.

رابط `PerformanceServerTiming` به همان مبدأ (same-origin) محدود است، اما می‌توانید از هدر {{HTTPHeader("Timing-Allow-Origin")}} برای تعیین دامنه‌هایی استفاده کنید که اجازه‌ی دسترسی به معیارهای سرور را دارند. همچنین توجه داشته باشید که در برخی مرورگرها این رابط فقط در زمینه‌های امن (HTTPS) در دسترس است.