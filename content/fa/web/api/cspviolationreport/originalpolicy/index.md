---
title: "CSPViolationReport: originalPolicy property"
short-title: originalPolicy
slug: Web/API/CSPViolationReport/originalPolicy
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

ویژگی **`originalPolicy`** در دیکشنری {{domxref("CSPViolationReport")}} یک رشته است که [خط‌مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) را نشان می‌دهد که اعمال آن تخلف را آشکار کرده است.

این رشته همان مقداری است که در هدر پاسخ HTTP {{HTTPHeader("Content-Security-Policy")}} قرار دارد و شامل فهرست [دستورها](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#directives) و مقادیرشان است که خط‌مشی CSP را تشکیل می‌دهند.
توجه کنید که این ویژگی با {{domxref("CSPViolationReport.effectiveDirective","effectiveDirective")}} تفاوت دارد؛ دستوری که عملاً در حال نقض شدن است (و ممکن است به صراحت در خط‌مشی ذکر نشده باشد، اگر از `default-src` استفاده شده باشد).

## مقدار

یک رشته که نشان‌دهنده خط‌مشی‌ای است که اعمال آن تخلف را آشکار کرده است.

## مثال‌ها

### نقض اسکریپت درون‌خطی CSP

این مثال با استفاده از یک اسکریپت درون‌خطی، یک تخلف CSP را فعال می‌کند و تخلف را با استفاده از یک {{domxref("ReportingObserver")}} گزارش می‌دهد.
به‌طور خاص، `effectiveDirective` و `originalPolicy` را ثبت می‌کند و تفاوت بین آن‌ها را روشن می‌سازد.

#### HTML

فایل HTML زیر از عنصر [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) استفاده می‌کند تا {{httpheader('Content-Security-Policy')}} را با `default-src` برابر با `self` تنظیم کند. این کار اجازه می‌دهد اسکریپت‌ها و سایر منابع از همان دامنه بارگذاری شوند، اما اجازه اجرای اسکریپت‌های درون‌خطی را نمی‌دهد.
سند همچنین شامل یک اسکریپت درون‌خطی است که باید یک تخلف CSP را فعال کند.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta
      http-equiv="Content-Security-Policy"
      content="default-src 'self'; report-to csp-endpoint" />
    <!-- This is the (original) CSP policy -->
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
از آنجا که این اسکریپت از همان دامنه‌ای بارگذاری می‌شود که HTML در آن قرار دارد، توسط CSP مسدود نمی‌شود.

این اسکریپت یک {{domxref("ReportingObserver")}} جدید ایجاد می‌کند تا گزارش‌های تخلف محتوا از نوع `"csp-violation"` را مشاهده کند.
هر بار که تابع callback فراخوانده می‌شود، بدنه اولین عنصر آرایه گزارش‌ها را می‌گیریم و از آن برای ثبت `effectiveDirective` و `originalPolicy` تخلف در کنسول استفاده می‌کنیم.

```js
// main.js
const observer = new ReportingObserver(
  (reports, observer) => {
    console.log(`effectiveDirective: ${reports[0].body.effectiveDirective}`);
    // effectiveDirective: script-src-elem
    console.log(`originalPolicy: ${reports[0].body.originalPolicy}`);
    // originalPolicy: default-src 'self'; report-to csp-endpoint
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

خروجی کنسول برای کد بالا به این صورت است:

```plain
effectiveDirective: script-src-elem
originalPolicy: default-src 'self'; report-to csp-endpoint
```

توجه کنید که `originalPolicy` با محتوای عنصر `<meta>` مربوط به دستور `Content-Security-Policy` در HTML مطابقت دارد و مشخص می‌کند که خط‌مشی به‌طور پیش‌فرض `self` است (`default-src 'self'`).

`effectiveDirective` برابر با `script-src-elem` است که منابع معتبر برای عناصر {{htmlelement("script")}} جاوااسکریپت را مشخص می‌کند.
این دستور خاصی است که عملاً نقض شده است، حتی با وجود اینکه `default-src` در خط‌مشی تنظیم شده بود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.originalPolicy")}}