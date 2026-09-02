---
title: "IntegrityViolationReport"
---

---
title: IntegrityViolationReport
slug: Web/API/IntegrityViolationReport
page-type: web-api-interface
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.integrity-violation
spec-urls: https://w3c.github.io/webappsec-subresource-integrity/#report-violations
---

{{APIRef("Reporting API")}}

دیکشنری `IntegrityViolationReport` از [API Reporting](/en-US/docs/Web/API/Reporting_API) گزارشی را نشان می‌دهد که وقتی یک سند [خط‌مشی یکپارچگی](/en-US/docs/Web/HTTP/Reference/Headers/Integrity-Policy) خود را نقض می‌کند تولید می‌شود.

گزارش‌های این نوع را می‌توان از داخل یک صفحه با استفاده از {{domxref("ReportingObserver")}} مشاهده کرد و نسخهٔ سریال‌سازی‌شدهٔ آن را می‌توان به یک [نقطه پایانی سرور گزارش‌گیری](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) ارسال کرد.

## ویژگی‌های نمونه

- `body`
  - : بدنهٔ گزارش. این یک شیء با ویژگی‌های زیر است:
    - `blockedURL`
      - : رشته‌ای که URL منبع مسدودشده توسط یک خط‌مشی یکپارچگی اعمال‌شده (یا فقط برای یک خط‌مشی [`reportOnly`](#reportonly) گزارش‌شده) را نشان می‌دهد.
    - `documentURL`
      - : رشته‌ای که URL سندی را نشان می‌دهد که در تلاش برای بارگذاری منبع است.
    - `destination`
      - : رشته‌ای که [`Request.destination`](/en-US/docs/Web/API/Request/destination#script) منبع مسدودشده را نشان می‌دهد. در حال حاضر فقط می‌تواند `"script"` باشد.
    - `reportOnly`
      - : یک مقدار بولی: اگر خط‌مشی اعمال شده باشد `false` و اگر تخلف فقط گزارش شده باشد `true`. این مقادیر نشان می‌دهند که خط‌مشی به ترتیب با {{httpheader("Integrity-Policy")}} و {{httpheader("Integrity-Policy-Report-Only")}} تنظیم شده است.

- `type`
  - : رشتهٔ `"integrity-violation"` که نشان می‌دهد این یک گزارش تخلف یکپارچگی است.
- `url`
  - : رشته‌ای که URL سند تولیدکنندهٔ گزارش را نشان می‌دهد.

## توضیحات

تخلف‌های خط‌مشی یکپارچگی زمانی گزارش می‌شوند که یک سند تلاش کند منبعی را بارگذاری کند که تضمین‌های Subresource Integrity خط‌مشی تنظیم‌شده با استفاده از هدرهای HTTP {{httpheader("Integrity-Policy")}} یا {{httpheader("Integrity-Policy-Report-Only")}} را برآورده نمی‌کند.

به‌طور خاص، یک گزارش زمانی ارسال می‌شود که یک سند تلاش کند منبع {{htmlelement("script")}} (یا دیگر [مقصدهای درخواست](/en-US/docs/Web/API/Request/destination) فهرست‌شده در خط‌مشی) را بارگذاری کند که فرادادهٔ یکپارچگی معتبری ندارد، یا درخواستی را در حالت [no-cors](/en-US/docs/Web/API/Request/mode#no-cors) ارسال کند.

می‌توانید گزارش‌های تخلف یکپارچگی را در داخل صفحه‌ای که خط‌مشی را تنظیم می‌کند، با استفاده از [Reporting API](/en-US/docs/Web/API/Reporting_API) پایش کنید. برای این کار یک شیء {{domxref("ReportingObserver")}} می‌سازید تا به گزارش‌ها گوش دهد و یک متد callback و یک ویژگی (اختیاری) `options` به آن می‌دهید که انواع گزارش‌هایی را که می‌خواهید دریافت کنید مشخص می‌کند. سپس متد callback با گزارش‌های انواع درخواستی فراخوانی می‌شود و یک شیء گزارش به آن ارسال می‌شود. برای تخلف‌های یکپارچگی، شیء یک نمونهٔ `IntegrityViolationReport` خواهد بود (که ویژگی [`type`](#type) آن روی `"integrity-violation"` تنظیم شده است).

ساختار یک گزارش معمولی در زیر نشان داده شده است. توجه کنید که می‌توانیم URL صفحه‌ای را که خط‌مشی آن نقض شده است (`url`)، سندی را که تلاش کرده منبع را بارگذاری کند (`body.documentURL`)، و منبعی را که از بارگذاری مسدود شده است (`body.blockedURL`) ببینیم. همچنین می‌توانیم ببینیم که گزارش به دلیل بارگذاری یک اسکریپت بوده است و توسط یک تخلف اعمال‌شده (و نه فقط گزارش‌شده) ایجاد شده است.

```json
{
  "type": "integrity-violation",
  "url": "https://url-of-page-attempting-to-load-resource-in-violation",
  "body": {
    "documentURL": "https://localhost:8443/",
    "blockedURL": "https://url-of-blocked-resource.js",
    "destination": "script",
    "reportOnly": false
  }
}
```

گزارش‌های تخلف همچنین ممکن است به‌صورت یک شیء JSON در یک درخواست {{httpmethod("POST")}} به یک یا چند [نقطه پایانی سرور گزارش‌گیری](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) پیکربندی‌شده ارسال شوند. نام نقاط پایانی سرور گزارش‌گیری هنگام تنظیم {{httpheader("Integrity-Policy")}} یا {{httpheader("Integrity-Policy-Report-Only")}} در [فهرست `endpoints`](/en-US/docs/Web/HTTP/Reference/Headers/Integrity-Policy#endpoints) مشخص می‌شوند. نام‌های معتبر نقاط پایانی و نگاشت آن‌ها به یک URL خاص با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تعریف می‌شوند.

ساختار گزارش سرور تقریباً دقیقاً همانند `IntegrityViolationReport` است، با این تفاوت که به‌طور اضافی شامل فیلدهای `age` و `user_agent` می‌شود.

```json
{
  "age": "176279",
  "body": {
    "documentURL": "https://localhost:8443/",
    "blockedURL": "https://url-of-blocked-resource.js",
    "destination": "script",
    "reportOnly": false
  },
  "type": "integrity-violation",
  "url": "https://url-of-page-attempting-to-load-resource-in-violation",
  "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36"
}
```

## مثال‌ها

### استفاده از رابط `ReportingObserver`

این مثال نشان می‌دهد که چگونه می‌توانید گزارش‌های تخلف خط‌مشی یکپارچگی را با استفاده از {{domxref("ReportingObserver")}} دریافت کنید.

ابتدا خط‌مشی یکپارچگی یک صفحه را با استفاده از هدر {{httpheader("Integrity-Policy")}} تنظیم می‌کنیم. خط‌مشی زیر بارگذاری هر عنصر {{htmlelement("script")}} یا شیء {{domxref("HTMLScriptElement")}} را که ویژگی `integrity` را مشخص نکرده باشد، یا زمانی که یک منبع اسکریپت در حالت [no-cors](/en-US/docs/Web/API/Request/mode#no-cors) درخواست شود، گزارش و مسدود می‌کند. توجه کنید که در این مثال فقط به گزارش تخلف‌ها از طریق API علاقه‌مندیم، بنابراین نقاط پایانی گزارش‌گیری را حذف کرده‌ایم:

```http
Integrity-Policy: blocked-destinations=(script)
```

بعد، فرض می‌کنیم صفحهٔ ما عنصر زیر را برای بارگذاری یک اسکریپت شامل است. چون می‌خواهیم تخلفی ایجاد کنیم، ویژگی `integrity` را که برای بررسی مطابقت اسکریپت با نسخهٔ مورد انتظار استفاده می‌شود حذف کرده‌ایم. همچنین می‌توانیم ویژگی `cross-origin` را حذف کنیم تا درخواست در حالت `no-cors` ارسال شود.

```html
<script
  src="https://example.com/example-framework.js"
  crossorigin="anonymous"></script>
```

> [!NOTE]
> یک اسکریپت که با خط‌مشی مطابقت دارد ممکن است به این شکل باشد:
>
> ```html
> <script
>   src="https://example.com/example-framework.js"
>   integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC"
>   crossorigin="anonymous"></script>
> ```

برای مشاهدهٔ تخلف‌ها در داخل صفحه، یک شیء جدید {{domxref("ReportingObserver")}} می‌سازیم تا به گزارش‌هایی از نوع `"integrity-violation"` گوش دهد و یک callback به آن می‌دهیم که گزارش‌ها را دریافت و ثبت کند. این کد باید قبل از اسکریپتی که باعث تخلف می‌شود، در همان صفحه بارگذاری شود:

```js
const observer = new ReportingObserver(
  (reports, observer) => {
    reports.forEach((violation) => {
      console.log(violation);
      console.log(JSON.stringify(violation));
    });
  },
  {
    types: ["integrity-violation"],
    buffered: true,
  },
);

observer.observe();
```

در بالا، هر شیء گزارش تخلف و نسخهٔ JSON-رشته‌ای آن شیء را ثبت می‌کنیم که ممکن است مشابه شیء زیر باشد.

```json
{
  "type": "integrity-violation",
  "url": "https://example.com",
  "body": {
    "documentURL": "https://example.com",
    "blockedURL": "https://example.com/example-framework.js",
    "destination": "script",
    "reportOnly": false
  }
}
```

### ارسال گزارش به یک نقطه پایانی گزارش‌گیری

پیکربندی یک صفحهٔ وب برای ارسال گزارش تخلف خط‌مشی یکپارچگی به یک [نقطه پایانی سرور گزارش‌گیری](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) بسیار شبیه به مثال قبلی است.

تفاوت اصلی این است که باید یک یا چند نقطه پایانی گزارش‌گیری را که می‌خواهیم گزارش‌ها به آن‌جا ارسال شوند، با استفاده از هدر پاسخ {{httpheader("Reporting-Endpoints")}} مشخص کنیم و سپس هنگام تنظیم خط‌مشی به این‌ها در فیلد `endpoints` ارجاع دهیم.

این را در زیر می‌بینید؛ ابتدا دو نقطه پایانی گزارش‌گیری — `integrity-endpoint` و `backup-integrity-endpoint` — تعریف می‌کنیم و سپس در خط‌مشی خود به آن‌ها ارجاع می‌دهیم:

```http
Reporting-Endpoints: integrity-endpoint=https://example.com/integrity, backup-integrity-endpoint=https://report-provider.example/integrity
Integrity-Policy: blocked-destinations=(script), endpoints=(integrity-endpoint, backup-integrity-endpoint)
```

می‌توانیم با بارگذاری یک اسکریپت خارجی از صفحه‌ای که دستورالعمل‌های یکپارچگی زیرمنابع را برآورده نمی‌کند، تخلفی ایجاد کنیم. فقط برای تفاوت با مثال قبلی، در اینجا درخواست را در حالت `no-cors` ارسال می‌کنیم:

```html
<script
  src="https://example.com/example-framework.js"
  integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC"></script>
```

گزارش تخلف سپس به‌صورت یک فایل JSON به نقطه پایانی مشخص‌شده ارسال می‌شود. همان‌طور که در مثال زیر می‌بینید، `type` برابر با `"integrity-violation"` است و ویژگی `body` یک سریال‌سازی از این شیء `IntegrityViolationReport` است:

گزارش در این مورد همانند گزارش JSON مثال قبلی خواهد بود.

```json
{
  "type": "integrity-violation",
  "url": "https://example.com",
  "body": {
    "documentURL": "https://example.com",
    "blockedURL": "https://example.com/example-framework.js",
    "destination": "script",
    "reportOnly": false
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ReportingObserver")}}
- {{HTTPHeader("Integrity-Policy")}}
- {{HTTPHeader("Integrity-Policy-Report-Only")}}
- {{HTTPHeader("Reporting-Endpoints")}}
- [خط‌مشی یکپارچگی](/en-US/docs/Web/Security/Defenses/Subresource_Integrity#integrity_policy) در [یکپارچگی زیرمنابع](/en-US/docs/Web/Security/Defenses/Subresource_Integrity#integrity_policy)
- [Reporting API](/en-US/docs/Web/API/Reporting_API)