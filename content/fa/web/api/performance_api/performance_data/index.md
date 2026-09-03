---
title: Performance data
slug: Web/API/Performance_API/Performance_data
page-type: guide
---

{{DefaultAPISidebar("Performance API")}}

API عملکرد، داده‌های عملکرد را اندازه‌گیری کرده و در معرض دید قرار می‌دهد که می‌توان آن‌ها را به‌عنوان معیارهای عملکرد (performance metrics) برای برنامه وب شما جمع‌آوری کرد. این API روش‌هایی برای مشاهده جنبه‌های مختلف عملکرد برنامه فراهم می‌کند. این API تحلیل داده‌های عملکرد یا تجسم آن‌ها را ارائه نمی‌دهد. با این حال، Performance API به‌خوبی با ابزارهای توسعه‌دهنده در مرورگرها یکپارچه شده است و داده‌های آن اغلب به نقاط پایانی تحلیل و کتابخانه‌ها ارسال می‌شود تا معیارهای عملکرد را ثبت کنند؛ این کار به شما کمک می‌کند داده‌ها را ارزیابی کرده و گلوگاه‌های عملکردی را که بر کاربران تأثیر می‌گذارند پیدا کنید.

این صفحه یک نمای کلی از انواع داده‌های Performance API، نحوه جمع‌آوری آن‌ها و نحوه دسترسی به آن‌ها ارائه می‌دهد.

## جمع‌آوری داده‌ها

بیشتر معیارهای ارائه‌شده توسط Performance API به‌طور خودکار توسط مرورگر جمع‌آوری می‌شوند و شما نیازی به دستور دادن به مرورگر برای جمع‌آوری آن‌ها ندارید؛ فقط باید آن‌ها را بازیابی کنید.

برای برخی از معیارها باید به مرورگر بگویید چه چیزی را اندازه‌گیری کند:

- معیار [Element Timing](/en-US/docs/Web/API/PerformanceElementTiming) زمان لازم برای بارگذاری و رندر کردن عناصر خاصی از DOM را اندازه‌گیری می‌کند. این معیار اختیاری (opt-in) است: برای اینکه از مرورگر بخواهید معیارهای مربوط به یک عنصر خاص را شامل شود، باید ویژگی `elementtiming` را به آن عنصر اضافه کنید.
- معیار [User Timing](/en-US/docs/Web/API/Performance_API/User_timing) به شما امکان می‌دهد زمان بین نقاط دلخواه در برنامه‌تان را اندازه‌گیری کنید، که ممکن است به عملیات‌های تعریف‌شده توسط برنامه (مانند ورود کاربر) نگاشت شوند. برای جمع‌آوری این معیارها باید فراخوانی‌های Performance API را در نقاط مربوطه اضافه کنید.
- معیار [Server Timing](/en-US/docs/Web/API/Performance_API/Server_timing) به شما امکان می‌دهد زمان صرف‌شده برای عملیات‌های سمت سرور تعریف‌شده توسط برنامه را اندازه‌گیری کنید. برای جمع‌آوری این معیارها، سرور شما باید هدر HTTP `Server-Timing` را ارسال کند.

## ساختار داده‌های عملکرد

با استفاده از Performance API می‌توانید داده‌های عملکرد را در هر دو بافت (context) سراسری {{domxref("Window.performance", "Window")}} و {{domxref("WorkerGlobalScope.performance", "Worker")}} جمع‌آوری کنید. اگر معیارهای عملکرد را برای چند بافت جمع‌آوری می‌کنید، به {{domxref("performance.timeOrigin")}} نگاهی بیندازید تا مبدأ زمان را بین بافت‌ها همگام‌سازی کنید.

در این بافت‌ها، داده‌های عملکردِ تکتک به‌صورت ورودی‌های عملکرد (performance entries) نمایش داده می‌شوند.

### ورودی‌های عملکرد

یک نقطه داده عملکرد ثبت‌شده، _perfomance entry_ (ورودی عملکرد) نامیده می‌شود و با نمونه‌ای از رابط {{domxref("PerformanceEntry")}} نمایش داده می‌شود.

Performance API انواع مختلفی از داده‌های عملکرد را ثبت می‌کند و `PerformanceEntry` دارای ویژگی {{domxref("PerformanceEntry.entryType", "entryType")}} است که رشته‌ای است و نوع این ورودی عملکرد را توصیف می‌کند:

- `"element"` مدت زمان بارگذاری و رندر یک عنصر را ثبت می‌کند.
- `"event"` مدت زمانی که طول کشیده تا مرورگر در پاسخ به رویداد، اجرای یک event handler را آغاز کند و همچنین مدت زمان اجرای event handler را ثبت می‌کند. برای اندازه‌گیری {{Glossary("Interaction to Next Paint")}} استفاده می‌شود.
- `"first-input"` مقدار {{Glossary("First Input Delay")}} را ثبت می‌کند.
- `"largest-contentful-paint"` بزرگ‌ترین نقاشی (paint) را در طول بارگذاری صفحه ثبت می‌کند.
- `"layout-shift"` معیاری را ثبت می‌کند که میزان جابه‌جایی چیدمان (layout) صفحه را در هر فریم انیمیشن نشان می‌دهد.
- `"longtask"` وظایفی (tasks) را ثبت می‌کند که ۵۰ میلی‌ثانیه یا بیشتر طول کشیده‌اند.
- `"mark"` یک برچسب زمانی سفارشی که توسط توسعه‌دهنده ساخته شده را ثبت می‌کند.
- `"measure"` یک اندازه‌گیری سفارشی بین دو برچسب زمانی که توسط توسعه‌دهنده ساخته شده را ثبت می‌کند.
- `"navigation"` معیارهای مرتبط با ناوبری به صفحه و بارگذاری اولیه آن را ثبت می‌کند.
- `"paint"` لحظات کلیدی رندر را در طول بارگذاری صفحه ثبت می‌کند.
- `"resource"` مدت زمانی که مرورگر برای واکشی (fetch) یک منبع صرف کرده است را ثبت می‌کند.
- `"visibility-state"` زمان تغییر وضعیت قابلیت مشاهده صفحه را ثبت می‌کند، یعنی زمانی که یک تب از پیش‌زمینه به پس‌زمینه می‌رود یا برعکس.

### زیرکلاس‌های ورودی عملکرد

انواع خاصی از ورودی‌ها معمولاً داده‌های اضافی مخصوص به نوع خود را شامل می‌شوند: برای مثال، نوع «resource» زمان شروع و پایان جستجوی DNS را ثبت می‌کند. بنابراین ورودی‌ها توسط زیرکلاس‌هایی نمایش داده می‌شوند که رابط پایه `PerformanceEntry` را توسعه می‌دهند. برای مثال، یک ورودی «resource» با نمونه‌ای از {{domxref("PerformanceResourceTiming")}} نمایش داده می‌شود که از `PerformanceEntry` ارث می‌برد و ویژگی‌هایی برای ثبت زمان‌های جستجوی DNS اضافه می‌کند.

زیرکلاس‌های `PerformanceEntry` همچنین معنای ویژگی‌های متعلق به خود `PerformanceEntry` را تعریف می‌کنند: برای مثال، `PerformanceEntry` دارای ویژگی {{domxref("PerformanceEntry.name", "name")}} است که معنای آن به زیرکلاس بستگی دارد.

رابط‌های زیر از `PerformanceEntry` ارث می‌برند:

- {{domxref("LargestContentfulPaint")}}
- {{domxref("LayoutShift")}}
- {{domxref("PerformanceElementTiming")}}
- {{domxref("PerformanceEventTiming")}}
- {{domxref("PerformanceLongTaskTiming")}}
- {{domxref("PerformanceMark")}}
- {{domxref("PerformanceMeasure")}}
- {{domxref("PerformancePaintTiming")}}
- {{domxref("PerformanceResourceTiming")}}
  - {{domxref("PerformanceNavigationTiming")}} inherits from `PerformanceResourceTiming`
- {{domxref("TaskAttributionTiming")}}
- {{domxref("VisibilityStateEntry")}}

## دسترسی به داده‌ها

می‌توانید به ورودی‌های عملکرد به یکی از دو روش دسترسی پیدا کنید. روش ترجیحی استفاده از رابط {{domxref("PerformanceObserver")}} است که با یک تابع callback ساخته می‌شود که وقتی ورودی‌های عملکرد خاصی ثبت می‌شوند فراخوانی می‌شود. سپس متد {{domxref("PerformanceObserver.observe", "observe")}} آن را فراخوانی می‌کنید و نوع‌هایی را که باید مشاهده شوند پاس می‌دهید و از گزینه `buffered` برای بازیابی ورودی‌هایی که قبل از مشاهده رخ داده‌اند استفاده می‌کنید.

```js
function logEventDuration(entries) {
  const events = entries.getEntriesByType("event");
  for (const event of events) {
    console.log(
      `Event handler took: ${
        event.processingEnd - event.processingStart
      } milliseconds`,
    );
  }
}

const observer = new PerformanceObserver(logEventDuration);
observer.observe({ type: "event", buffered: true });
```

از طرف دیگر، می‌توانید از متدهای {{domxref("Performance.getEntries()")}}، {{domxref("Performance.getEntriesByName()")}} و {{domxref("Performance.getEntriesByType()")}} برای بازیابی همه ورودی‌های عملکرد برای یک صفحه، یا ورودی‌های منطبق با نام یا نوع داده‌شده استفاده کنید.

```js
const events = performance.getEntriesByType("event");

for (const event of events) {
  console.log(
    `Event handler took: ${
      event.processingEnd - event.processingStart
    } milliseconds`,
  );
}
```

گزینه `PerformanceObserver` ترجیح داده می‌شود زیرا:

- متدهای `getEntries*` همیشه همه ورودی‌های مربوطه را از آغاز خط زمانی (timeline) برمی‌گردانند؛ بنابراین اگر دوباره آن‌ها را فراخوانی کنید، دوباره همان ورودی‌ها را خواهید دید و باید ورودی‌هایی را که قبلاً دیده‌اید فیلتر کنید.
- اعلان‌های observer به‌صورت ناهمگام (asynchronously) تحویل داده می‌شوند، بنابراین مرورگر می‌تواند آن‌ها را در زمان بیکاری ارسال کند تا تأثیر آن‌ها بر عملکرد به حداقل برسد.
- همه انواع ورودی با متدهای `getEntries*` کار نمی‌کنند. برای برخی از آن‌ها باید از performance observer برای دسترسی به آن‌ها استفاده کنید.

## مدیریت اندازه بافرها

برای هر شیء سراسری، محدودیت بافر برای ورودی‌های عملکرد وجود دارد. این محدودیت تضمین می‌کند که مرورگر هنگام نگهداری داده‌های عملکرد، حافظه نامحدودی مصرف نکند. به‌ویژه وقتی وب‌سایت یا برنامه شما منابع زیادی را واکشی می‌کند (مثلاً هنگام استفاده از polling)، ممکن است لازم باشد محدودیت‌های بافرها را بررسی کنید:

| شناسه {{domxref("PerformanceEntry.entryType", "entryType")}} | رابط | حداکثر تعداد ورودی‌های بافر |
| ----------------------------------------------------------------- | ------------------------------------------ | -------------------------------- |
| `"mark"`                                                          | {{domxref("PerformanceMark")}}             | نامحدود                         |
| `"measure"`                                                       | {{domxref("PerformanceMeasure")}}          | نامحدود                         |
| `"navigation"`                                                    | {{domxref("PerformanceNavigationTiming")}} | نامحدود                         |
| `"resource"`                                                      | {{domxref("PerformanceResourceTiming")}}   | ۲۵۰ (قابل تنظیم، به پایین مراجعه کنید)      |
| `"longtask"`                                                      | {{domxref("PerformanceLongTaskTiming")}}   | ۲۰۰                             |
| `"paint"`                                                         | {{domxref("PerformancePaintTiming")}}      | ۲ (بیشتر از این نخواهد بود)          |
| `"element"`                                                       | {{domxref("PerformanceElementTiming")}}    | ۱۵۰                             |
| `"event"`                                                         | {{domxref("PerformanceEventTiming")}}      | ۱۵۰                             |
| `"first-input"`                                                   | {{domxref("PerformanceEventTiming")}}      | ۱ (بیشتر از این نخواهد بود)          |
| `"layout-shift"`                                                  | {{domxref("LayoutShift")}}                 | ۱۵۰                             |
| `"largest-contentful-paint"`                                      | {{domxref("LargestContentfulPaint")}}      | ۱۵۰                             |
| `"visibility-state"`                                              | {{domxref("VisibilityStateEntry")}}        | ۵۰                              |

جدول ۱. اندازه بافرها ([منبع](https://w3c.github.io/timing-entrytypes-registry/#registry)).

برای نوع ورودی «resource»، به [مدیریت اندازه بافر منابع](/en-US/docs/Web/API/Performance_API/Resource_timing#managing_resource_buffer_sizes) مراجعه کنید تا نحوه تنظیم اندازه بافر متفاوت را ببینید.

برای «first-input» و «paint»، محدودیت ذاتاً در تعریف معیار وجود دارد. ورودی‌های بیشتری بیش از یک (یا دو) وجود نخواهد داشت.

callback [performance observer](/en-US/docs/Web/API/PerformanceObserver/PerformanceObserver) شامل یک پارامتر اختیاری `droppedEntriesCount` است که به شما می‌گوید چند ورودی به دلیل پر بودن فضای بافر از دست رفته‌اند.

```js
function perfObserver(list, observer, droppedEntriesCount) {
  list.getEntries().forEach((entry) => {
    // do something with the entries
  });
  if (droppedEntriesCount > 0) {
    console.warn(
      `${droppedEntriesCount} entries were dropped because the buffer was full.`,
    );
  }
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ type: "resource", buffered: true });
```

یک روش مفید دیگر {{domxref("PerformanceObserver.takeRecords()")}} است که فهرست فعلی ورودی‌های عملکرد ذخیره‌شده در performance observer را بازمی‌گرداند و همچنین آن را خالی می‌کند.

## داده‌های JSON

همه ورودی‌های عملکرد یک {{Glossary("Serialization","serializer")}} به نام `toJSON()` ارائه می‌دهند که یک نمایش {{jsxref("JSON")}} از ورودی برمی‌گرداند. اگر بخواهید همه داده‌های موجود را جمع‌آوری کرده و در جایی ذخیره کنید، این می‌تواند مفید باشد.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(entry.toJSON());
  });
});

observer.observe({ type: "event", buffered: true });
```

این یک شیء JSON را به شکل زیر ثبت می‌کند:

```json
{
  "name": "dragover",
  "entryType": "event",
  "startTime": 67090751.599999905,
  "duration": 128,
  "processingStart": 67090751.70000005,
  "processingEnd": 67090751.900000095,
  "cancelable": true
}
```

برای دریافت نمایش رشته‌ای از ورودی، می‌توانید [`JSON.stringify(entry)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) را مستقیماً با هر شیء `PerformanceEntry` استفاده کنید؛ این کار به‌طور خودکار متد `toJSON()` ورودی را فراخوانی می‌کند.

## همچنین ببینید

- {{domxref("PerformanceEntry")}}
- {{domxref("PerformanceObserver.observe()")}}