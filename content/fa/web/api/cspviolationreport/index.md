---
title: CSPViolationReport
slug: Web/API/CSPViolationReport
page-type: web-api-interface
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

دیکشنری `CSPViolationReport` از [Reporting API](/en-US/docs/Web/API/Reporting_API) گزارشی را نشان می‌دهد که وقتی یک سند [سیاست امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) خود را نقض می‌کند، تولید می‌شود.

گزارش‌های این نوع را می‌توان از داخل یک صفحه با استفاده از {{domxref("ReportingObserver")}} مشاهده کرد و یک نسخه سریالی شده را می‌توان به [نقاط پایانی سرور گزارش‌دهی](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) ارسال کرد.

## ویژگی‌های نمونه

- `body`
  - : بدنه گزارش.
    این یک شیء با ویژگی‌های زیر است:
    - {{domxref("CSPViolationReport.blockedURL","blockedURL")}}
      - : رشته‌ای که نشان‌دهنده نوع یا URL منبعی است که به دلیل نقض CSP مسدود شده است.
    - {{domxref("CSPViolationReport.columnNumber", "columnNumber")}}
      - : موقعیت کاراکتر در خط اسکریپت که نقض در آن رخ داده است.
    - {{domxref("CSPViolationReport.disposition","disposition")}}
      - : رشته‌ای که نشان می‌دهد نقض اعمال شده یا فقط گزارش شده است.
        این مقدار می‌تواند `"enforce"` برای نقض سیاست‌های تنظیم شده با {{httpheader("Content-Security-Policy")}}، یا `"reporting"` برای سیاست‌های تنظیم شده با {{httpheader("Content-Security-Policy-Report-Only")}} باشد.
    - {{domxref("CSPViolationReport.documentURL","documentURL")}}
      - : رشته‌ای که نشان‌دهنده URL سند یا workerای است که نقض در آن یافت شده است.
    - {{domxref("CSPViolationReport.effectiveDirective","effectiveDirective")}}
      - : رشته‌ای که نشان‌دهنده دستورالعملی است که اعمال آن نقض را آشکار کرده است.
    - {{domxref("CSPViolationReport.lineNumber", "lineNumber")}}
      - : شماره خط در اسکریپت که نقض در آن رخ داده است.
    - {{domxref("CSPViolationReport.originalPolicy","originalPolicy")}}
      - : رشته‌ای حاوی سیاستی که اعمال آن نقض را آشکار کرده است.
    - {{domxref("CSPViolationReport.referrer","referrer")}}
      - : رشته‌ای که نشان‌دهنده URL ارجاع‌دهنده (referrer) منابعی است که سیاست آن نقض شده است، یا `null`.
    - {{domxref("CSPViolationReport.sample","sample")}}
      - : رشته‌ای که نمونه‌ای از منبعی که باعث نقض شده است را نشان می‌دهد، معمولاً ۴۰ کاراکتر اول.
        این مقدار فقط زمانی پر می‌شود که منبع یک اسکریپت درون‌خطی (inline)، event handler یا style باشد — منابع خارجی که باعث نقض می‌شوند نمونه تولید نمی‌کنند.
    - {{domxref("CSPViolationReport.sourceFile","sourceFile")}}
      - : اگر نقض در نتیجه یک اسکریپت رخ داده باشد، این URL آن اسکریپت خواهد بود؛ در غیر این صورت `null` خواهد بود.
        اگر این ویژگی `null` نباشد، `columnNumber` و `lineNumber` باید مقادیر غیر null داشته باشند.
    - {{domxref("CSPViolationReport.statusCode","statusCode")}}
      - : عددی که نشان‌دهنده کد وضعیت HTTP سند یا workerای است که نقض در آن رخ داده است.

- `type`
  - : رشته `"csp-violation"` که نشان می‌دهد این یک گزارش نقض CSP است.
- `url`
  - : رشته‌ای که نشان‌دهنده URL سند تولیدکننده گزارش است.

## توضیحات

گزارش‌های نقض CSP ممکن است زمانی ایجاد شوند که یک صفحه وب تلاش می‌کند منبعی را بارگذاری کند که [CSP](/en-US/docs/Web/HTTP/Guides/CSP) تنظیم شده با استفاده از هدرهای HTTP {{HTTPHeader("Content-Security-Policy")}} یا {{HTTPHeader("Content-Security-Policy-Report-Only")}} را نقض می‌کند.

می‌توانید گزارش‌های نقض CSP را در داخل صفحه‌ای که سیاست را تنظیم می‌کند با استفاده از [Reporting API](/en-US/docs/Web/API/Reporting_API) رصد کنید.
برای این کار یک شیء {{domxref("ReportingObserver")}} ایجاد می‌کنید تا به گزارش‌ها گوش دهد، یک متد callback و یک ویژگی (اختیاری) `options` که انواع گزارش‌هایی را که می‌خواهید گزارش کنید مشخص می‌کند، ارسال می‌کنید.
سپس متد callback با گزارش‌های انواع درخواست‌شده فراخوانی می‌شود و یک شیء گزارش را ارسال می‌کند.
برای نقض‌های CSP، شیء یک نمونه از `CSPViolationReport` خواهد بود (که ویژگی [`type`](#type) آن روی `"csp-violation"` تنظیم شده است).

ساختار یک گزارش معمولی در زیر نشان داده شده است.
توجه کنید که می‌توانیم URL هر دو صفحه‌ای که سیاست آن نقض شده است (`url`)، سندی که تلاش کرده منبع را بارگذاری کند (`body.documentURL`) و منبعی که از بارگذاری مسدود شده است (`body.blockedURL`) را ببینیم.
همچنین می‌توانیم ببینیم که نقض ناشی از تلاش صفحه برای بارگذاری یک عنصر اسکریپت با منبعی از یک مبدأ دیگر بوده است که `body.originalPolicy` را نقض کرده است، و اینکه نقض اعمال شده است (و فقط گزارش نشده است).

```json
{
  "type": "csp-violation",
  "url": "https://url-of-page-enforcing-policy",
  "body": {
    "sourceFile": null,
    "lineNumber": null,
    "columnNumber": null,
    "documentURL": "https://url-of-document-attempting-to-load-resource-in-violation",
    "referrer": "",
    "blockedURL": "https://url-of-blocked-resource.js",
    "effectiveDirective": "script-src-elem",
    "originalPolicy": "default-src 'self';",
    "sample": "",
    "disposition": "enforce",
    "statusCode": 200
  }
}
```

گزارش‌های نقض همچنین ممکن است به عنوان یک شیء JSON در یک درخواست {{httpmethod("POST")}} به یک یا چند [نقطه پایانی سرور گزارش‌دهی](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) پیکربندی شده ارسال شوند.
نام نقاط پایانی سرور گزارش‌دهی در دستورالعمل سیاست [`report-to`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/report-to) هدر {{HTTPHeader("Content-Security-Policy")}} یا {{HTTPHeader("Content-Security-Policy-Report-Only")}} مشخص می‌شوند.
نام نقاط پایانی معتبر و نگاشت آن‌ها به یک URL خاص با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تعریف می‌شوند.

> [!NOTE]
> گزارش‌های نقض CSP که توسط Reporting API ارسال می‌شوند، زمانی که یک نقطه پایانی با استفاده از دستورالعمل CSP [`report-to`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/report-to) مشخص شده باشد، مشابه (اما نه یکسان) با "گزارش CSP" [اشیاء JSON](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/report-uri#violation_report_syntax) هستند که زمانی ارسال می‌شوند که نقاط پایانی با استفاده از دستورالعمل [`report-uri`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/report-uri) مشخص شده باشند.
> هدف Reporting API و دستورالعمل `report-to` جایگزینی فرمت گزارش قدیمی و دستورالعمل `report-uri` است.

ساختار گزارش سرور تقریباً دقیقاً مشابه `CSPViolationReport` است، با این تفاوت که شامل فیلدهای `age` و `user_agent` نیز می‌شود.

```json
{
  "age": "176279",
  "type": "csp-violation",
  "url": "https://url-of-page-enforcing-policy",
  "body": {
    "sourceFile": null,
    "lineNumber": null,
    "columnNumber": null,
    "documentURL": "https://url-of-document-attempting-to-load-resource-in-violation",
    "referrer": "",
    "blockedURL": "https://url-of-blocked-resource.js",
    "effectiveDirective": "script-src-elem",
    "originalPolicy": "default-src 'self';",
    "sample": "",
    "disposition": "enforce",
    "statusCode": 200
  },
  "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36"
}
```

## مثال‌ها

### استفاده از رابط `ReportingObserver`

می‌توانید یک شیء `CSPViolationReport` را با پیکربندی صفحه خود به گونه‌ای که یک نقض CSP رخ دهد، به دست آورید.
در این مثال، CSP خود را طوری تنظیم می‌کنیم که فقط محتوای مبدأ خود سایت مجاز باشد، و سپس سعی می‌کنیم یک اسکریپت از `apis.google.com` که یک مبدأ خارجی است، بارگذاری کنیم.

ابتدا، هدر {{HTTPHeader("Content-Security-Policy")}} خود را در پاسخ HTTP تنظیم می‌کنیم:

```http
Content-Security-Policy: default-src 'self';
```

یا در عنصر HTML [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta):

```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self'" />
```

سپس، سعی می‌کنیم یک اسکریپت خارجی بارگذاری کنیم:

```html
<!-- این باید یک نقض CSP ایجاد کند -->
<script src="https://apis.google.com/js/platform.js"></script>
```

در نهایت، یک شیء جدید {{domxref("ReportingObserver")}} برای گوش دادن به نقض‌های CSP ایجاد می‌کنیم (این باید از همان مکان، قبل از اسکریپتی که باعث نقض می‌شود، بارگذاری شود).

```js
const observer = new ReportingObserver(
  (reports, observer) => {
    reports.forEach((violation) => {
      console.log(violation);
      console.log(JSON.stringify(violation));
    });
  },
  {
    types: ["csp-violation"],
    buffered: true,
  },
);

observer.observe();
```

در بالا هر شیء گزارش نقض و یک نسخه JSON-string از شیء را لاگ می‌کنیم، که ممکن است شبیه به شیء زیر باشد.
توجه کنید که گزارش یک نمونه از `CSPViolationReport` است و `type` برابر با `"csp-violation"` است.

```json
{
  "type": "csp-violation",
  "url": "http://127.0.0.1:9999/",
  "body": {
    "sourceFile": null,
    "lineNumber": null,
    "columnNumber": null,
    "documentURL": "http://127.0.0.1:9999/",
    "referrer": "",
    "blockedURL": "https://apis.google.com/js/platform.js",
    "effectiveDirective": "script-src-elem",
    "originalPolicy": "default-src 'self';",
    "sample": "",
    "disposition": "enforce",
    "statusCode": 200
  }
}
```

### ارسال گزارش نقض CSP

پیکربندی یک صفحه وب برای ارسال گزارش نقض CSP مشابه مثال قبلی است.
مانند قبل، باید صفحه خود را به گونه‌ای پیکربندی کنید که یک نقض رخ دهد.

علاوه بر این، باید نقطه(های) پایانی که گزارش به آن ارسال می‌شود را نیز مشخص کنید.
یک سرور نقاط پایانی را با استفاده از هدر پاسخ {{httpheader("Reporting-Endpoints")}} مشخص می‌کند: اینها باید URLهای امن (HTTPS) باشند.
سپس از دستورالعمل CSP {{CSP("report-to")}} برای مشخص کردن اینکه یک نقطه پایانی خاص برای گزارش نقض‌های CSP استفاده می‌شود، استفاده می‌شود:

```http
Reporting-Endpoints: csp-endpoint="https://example.com/csp-report-to"
Content-Security-Policy: default-src 'self'; report-to csp-endpoint
```

مانند قبل، می‌توانیم با بارگذاری یک اسکریپت خارجی از مکانی که توسط هدر CSP ما مجاز نیست، یک نقض ایجاد کنیم:

```html
<!-- این باید یک نقض CSP ایجاد کند -->
<script src="https://apis.google.com/js/platform.js"></script>
```

سپس گزارش نقض به عنوان یک فایل JSON به نقطه پایانی مشخص شده ارسال می‌شود.
همانطور که از مثال زیر می‌بینید، `type` برابر با `"csp-violation"` است و ویژگی `body` یک سریال‌سازی از شیء `CSPViolationReport` است:

```json
[
  {
    "age": 53531,
    "body": {
      "blockedURL": "inline",
      "columnNumber": 59,
      "disposition": "enforce",
      "documentURL": "https://example.com/csp-report-to",
      "effectiveDirective": "script-src-elem",
      "lineNumber": 1441,
      "originalPolicy": "default-src 'self'; report-to csp-endpoint",
      "referrer": "https://www.google.com/",
      "sample": "",
      "sourceFile": "https://example.com/csp-report-to",
      "statusCode": 200
    },
    "type": "csp-violation",
    "url": "https://example.com/csp-report-to",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36"
  }
]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ReportingObserver")}}
- {{HTTPHeader("Content-Security-Policy")}}
- {{HTTPHeader("Content-Security-Policy-Report-Only")}}
- {{domxref("SecurityPolicyViolationEvent")}}
- {{HTTPHeader("Reporting-Endpoints")}}
- [Reporting API](/en-US/docs/Web/API/Reporting_API)