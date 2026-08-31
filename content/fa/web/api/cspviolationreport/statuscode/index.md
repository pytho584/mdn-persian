---
title: "CSPViolationReport: statusCode property"
short-title: statusCode
slug: Web/API/CSPViolationReport/statusCode
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

ویژگی **`statusCode`** از دیکشنری {{domxref("CSPViolationReport")}} عددی است که [کد وضعیت HTTP](/en-US/docs/Web/HTTP/Reference/Status) پاسخ به درخواستی را نشان می‌دهد که باعث نقض [خط‌مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) شده است (هنگام بارگذاری یک پنجره یا worker).

## مقدار

عددی که کد وضعیت HTTP پاسخ به درخواست منجر به نقض CSP را نشان می‌دهد.

## مثال‌ها

در این مثال یک {{domxref("ReportingObserver")}} جدید می‌سازیم تا گزارش‌های نقض محتوا از نوع `"csp-violation"` را مشاهده کنیم.
هر بار که تابع callback فراخوانده می‌شود، کد وضعیت اولین ورودی آرایه reports را در کنسول ثبت می‌کنیم.

```js
const observer = new ReportingObserver(
  (reports, observer) => {
    console.log(`statusCode: ${reports[0].body.statusCode}`);
    // For example: 200
  },
  {
    types: ["csp-violation"],
    buffered: true,
  },
);

observer.observe();
```

توجه داشته باشید که اگرچه ممکن است چندین گزارش در آرایه بازگشتی وجود داشته باشد، برای اختصار فقط کد وضعیت اولین گزارش را ثبت می‌کنیم.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.statusCode")}}