---
title: "console: timeStamp() static method"
short-title: timeStamp()
slug: Web/API/console/timeStamp_static
page-type: web-api-static-method
status:
  - non-standard
browser-compat: api.console.timeStamp_static
---

{{APIRef("Console API")}}{{Non-standard_header}} {{AvailableInWorkers}}

متد استاتیک **`console.timeStamp()`** یک نشانه‌گذار (marker) واحد به ابزار Performance مرورگر اضافه می‌کند ([باگ فایرفاکس 1387528](https://bugzil.la/1387528)، [کروم](https://developer.chrome.com/docs/devtools/performance/reference)). این به شما امکان می‌دهد یک نقطه در کد خود را با سایر رویدادهای ثبت‌شده در خط زمانی (timeline) مانند رویدادهای layout و paint مرتبط کنید.

شما می‌توانید به صورت اختیاری یک آرگومان برای برچسب‌گذاری timestamp ارائه دهید و این برچسب در کنار نشانه‌گذار نمایش داده می‌شود.

برخی مرورگرها این متد `console.timeStamp()` را بیشتر گسترش داده‌اند تا امکان ارائه پارامترهای اختیاری اضافی به عنوان بخشی از API توسعه‌پذیری (extensibility API) خود فراهم کنند که این موارد را در ردیابی‌های عملکرد (performance traces) نمایش می‌دهد. برای اطلاعات بیشتر به [مستندات API توسعه‌پذیری کروم](https://developer.chrome.com/docs/devtools/performance/extension#inject_your_data_with_consoletimestamp) مراجعه کنید.

## Syntax

```js-nolint
console.timeStamp(label);
console.timeStamp(label, start, end, trackName, trackGroup, color, data);
```

### Parameters

- `color` {{Optional_Inline}} {{Experimental_Inline}}
  - : یک رشته برای رنگ نمایش ورودی. باید یکی از `"primary"`, `"primary-light"`, `"primary-dark"`, `"secondary"`, `"secondary-light"`, `"secondary-dark"`, `"tertiary"`, `"tertiary-light"`, `"tertiary-dark"`, `"error"` باشد.

- `data` {{Optional_Inline}} {{Experimental_Inline}}
  - : یک شیء با داده‌های اضافی برای نمایش. URLها ممکن است به طور خودکار توسط برخی مرورگرها به پیوند تبدیل شوند.

> [!NOTE]
> پشتیبانی از پارامتر `data` در مرورگرها و پیاده‌سازی‌های DevTools آنها متفاوت است. به عنوان مثال، در برخی نسخه‌های کروم، این داده ممکن است در پنل Performance ظاهر نشود.

- `end` {{Optional_Inline}} {{Experimental_Inline}}
  - : یک رشته که به یک برچسب `timeStamp` تعریف‌شده قبلی یا یک timestamp ({{domxref("DOMHighResTimeStamp")}}) اشاره می‌کند و به عنوان زمان پایان استفاده می‌شود.

- `label` {{Optional_Inline}}
  - : برچسب برای timestamp.

- `start` {{Optional_Inline}} {{Experimental_Inline}}
  - : یک رشته که به یک برچسب `timeStamp` تعریف‌شده قبلی یا یک timestamp ({{domxref("DOMHighResTimeStamp")}}) اشاره می‌کند و به عنوان زمان شروع استفاده می‌شود.

- `trackName` {{Optional_Inline}} {{Experimental_Inline}}
  - : نام ردیف سفارشی (custom track) که برای نمایش داده‌های timestamp استفاده می‌شود.

- `trackGroup` {{Optional_Inline}} {{Experimental_Inline}}
  - : گروه ردیف سفارشی که برای نمایش داده‌های timestamp استفاده می‌شود.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

### استفاده پایه

```js
console.timeStamp("marker 1");
```

### استفاده از API توسعه‌پذیری برای ارائه جزئیات غنی‌تر برای نمایش

```js
// 1. Create a duration event with rich data
const start = performance.now() - 150;
const end = performance.now() - 20;

const durationData = {
  processingTime: `${end - start}ms`,
  info: "Check this URL: https://example.com for more.",
  metrics: {
    items: 5,
    isCached: true,
  },
};

console.timeStamp(
  "My Timed Task", // label
  start, // startTime
  end, // endTime
  "Tasks", // trackName
  "My Extension", // trackGroup
  "tertiary", // color
  durationData, // data (object)
);

// 2. Create an instant event with a deep link for a DevTools extension
const linkData = {
  url: "ext://resource/123",
  description: "View Resource 123",
  otherDetail: "This data also appears in the JSON viewer",
};

console.timeStamp(
  "Event with Link", // label
  performance.now(), // startTime (instant)
  undefined, // endTime (instant)
  "Tasks", // trackName
  "My Extension", // trackGroup
  "primary-light", // color
  linkData, // data (object),
);
```

## Browser compatibility

{{Compat}}

## See also

- {{domxref("console/time_static", "console.time()")}}
- {{domxref("console/timeLog_static", "console.timeLog()")}}
- {{domxref("console/timeEnd_static", "console.timeEnd()")}}
- {{domxref("performance/mark", "performance.mark()")}}
- {{domxref("performance/measure", "performance.measure()")}}
- [افزودن نشانه‌گذارها با استفاده از API کنسول](https://web.archive.org/web/20211207010020/https://firefox-source-docs.mozilla.org/devtools-user/performance/waterfall/index.html#adding-markers-with-the-console-api)
- [API توسعه‌پذیری DevTools کروم](https://developer.chrome.com/docs/devtools/performance/extension#inject_your_data_with_consoletimestamp)