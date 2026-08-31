---
title: "CSPViolationReport: sourceFile property"
---

---
title: "CSPViolationReport: sourceFile property"
short-title: sourceFile
slug: Web/API/CSPViolationReport/sourceFile
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

ویژگی **`sourceFile`** از دیکشنری {{domxref("CSPViolationReport")}} نشانی URL فایل منبعی را نشان می‌دهد که [سیاست امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) را نقض کرده است.

برای نقضی که در اثر استفاده از یک اسکریپت درون‌خطی (inline script) رخ می‌دهد، `sourceFile` نشانی URL سند جاری است. به طور مشابه، اگر یک سند با موفقیت اسکریپتی را بارگذاری کند که سپس CSP سند را نقض کند، `sourceFile` نشانی URL آن اسکریپت خواهد بود.

این ویژگی به همراه ویژگی‌های {{domxref("CSPViolationReport.lineNumber")}} و {{domxref("CSPViolationReport.columnNumber")}} استفاده می‌شود که با هم موقعیت دقیق در منبع را که باعث نقض شده است، مشخص می‌کنند.

توجه داشته باشید که اگر یک سند با CSP که منابع خارجی را مسدود می‌کند، تلاش کند یک منبع خارجی را بارگذاری کند، `sourceFile` مقدار `null` خواهد داشت. دلیل این است که مرورگر مقدار را از _شیء سراسری (global object)_ فایلی که باعث نقض شده است استخراج می‌کند. به دلیل محدودیت CSP، منبع خارجی هرگز بارگذاری نمی‌شود و بنابراین شیء سراسری متناظری ندارد.

## مقدار

یک رشته شامل نشانی URL فایلی که باعث نقض شده است، یا `null`.

## مثال‌ها

### نقض CSP با اسکریپت درون‌خطی

این مثال با استفاده از یک اسکریپت درون‌خطی، نقض CSP را ایجاد کرده و آن را با استفاده از یک {{domxref("ReportingObserver")}} گزارش می‌دهد.

#### HTML

فایل HTML زیر از عنصر [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) برای تنظیم {{httpheader('Content-Security-Policy')}} با مقدار `default-src 'self'` استفاده می‌کند که اجازه می‌دهد اسکریپت‌ها و سایر منابع از همان خاستگاه (origin) بارگذاری شوند، اما اجازه اجرای اسکریپت‌های درون‌خطی را نمی‌دهد. سند همچنین شامل یک اسکریپت درون‌خطی است که بنابراین باید یک نقض CSP را ایجاد کند.

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

سند بالا همچنین اسکریپت خارجی `main.js` را بارگذاری می‌کند که در زیر نشان داده شده است. از آنجایی که این اسکریپت از همان دامنه HTML بارگذاری می‌شود، توسط CSP مسدود نمی‌شود.

این اسکریپت یک {{domxref("ReportingObserver")}} جدید برای مشاهده گزارش‌های نقض محتوا از نوع `"csp-violation"` ایجاد می‌کند. هر بار که تابع callback فراخوانی می‌شود، بدنه اولین ورودی آرایه reports را می‌گیریم و از آن برای ثبت فایل، خط و ستون نقض در کنسول استفاده می‌کنیم.

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

توجه داشته باشید که اگرچه ممکن است چندین گزارش در آرایه بازگشتی وجود داشته باشد، برای اختصار فقط مقادیر اولین عنصر را ثبت می‌کنیم.

#### نتایج

می‌توانید این را با استفاده از یک [سرور محلی](/en-US/docs/Learn_web_development/Howto/Tools_and_setup/set_up_a_local_testing_server) امتحان کنید. کد بالا را در فایل‌های `test/index.html` و `test/main.js` کپی کرده و سرور را در دایرکتوری ریشه اجرا کنید. با فرض اینکه آدرس سرور محلی `http://127.0.0.1:9999` است، می‌توانید فایل HTML را از `http://127.0.0.1:9999/test/` (یا `http://127.0.0.1:9999/test/index.html`) بارگذاری کنید.

با تنظیمات فوق، خروجی لاگ در کروم به صورت زیر است:

```plain
sourceFile: http://127.0.0.1:9999/test/
lineNumber: 15
columnNumber: 0
```

نتیجه برای فایرفاکس مشابه است:

```plain
sourceFile: http://127.0.0.1:9999/test/
lineNumber: 15
columnNumber: 13
```

توجه داشته باشید که شماره ستون برای دو مرورگر متفاوت است. کروم همیشه مقدار `0` را گزارش می‌دهد. مقدار در فایرفاکس نشان‌دهنده موقعیت اولین کاراکتر پس از پایان عنصر `<script>` بازشونده است.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.sourceFile")}}