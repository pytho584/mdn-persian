好的，这是根据您的要求将 MDN 文档翻译成的波斯语版本：

---
title: "CSPViolationReport: lineNumber property"
slug: Web/API/CSPViolationReport/lineNumber
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

ویژگی **`lineNumber`** در دیکشنری {{domxref("CSPViolationReport")}} نشان‌دهنده شماره خط در فایل منبع است که در آن، نقض [خط مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) رخ داده است.

این ویژگی همراه با ویژگی‌های {{domxref("CSPViolationReport.sourceFile")}} و {{domxref("CSPViolationReport.columnNumber")}} استفاده می‌شود که در مجموع موقعیت دقیق در منبع را فراهم می‌کنند که باعث نقض شده است.

توجه داشته باشید که مرورگر مقدار را از _شیء سراسری_ فایلی که باعث نقض شده است استخراج می‌کند.
اگر منبعی که باعث نقض CSP می‌شود بارگذاری نشده باشد، مقدار `null` خواهد بود.
برای اطلاعات بیشتر به {{domxref("CSPViolationReport.sourceFile")}} مراجعه کنید.

## مقدار

یک عدد صحیح شامل شماره خطی که باعث نقض شده است، یا `null`.

## مثال‌ها

### نقض اسکریپت درون‌خطی CSP

این مثال با استفاده از یک اسکریپت درون‌خطی، یک نقض CSP را ایجاد می‌کند و نقض را با استفاده از یک {{domxref("ReportingObserver")}} گزارش می‌دهد.

#### HTML

فایل HTML زیر از عنصر [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) برای تنظیم `default-src` به `self` برای {{httpheader('Content-Security-Policy')}} استفاده می‌کند، که اجازه می‌دهد اسکریپت‌ها و سایر منابع از همان مبدأ بارگذاری شوند، اما اجرای اسکریپت‌های درون‌خطی را مجاز نمی‌کند.
سند همچنین شامل یک اسکریپت درون‌خطی است که باید باعث نقض CSP شود.

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

#### جاوااسکریپت (main.js)

سند بالا همچنین اسکریپت خارجی `main.js` را بارگذاری می‌کند که در زیر نشان داده شده است.
از آنجایی که این اسکریپت از همان دامنه HTML بارگذاری می‌شود، توسط CSP مسدود نمی‌شود.

اسکریپت یک {{domxref("ReportingObserver")}} جدید برای مشاهده گزارش‌های نقض محتوای نوع `"csp-violation"` ایجاد می‌کند.
هر بار که تابع callback فراخوانی می‌شود، بدنه اولین ورودی آرایه گزارش‌ها را دریافت می‌کنیم و از آن برای ثبت فایل، خط و ستون نقض در کنسول استفاده می‌کنیم.

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

توجه داشته باشید که اگرچه ممکن است چندین گزارش در آرایه بازگشتی وجود داشته باشد، برای اختصار ما فقط مقادیر عنصر اول را ثبت می‌کنیم.

#### نتایج

می‌توانید این مورد را با استفاده از یک [سرور محلی](/en-US/docs/Learn_web_development/Howto/Tools_and_setup/set_up_a_local_testing_server) امتحان کنید.
کد بالا را در `test/index.html` و `test/main.js` کپی کنید و سرور را در دایرکتوری ریشه اجرا کنید.
با فرض اینکه آدرس سرور محلی `http://127.0.0.1:9999` باشد، می‌توانید فایل HTML را از `http://127.0.0.1:9999/test/` (یا `http://127.0.0.1:9999/test/index.html`) بارگذاری کنید.

با تنظیمات فوق، خروجی لاگ در Chrome به صورت زیر است:

```plain
sourceFile: http://127.0.0.1:9999/test/
lineNumber: 15
columnNumber: 0
```

نتیجه برای Firefox مشابه است:

```plain
sourceFile: http://127.0.0.1:9999/test/
lineNumber: 15
columnNumber: 13
```

توجه داشته باشید که شماره ستون برای دو مرورگر متفاوت است.
به نظر می‌رسد Chrome همیشه `0` را گزارش می‌دهد.
مقدار در Firefox موقعیت اولین کاراکتر پس از پایان عنصر `<script>` آغازین را نشان می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.lineNumber")}}