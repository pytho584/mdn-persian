---
title: "PerformanceResourceTiming"
slug: Web/API/PerformanceResourceTiming
page-type: web-api-interface
browser-compat: api.PerformanceResourceTiming
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

رابط **`PerformanceResourceTiming`** امکان دریافت و تحلیل داده‌های زمان‌بندی دقیق شبکه را در مورد بارگذاری منابع یک برنامه فراهم می‌کند. یک برنامه می‌تواند از معیارهای زمان‌بندی برای تعیین مثلاً مدت زمانی که برای دریافت یک منبع خاص مانند {{domxref("XMLHttpRequest")}}، {{SVGElement("SVG","SVG element")}}، تصویر یا اسکریپت طول می‌کشد، استفاده کند.

{{InheritanceDiagram}}

## توضیحات

ویژگی‌های این رابط یک جدول زمانی بارگذاری منبع با برچسب‌های زمانی با وضوح بالا برای رویدادهای شبکه مانند زمان شروع و پایان تغییر مسیر (redirect)، شروع دریافت (fetch)، زمان شروع و پایان جستجوی DNS، زمان شروع و پایان پاسخ و موارد دیگر ایجاد می‌کنند. علاوه بر این، این رابط {{domxref("PerformanceEntry")}} را با ویژگی‌های دیگری گسترش می‌دهد که داده‌هایی درباره اندازه منبع دریافت شده و همچنین نوع منبعی که دریافت را آغاز کرده است، ارائه می‌دهند.

### معیارهای معمول زمان‌بندی منبع

ویژگی‌های این رابط به شما امکان می‌دهد معیارهای خاصی از زمان‌بندی منبع را محاسبه کنید. موارد استفاده رایج عبارتند از:

- اندازه‌گیری زمان دست‌دهی TCP (`connectEnd` - `connectStart`)
- اندازه‌گیری زمان جستجوی DNS (`domainLookupEnd` - `domainLookupStart`)
- اندازه‌گیری زمان تغییر مسیر (`redirectEnd` - `redirectStart`)
- اندازه‌گیری زمان درخواست موقت (`firstInterimResponseStart` - `finalResponseHeadersStart`)
- اندازه‌گیری زمان درخواست (`responseStart` - `requestStart`)
- اندازه‌گیری زمان درخواست سند (`finalResponseHeadersStart` - `requestStart`)
- اندازه‌گیری زمان مذاکره TLS (`requestStart` - `secureConnectionStart`)
- اندازه‌گیری زمان دریافت (بدون تغییر مسیر) (`responseEnd` - `fetchStart`)
- اندازه‌گیری زمان پردازش ServiceWorker (`fetchStart` - `workerStart`)
- بررسی اینکه آیا محتوا فشرده شده است (`decodedBodySize` نباید برابر `encodedBodySize` باشد)
- بررسی اینکه آیا حافظه‌های نهان محلی استفاده شده‌اند (`transferSize` باید `0` باشد)
- بررسی اینکه آیا از پروتکل‌های مدرن و سریع استفاده شده است (`nextHopProtocol` باید HTTP/2 یا HTTP/3 باشد)
- بررسی اینکه آیا منابع صحیح مسدودکننده رندر هستند (`renderBlockingStatus`)

### مدیریت اندازه بافر منابع

به طور پیش‌فرض فقط ۲۵۰ ورودی زمان‌بندی منبع بافر می‌شوند. برای اطلاعات بیشتر به [اندازه‌های بافر منبع](/en-US/docs/Web/API/Performance_API/Resource_timing#managing_resource_buffer_sizes) در راهنمای زمان‌بندی منبع مراجعه کنید.

### اطلاعات زمان‌بندی بین‌مبدا (Cross-origin)

بسیاری از ویژگی‌های زمان‌بندی منبع محدود به بازگرداندن `0` یا یک رشته خالی هستند زمانی که منبع یک درخواست بین‌مبدا (cross-origin) باشد. برای افشای اطلاعات زمان‌بندی بین‌مبدا، هدر پاسخ HTTP {{HTTPHeader("Timing-Allow-Origin")}} باید تنظیم شود.

ویژگی‌هایی که به طور پیش‌فرض هنگام بارگذاری یک منبع از مبدایی غیر از مبدا خود صفحه وب به صورت `0` بازگردانده می‌شوند: `redirectStart`، `redirectEnd`، `domainLookupStart`، `domainLookupEnd`، `connectStart`، `connectEnd`، `secureConnectionStart`، `requestStart` و `responseStart`.

برای مثال، برای اینکه `https://developer.mozilla.org` اجازه دیدن اطلاعات زمان‌بندی منبع را داشته باشد، منبع بین‌مبدا باید ارسال کند:

```http
Timing-Allow-Origin: https://developer.mozilla.org
```

## ویژگی‌های نمونه

### به ارث رسیده از `PerformanceEntry`

این رابط ویژگی‌های زیر {{domxref("PerformanceEntry")}} را برای انواع ورودی عملکرد منبع با تعیین محدودیت‌های زیر گسترش می‌دهد:

- {{domxref("PerformanceEntry.duration")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp","timestamp")}} که تفاوت بین ویژگی‌های {{domxref("PerformanceResourceTiming.responseEnd","responseEnd")}} و {{domxref("PerformanceEntry.startTime","startTime")}} است را برمی‌گرداند.
- {{domxref("PerformanceEntry.entryType")}} {{ReadOnlyInline}}
  - : `"resource"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}} {{ReadOnlyInline}}
  - : URL منبع را برمی‌گرداند.
- {{domxref("PerformanceEntry.startTime")}} {{ReadOnlyInline}}
  - : {{domxref("DOMHighResTimeStamp","timestamp")}} مربوط به زمان شروع دریافت یک منبع را برمی‌گرداند. این مقدار معادل {{domxref("PerformanceResourceTiming.fetchStart")}} است.

### برچسب‌های زمانی

این رابط از ویژگی‌های برچسب زمانی زیر پشتیبانی می‌کند که در نمودار مشاهده می‌کنید و به ترتیب ثبت آنها برای دریافت یک منبع فهرست شده‌اند. یک فهرست الفبایی در ناوبری سمت چپ نشان داده شده است.

![نمودار برچسب‌های زمانی که به ترتیب ثبت آنها برای دریافت یک منبع فهرست شده‌اند](https://mdn.github.io/shared-assets/images/diagrams/api/performance/resource-timing/timestamp-diagram.svg)

- {{domxref('PerformanceResourceTiming.redirectStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان شروع دریافت (fetch) است که تغییر مسیر را آغاز می‌کند.
- {{domxref('PerformanceResourceTiming.redirectEnd')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پس از دریافت آخرین بایت از پاسخ آخرین تغییر مسیر.
- {{domxref('PerformanceResourceTiming.workerStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} را درست قبل از ارسال {{domxref("FetchEvent")}} برمی‌گرداند، اگر یک رشته Service Worker از قبل در حال اجرا باشد، یا درست قبل از شروع رشته Service Worker در صورت عدم اجرا. اگر منبع توسط یک Service Worker رهگیری نشود، این ویژگی همیشه 0 برمی‌گرداند.
- {{domxref('PerformanceResourceTiming.fetchStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} درست قبل از اینکه مرورگر شروع به دریافت منبع کند.
- {{domxref('PerformanceResourceTiming.domainLookupStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} درست قبل از اینکه مرورگر جستجوی نام دامنه برای منبع را شروع کند.
- {{domxref('PerformanceResourceTiming.domainLookupEnd')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان بلافاصله پس از پایان جستجوی نام دامنه توسط مرورگر برای منبع است.
- {{domxref('PerformanceResourceTiming.connectStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} درست قبل از اینکه مرورگر شروع به برقراری اتصال به سرور برای دریافت منبع کند.
- {{domxref('PerformanceResourceTiming.secureConnectionStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} درست قبل از اینکه مرورگر فرآیند دست‌دهی (handshake) برای ایمن‌سازی اتصال فعلی را شروع کند.
- {{domxref('PerformanceResourceTiming.connectEnd')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پس از اینکه مرورگر برقراری اتصال به سرور برای دریافت منبع را به پایان رساند.
- {{domxref('PerformanceResourceTiming.requestStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} درست قبل از اینکه مرورگر شروع به درخواست منبع از سرور کند.
- {{domxref('PerformanceResourceTiming.firstInterimResponseStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان پاسخ موقت (مثلاً 100 Continue یا 103 Early Hints) است.
- {{domxref('PerformanceResourceTiming.responseStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پس از اینکه مرورگر اولین بایت پاسخ را از سرور دریافت کند (که ممکن است یک پاسخ موقت باشد).
- {{domxref('PerformanceResourceTiming.finalResponseHeadersStart')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان پاسخ هدر نهایی (مثلاً 200 Success) پس از هر زمان پاسخ موقت است.
- {{domxref('PerformanceResourceTiming.responseEnd')}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMHighResTimeStamp")}} بلافاصله پس از اینکه مرورگر آخرین بایت منبع را دریافت کند یا بلافاصله قبل از بسته شدن اتصال انتقال، هر کدام زودتر اتفاق بیفتد.

### اطلاعات اضافی منبع

علاوه بر این، این رابط ویژگی‌های زیر را که حاوی اطلاعات بیشتری درباره یک منبع هستند، ارائه می‌دهد:

- {{domxref("PerformanceResourceTiming.contentType")}} {{ReadOnlyInline}}
  - : یک رشته که نسخه کوچک‌شده و استاندارد شده از نوع MIME منبع دریافت شده را نشان می‌دهد.
- {{domxref('PerformanceResourceTiming.decodedBodySize')}} {{ReadOnlyInline}}
  - : عددی که اندازه (به اکتت) دریافت شده از دریافت (HTTP یا حافظه نهان) بدنه پیام، پس از حذف هرگونه رمزگذاری محتوای اعمال شده، است.
- {{domxref("PerformanceResourceTiming.deliveryType")}} {{ReadOnlyInline}}
  - : نحوه تحویل منبع را نشان می‌دهد - مثلاً از حافظه نهان یا از یک پیش‌دریافت ناوبری (navigational prefetch).
- {{domxref('PerformanceResourceTiming.encodedBodySize')}} {{ReadOnlyInline}}
  - : عددی که اندازه (به اکتت) دریافت شده از دریافت (HTTP یا حافظه نهان) بدنه بار (payload) را قبل از حذف هرگونه رمزگذاری محتوای اعمال شده، نشان می‌دهد.
- {{domxref('PerformanceResourceTiming.initiatorType')}} {{ReadOnlyInline}}
  - : رشته‌ای که نشان‌دهنده ویژگی پلتفرم وب است که ورودی عملکرد را آغاز کرده است.
- {{domxref('PerformanceResourceTiming.nextHopProtocol')}} {{ReadOnlyInline}}
  - : رشته‌ای که نشان‌دهنده پروتکل شبکه استفاده شده برای دریافت منبع است، همانطور که توسط [شناسه پروتکل ALPN (RFC7301)](https://datatracker.ietf.org/doc/html/rfc7301) شناسایی شده است.
- {{domxref('PerformanceResourceTiming.renderBlockingStatus')}} {{ReadOnlyInline}}
  - : رشته‌ای که وضعیت مسدودکننده رندر را نشان می‌دهد. یا `"blocking"` یا `"non-blocking"`.
- {{domxref('PerformanceResourceTiming.responseStatus')}} {{ReadOnlyInline}}
  - : عددی که کد وضعیت پاسخ HTTP بازگردانده شده هنگام دریافت منبع را نشان می‌دهد.
- {{domxref('PerformanceResourceTiming.transferSize')}} {{ReadOnlyInline}}
  - : عددی که اندازه (به اکتت) منبع دریافت شده را نشان می‌دهد. اندازه شامل فیلدهای هدر پاسخ به اضافه بدنه بار پاسخ است.
- {{domxref('PerformanceResourceTiming.serverTiming')}} {{ReadOnlyInline}}
  - : آرایه‌ای از ورودی‌های {{domxref("PerformanceServerTiming")}} حاوی معیارهای زمان‌بندی سرور.

## روش‌های نمونه

- {{domxref("PerformanceResourceTiming.toJSON()")}}
  - : یک نمایش JSON از شیء `PerformanceResourceTiming` را برمی‌گرداند.

## مثال‌ها

### ثبت اطلاعات زمان‌بندی منبع

مثال با استفاده از {{domxref("PerformanceObserver")}} که ورودی‌های عملکرد جدید از نوع `resource` را هنگام ثبت در جدول زمانی عملکرد مرورگر اعلام می‌کند. از گزینه `buffered` برای دسترسی به ورودی‌های قبل از ایجاد ناظر استفاده کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry);
  });
});

observer.observe({ type: "resource", buffered: true });
```

مثال با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های عملکرد `resource` موجود در جدول زمانی عملکرد مرورگر را در زمان فراخوانی این روش نشان می‌دهد:

```js
const resources = performance.getEntriesByType("resource");
resources.forEach((entry) => {
  console.log(entry);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [زمان‌بندی منبع (نمای کلی)](/en-US/docs/Web/API/Performance_API/Resource_timing)