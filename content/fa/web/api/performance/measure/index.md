---
title: "Performance: measure() method"
short-title: measure()
slug: Web/API/Performance/measure
page-type: web-api-instance-method
browser-compat: api.Performance.measure
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

متد **`measure()`** یک شیء {{domxref("PerformanceMeasure")}} نام‌گذاری‌شده ایجاد می‌کند که اندازه‌گیری زمان بین دو نشان (mark) را در خط زمانی عملکرد مرورگر نمایش می‌دهد.

هنگام اندازه‌گیری بین دو نشان، به ترتیب یک _نشان شروع_ و یک _نشان پایان_ وجود دارد.
مهر زمانی نام‌گذاری‌شده به عنوان _اندازه‌گیری (measure)_ شناخته می‌شود.

## نحو (Syntax)

```js-nolint
measure(measureName)
measure(measureName, startMark)
measure(measureName, startMark, endMark)
measure(measureName, measureOptions)
measure(measureName, measureOptions, endMark)
```

اگر فقط `measureName` مشخص شود، زمان شروع برابر صفر قرار می‌گیرد و زمان پایان (که برای محاسبه مدت‌زمان استفاده می‌شود) مقداری است که توسط {{domxref("Performance.now()")}} برگردانده می‌شود.

می‌توانید از رشته‌ها برای شناسایی اشیاء {{domxref("PerformanceMark")}} به عنوان نشان‌های شروع و پایان استفاده کنید.

برای ارائه فقط یک `endMark`، باید یک شیء `measureOptions` خالی ارائه دهید:
`performance.measure("myMeasure", {}, "myEndMarker")`.

### پارامترها

- `measureName`
  - : رشته‌ای که نام اندازه‌گیری را نشان می‌دهد.

- `measureOptions` {{optional_inline}}
  - : شیءای که ممکن است شامل گزینه‌های اندازه‌گیری باشد.
    - `detail` {{optional_inline}}
      - : ابرداده دلخواه که در اندازه‌گیری گنجانده می‌شود. پیش‌فرض `null` است. باید [قابل شبیه‌سازی ساختاریافته (structured-cloneable)](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) باشد.
        - `devtools`
          - : برخی مرورگرها از یک شیء `devtools` ساختاریافته در داخل شیء `detail` به عنوان بخشی از یک API قابلیت توسعه (Extensibility API) استفاده می‌کنند که این داده‌ها را در مسیرهای سفارشی در پروفایل‌های عملکرد نمایش می‌دهد. برای اطلاعات بیشتر به [مستندات API قابلیت توسعه Chrome](https://developer.chrome.com/docs/devtools/performance/extension#inject_your_data_with_the_user_timings_api) مراجعه کنید.
            - `dataType` {{experimental_inline}}
              - : رشته‌ای با مقدار `track-entry` (برای تعریف یک مسیر جدید) یا `marker` (برای تعریف یک ورودی در یک مسیر).
            - `color` {{optional_inline}} {{experimental_inline}}
              - : پیش‌فرض `"primary"` است. باید یکی از مقادیر `"primary"`, `"primary-light"`, `"primary-dark"`, `"secondary"`, `"secondary-light"`, `"secondary-dark"`, `"tertiary"`, `"tertiary-light"`, `"tertiary-dark"`, `"error"` باشد.
            - `track` {{optional_inline}} {{experimental_inline}}
              - : رشته‌ای شامل نام مسیر سفارشی (برای `track-entry` الزامی است)
            - `trackGroup` {{optional_inline}} {{experimental_inline}}
              - : رشته‌ای شامل نام گروه‌بندی در یک مسیر سفارشی (برای `track-entry` الزامی است)
            - `properties` {{optional_inline}} {{experimental_inline}}
              - : آرایه‌ای از جفت‌های کلید-مقدار. مقادیر می‌توانند هر نوع سازگار با JSON باشند.
            - `tooltipText` {{optional_inline}} {{experimental_inline}}
              - : توضیح کوتاه برای راهنمای ابزار (tooltip).

    - `start` {{optional_inline}}
      - : مهر زمانی ({{domxref("DOMHighResTimeStamp")}}) که به عنوان زمان شروع استفاده می‌شود، یا رشته‌ای که نام یک {{domxref("PerformanceMark")}} را برای زمان شروع مشخص می‌کند.

        اگر این یک رشته باشد که نام یک {{domxref("PerformanceMark")}} است، همانند `startMark` تعریف می‌شود.

    - `duration` {{optional_inline}}
      - : مدت‌زمان (به میلی‌ثانیه) بین زمان‌های نشان شروع و پایان. اگر حذف شود، پیش‌فرض آن {{domxref("performance.now()")}} است؛ یعنی زمانی که از ایجاد context گذشته است. اگر ارائه شود، باید `start` یا `end` را نیز مشخص کنید اما نه هر دو را.

    - `end` {{optional_inline}}
      - : مهر زمانی ({{domxref("DOMHighResTimeStamp")}}) که به عنوان زمان پایان استفاده می‌شود، یا رشته‌ای که نام یک {{domxref("PerformanceMark")}} را برای زمان پایان مشخص می‌کند.

        اگر این یک رشته باشد که نام یک {{domxref("PerformanceMark")}} است، همانند `endMark` تعریف می‌شود.

- `startMark` {{optional_inline}}
  - : رشته‌ای که نام یک {{domxref("PerformanceMark")}} را در خط زمانی عملکرد مشخص می‌کند. ویژگی {{domxref("PerformanceEntry.startTime")}} این نشان برای محاسبه اندازه‌گیری استفاده خواهد شد.

- `endMark` {{optional_inline}}
  - : رشته‌ای که نام یک {{domxref("PerformanceMark")}} را در خط زمانی عملکرد مشخص می‌کند. ویژگی {{domxref("PerformanceEntry.startTime")}} این نشان برای محاسبه اندازه‌گیری استفاده خواهد شد.
    اگر می‌خواهید این آرگومان را ارسال کنید، باید `startMark` یا یک شیء `measureOptions` خالی نیز ارسال کنید.

### مقدار بازگشتی

ورودی {{domxref("PerformanceMeasure")}} که ایجاد شده است.

_اندازه‌گیری_ بازگشتی مقادیر ویژگی زیر را خواهد داشت:

- {{domxref("PerformanceEntry.entryType","entryType")}} - برابر با `"measure"` تنظیم می‌شود.
- {{domxref("PerformanceEntry.name","name")}} - برابر با آرگومان `name` تنظیم می‌شود.
- {{domxref("PerformanceEntry.startTime","startTime")}} - به یکی از موارد زیر تنظیم می‌شود:
  - یک {{domxref("DOMHighResTimeStamp","timestamp")}}، اگر در `measureOptions.start` مشخص شده باشد.
  - {{domxref("DOMHighResTimeStamp","timestamp")}} یک نشان شروع، اگر در `measureOptions.start` یا `startMark` مشخص شده باشد.
  - مهر زمانی محاسبه‌شده از `measureOptions.end` و `measureOptions.duration` (اگر `measureOptions.start` مشخص نشده باشد)
  - 0، اگر مشخص نشده باشد و نتوان از مقادیر دیگر تعیین کرد.

- {{domxref("PerformanceEntry.duration","duration")}} - به یک {{domxref("DOMHighResTimeStamp")}} تنظیم می‌شود که مدت‌زمان اندازه‌گیری با کم کردن `startTime` از مهر زمانی پایان محاسبه می‌شود.

  مهر زمانی پایان یکی از موارد زیر است:
  - یک {{domxref("DOMHighResTimeStamp","timestamp")}}، اگر در `measureOptions.end` مشخص شده باشد.
  - {{domxref("DOMHighResTimeStamp","timestamp")}} یک نشان پایان، اگر در `measureOptions.end` یا `endMark` مشخص شده باشد.
  - مهر زمانی محاسبه‌شده از `measureOptions.start` و `measureOptions.duration` (اگر `measureOptions.end` مشخص نشده باشد)
  - مقدار بازگشتی {{domxref("Performance.now()")}}، اگر هیچ نشان پایانی مشخص نشده باشد یا نتوان از مقادیر دیگر تعیین کرد.

- {{domxref("PerformanceMeasure","detail")}} - برابر با مقدار ارسال‌شده در `measureOptions` تنظیم می‌شود.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : این خطا در هر حالتی که شروع، پایان یا مدت‌زمان ممکن است مبهم باشد پرتاب می‌شود:
    - هر دو `endMark` و `measureOptions` مشخص شده باشند.
    - `measureOptions` با `duration` مشخص شده باشد اما بدون تعیین `start` یا `end`.
    - `measureOptions` با هر سه `start`، `end` و `duration` مشخص شده باشد.

- `SyntaxError` {{domxref("DOMException")}}
  - : نشان نام‌برده وجود ندارد.
    - یک نشان پایان با استفاده از `endMark` یا `measureOptions.end` مشخص شده باشد، اما هیچ {{domxref('PerformanceMark')}} با نام منطبق در بافر عملکرد وجود نداشته باشد.
    - یک نشان پایان با استفاده از `endMark` یا `measureOptions.end` مشخص شده باشد، اما نتوان آن را به ویژگی فقط‌خواندنی در رابط {{domxref("PerformanceTiming")}} تبدیل کرد.
    - یک نشان شروع با استفاده از `startMark` یا `measureOptions.start` مشخص شده باشد، اما هیچ {{domxref('PerformanceMark')}} با نام منطبق در بافر عملکرد وجود نداشته باشد.
    - یک نشان شروع با استفاده از `startMark` یا `measureOptions.start` مشخص شده باشد، اما نتوان آن را به ویژگی فقط‌خواندنی در رابط {{domxref("PerformanceTiming")}} تبدیل کرد.

- `DataCloneError` {{domxref("DOMException")}}
  - : مقدار `measureOptions.detail` غیر از `null` باشد و نتوان با استفاده از الگوریتم "StructuredSerialize" در HTML سری‌سازی کرد.

- {{jsxref("RangeError")}}
  - : مقدار `measureOptions.detail` غیر از `null` باشد و حافظه در طول سری‌سازی با استفاده از الگوریتم "StructuredSerialize" در HTML قابل تخصیص نباشد.

## مثال‌ها

### اندازه‌گیری مدت‌زمان بین نشانگرهای نام‌گذاری‌شده

با دو نشانگر سفارشی خود مانند `"login-started"` و `"login-finished"`، می‌توانید یک اندازه‌گیری به نام `"login-duration"` ایجاد کنید، همان‌طور که در مثال زیر نشان داده شده است. شیء {{domxref("PerformanceMeasure")}} بازگشتی یک ویژگی `duration` فراهم می‌کند که مدت‌زمان سپری‌شده بین دو نشانگر را نشان می‌دهد.

```js
const loginMeasure = performance.measure(
  "login-duration",
  "login-started",
  "login-finished",
);
console.log(loginMeasure.duration);
```

### اندازه‌گیری مدت‌زمان با زمان‌های شروع و پایان سفارشی

برای اندازه‌گیری‌های پیشرفته‌تر، می‌توانید پارامتر `measureOptions` را ارسال کنید. برای مثال، می‌توانید از ویژگی [`event.timeStamp`](/en-US/docs/Web/API/Event/timeStamp) رویداد [`click`](/en-US/docs/Web/API/Element/click_event) به عنوان زمان شروع استفاده کنید.

```js
performance.measure("login-click", {
  start: myClickEvent.timeStamp,
  end: myMarker.startTime,
});
```

### ارائه جزئیات اضافی اندازه‌گیری

می‌توانید از ویژگی `details` برای ارائه اطلاعات اضافی از هر نوع استفاده کنید. شاید بخواهید ثبت کنید کدام عنصر HTML کلیک شده است، برای مثال.

```js
performance.measure("login-click", {
  detail: { htmlElement: myElement.id },
  start: myClickEvent.timeStamp,
  end: myMarker.startTime,
});
```

### API قابلیت توسعه DevTools

برای مرورگرهایی که از [API قابلیت توسعه](https://developer.chrome.com/docs/devtools/performance/extension) پشتیبانی می‌کنند، می‌توانید از پارامتر `detail` برای ارائه جزئیات بیشتر در یک شیء `devtools` استفاده کنید که برای نمایش این مورد در پروفایل‌های عملکرد استفاده می‌شود:

```js
const imageProcessingTimeStart = performance.now();

// ... بعداً در کد شما

performance.measure("Image Processing Complete", {
  start: imageProcessingTimeStart,
  end: performance.now(),
  detail: {
    // این داده در بخش "Summary" ظاهر می‌شود
    extraInfo: {
      imageId: "xyz-123",
      source: "cache",
      checkUrl: "https://example.com/check/xyz-123",
    },
    // شیء devtools نمایش مسیر را کنترل می‌کند
    devtools: {
      dataType: "track-entry",
      track: "Image Processing Tasks",
      trackGroup: "My Tracks",
      color: "tertiary-dark",
      properties: [
        ["Filter Type", "Gaussian Blur"],
        // مقادیر می‌توانند اشیاء، آرایه‌ها یا انواع دیگر باشند
        ["Resize Dimensions", { w: 500, h: 300 }],
        // مقادیر رشته‌ای که URL هستند به پیوند تبدیل می‌شوند
        ["Image URL", "https://example.com/img.png"],
      ],
      tooltipText: "Image processed successfully",
    },
  },
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}