---
title: CrashReport
slug: Web/API/CrashReport
page-type: web-api-interface
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.crash
---

{{APIRef("Reporting API")}}

دیکشنری `CrashReport` در [Reporting API](/en-US/docs/Web/API/Reporting_API) نشان‌دهندهٔ یک گزارش خرابی (crash report) است.

> [!NOTE]
> دریافت گزارش‌های خرابی با استفاده از {{domxref("ReportingObserver")}} امکان‌پذیر نیست — این گزارش‌ها تنها زمانی تولید می‌شوند که مرورگر دچار خرابی شود، و در آن لحظه کد observer برای اجرا در دسترس نیست.

## ویژگی‌های نمونه

- `age`
  - : سن گزارش بر حسب میلی‌ثانیه.
- `type`
  - : رشتهٔ `"crash"` که نشان می‌دهد این یک گزارش خرابی است.
- `url`
  - : رشته‌ای که URL سندی که گزارش را تولید کرده است نشان می‌دهد.
- `user_agent`
  - : رشتهٔ user agent مرورگری که گزارش را تولید کرده است.
- `body`
  - : بدنهٔ گزارش.
    این یک شیء با ویژگی‌های زیر است:
    - `crash_report_api` {{experimental_inline}} {{optional_inline}}
      - : شیءای شامل جفت‌های کلید-مقدار که از طریق متد {{domxref("CrashReportContext.set()")}} تنظیم شده‌اند، در صورت وجود.
    - `is_top_level` {{experimental_inline}}
      - : مقدار بولی که نشان می‌دهد آیا سند خراب‌شده یک سند سطح بالا (`true`) بود یا یک سند جاسازی‌شده (`false`).
    - `reason` {{experimental_inline}} {{optional_inline}}
      - : رشته‌ای که دلیل خاص وقوع خرابی را در صورت مشخص بودن نشان می‌دهد. مقادیر ممکن عبارت‌اند از:
        - `oom`
          - : حافظهٔ صفحه تمام شده است.
        - `unresponsive`
          - : صفحه به دلیل عدم پاسخ‌گویی از بین رفته است.
    - `stack` {{experimental_inline}} {{optional_inline}}
      - : رشته‌ای که پشتهٔ فراخوانی جاوااسکریپت را در زمان خرابی نشان می‌دهد. این مورد در صورتی گنجانده می‌شود که `reason` برابر با `unresponsive` باشد، مقدار `Document-Policy` برای `include-js-call-stacks-in-crash-reports` در سند خراب‌شده `true` باشد، و پشتهٔ فراخوانی از سند خراب‌شده قابل بازیابی باشد.
    - `visibility_state` {{experimental_inline}}
      - : مقدار شمارشی که نشان می‌دهد آیا سند قابل مشاهده است. این مقدار با ویژگی {{domxref("Document.visibilityState")}} مطابقت دارد. مقادیر ممکن عبارت‌اند از:
        - `visible`
          - : محتوای سند حداقل تا حدی قابل مشاهده است.
        - `hidden`
          - : محتوای سند کاملاً پنهان است.

## توضیحات

گزارش‌های خرابی حاوی اطلاعات دلخواه را می‌توان با استفاده از [Reporting API](/en-US/docs/Web/API/Reporting_API) به یک سرور گزارش‌دهنده ارسال کرد.
این ویژگی مفید است زیرا می‌توانیم اطلاعات تشخیصی دقیق را در طول عمر یک برنامه ذخیره کنیم و از گزارش‌ها برای اشکال‌زدایی مؤثرتر خرابی‌ها استفاده کنیم.

اطلاعات تشخیصی در یک فروشگاه کلید-مقدار ویژه ذخیره می‌شود که می‌توان آن را از طریق شیء {{domxref("CrashReportContext")}} سند دستکاری کرد.
این شیء از طریق ویژگی {{domxref("Window.crashReport")}} قابل دسترسی است.

هنگامی که مرورگر خراب می‌شود، اطلاعات ذخیره‌شده در فروشگاه کلید-مقدار به یک `CrashReport` اضافه شده و به یک سرور گزارش‌دهنده ارسال می‌شود. نقطهٔ پایانی سرور گزارش‌دهنده و نگاشت آن به یک URL خاص با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تنظیم می‌شود.

- اگر نقطهٔ پایانی سرور `crash-reporting` تعریف شده باشد، گزارش‌های خرابی به آنجا ارسال می‌شوند. برای مثال:
  ```http
  Reporting-Endpoints: crash-reporting="https://example.com/reports"
  ```
- اگر نقطهٔ پایانی `crash-reporting` تعریف نشده باشد، اما یک [نقطهٔ پایانی سرور گزارش‌دهندهٔ `default`](/en-US/docs/Web/HTTP/Reference/Headers/Reporting-Endpoints#default_reporting_endpoint) تعریف شده باشد، گزارش‌های خرابی به آنجا ارسال می‌شوند. برای مثال:
  ```http
  Reporting-Endpoints: default="https://example.com/reports"
  ```
- اگر هیچ نقطهٔ پایانی تعریف نشده باشد، گزارش‌های خرابی ارسال نمی‌شوند.

## مثال‌ها

### ارسال گزارش به یک نقطهٔ پایانی گزارش‌دهنده

برای پیکربندی یک صفحهٔ وب جهت ارسال گزارش خرابی، باید یک نقطهٔ پایانی سرور گزارش‌دهنده با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تعریف کنید، مثلاً `https://example.com/reports`، همان‌طور که قبلاً توضیح داده شد.

یک ساختار گزارش معمولی به صورت زیر است:

```json
{
  "age": 27,
  "type": "crash",
  "url": "https://example.com/",
  "user_agent": "Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0",
  "body": {
    "sourceFile": "https://example.com/",
    "reason": "unresponsive",
    "stack": "SomeError: ... at ...",
    "is_top_level": true,
    "visibility_state": "visible",
    "crash_report_api": {
      "crash_data_1": "0001",
      "crash_data_2": "0002"
    }
  }
}
```

گزارش به صورت یک شیء JSON در یک درخواست {{httpmethod("POST")}} به نقطهٔ پایانی ارسال می‌شود، هر زمان که مرورگر خراب شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CrashReportContext")}}
- {{HTTPHeader("Reporting-Endpoints")}}
- [Reporting API](/en-US/docs/Web/API/Reporting_API)