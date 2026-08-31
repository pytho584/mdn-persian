---
title: "CSPViolationReport: columnNumber property"
short-title: columnNumber
slug: Web/API/CSPViolationReport/columnNumber
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

خاصیت **`columnNumber`** از دیکشنری {{domxref("CSPViolationReport")}} موقعیت کاراکتری در خط فایل مبدأ را نشان می‌دهد که باعث نقض [Content Security Policy (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) شده است.

این خاصیت همراه با خاصیت‌های {{domxref("CSPViolationReport.sourceFile")}} و {{domxref("CSPViolationReport.lineNumber")}} استفاده می‌شود که با هم مکان دقیق در فایل مبدأ را که باعث نقض شده است مشخص می‌کنند.

توجه داشته باشید که مرورگر مقدار را از _شیء سراسری_ فایلی که باعث نقض شده است استخراج می‌کند.
اگر منبعی که باعث نقض CSP می‌شود بارگذاری نشود، مقدار `null` خواهد بود.
برای اطلاعات بیشتر به {{domxref("CSPViolationReport.sourceFile")}} مراجعه کنید.

## مقدار

یک عدد صحیح که شماره ستون مربوط به نقض را نشان می‌دهد، یا `null`.

## مثال‌ها

### نقض اسکریپت درون‌خطی CSP

این مثال با استفاده از یک اسکریپت درون‌خطی یک نقض CSP را ایجاد کرده و آن را با استفاده از {{domxref("ReportingObserver")}} گزارش می‌کند.

#### HTML

فایل HTML زیر از عنصر [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) برای تنظیم {{httpheader('Content-Security-Policy')}} با مقدار `default-src` به `self` استفاده می‌کند که اجازه می‌دهد اسکریپت‌ها و سایر منابع از همان مبدأ بارگذاری شوند، اما اجازه اجرای اسکریپت‌های درون‌خطی را نمی‌دهد.
سند همچنین شامل یک اسکریپت درون‌خطی است که بنابراین باید باعث نقض CSP شود.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta
      http-equiv="Content-Security-Policy"
      content="default-src 'self'; report-to csp-endpoint" />
    <meta
      http-equiv="Reporting-Endpoints"
      content="csp-endpoint='https://example.com/csp-reports'" />
    <script src="main.js"></script>
    <title>CSP: Violation due to inline script</title>
  </head>
  <body>
    <h1>CSP: Violation due to inline script</h1>
    <script>
      const int = 4;
    </script>
  </body>
</html>
```

#### JavaScript (main.js)

سند بالا همچنین اسکریپت خارجی `main.js` را بارگذاری می‌کند که در زیر نشان داده شده است.
از آنجایی که این اسکریپت از همان دامنه HTML بارگذاری می‌شود، توسط CSP مسدود نمی‌شود.

این اسکریپت یک {{domxref("ReportingObserver")}} جدید ایجاد می‌کند تا گزارش‌های نقض محتوای از نوع `"csp-violation"` را مشاهده کند.
هر بار که تابع بازخوانی (callback) فراخوانی می‌شود، بدنه اولین ورودی آرایه گزارش‌ها را گرفته و از آن برای ثبت فایل، خط و ستون نقض در کنسول استفاده می‌کند.

```js
// main.js
const observer = new ReportingObserver(
  (reports, observer) => {
    const cspViolationBody = reports[0].body;
    console.log(`sourceFile: ${cspViolationBody.sourceFile}`);
    console.log(`lineNumber: ${cspViolationBody.lineNumber}`);
    console.log(`columnNumber: ${cspViolationBody.columnNumber}`);
  },
  {
    types: ["csp-violation"],
    buffered: true,
  },
);

observer.observe();
```

توجه داشته باشید که ممکن است چندین گزارش در آرایه برگشتی وجود داشته باشد، اما برای اختصار فقط مقادیر عنصر اول را ثبت می‌کنیم.

#### نتایج

می‌توانید این را با استفاده از یک [سرور محلی](/en-US/docs/Learn_web_development/Howto/Tools_and_setup/set_up_a_local_testing_server) امتحان کنید.
کد بالا را در `test/index.html` و `test/main.js` کپی کرده و سرور را در دایرکتوری ریشه اجرا کنید.
با فرض اینکه آدرس سرور محلی `http://127.0.0.1:9999` باشد، می‌توانید فایل HTML را از `http://127.0.0.1:9999/test/` (یا `http://127.0.0.1:9999/test/index.html`) بارگذاری کنید.

با تنظیمات بالا، خروجی لاگ در کروم به صورت زیر است:

```plain
sourceFile: http://127.0.0.1:9999/test/
lineNumber: 15
columnNumber: 0
```

نتیجه در فایرفاکس مشابه است:

```plain
sourceFile: http://127.0.0.1:9999/test/
lineNumber: 15
columnNumber: 13
```

توجه داشته باشید که شماره ستون برای دو مرورگر متفاوت است.
کروم همیشه `0` را گزارش می‌دهد.
مقدار در فایرفاکس موقعیت اولین کاراکتر بعد از پایان عنصر `<script>` بازشونده را نشان می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.columnNumber")}}