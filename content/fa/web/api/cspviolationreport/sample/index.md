---
title: "CSPViolationReport: sample property"
---

---
title: "CSPViolationReport: sample property"
short-title: sample
slug: Web/API/CSPViolationReport/sample
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

ویژگی **`sample`** در دیکشنری {{domxref("CSPViolationReport")}} رشته‌ای است که شامل بخشی از منبعی است که [سیاست امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) را نقض کرده است.

این نمونه معمولاً ۴۰ کاراکتر نخست اسکریپت درون‌خطی، کنترل‌کنندهٔ رویداد یا استایلی است که یک محدودیت CSP را نقض کرده است. اگر پر نشده باشد، رشتهٔ خالی `""` است.

توجه داشته باشید که این مقدار تنها زمانی پر می‌شود که تلاش شود اسکریپت‌های _درون‌خطی_، کنترل‌کننده‌های رویداد یا استایل‌هایی بارگذاری شوند که قوانین [`script-src*`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src) و [`style-src*`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/style-src) CSP را نقض می‌کنند — منابع خارجی که CSP را نقض می‌کنند، نمونه‌ای تولید نمی‌کنند. علاوه بر این، نمونه تنها زمانی گنجانده می‌شود که دایرکتیو `Content-Security-Policy` نقض‌شده نیز کلیدواژهٔ [`'report-sample'`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#report-sample) را داشته باشد.

> [!NOTE]
> گزارش‌های نقض باید داده‌هایی در نظر گرفته شوند که توسط مهاجم کنترل می‌شوند. محتوای این فیلد _به‌ویژه_ باید پیش از ذخیره‌سازی یا رندر کردن پاکسازی شود.

## مقدار

رشته‌ای شامل نمونه‌ای از منبع درون‌خطی که CSP را نقض کرده است؛ معمولاً ۴۰ کاراکتر نخست، یا رشتهٔ خالی.

## مثال‌ها

### نقض CSP با اسکریپت درون‌خطی

این مثال با استفاده از یک اسکریپت درون‌خطی، یک نقض CSP ایجاد می‌کند و این نقض را با استفاده از یک {{domxref("ReportingObserver")}} گزارش می‌دهد. ما همچنین `'report-sample'` را به CSP اضافه می‌کنیم تا مقدار `sample` در بدنهٔ گزارش پر شود.

#### HTML

فایل HTML زیر از عنصر [`<meta>`](/en-US/docs/Web/HTML/Reference/Elements/meta) برای تنظیم دایرکتیو `script-src-elem` هدر {{httpheader('Content-Security-Policy')}} روی مقدار `self` استفاده می‌کند؛ این کار اجازه می‌دهد اسکریپت‌ها از همان دامنه بارگذاری شوند، اما اجازهٔ اجرای اسکریپت‌های درون‌خطی را نمی‌دهد. ما `'report-sample'` را در دایرکتیو قرار می‌دهیم تا یک نمونه تولید شود. سند همچنین شامل یک اسکریپت درون‌خطی است که باید یک نقض CSP ایجاد کند.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta
      http-equiv="Content-Security-Policy"
      content="script-src-elem 'self' 'report-sample'" />
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

سند بالا همچنین اسکریپت خارجی `main.js` را بارگذاری می‌کند که در ادامه نشان داده شده است. از آنجا که این اسکریپت از همان دامنه‌ای بارگذاری می‌شود که HTML در آن قرار دارد، توسط CSP مسدود نمی‌شود.

این اسکریپت یک {{domxref("ReportingObserver")}} جدید می‌سازد تا گزارش‌های نقض محتوا از نوع `"csp-violation"` را مشاهده کند. هر بار که تابع callback فراخوانی می‌شود، بدنهٔ اولین عنصر آرایهٔ گزارش‌ها را می‌گیریم و از آن برای ثبت مقدار `sample` این نقض در کنسول استفاده می‌کنیم.

```js
// main.js
const observer = new ReportingObserver(
  (reports, observer) => {
    console.log(`sample: ${reports[0].body.sample}`);
  },
  {
    types: ["csp-violation"],
    buffered: true,
  },
);

observer.observe();
```

توجه داشته باشید که اگرچه ممکن است چندین گزارش در آرایهٔ بازگشتی وجود داشته باشد، برای اختصار فقط مقدار اولین عنصر را ثبت می‌کنیم.

#### نتایج

خروجی کنسول برای کد بالا به این صورت است:

```plain
sample: const int = 4;
```

در این حالت، نمونه شامل تمام محتوای اسکریپت درون‌خطی است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.sample")}}