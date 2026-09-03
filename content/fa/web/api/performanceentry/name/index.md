---
title: "PerformanceEntry: name property"
short-title: name
slug: Web/API/PerformanceEntry/name
page-type: web-api-instance-property
browser-compat: api.PerformanceEntry.name
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

ویژگی فقط خواندنی **`name`** در رابط {{domxref("PerformanceEntry")}} یک رشته است که نام یک ورودی عملکرد را نشان می‌دهد. این ویژگی به‌عنوان یک شناسه عمل می‌کند، اما لزوماً یکتا نیست. مقدار آن به زیرکلاس (subclass) بستگی دارد.

## مقدار

یک رشته. مقدار آن به زیرکلاس شیء `PerformanceEntry` بستگی دارد، همان‌طور که در جدول زیر نشان داده شده است.

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">زیرکلاس</th>
      <th scope="col">مقدار</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>{{domxref('InteractionContentfulPaint')}}</td>
      <td>همیشه یک رشتهٔ خالی برمی‌گرداند.</td>
    </tr>
    <tr>
      <td>{{domxref('LargestContentfulPaint')}}</td>
      <td>همیشه یک رشتهٔ خالی برمی‌گرداند.</td>
    </tr>
    <tr>
      <td>{{domxref('LayoutShift')}}</td>
      <td>همیشه <code>"layout-shift"</code> را برمی‌گرداند.</td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceElementTiming')}}</td>
      <td>یکی از رشته‌های زیر:
        <ul>
          <li><code>"image-paint"</code></li>
          <li><code>"text-paint"</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceEventTiming')}}</td>
      <td>نوع رویداد مرتبط.</td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceLongAnimationFrameTiming')}}</td>
      <td>همیشه <code>"long-animation-frame"</code> را برمی‌گرداند.</td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceLongTaskTiming')}}</td>
      <td>یکی از رشته‌های زیر:
        <ul>
          <li><code>"cross-origin-ancestor"</code></li>
          <li><code>"cross-origin-descendant"</code></li>
          <li><code>"cross-origin-unreachable"</code></li>
          <li><code>"multiple-contexts"</code></li>
          <li><code>"same-origin-ancestor"</code></li>
          <li><code>"same-origin-descendant"</code></li>
          <li><code>"same-origin"</code></li>
          <li><code>"self"</code></li>
          <li><code>"unknown"</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceMark')}}</td>
      <td>
        نامی که هنگام ایجاد نشانه (mark) با فراخوانی
        {{domxref("Performance.mark","performance.mark()")}} استفاده شده است.
      </td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceMeasure')}}</td>
      <td>
        نامی که هنگام ایجاد اندازه‌گیری (measure) با فراخوانی
        {{domxref("Performance.measure","performance.measure()")}} استفاده شده است.
      </td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceNavigationTiming')}}</td>
      <td>URL تفکیک‌شدهٔ منبع درخواست‌شده.
      توجه کنید که این مقدار شامل هیچ <a href="/en-US/docs/Web/URI/Reference/Fragment/Text_fragments">قطعه‌متن (text fragment)</a> یا دیگر دستورالعمل‌های قطعه (fragment directives) نمی‌شود.
      این مقدار حتی اگر درخواست تغییر مسیر داده شود نیز تغییر نمی‌کند.
      </td>
    </tr>
    <tr>
      <td>{{domxref('PerformancePaintTiming')}}</td>
      <td>یکی از رشته‌های زیر:
        <ul>
          <li><code>"first-paint"</code></li>
          <li><code>"first-contentful-paint"</code></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceResourceTiming')}}</td>
      <td>URL تفکیک‌شدهٔ منبع درخواست‌شده. این مقدار حتی اگر درخواست تغییر مسیر داده شود نیز تغییر نمی‌کند.</td>
    </tr>
    <tr>
      <td>{{domxref('PerformanceSoftNavigation')}}</td>
      <td>URL جدیدی که به آن ناوبری شده است.</td>
    </tr>
    <tr>
      <td>{{domxref('TaskAttributionTiming')}}</td>
      <td>همیشه <code>"unknown"</code> را برمی‌گرداند.</td>
    </tr>
    <tr>
      <td>{{domxref('VisibilityStateEntry')}}</td>
      <td>یکی از رشته‌های زیر:
        <ul>
          <li><code>"visible"</code></li>
          <li><code>"hidden"</code></li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## مثال‌ها

### فیلتر کردن ورودی‌های عملکرد بر اساس نام

وقتی `PerformanceEntry` یک شیء {{domxref('PerformanceResourceTiming')}} باشد، ویژگی `name` به URL تفکیک‌شدهٔ منبع درخواست‌شده اشاره دارد. در این حالت، ویژگی `name` می‌تواند برای فیلتر کردن منابع خاص، مثلاً همهٔ تصاویر SVG، مفید باشد.

```js
// ثبت مدت‌زمان منابع SVG
performance.getEntriesByType("resource").forEach((entry) => {
  if (entry.name.endsWith(".svg")) {
    console.log(`${entry.name}'s duration: ${entry.duration}`);
  }
});
```

### دریافت ورودی‌های عملکرد بر اساس نام

هر دو {{domxref("Performance")}} و {{domxref("PerformanceObserver")}} روش‌هایی ارائه می‌دهند که به شما امکان می‌دهند ورودی‌های عملکرد را مستقیماً بر اساس نام دریافت کنید. لزوماً به ویژگی `name` برای این کار نیاز ندارید، در عوض می‌توانید از {{domxref("Performance.getEntriesByName()")}} یا {{domxref("PerformanceObserverEntryList.getEntriesByName()")}} استفاده کنید.

```js
// ثبت تمام نشانه‌هایی به نام "debug-marks" در این نقطه از زمان
const debugMarks = performance.getEntriesByName("debug-mark", "mark");
debugMarks.forEach((entry) => {
  console.log(`${entry.name}'s startTime: ${entry.startTime}`);
});

// نسخهٔ PerformanceObserver
// ثبت تمام نشانه‌هایی به نام "debug-marks" هنگام وقوع
function perfObserver(list, observer) {
  list.getEntriesByName("debug-mark", "mark").forEach((entry) => {
    console.log(`${entry.name}'s startTime: ${entry.startTime}`);
  });
}
const observer = new PerformanceObserver(perfObserver);
observer.observe({ entryTypes: ["measure", "mark"] });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Performance.getEntriesByName()")}}
- {{domxref("PerformanceObserverEntryList.getEntriesByName()")}}