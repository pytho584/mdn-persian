---
title: PermissionsPolicyViolationReport
slug: Web/API/PermissionsPolicyViolationReport
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.permissions-policy-violation
---

{{APIRef("Reporting API")}}{{SeeCompatTable}}

دیکشنری `PermissionsPolicyViolationReport` متعلق به [Reporting API](/en-US/docs/Web/API/Reporting_API) نشان‌دهندهٔ گزارشی است که هنگام نقض [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) توسط یک سند (document) تولید می‌شود.

گزارش‌های این نوع را می‌توان از داخل یک صفحه با استفاده از {{domxref("ReportingObserver")}} مشاهده کرد و همچنین یک نسخهٔ سریالایز شده از آن‌ها را می‌توان به یک نقطهٔ پایانی (endpoint) سرور گزارش ارسال کرد.

## ویژگی‌های نمونه

- `body`
  - : بدنهٔ گزارش.
    این یک شیء با ویژگی‌های زیر است:
    - `columnNumber`
      - : موقعیت نویسه (character) در خط اسکریپتی که تخلف در آن رخ داده است؛ یا اگر ناشناخته باشد، `null`.
    - `disposition`
      - : رشته‌ای که نشان می‌دهد سیاستِ نقض‌شده اعمال شده است یا فقط گزارش شده است. این مقدار می‌تواند برای نقض سیاست‌های تنظیم‌شده با {{httpheader("Permissions-Policy")}} برابر `"enforce"` باشد و برای نقض‌های تنظیم‌شده با `Permissions-Policy-Report-Only` برابر `report` باشد.
    - `featureId`
      - : رشته‌ای که نمایانگر [دستور Permissions Policy](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy#directives) نقض‌شده است (برای مثال، `"geolocation"`).
    - `lineNumber`
      - : شمارهٔ خط در اسکریپتی که تخلف در آن رخ داده است؛ یا اگر ناشناخته باشد، `null`.
    - `message`
      - : رشته‌ای شامل توصیفی قابل‌خواندن برای انسان از تخلف.
    - `sourceFile`
      - : رشته‌ای که نشانی URL اسکریپتی را نشان می‌دهد که تخلف در آن رخ داده است؛ یا اگر ناشناخته باشد، `null`. اگر این ویژگی `null` نباشد، هر دو ویژگی `columnNumber` و `lineNumber` باید مقادیری غیر از `null` داشته باشند.

- `type`
  - : رشتهٔ `"permissions-policy-violation"` که نشان می‌دهد این یک گزارش نقض Permissions Policy است.
- `url`
  - : رشته‌ای که نشانی URL سندِ تولیدکنندهٔ گزارش را نشان می‌دهد.

> [!NOTE]
> سریالایز کردن سمت سرور در کروم برای نام ویژگی در بدنهٔ یک گزارش سرور، به‌جای `featureId` از `policyId` استفاده می‌کند. برای سازگاری بین مرورگرها، توسعه‌دهندگان باید هر دو فیلد را در نقطه‌های پایانی گزارش‌دهی پردازش کنند. گزارشی که توسط [`ReportingObserver`](/en-US/docs/Web/API/ReportingObserver) بازگردانده می‌شود مطابق با مشخصات (specification) است.

## توضیحات

نقض‌های Permissions Policy زمانی گزارش می‌شوند که یک سند تلاش کند از قابلیتی در مرورگر استفاده کند که توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) آن مسدود شده است. این سیاست با استفاده از هدر HTTP {{httpheader("Permissions-Policy")}} یا یک عنصر `<meta http-equiv="permissions-policy">` تنظیم می‌شود. همچنین ممکن است نقض‌های سیاست بدون اعمال شدن، فقط با هدر HTTP {{httpheader("Permissions-Policy-Report-Only")}} یا یک عنصر `<meta http-equiv="permissions-policy-report-only">` گزارش شوند.

می‌توانید گزارش‌های نقض Permissions-Policy را در همان صفحه‌ای که سیاست را تنظیم کرده است و با استفاده از [Reporting API](/en-US/docs/Web/API/Reporting_API) پایش کنید. برای این کار یک شیء {{domxref("ReportingObserver")}} می‌سازید تا به گزارش‌ها گوش دهد؛ این سازنده یک متد بازخوانی (callback) و یک ویژگی (اختیاری) `options` شامل انواع گزارش‌هایی که می‌خواهید دریافت کنید را می‌گیرد. سپس متد بازخوانی با گزارش‌های نوع درخواستی فراخوانی می‌شود و یک شیء گزارش به آن داده می‌شود. برای نقض‌های `Permissions-Policy` یا `Permissions-Policy-Report-Only`، آن شیء یک نمونه از `PermissionsPolicyViolationReport` خواهد بود که در آن `PermissionsPolicyViolationReport.type === "permissions-policy-violation"` است.

ساختار یک گزارش نمونهٔ درون‌صفحه‌ای در زیر نشان داده شده است. توجه کنید که می‌توانیم نشانی URL صفحه‌ای را ببینیم که سیاستش نقض شده است (`url`) و از روی `body.featureId` نیز می‌توانیم بفهمیم کدام قابلیت مسدود شده است. فیلد `body.disposition` نشان می‌دهد که تخلف اعمال شده است یا فقط گزارش شده است.

```json
{
  "type": "permissions-policy-violation",
  "url": "https://example.com/",
  "body": {
    "sourceFile": "https://example.com/",
    "lineNumber": 44,
    "columnNumber": 29,
    "featureId": "geolocation",
    "disposition": "enforce", // Policy was enforced!
    "message": "Permissions policy violation: geolocation access has been blocked because of a permissions policy applied to the current document."
  }
}
```

گزارش‌های تخلف همچنین ممکن است به‌صورت یک شیء JSON در یک درخواست {{httpmethod("POST")}} به [نقطهٔ پایانی سرور گزارش‌دهی](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) ارسال شوند؛ این نقطهٔ پایانی با نام در پارامتر `report-to` مربوط به همان دستور (directive) مشخص می‌شود و در صورت تعریف‌نشدن، به [نقطهٔ پایانی پیش‌فرضِ گزارش‌دهی سرور](/en-US/docs/Web/HTTP/Reference/Headers/Reporting-Endpoints#default_reporting_endpoint) برمی‌گردد. نقطهٔ پایانی گزارش‌دهی و نگاشت آن به یک نشانی URL مشخص با استفاده از هدر پاسخ {{httpheader("Reporting-Endpoints")}} تنظیم می‌شود.

ساختار گزارش سرور تقریباً دقیقاً مشابه `PermissionsPolicyViolationReport` است، با این تفاوت که فیلدهای `age` و `user_agent` را نیز به‌صورت اضافه شامل می‌شود.

```json
[
  {
    "age": 48512,
    "body": {
      "columnNumber": 29,
      "disposition": "enforce",
      "lineNumber": 44,
      "message": "Permissions policy violation: geolocation access has been blocked because of a permissions policy applied to the current document.",
      "policyId": "geolocation",
      "sourceFile": "https://example.com/"
    },
    "type": "permissions-policy-violation",
    "url": "https://example.com/",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/146.0.0.0 Safari/537.36"
  }
]
```

## مثال‌ها

### استفاده از رابط `ReportingObserver`

می‌توانید یک شیء `PermissionsPolicyViolationReport` به دست آورید؛ بدین منظور صفحه را طوری پیکربندی می‌کنید که یک قابلیت مرورگر را مسدود کند و سپس تلاش کنید از آن قابلیت استفاده کنید.

در این مثال، ما Geolocation API را برای سند جاری با استفاده از هدر HTTP {{httpheader("Permissions-Policy")}} مسدود می‌کنیم:

```http
Permissions-Policy: geolocation=()
```

یا به‌طور معادل از طریق یک عنصر HTML `<meta>`:

```html
<meta http-equiv="permissions-policy" content="geolocation=()" />
```

سپس تلاش می‌کنیم از Geolocation API استفاده کنیم:

```js
// This should generate a Permissions Policy violation
navigator.geolocation.getCurrentPosition(
  () => {},
  () => {},
);
```

در نهایت، یک شیء جدید {{domxref("ReportingObserver")}} می‌سازیم تا به نقض‌های Permissions Policy گوش دهد (این کد باید پیش از کدی که تخلف را فعال می‌کند بارگذاری شود).

```js
const observer = new ReportingObserver(
  (reports, observer) => {
    reports.forEach((violation) => {
      console.log(violation);
      console.log(JSON.stringify(violation));
    });
  },
  {
    types: ["permissions-policy-violation"],
    buffered: true,
  },
);

observer.observe();
```

در بالا، هر شیء گزارش تخلف و نسخهٔ رشته JSON آن را در کنسول ثبت می‌کنیم؛ خروجی ممکن است شبیه به شیء زیر باشد. توجه کنید که `type` برابر `"permissions-policy-violation"` است و `body.featureId` قابلیت مسدودشده را مشخص می‌کند.

```json
{
  "type": "permissions-policy-violation",
  "url": "https://example.com/",
  "body": {
    "sourceFile": "https://example.com/",
    "lineNumber": 44,
    "columnNumber": 29,
    "featureId": "geolocation",
    "disposition": "enforce",
    "message": "Permissions policy violation: geolocation access has been blocked because of a permissions policy applied to the current document."
  }
}
```

### ارسال گزارش نقض Permissions Policy به یک نقطهٔ پایانی گزارش‌دهی

این مثال نشان می‌دهد که چگونه گزارش نقض‌های `Permissions-Policy` را برای ارسال به یک نقطهٔ پایانی سرور پیکربندی کنید.

هدرهای پاسخ زیر قابلیت موقعیت‌یاب را مسدود می‌کنند و نام نقطهٔ پایانی گزارش‌دهی این ویژگی را «geo_endpoint» تعیین می‌کنند. از هدر پاسخ HTTP {{HTTPHeader("Reporting-Endpoints")}} برای تعیین نشانی URL مربوط به این نام نقطهٔ پایانی استفاده شده است.

```http
Reporting-Endpoints: geo_endpoint="https://example.com/reports"
Permissions-Policy: geolocation=();report-to=geo_endpoint
```

> [!NOTE]
> برای ارسال همهٔ گزارش‌های تخلف به یک نقطهٔ پایانی واحد، می‌توانیم در عوض [نقطهٔ پایانی گزارش‌دهی «default»](/en-US/docs/Web/HTTP/Reference/Headers/Reporting-Endpoints#default_reporting_endpoint) را تعریف کنیم:
>
> ```http
> Reporting-Endpoints: default="https://example.com/reports"
> Permissions-Policy: geolocation=()
> ```

مانند قبل، تخلف با تلاش برای استفاده از یک قابلیت مسدودشده فعال می‌شود:

```js
// This should generate a Permissions Policy violation
navigator.geolocation.getCurrentPosition(
  () => {},
  () => {},
);
```

سپس گزارش تخلف به‌صورت یک آرایه JSON به نقطهٔ پایانی پیش‌فرض ارسال می‌شود. توجه کنید که `type` برابر `"permissions-policy-violation"` است و ویژگی `body` یک سریالایز از شیء `PermissionsPolicyViolationReport` است.

```json
[
  {
    "age": 48512,
    "body": {
      "columnNumber": 29,
      "disposition": "enforce",
      "lineNumber": 44,
      "message": "Permissions policy violation: geolocation access has been blocked because of a permissions policy applied to the current document.",
      "policyId": "geolocation", // Note: Chrome server-report version of featureId
      "sourceFile": "https://example.com/"
    },
    "type": "permissions-policy-violation",
    "url": "https://example.com/",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/146.0.0.0 Safari/537.36"
  }
]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("ReportingObserver")}}
- {{httpheader("Permissions-Policy")}}
- {{httpheader("Permissions-Policy-Report-Only")}}
- {{httpheader("Reporting-Endpoints")}}
- [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)
- [Reporting API](/en-US/docs/Web/API/Reporting_API)