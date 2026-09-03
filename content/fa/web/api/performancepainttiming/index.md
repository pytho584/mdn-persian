---
title: PerformancePaintTiming
slug: Web/API/PerformancePaintTiming
page-type: web-api-interface
browser-compat: api.PerformancePaintTiming
---

{{APIRef("Performance API")}}

رابط **`PerformancePaintTiming`** اطلاعات زمان‌بندی عملیات «paint» (که «render» نیز نامیده می‌شود) را هنگام ساخت صفحه وب فراهم می‌کند. «paint» به تبدیل درخت رندر به پیکسل‌های روی صفحه اشاره دارد.

دو لحظه کلیدی paint که این API فراهم می‌کند عبارتند از:

- {{Glossary("First Paint")}} (FP): زمانی که هر چیزی رندر می‌شود. توجه داشته باشید که ثبت اولین paint اختیاری است و همه user agentها آن را گزارش نمی‌دهند.
- {{Glossary("First Contentful Paint")}} (FCP): زمانی که نخستین بخش از محتوای متنی یا تصویری DOM رندر می‌شود.

سومین لحظه کلیدی paint توسط API زیر فراهم می‌شود:

- {{Glossary("Largest Contentful Paint")}} (LCP): زمان رندر بزرگ‌ترین تصویر یا بلوک متنی قابل مشاهده در viewport، که از زمانی که صفحه برای نخستین بار شروع به بارگذاری می‌کند ثبت می‌شود.

داده‌های این API به شما کمک می‌کند تا مدت انتظار کاربران برای دیده‌شدن محتوای سایت را به حداقل برسانید. کاهش زمان رسیدن به این لحظات کلیدی paint باعث می‌شود سایت برای کاربران شما واکنش‌گراتر، پربازده‌تر و جذاب‌تر به نظر برسد.

این API مانند سایر APIهای Performance، رابط {{domxref("PerformanceEntry")}} را گسترش می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

این رابط مستقیماً ویژگی‌های زیر را تعریف می‌کند:

- {{domxref("PerformancePaintTiming.paintTime")}}
  - : {{domxref("DOMHighResTimeStamp","timestamp")}} پایان فاز رندر و شروع فاز paint را برمی‌گرداند.
- {{domxref("PerformancePaintTiming.presentationTime")}}
  - : {{domxref("DOMHighResTimeStamp","timestamp")}} زمانی که پیکسل‌های paint‌شده در واقع روی صفحه رسم شدند را برمی‌گرداند.

همچنین ویژگی‌های زیر از {{domxref("PerformanceEntry")}} را گسترش می‌دهد و آن‌ها را به صورت توصیف‌شده محدود و مقید می‌کند:

- {{domxref("PerformanceEntry.entryType")}}
  - : مقدار `"paint"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.name")}}
  - : یکی از مقادیر `"first-paint"` یا `"first-contentful-paint"` را برمی‌گرداند.
- {{domxref("PerformanceEntry.startTime")}}
  - : {{domxref("DOMHighResTimeStamp","timestamp")}} زمان وقوع paint را برمی‌گرداند.
- {{domxref("PerformanceEntry.duration")}}
  - : عدد 0 را برمی‌گرداند.

## متدهای نمونه

- {{domxref("PerformancePaintTiming.toJSON()")}}
  - : یک نمایش JSON از شیء `PerformancePaintTiming` برمی‌گرداند.

## مثال‌ها

### به دست آوردن زمان‌بندی‌های پایه paint

مثالی با استفاده از {{domxref("PerformanceObserver")}} که هنگام ثبت ورودی‌های جدید عملکردی `paint` در خط زمانی عملکرد مرورگر اطلاع می‌دهد. با استفاده از گزینه `buffered` به ورودی‌هایی که قبل از ایجاد observer ثبت شده‌اند دسترسی پیدا کنید.

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    console.log(
      `The time to ${entry.name} was ${entry.startTime} milliseconds.`,
    );
    // Logs "The time to first-paint was 386.7999999523163 milliseconds."
    // Logs "The time to first-contentful-paint was 400.6999999284744 milliseconds."
  });
});

observer.observe({ type: "paint", buffered: true });
```

مثالی با استفاده از {{domxref("Performance.getEntriesByType()")}} که فقط ورودی‌های عملکردی `paint` موجود در خط زمانی عملکرد مرورگر را در زمان فراخوانی این متد نشان می‌دهد:

```js
const entries = performance.getEntriesByType("paint");
entries.forEach((entry) => {
  console.log(`The time to ${entry.name} was ${entry.startTime} milliseconds.`);
  // Logs "The time to first-paint was 386.7999999523163 milliseconds."
  // Logs "The time to first-contentful-paint was 400.6999999284744 milliseconds."
});
```

### به دست آوردن زمان‌بندی‌های جداگانه paint و presentation

ویژگی‌های `paintTime` و `presentationTime` به شما امکان می‌دهند زمان‌بندی‌های خاص شروع فاز paint و رسم پیکسل‌های paint‌شده روی صفحه را بازیابی کنید. `paintTime` به طور گسترده‌ای سازگار است، در حالی که `presentationTime` وابسته به پیاده‌سازی مرورگر است.

این مثال بر پایه مثال قبلی {{domxref("Performance.getEntriesByType()")}} ساخته شده است و نشان می‌دهد چگونه پشتیبانی از `paintTime` و `presentationTime` را بررسی کنید و در صورت موجود بودن این مقادیر را بازیابی کنید. در مرورگرهای بدون پشتیبانی، کد `loadTime` را بازیابی می‌کند.

```js
const entries = performance.getEntriesByType("paint");
entries.forEach((entry) => {
  if (entry.presentationTime) {
    console.log(
      "paintTime:",
      entry.paintTime,
      "presentationTime:",
      entry.presentationTime,
    );
  } else if (entry.paintTime) {
    console.log("paintTime:", entry.paintTime);
  } else {
    console.log("loadTime", entry.loadTime);
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

### همچنین ببینید

- {{domxref("LargestContentfulPaint")}}