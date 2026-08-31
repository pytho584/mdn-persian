---
title: "CSPViolationReport: disposition property"
short-title: disposition
slug: Web/API/CSPViolationReport/disposition
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

ویژگی **`disposition`** در دیکشنری {{domxref("CSPViolationReport")}} مشخص می‌کند که آیا عامل کاربر (user agent) برای اعمالِ نقض‌های [Content Security Policy (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) پیکربندی شده است یا فقط آن‌ها را گزارش می‌دهد.

## مقدار

مقدارهای ممکن عبارت‌اند از:

- `"enforce"`
  - : سیاست اعمال می‌شود و درخواست منبع مسدود می‌شود.
    این مقدار برای نقضِ سیاست‌های تنظیم‌شده با {{httpheader("Content-Security-Policy")}} استفاده می‌شود.
- `"report"`
  - : نقض گزارش می‌شود اما درخواست منبع مسدود نمی‌شود.
    این مقدار برای نقضِ سیاست‌های تنظیم‌شده با {{httpheader("Content-Security-Policy-Report-Only")}} استفاده می‌شود.

## مثال‌ها

### نمایش disposition در نقض اسکریپت درون‌خطی CSP

این مثال یک نقض CSP را با استفاده از یک اسکریپت درون‌خطی فعال می‌کند و آن را با کمک یک {{domxref("ReportingObserver")}} گزارش می‌دهد. سپس مقدار `disposition` در لاگ ثبت می‌شود.

#### HTML

پرونده HTML زیر از عنصر [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) استفاده می‌کند تا {{httpheader('Content-Security-Policy')}} را با `default-src` برابر با `self` تنظیم کند. این تنظیم اجازه می‌دهد اسکریپت‌ها و سایر منابع از همان دامنه بارگیری شوند، اما اجازه نمی‌دهد اسکریپت‌های درون‌خطی اجرا شوند. سند همچنین شامل یک اسکریپت درون‌خطی است، بنابراین باید یک نقض CSP را فعال کند.

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

سند بالا همچنین اسکریپت خارجی `main.js` را که در زیر نشان داده شده است بارگیری می‌کند. از آنجا که این اسکریپت از همان دامنه HTML بارگیری می‌شود، توسط CSP مسدود نمی‌شود.

اسکریپت یک {{domxref("ReportingObserver")}} جدید می‌سازد تا گزارش‌های نقض محتوا از نوع `"csp-violation"` را مشاهده کند. هر بار که تابع callback فراخوانده می‌شود، body اولین ورودی آرایه `reports` را می‌گیریم و از آن برای ثبت نام فایل، شماره خط و شماره ستون نقض در کنسول استفاده می‌کنیم.

```js
// main.js
const observer = new ReportingObserver(
  (reports, observer) => {
    const cspViolationBody = reports[0].body;
    console.log(`disposition: ${cspViolationBody.disposition}`);
    // For example: "enforce"
  },
  {
    types: ["csp-violation"],
    buffered: true,
  },
);

observer.observe();
```

توجه داشته باشید که اگرچه ممکن است چندین گزارش در آرایه بازگشتی وجود داشته باشد، برای اختصار فقط مقادیر اولین عنصر را در لاگ ثبت می‌کنیم.

#### نتایج

اگر کد بالا را سرو کنید، خروجی لاگ به شکل زیر خواهد بود:

```plain
disposition: enforce
```

> [!NOTE]
> اگر `Content-Security-Policy-Reporting-Only` فعال باشد، `disposition` برابر با `report` خواهد بود.
> با این حال توجه داشته باشید که `Content-Security-Policy-Reporting-Only` باید سرو شود: نمی‌توان آن را در عنصر `<meta>` تنظیم کرد، همان‌طور که در بالا برای `Content-Security-Policy` انجام دادیم.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.disposition")}}