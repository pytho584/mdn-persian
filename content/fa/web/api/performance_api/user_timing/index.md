---
title: "User timing"
---

---
title: User timing
slug: Web/API/Performance_API/User_timing
page-type: guide
---

{{DefaultAPISidebar("Performance API")}}

زمان‌بندی کاربر (User Timing) بخشی از API عملکرد (Performance API) است و به شما امکان می‌دهد عملکرد برنامه‌ها را با استفاده از [برچسب‌های زمانی با دقت بالا](/en-US/docs/Web/API/DOMHighResTimeStamp) که بخشی از جدول زمانی عملکرد مرورگر هستند، اندازه‌گیری کنید. دو نوع ورودی عملکرد زمانی وجود دارد:

- ورودی‌های {{domxref("PerformanceMark")}} نشانه‌هایی هستند که می‌توانید نام‌گذاری کرده و در هر نقطه‌ای از برنامه اضافه کنید.
- ورودی‌های {{domxref("PerformanceMeasure")}} اندازه‌گیری‌های زمانی بین دو نشانه هستند.

## زمان‌بندی کاربر چیست؟

مرورگر اطلاعات خاصی (به نام _ورودی‌های عملکرد_) را در جدول زمانی عملکرد مرورگر برای شما فراهم می‌کند. این شامل، برای مثال، ورودی‌هایی است که توسط [Resource Timing API](/en-US/docs/Web/API/Performance_API/Resource_timing) ارائه می‌شوند و زمان لازم برای دریافت یک منبع مانند تصویر را تعیین می‌کنند.

با این حال، مرورگر نمی‌تواند تعیین کند که در برنامه شما چه اتفاقی می‌افتد. مثلاً وقتی کاربر روی دکمه‌ای کلیک می‌کند یا کار خاصی را در برنامه شما انجام می‌دهد، هیچ اندازه‌گیری عملکرد با دقت بالا وجود ندارد. User Timing API یک افزونه برای جدول زمانی عملکرد مرورگر است و به شما کمک می‌کند داده‌های عملکردی را که مخصوص برنامه شما هستند اندازه‌گیری و ثبت کنید.

مزیت استفاده از این API نسبت به فراخوانی {{jsxref("Date.now()")}} یا {{domxref("performance.now()")}} این است که می‌توانید به نشانه‌ها نام بدهید و با ابزارهای تحلیل عملکرد به خوبی یکپارچه می‌شود. ابزارهای توسعه‌دهنده مرورگر می‌توانند نشانه‌های عملکرد را در پنل‌های عملکرد نمایش دهند و همچنین با سایر APIهای عملکرد مانند اشیاء {{domxref("PerformanceObserver")}} کار می‌کند.

## افزودن نشانه‌های عملکرد

به عنوان اولین قدم برای شروع اندازه‌گیری عملکرد قابلیت‌های برنامه خود، باید نشانه‌های عملکرد نام‌گذاری شده را در مکان‌های مهم کد خود اضافه کنید. در حالت ایده‌آل، کد خود را مرور می‌کنید و مسیرهای بحرانی و وظایف مهمی را که می‌خواهید از سرعت اجرای آن‌ها مطمئن شوید، تعیین می‌کنید.

از متد {{domxref("Performance.mark","performance.mark()")}} برای ایجاد یک {{domxref("PerformanceMark")}} استفاده می‌شود. این متد یک آرگومان به نام `name` (نام نشانه) می‌گیرد، همانطور که در مثال زیر نشان داده شده است.

```js
// در قسمتی از کد که ورود شروع می‌شود قرار دهید
performance.mark("login-started");

// در قسمتی از کد که ورود پایان می‌یابد قرار دهید
performance.mark("login-finished");
```

اگر آرگومان `name` کافی نباشد، می‌توان متد `mark()` را با استفاده از یک شیء پیکربندی تنظیم کرد که در آن می‌توانید اطلاعات اضافی را در ویژگی `detail` قرار دهید که می‌تواند از هر نوعی باشد. همچنین می‌توانید در صورت نیاز مقدار `startTime` متفاوتی تنظیم کنید. در کد زیر، `startTime` برابر `12.5` تنظیم شده است و اطلاعات اضافی مانند عنصر HTML استفاده‌شده از طریق `detail` ارائه می‌شود.

```js
performance.mark("login-started", {
  startTime: 12.5,
  detail: { htmlElement: myElement.id },
});
```

## اندازه‌گیری مدت زمان بین نشانه‌ها

حال که نشانه‌ها را به برنامه خود اضافه کرده‌اید، می‌توانید زمان بین آن‌ها را اندازه‌گیری کنید.

از متد {{domxref("Performance.measure()")}} برای ایجاد یک شیء {{domxref("PerformanceMeasure")}} استفاده می‌شود. این متد یک پارامتر `name` می‌گیرد که برای شناسایی اندازه‌گیری استفاده می‌شود و دو نشانه با نام‌های `start` و `end` که باید بین آن‌ها اندازه‌گیری کند. مثال زیر یک اندازه‌گیری به نام «مدت ورود» (login-duration) ایجاد می‌کند و بین شروع و پایان فرآیند ورود اندازه‌گیری می‌کند.

سپس شیء دارای ویژگی `duration` است که تفاوت زمانی بین نشانه پایان و نشانه شروع را برای شما محاسبه می‌کند. برای مثال، می‌توانید این مقدار را ثبت (log) کنید یا به یک نقطه پایانی تحلیلی ارسال کنید.

```js
const loginMeasure = performance.measure(
  "login-duration",
  "login-started",
  "login-finished",
);

console.log(loginMeasure.duration);
```

متد {{domxref("Performance.measure()")}} نیز با استفاده از یک شیء پیکربندی قابل تنظیم است، بنابراین می‌توانید اندازه‌گیری‌های پیشرفته‌تری انجام دهید یا اطلاعات اضافی را از طریق ویژگی `detail` فراهم کنید.

برای مثال، می‌توانید از ویژگی [`event.timestamp`](/en-US/docs/Web/API/Event/timeStamp) از یک [رویداد کلیک](/en-US/docs/Web/API/Element/click_event) استفاده کنید تا دقیقاً زمان کلیک کاربر روی ورود را بدانید و آن را تا نقطه‌ای که رابط کاربری به‌روزرسانی می‌شود اندازه‌گیری کنید، که در اینجا نشانه «پایان ورود» (`login-finished`) است.

```js
loginButton.addEventListener("click", (clickEvent) => {
  fetch(loginURL).then((data) => {
    renderLoggedInUser(data);

    const marker = performance.mark("login-finished");

    performance.measure("login-click", {
      detail: { htmlElement: myElement.id },
      start: clickEvent.timeStamp,
      end: marker.startTime,
    });
  });
});
```

## نظارت بر اندازه‌گیری‌های عملکرد

روش ترجیحی برای دریافت اطلاع از اندازه‌گیری‌های عملکرد سفارشی خود، استفاده از اشیاء {{domxref("PerformanceObserver")}} است. ناظران عملکرد به شما امکان می‌دهند به صورت غیرفعال (passive) در هنگام وقوع، نشانه‌های عملکرد و اندازه‌گیری‌ها را دنبال کنید.

```js
function perfObserver(list, observer) {
  list.getEntries().forEach((entry) => {
    if (entry.entryType === "mark") {
      console.log(`${entry.name}'s startTime: ${entry.startTime}`);
    }
    if (entry.entryType === "measure") {
      console.log(`${entry.name}'s duration: ${entry.duration}`);
    }
  });
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ entryTypes: ["measure", "mark"] });
```

برای اطلاعات بیشتر، به {{domxref("PerformanceObserver")}} مراجعه کنید.

## بازیابی نشانه‌ها و اندازه‌گیری‌ها

ورودی‌های عملکرد مختلفی در جدول زمانی عملکرد مرورگر وجود دارد. برخی توسط مرورگر اضافه می‌شوند و برخی ممکن است توسط شما اضافه شوند، مانند نشانه‌ها و اندازه‌گیری‌های ورود در مثال‌های بالا.

برای بازیابی نشانه‌ها و اندازه‌گیری‌های عملکرد در یک نقطه زمانی خاص، رابط {{domxref("Performance")}} سه روش ارائه می‌دهد، همانطور که در زیر نشان داده شده است.

> [!NOTE]
> روش‌های زیر شما را از وجود نشانه‌های عملکرد جدید مطلع نمی‌کنند؛ شما فقط نشانه‌هایی را دریافت می‌کنید که هنگام فراخوانی این روش‌ها ایجاد شده‌اند.
> برای دریافت اعلان در مورد معیارهای جدید به محض در دسترس شدن، به بخش [نظارت بر اندازه‌گیری‌های عملکرد](#observing_performance_measures) در بالا مراجعه کنید. معمولاً استفاده از ناظران عملکرد روش ترجیحی برای دریافت نشانه‌ها و اندازه‌گیری‌های عملکرد است.

متد {{domxref("Performance.getEntries","performance.getEntries()")}} همه ورودی‌های عملکرد را دریافت می‌کند. می‌توانید آن‌ها را در صورت نیاز فیلتر کنید.

```js
const entries = performance.getEntries();
entries.forEach((entry) => {
  if (entry.entryType === "mark") {
    console.log(`${entry.name}'s startTime: ${entry.startTime}`);
  }
  if (entry.entryType === "measure") {
    console.log(`${entry.name}'s duration: ${entry.duration}`);
  }
});
```

متد {{domxref("Performance.getEntriesByType","performance.getEntriesByType(entryType)")}} ورودی‌ها را از قبل بر اساس نوع فیلتر می‌کند.

```js
const marks = performance.getEntriesByType("mark");
marks.forEach((entry) => {
  console.log(`${entry.name}'s startTime: ${entry.startTime}`);
});

const measures = performance.getEntriesByType("measure");
measures.forEach((entry) => {
  console.log(`${entry.name}'s duration: ${entry.duration}`);
});
```

متد {{domxref("Performance.getEntriesByName","performance.getEntriesByName(name, entryType)")}} به شما امکان می‌دهد نشانه‌ها یا اندازه‌گیری‌های خاصی را بر اساس نام دریافت کنید.

```js
// ثبت همه نشانه‌های با نام "debug-mark"
const debugMarks = performance.getEntriesByName("debug-mark", "mark");
debugMarks.forEach((entry) => {
  console.log(`${entry.name}'s startTime: ${entry.startTime}`);
});
```

## حذف نشانه‌ها و اندازه‌گیری‌ها

برای پاک‌سازی همه نشانه‌ها یا اندازه‌گیری‌های عملکرد، یا فقط ورودی‌های خاص، روش‌های زیر در دسترس هستند:

- [`performance.clearMarks()`](/en-US/docs/Web/API/Performance/clearMarks)
- [`performance.clearMeasures()`](/en-US/docs/Web/API/Performance/clearMeasures)

```js
// پاک کردن همه نشانه‌ها
performance.clearMarks();

// حذف نشانه با نام "myMarker"
performance.clearMarks("myMarker");

// پاک کردن همه اندازه‌گیری‌ها
performance.clearMeasures();

// حذف اندازه‌گیری با نام "myMeasure"
performance.clearMeasures("myMeasure");
```

## همچنین ببینید

- {{domxref("Performance")}}
- {{domxref("PerformanceMark")}}
- {{domxref("PerformanceMeasure")}}
- {{domxref("PerformanceEntry")}}
- {{domxref("PerformanceObserver")}}