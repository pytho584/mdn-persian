---
title: Long animation frame timing
slug: Web/API/Performance_API/Long_animation_frame_timing
page-type: guide
---

{{DefaultAPISidebar("Performance API")}}

**فریم‌های انیمیشن طولانی** (LoAF) می‌توانند تجربه کاربری یک وب‌سایت را تحت تأثیر قرار دهند. این فریم‌ها باعث به‌روزرسانی‌های کند رابط کاربری (UI) می‌شوند که در نتیجه کنترل‌هایی به‌ظاهر غیرفعال، افکت‌های انیمیشنی ناهموار (janky) و اسکرول نامطلوب ایجاد کرده و باعث نارضایتی کاربر می‌شوند. [Long Animation Frames API](https://w3c.github.io/long-animation-frames/) به توسعه‌دهندگان امکان می‌دهد تا اطلاعاتی درباره فریم‌های انیمیشن طولانی به دست آورده و علل ریشه‌ای آن‌ها را بهتر درک کنند. این مقاله نحوه استفاده از Long Animation Frames API را نشان می‌دهد.

## فریم انیمیشن طولانی چیست؟

یک فریم انیمیشن طولانی — یا LoAF — به‌روزرسانی رندرینگی است که بیش از ۵۰ میلی‌ثانیه به تأخیر افتاده است.

پاسخ‌گویی خوب به این معناست که یک صفحه به سرعت به تعاملات کاربر واکنش نشان دهد. این شامل ترسیم به‌موقع هرگونه به‌روزرسانی مورد نیاز کاربر و اجتناب از هر چیزی است که ممکن است این به‌روزرسانی‌ها را مسدود کند. به عنوان مثال، معیار [Interaction to Next Paint (INP)](https://web.dev/articles/inp) گوگل توصیه می‌کند که یک وب‌سایت باید در عرض ۲۰۰ میلی‌ثانیه به تعاملات صفحه (مانند کلیک‌ها یا فشار دادن کلیدها) پاسخ دهد.

برای انیمیشن‌های روان، به‌روزرسانی‌ها باید سریع باشند — برای اینکه یک انیمیشن با نرخ روان ۶۰ فریم در ثانیه اجرا شود، هر فریم انیمیشن باید در حدود ۱۶ میلی‌ثانیه (۱۰۰۰/۶۰) رندر شود.

## مشاهده فریم‌های انیمیشن طولانی

برای به‌دست آوردن اطلاعات در مورد LoAFها و شناسایی عوامل مشکل‌ساز، می‌توانید ورودی‌های جدول زمانی عملکرد (performance timeline) با {{domxref("PerformanceEntry.entryType", "entryType")}} برابر با `"long-animation-frame"` را با استفاده از یک {{domxref("PerformanceObserver")}} استاندارد مشاهده کنید:

```js
const observer = new PerformanceObserver((list) => {
  console.log(list.getEntries());
});

observer.observe({ type: "long-animation-frame", buffered: true });
```

همچنین می‌توان فریم‌های انیمیشن طولانی قبلی را با استفاده از روشی مانند {{domxref("Performance.getEntriesByType()")}} پرس‌وجو کرد:

```js
const loafs = performance.getEntriesByType("long-animation-frame");
```

توجه داشته باشید که حداکثر اندازه بافر برای نوع ورودی `"long-animation-frame"` ۲۰۰ است و پس از آن ورودی‌های جدید حذف می‌شوند؛ بنابراین استفاده از روش `PerformanceObserver` توصیه می‌شود.

## بررسی ورودی‌های `"long-animation-frame"`

ورودی‌های جدول زمانی عملکرد که با نوع `"long-animation-frame"` بازگردانده می‌شوند، توسط اشیاء {{domposxref("PerformanceLongAnimationFrameTiming")}} نمایش داده می‌شوند. این شیء دارای یک ویژگی {{domxref("PerformanceLongAnimationFrameTiming.scripts", "scripts")}} است که شامل آرایه‌ای از اشیاء {{domxref("PerformanceScriptTiming")}} می‌باشد. هر یک از این اشیاء حاوی اطلاعاتی درباره اسکریپتی است که در فریم انیمیشن طولانی نقش داشته است.

در زیر یک مثال کامل از یک ورودی عملکرد `"long-animation-frame"` با یک اسکریپت آورده شده است:

```js
({
  blockingDuration: 0,
  duration: 60,
  entryType: "long-animation-frame",
  firstUIEventTimestamp: 11801.099999999627,
  name: "long-animation-frame",
  paintTime: 11862.400000000373,
  presentationTime: 11863.199999999255,
  renderStart: 11858.800000000745,
  scripts: [
    {
      duration: 45,
      entryType: "script",
      executionStart: 11803.199999999255,
      forcedStyleAndLayoutDuration: 0,
      invoker: "DOMWindow.onclick",
      invokerType: "event-listener",
      name: "script",
      pauseDuration: 0,
      sourceURL: "https://web.dev/js/index-ffde4443.js",
      sourceFunctionName: "myClickHandler",
      sourceCharPosition: 17796,
      startTime: 11803.199999999255,
      window: {
        // …شیء Window…
      },
      windowAttribution: "self",
    },
  ],
  startTime: 11802.400000000373,
  styleAndLayoutStart: 11858.800000000745,
});
```

فراتر از داده‌های استاندارد بازگردانده شده توسط یک ورودی {{domxref("PerformanceEntry")}}، این موارد شامل موارد قابل توجه زیر است:

- {{domxref("PerformanceLongAnimationFrameTiming.blockingDuration", "blockingDuration")}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده کل زمان (بر حسب میلی‌ثانیه) است که در آن نخ اصلی از پاسخ‌دهی به وظایف با اولویت بالا، مانند ورودی کاربر، مسدود شده است. این مقدار با در نظر گرفتن تمام [وظایف طولانی](/en-US/docs/Web/API/PerformanceLongTaskTiming#description) در داخل LoAF که `duration` آن‌ها بیش از ۵۰ میلی‌ثانیه است، با کسر ۵۰ میلی‌ثانیه از هر یک، اضافه کردن زمان رندرینگ به طولانی‌ترین زمان وظیفه، و جمع نتایج محاسبه می‌شود.
- {{domxref("PerformanceLongAnimationFrameTiming.firstUIEventTimestamp", "firstUIEventTimestamp")}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان اولین رویداد UI (مانند رویداد ماوس یا صفحه کلید) است که در طول فریم انیمیشن جاری پردازش شده است. توجه داشته باشید که این مهر زمانی می‌تواند قبل از شروع این فریم انیمیشن باشد، اگر بین وقوع رویداد و پردازش آن تأخیر وجود داشته باشد.
- {{domxref("PerformanceLongAnimationFrameTiming.paintTime", "paintTime")}}
  - : {{domxref("DOMHighResTimeStamp","مهر زمانی")}} را که فاز رندرینگ به پایان رسید و فریم انیمیشن شروع شد، بازمی‌گرداند.
- {{domxref("PerformanceLongAnimationFrameTiming.presentationTime", "presentationTime")}}
  - : {{domxref("DOMHighResTimeStamp","مهر زمانی")}} را که به‌روزرسانی UI در واقع روی صفحه نمایش داده شد، بازمی‌گرداند.
- {{domxref("PerformanceLongAnimationFrameTiming.renderStart", "renderStart")}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان شروع چرخه رندرینگ است که شامل فراخوانی‌های {{domxref("Window.requestAnimationFrame()")}}، محاسبه استایل و طرح‌بندی، فراخوانی‌های {{domxref("ResizeObserver")}} و فراخوانی‌های {{domxref("IntersectionObserver")}} می‌شود.
- {{domxref("PerformanceLongAnimationFrameTiming.styleAndLayoutStart", "styleAndLayoutStart")}}
  - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده آغاز دوره زمانی صرف شده در محاسبات استایل و طرح‌بندی برای فریم انیمیشن جاری است.
- ویژگی‌های {{domxref("PerformanceScriptTiming")}}:
  - : ویژگی‌هایی که اطلاعاتی در مورد اسکریپت(هایی) که در LoAF نقش داشته‌اند ارائه می‌دهند:
    - {{domxref("PerformanceScriptTiming.executionStart", "script.executionStart")}}
      - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده زمان اتمام کامپایل اسکریپت و شروع اجرا است.
    - {{domxref("PerformanceScriptTiming.forcedStyleAndLayoutDuration", "script.forcedStyleAndLayoutDuration")}}
      - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده کل زمان صرف شده (بر حسب میلی‌ثانیه) توسط اسکریپت برای پردازش استایل/طرح‌بندی اجباری است. برای درک علت این امر، به [Avoid layout thrashing](https://web.dev/articles/avoid-large-complex-layouts-and-layout-thrashing#avoid_layout_thrashing) مراجعه کنید.
    - {{domxref("PerformanceScriptTiming.invoker", "script.invoker")}} و {{domxref("PerformanceScriptTiming.invokerType", "script.invokerType")}}
      - : مقادیر رشته‌ای که نحوه فراخوانی اسکریپت (مثلاً `"IMG#id.onload"` یا `"Window.requestAnimationFrame"`) و نوع نقطه ورود اسکریپت (مثلاً `"event-listener"` یا `"resolve-promise"`) را نشان می‌دهند.
    - {{domxref("PerformanceScriptTiming.pauseDuration", "script.pauseDuration")}}
      - : یک {{domxref("DOMHighResTimeStamp")}} که نشان‌دهنده کل زمان (بر حسب میلی‌ثانیه) صرف شده توسط اسکریپت برای عملیات همزمان "مکث" (مانند فراخوانی‌های {{domxref("Window.alert()")}} یا {{domxref("XMLHttpRequest")}} همزمان) است.
    - {{domxref("PerformanceScriptTiming.sourceCharPosition", "script.sourceCharPosition")}}، {{domxref("PerformanceScriptTiming.sourceFunctionName", "script.sourceFunctionName")}} و {{domxref("PerformanceScriptTiming.sourceURL", "script.sourceURL")}}
      - : مقادیری که به ترتیب موقعیت کاراکتر اسکریپت، نام تابع و URL اسکریپت را نشان می‌دهند. توجه به این نکته مهم است که نام تابع گزارش شده "نقطه ورود" اسکریپت (یعنی سطح بالای پشته) خواهد بود، نه هیچ زیرتابع کند خاصی.

        به عنوان مثال، اگر یک کنترل‌کننده رویداد یک تابع سطح بالا را فراخوانی کند که به نوبه خود یک زیرتابع کند را فراخوانی می‌کند، فیلدهای `source*` نام و مکان تابع سطح بالا را گزارش می‌دهند، نه زیرتابع کند را. این به دلایل عملکردی است — ردیابی کامل پشته هزینه‌بر است.

    - {{domxref("PerformanceScriptTiming.windowAttribution", "script.windowAttribution")}} و {{domxref("PerformanceScriptTiming.window", "script.window")}}
      - : یک مقدار شمارشی که رابطه کانتینر (یعنی سند سطح بالا یا یک {{htmlelement("iframe")}}) که این اسکریپت در آن اجرا شده است با سند سطح بالا را توصیف می‌کند، و یک ارجاع به شیء {{domxref("Window")}} آن.

    > [!NOTE]
    > انتساب اسکریپت فقط برای اسکریپت‌هایی که در نخ اصلی یک صفحه اجرا می‌شوند، از جمله `<iframe>`های هم‌منبع (same-origin) ارائه می‌شود. با این حال، `<iframe>`های متقاطع (cross-origin)، [web workerها](/en-US/docs/Web/API/Web_Workers_API)، [service workerها](/en-US/docs/Web/API/Service_Worker_API) و کدهای [افزونه‌ها](/en-US/docs/Mozilla/Add-ons/WebExtensions) در فریم‌های انیمیشن طولانی انتساب اسکریپت نخواهند داشت، حتی اگر بر مدت زمان آن تأثیر بگذارند.

## محاسبه مهرهای زمانی

مهرهای زمانی ارائه شده در کلاس {{domxref("PerformanceLongAnimationFrameTiming")}} امکان محاسبه چندین زمان‌بندی مفید دیگر را برای فریم انیمیشن طولانی فراهم می‌کنند:

| زمان‌بندی                      | محاسبه                                                                 |
| ------------------------------ | ---------------------------------------------------------------------- |
| زمان شروع                      | `startTime`                                                            |
| زمان پایان                     | `startTime + duration` (یا `paintTime`/`presentationTime`)              |
| مدت زمان کار                   | `renderStart ? renderStart - startTime : duration`                      |
| مدت زمان رندر                  | `renderStart ? (startTime + duration) - renderStart : 0`                |
| رندر: مدت زمان قبل از طرح‌بندی | `styleAndLayoutStart ? styleAndLayoutStart - renderStart : 0`           |
| رندر: مدت زمان استایل و طرح‌بندی | `styleAndLayoutStart ? (startTime + duration) - styleAndLayoutStart : 0` |

## مثال‌ها

### تشخیص پشتیبانی از Long Animation Frames API

می‌توانید با استفاده از {{domxref("PerformanceObserver.supportedEntryTypes_static", "PerformanceObserver.supportedEntryTypes")}} بررسی کنید که آیا Long Animation Frames API پشتیبانی می‌شود:

```js
if (PerformanceObserver.supportedEntryTypes.includes("long-animation-frame")) {
  // نظارت بر LoAFها
}
```

### گزارش LoAFهای بالاتر از یک آستانه مشخص

در حالی که آستانه‌های LoAF روی ۵۰ میلی‌ثانیه ثابت هستند، این ممکن است در ابتدای کار بهینه‌سازی عملکرد حجم زیادی از گزارش‌ها ایجاد کند. در ابتدا، ممکن است بخواهید LoAFها را با یک مقدار آستانه بالاتر گزارش کنید و به تدریج با بهبود سایت و حذف بدترین LoAFها، آستانه را کاهش دهید. کد زیر می‌تواند برای ضبط LoAFهای بالاتر از یک آستانه خاص برای تحلیل بیشتر استفاده شود (مثلاً با ارسال آن‌ها به یک نقطه پایانی تحلیلی):

```js
const REPORTING_THRESHOLD_MS = 150;

const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    if (entry.duration > REPORTING_THRESHOLD_MS) {
      // مثال در اینجا در کنسول ثبت می‌کند؛ کد واقعی می‌تواند به نقطه پایانی تحلیلی ارسال کند
      console.log(entry.paintTime);
      console.log(entry.presentationTime);
    }
  }
});

observer.observe({ type: "long-animation-frame", buffered: true });
```

ورودی‌های فریم انیمیشن طولانی می‌توانند بسیار بزرگ باشند؛ بنابراین درباره اینکه چه داده‌هایی از هر ورودی باید به تحلیل ارسال شود، با دقت فکر کنید. به عنوان مثال، زمان‌های خلاصه ورودی‌ها و URLهای اسکریپت ممکن است برای نیاز شما کافی باشد.

### مشاهده طولانی‌ترین فریم‌های انیمیشن

ممکن است بخواهید فقط داده‌های مربوط به طولانی‌ترین فریم‌های انیمیشن (مثلاً ۵ یا ۱۰ مورد برتر) را جمع‌آوری کنید تا حجم داده‌های مورد نیاز برای جمع‌آوری کاهش یابد. این کار می‌تواند به صورت زیر انجام شود:

```js
MAX_LOAFS_TO_CONSIDER = 10;
let longestBlockingLoAFs = [];

const observer = new PerformanceObserver((list) => {
  longestBlockingLoAFs = longestBlockingLoAFs
    .concat(list.getEntries())
    .sort((a, b) => b.blockingDuration - a.blockingDuration)
    .slice(0, MAX_LOAFS_TO_CONSIDER);
});
observer.observe({ type: "long-animation-frame", buffered: true });

// گزارش داده‌ها در رویداد visibilitychange
document.addEventListener("visibilitychange", () => {
  // مثال در اینجا در کنسول ثبت می‌کند؛ کد واقعی می‌تواند به نقطه پایانی تحلیلی ارسال کند
  console.log(longestBlockingLoAFs);
});
```

### گزارش فریم‌های انیمیشن طولانی با تعاملات

یکی دیگر از تکنیک‌های مفید، ارسال بزرگ‌ترین ورودی‌های LoAF است که در آن یک تعامل در طول فریم رخ داده است. این را می‌توان با وجود مقدار {{domxref("PerformanceLongAnimationFrameTiming.firstUIEventTimestamp", "firstUIEventTimestamp")}} تشخیص داد.

کد زیر تمام ورودی‌های LoAF بزرگتر از ۱۵۰ میلی‌ثانیه را که در آن یک تعامل در طول فریم رخ داده است، ثبت می‌کند. بسته به نیاز خود می‌توانید مقدار بالاتر یا پایین‌تری را انتخاب کنید.

```js
const REPORTING_THRESHOLD_MS = 150;

const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    if (
      entry.duration > REPORTING_THRESHOLD_MS &&
      entry.firstUIEventTimestamp > 0
    ) {
      // مثال در اینجا در کنسول ثبت می‌کند؛ کد واقعی می‌تواند به نقطه پایانی تحلیلی ارسال کند
      console.log(entry);
    }
  }
});

observer.observe({ type: "long-animation-frame", buffered: true });
```

### شناسایی الگوهای رایج اسکریپت در فریم‌های انیمیشن طولانی

یک استراتژی جایگزین این است که ببینیم کدام اسکریپت‌ها بیشتر در ورودی‌های LoAF ظاهر می‌شوند. داده‌ها می‌توانند در سطح یک اسکریپت و/یا موقعیت کاراکتر گزارش شوند تا مشکل‌دارترین اسکریپت‌ها شناسایی شوند. این در مواردی که تم‌ها یا افزونه‌های ایجاد کننده مشکلات عملکرد در چندین سایت استفاده می‌شوند، مفید است.

زمان‌های اجرای اسکریپت‌های رایج (یا منابع شخص ثالث) در LoAFها می‌تواند جمع‌بندی شده و به عنوان مشارکت‌کنندگان رایج در LoAFها در یک سایت یا مجموعه‌ای از سایت‌ها گزارش شود.

به عنوان مثال، برای گروه‌بندی اسکریپت‌ها بر اساس URL و نمایش مدت زمان کل:

```js
const observer = new PerformanceObserver((list) => {
  const allScripts = list.getEntries().flatMap((entry) => entry.scripts);
  const scriptSource = [
    ...new Set(allScripts.map((script) => script.sourceURL)),
  ];
  const scriptsBySource = scriptSource.map((sourceURL) => [
    sourceURL,
    allScripts.filter((script) => script.sourceURL === sourceURL),
  ]);
  const processedScripts = scriptsBySource.map(([sourceURL, scripts]) => ({
    sourceURL,
    count: scripts.length,
    totalDuration: scripts.reduce(
      (subtotal, script) => subtotal + script.duration,
      0,
    ),
  }));
  processedScripts.sort((a, b) => b.totalDuration - a.totalDuration);
  // مثال در اینجا در کنسول ثبت می‌کند؛ کد واقعی می‌تواند به نقطه پایانی تحلیلی ارسال کند
  console.table(processedScripts);
});

observer.observe({ type: "long-animation-frame", buffered: true });
```

## مقایسه با Long Tasks API

Long Animation Frames API توسط [Long Tasks API](https://w3c.github.io/longtasks/) (به {{domxref("PerformanceLongTaskTiming")}} مراجعه کنید) پیشی گرفته است. هر دو API هدف و کاربرد مشابهی دارند — افشای اطلاعات درباره [وظایف طولانی](/en-US/docs/Glossary/Long_task) که نخ اصلی را به مدت ۵۰ میلی‌ثانیه یا بیشتر مسدود می‌کنند.

کاهش تعداد وظایف طولانی که در وب‌سایت شما رخ می‌دهد مفید است زیرا وظایف طولانی می‌توانند مشکلات پاسخ‌دهی ایجاد کنند. به عنوان مثال، اگر کاربر در حالی که نخ اصلی در حال پردازش یک وظیفه طولانی است، روی دکمه‌ای کلیک کند، پاسخ UI به کلیک تا زمانی که وظیفه طولانی کامل شود، به تأخیر می‌افتد. خرد متعارف این است که وظایف طولانی را به چندین وظیفه کوچکتر تقسیم کنید تا تعاملات مهم بتوانند در بین آن‌ها مدیریت شوند.

با این حال، Long Tasks API محدودیت‌هایی دارد:

- یک فریم انیمیشن می‌تواند از چندین وظیفه تشکیل شده باشد که هر کدام زیر آستانه ۵۰ میلی‌ثانیه هستند، اما همچنان به طور جمعی نخ اصلی را مسدود می‌کنند. Long Animation Frames API این مشکل را با در نظر گرفتن فریم انیمیشن به عنوان یک کل حل می‌کند.
- نوع ورودی {{domxref("PerformanceLongTaskTiming")}} اطلاعات محدودتری نسبت به نوع {{domxref("PerformanceLongAnimationFrameTiming")}} افشا می‌کند — به عنوان مثال، می‌تواند کانتینری را که یک وظیفه طولانی در آن رخ داده است بگوید، اما نه اسکریپت یا تابعی که باعث آن شده است را.
- Long Tasks API یک دید ناقص ارائه می‌دهد، زیرا ممکن است برخی وظایف مهم را حذف کند. برخی به‌روزرسانی‌ها (رندرینگ، به عنوان مثال) در وظایف جداگانه‌ای رخ می‌دهند که باید به همراه اجرای قبلی که باعث آن به‌روزرسانی شده است، برای اندازه‌گیری دقیق "کل کار" برای آن تعامل، شامل شوند.

## همچنین ببینید

- [بهینه‌سازی وظایف طولانی](https://web.dev/articles/optimize-long-tasks) در web.dev (۲۰۲۴)
- [جایی که وظایف طولانی کوتاه می‌آیند](https://github.com/w3c/long-animation-frames#where-long-tasks-fall-short)، توضیح‌دهنده Long Animation Frames API (۲۰۲۴)