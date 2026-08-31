---
title: "CSPViolationReport: documentURL property"
---

---
title: "CSPViolationReport: documentURL property"
short-title: documentURL
slug: Web/API/CSPViolationReport/documentURL
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

خصوصیت **`documentURL`** در دیکشنری {{domxref("CSPViolationReport")}} یک رشته (string) است که نشانی (URL) سند یا worker ای را نشان می‌دهد که [خط مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) را نقض کرده است.

## مقدار

رشته‌ای که نشانی (URL) سند یا worker نقض‌کنندهٔ CSP را شامل می‌شود.

## مثال‌ها

### نقض CSP توسط اسکریپت درون‌خطی همراه با نمایش referrer

این مثال با استفاده از یک اسکریپت درون‌خطی (inline script) یک نقض CSP را فعال می‌کند و این نقض را با استفاده از یک {{domxref("ReportingObserver")}} گزارش می‌دهد. ما از صفحه‌ای دیگر به این صفحه می‌رویم و مقادیر `referrer`، `documentURL` و `blockedURL` را در کنسول ثبت می‌کنیم.

#### HTML

ابتدا صفحهٔ ارجاع‌دهنده (referrer) خود یعنی `/bounce/index.html` را تعریف می‌کنیم. این صفحه فقط شامل یک پیوند به صفحهٔ دیگر یعنی `../report_sample/index.html` است.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  </head>
  <body>
    <ul>
      <li><a href="../report_sample/">report sample</a></li>
    </ul>
  </body>
</html>
```

فایل HTML مربوط به `../report_sample/index.html` در ادامه تعریف شده است. این فایل با استفاده از عنصر [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) مقدار {{httpheader('Content-Security-Policy')}} را طوری تنظیم می‌کند که `script-src-elem` برابر با `self` باشد؛ این کار اجازه می‌دهد اسکریپت‌ها از همان دامنه بارگذاری شوند، اما اجرای اسکریپت‌های درون‌خطی را مجاز نمی‌داند. سند همچنین شامل یک اسکریپت درون‌خطی است که باعث فعال‌شدن یک نقض CSP می‌شود.

```html
<!doctype html>
<!-- /report_sample/index.html -->
<html lang="en">
  <head>
    <meta
      http-equiv="Content-Security-Policy"
      content="script-src-elem 'self' 'report-sample'" />
    <script src="main.js"></script>
  </head>
  <body>
    <script>
      const int = 4;
    </script>
  </body>
</html>
```

#### JavaScript (main.js)

نمونهٔ گزارش بالا همچنین اسکریپت خارجی `main.js` را بارگذاری می‌کند که در ادامه نشان داده شده است. از آنجا که این اسکریپت از همان دامنه‌ای که HTML از آن ارائه می‌شود بارگذاری شده است، توسط CSP مسدود نمی‌شود.

اسکریپت یک {{domxref("ReportingObserver")}} جدید می‌سازد تا گزارش‌های نقض محتوا از نوع `"csp-violation"` را مشاهده کند. هر بار که تابع callback فراخوانی می‌شود، بدنهٔ (body) اولین ورودی آرایهٔ reports را می‌گیریم و از آن برای ثبت مقادیر `documentURL`، `referrer` و `blockedURL` مربوط به نقض در کنسول استفاده می‌کنیم.

```js
// main.js
const observer = new ReportingObserver(
  (reports, observer) => {
    console.log(`documentURL: ${reports[0].body.documentURL}`);
    console.log(`referrer: ${reports[0].body.referrer}`);
    console.log(`blockedURL: ${reports[0].body.blockedURL}`);
  },
  {
    types: ["csp-violation"],
    buffered: true,
  },
);

observer.observe();
```

توجه داشته باشید که اگرچه ممکن است چندین گزارش در آرایهٔ بازگشتی وجود داشته باشد، برای اختصار فقط مقادیر عنصر اول را ثبت می‌کنیم.

#### نتایج

خروجی کنسول برای کد بالا تقریباً به شکل زیر خواهد بود (مقدار سایت به نحوهٔ ارائهٔ صفحات بستگی دارد):

```plain
documentURL: http://127.0.0.1:9999/report_sample/
referrer: http://127.0.0.1:9999/bounce/
blockedURL: inline
```

توجه کنید که `referrer` صفحه‌ای است که از آن به این صفحه آمده‌ایم، `documentURL` صفحه‌ای است که نقض CSP در آن رخ داده است، و `blockedURL` در این مورد اصلاً یک URL نیست، بلکه نشانه‌ای است مبنی بر اینکه نقض توسط یک اسکریپت درون‌خطی ایجاد شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("SecurityPolicyViolationEvent.documentURI")}}