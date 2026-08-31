---
title: "CSPViolationReport: referrer property"
short-title: referrer
slug: Web/API/CSPViolationReport/referrer
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

ویژگی **`referrer`** از دیکشنری {{domxref("CSPViolationReport")}} یک رشته است که URL صفحه ارجاعدهنده را برای منبعی که [Content Security Policy (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) آن نقض شده است، نمایش می‌دهد.

ارجاع‌دهنده، صفحه‌ای است که باعث بارگذاری صفحه‌ای با نقض CSP شده است. به‌عنوان مثال، اگر از طریق یک پیوند به صفحه‌ای با نقض CSP برویم، `referrer` همان صفحه‌ای است که از آن به این صفحه آمده‌ایم.

## مقدار

یک رشته که URL ارجاع‌دهنده صفحه دارای نقض CSP را نشان می‌دهد، یا `null`.

توجه داشته باشید که اگر ارجاع‌دهنده یک URL با پروتکل HTTP(S) باشد، هرگونه نام کاربری، گذرواژه یا fragment حذف می‌شود. اگر طرح نشانی (URL scheme) از نوع `http:` یا `https:` نباشد، فقط همین طرح بازگردانده می‌شود.

## مثال‌ها

### مثال نقض CSP با اسکریپت درون‌خطی که referrer را نشان می‌دهد

این مثال با استفاده از یک اسکریپت درون‌خطی، نقض CSP را ایجاد می‌کند و گزارش آن را با استفاده از {{domxref("ReportingObserver")}} ثبت می‌کند. ما از صفحه دیگری به این صفحه می‌آییم و `referrer`، `documentURL` و `blockedURL` را در کنسول ثبت می‌کنیم.

#### HTML

ابتدا صفحه ارجاع‌دهنده خود را با مسیر `/bounce/index.html` تعریف می‌کنیم. این صفحه فقط حاوی یک پیوند به صفحه دیگر یعنی `../report_sample/index.html` است.

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

فایل HTML مربوط به `../report_sample/index.html` در پایین تعریف شده است. این فایل از عنصر [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) برای تنظیم {{httpheader('Content-Security-Policy')}} با مقدار `script-src-elem` به `self` استفاده می‌کند؛ این کار اجازه می‌دهد اسکریپت‌ها از همان دامنه بارگذاری شوند، اما اجرای اسکریپت‌های درون‌خطی را مجاز نمی‌داند. این سند همچنین شامل یک اسکریپت درون‌خطی است که باعث ایجاد نقض CSP می‌شود.

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

نمونه گزارش بالا همچنین اسکریپت خارجی `main.js` را بارگذاری می‌کند که در پایین نشان داده شده است. از آنجا که این اسکریپت از همان دامنه HTML بارگذاری می‌شود، توسط CSP مسدود نمی‌شود.

این اسکریپت یک {{domxref("ReportingObserver")}} جدید می‌سازد تا گزارش‌های نقض محتوا از نوع `"csp-violation"` را مشاهده کند. هر بار که تابع callback فراخوانده می‌شود، بدنه اولین ورودی آرایه گزارش‌ها را می‌گیریم و از آن برای ثبت `documentURL`، `referrer` و `blockedURL` در کنسول استفاده می‌کنیم.

```js
// main.js
const observer = new ReportingObserver(
  (reports, observer) => {
    console.log(`documentURL: ${reports[0].body.referrer}`);
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

توجه داشته باشید که اگرچه ممکن است چندین گزارش در آرایه بازگشتی وجود داشته باشد، برای اختصار فقط مقادیر عنصر اول را ثبت می‌کنیم.

#### نتایج

خروجی کنسول برای کد بالا تقریباً به شکل زیر خواهد بود (سایت به نحوه سرو شدن صفحات بستگی دارد):

```plain
documentURL: http://127.0.0.1:9999/report_sample/
referrer: http://127.0.0.1:9999/bounce/
blockedURL: inline
```

توجه کنید که `referrer` صفحه‌ای است که از آن به این صفحه آمده‌ایم، `documentURL` صفحه‌ای است که نقض CSP در آن رخ داده است، و `blockedURL` در این مورد اصلاً یک URL نیست، بلکه نشانه‌ای است که نقض توسط یک اسکریپت درون‌خطی ناایمن ایجاد شده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.referrer")}}
- {{httpheader("Referer")}}