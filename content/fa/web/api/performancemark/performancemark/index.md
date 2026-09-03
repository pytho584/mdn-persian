---
title: "PerformanceMark: PerformanceMark() constructor"
short-title: PerformanceMark()
slug: Web/API/PerformanceMark/PerformanceMark
page-type: web-api-constructor
browser-compat: api.PerformanceMark.PerformanceMark
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

سازنده **`PerformanceMark()`** یک {{domxref("DOMHighResTimeStamp","timestamp")}} با نام مشخص‌شده ایجاد می‌کند.

برخلاف {{domxref("Performance.mark","performance.mark()")}}، نشانه‌های عملکرد (performance marks) ایجادشده توسط سازنده به خط زمانی عملکرد (performance timeline) مرورگر اضافه نمی‌شوند. این بدان معناست که فراخوانی‌های متدهای `getEntries*()` در رابط {{domxref("Performance")}} (شامل {{domxref("Performance.getEntries","getEntries()")}}، {{domxref("Performance.getEntriesByName","getEntriesByName()")}} و {{domxref("Performance.getEntriesByType","getEntriesByType()")}}) ورودی‌هایی برای این نشانه‌ها نمایش نخواهند داد.

## Syntax

```js-nolint
new PerformanceMark(name)
new PerformanceMark(name, markOptions)
```

### Parameters

- `name`
  - : یک رشته (string) که نام نشانه را مشخص می‌کند.
- `markOptions` {{optional_inline}}
  - : یک شیء برای مشخص‌کردن یک timestamp و ابرداده (metadata) اضافی برای نشانه.
    - `detail` {{optional_inline}}
      - : ابرداده دلخواه برای گنجاندن در نشانه. پیش‌فرض `null` است.
        - `devtools` {{optional_inline}} {{experimental_inline}}
          - : برخی مرورگرها از یک شیء ساختاریافته `devtools` درون شیء `detail` به عنوان بخشی از یک API توسعه‌پذیری (Extensibility API) استفاده می‌کنند که این موارد را در مسیرهای سفارشی در ردیابی‌های عملکرد (performance traces) نمایش می‌دهد. برای اطلاعات بیشتر به [مستندات API توسعه‌پذیری کروم](https://developer.chrome.com/docs/devtools/performance/extension#inject_your_data_with_the_user_timings_api) مراجعه کنید.
            - `dataType` {{experimental_inline}}
              - : یک رشته که باید روی `marker` تنظیم شود. به عنوان یک نشانه (marker) شناسایی می‌شود.
            - `color` {{optional_inline}} {{experimental_inline}}
              - : پیش‌فرض `"primary"` است. باید یکی از مقادیر `"primary"`, `"primary-light"`, `"primary-dark"`, `"secondary"`, `"secondary-light"`, `"secondary-dark"`, `"tertiary"`, `"tertiary-light"`, `"tertiary-dark"`, `"error"` باشد.
            - `properties` {{optional_inline}} {{experimental_inline}}
              - : آرایه‌ای از جفت‌های کلید-مقدار. مقادیر می‌توانند هر نوع سازگار با JSON باشند.
            - `tooltipText` {{optional_inline}} {{experimental_inline}}
              - : توضیح کوتاه برای tooltip.
    - `startTime` {{optional_inline}}
      - : یک {{domxref("DOMHighResTimeStamp")}} برای استفاده به عنوان زمان نشانه. پیش‌فرض {{domxref("performance.now()")}} است.

### Return value

یک شیء {{domxref("PerformanceMark")}}.

### Exceptions

- {{jsxref("SyntaxError")}}
  - : اگر `name` داده‌شده به این متد از قبل در رابط {{domxref("PerformanceTiming")}} وجود داشته باشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر `startTime` منفی باشد، پرتاب می‌شود.

## Examples

### ایجاد نشانه‌های نام‌دار (named markers)

مثال زیر نشان می‌دهد که چگونه ورودی‌های {{domxref("PerformanceMark")}} ساخته می‌شوند و سپس بخشی از خط زمانی عملکرد مرورگر نیستند.

```js
new PerformanceMark("squirrel");
new PerformanceMark("monkey");
new PerformanceMark("dog");

const allEntries = performance.getEntriesByType("mark");
console.log(allEntries.length);
// 0
```

### API توسعه‌پذیری DevTools

برای مرورگرهایی که از [API توسعه‌پذیری](https://developer.chrome.com/docs/devtools/performance/extension) پشتیبانی می‌کنند، می‌توانید از پارامتر `detail` برای ارائه جزئیات بیشتر در یک شیء `devtools` استفاده کنید که برای نمایش این مورد در پروفایل‌های عملکرد استفاده خواهد شد:

```js
// Marker indicating when the processed image was uploaded
performance.mark("Image Upload", {
  detail: {
    devtools: {
      dataType: "marker",
      color: "secondary",
      properties: [
        ["Image Size", "2.5MB"],
        ["Upload Destination", "Cloud Storage"],
      ],
      tooltipText: "Processed image uploaded",
    },
  },
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Performance.mark","performance.mark()")}}