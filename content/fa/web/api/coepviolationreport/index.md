---
title: "COEPViolationReport"
---

---
title: COEPViolationReport
slug: Web/API/COEPViolationReport
page-type: web-api-interface
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.coep
spec-urls:
  - https://html.spec.whatwg.org/multipage/browsers.html#embedder-policy-checks
  - https://html.spec.whatwg.org/multipage/browsers.html#coep
---

{{APIRef("Reporting API")}}

دیکشنری `COEPViolationReport` از [Reporting API](/en-US/docs/Web/API/Reporting_API) نشان‌دهنده گزارشی است که زمانی تولید می‌شود که یک سند خط‌مشی {{httpheader("Cross-Origin-Embedder-Policy")}} (COEP) خود را نقض کند.

گزارش‌های این نوع را می‌توان در یک صفحه با استفاده از {{domxref("ReportingObserver")}} مشاهده کرد، یا یک نسخه سریال‌شده را به یک [نقطه پایانی سرور گزارش‌دهی](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) ارسال نمود.

## ویژگی‌های نمونه

- `body`
  - : بدنه گزارش. این یک شیء با ویژگی‌های زیر است:
    - `type`
      - : رشته‌ای است که دلیل نقضی که باعث تولید گزارش شده را نشان می‌دهد. این مقدار یکی از مقادیر زیر را دارد:
        - `"corp"`
          - : یک سند با {{httpheader("Cross-Origin-Embedder-Policy")}} تنظیم‌شده روی [`require-corp`](/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Embedder-Policy#require-corp) تلاش کرد یک زیرمنبع متقاطع-خاستگاه (cross-origin) را بارگذاری کند که به صراحت اجازه جاسازی شدن خود را نمی‌دهد (با تنظیم یک {{httpheader("Cross-Origin-Resource-Policy")}} مناسب).
        - `"navigation"`
          - : یک عنصر {{htmlelement("iframe")}} در سندی که دارای دستورهای COEP `require-corp` یا `credentialless` است، سندی را بارگذاری می‌کند که:
            - نه دستور COEP `require-corp` و نه `credentialless` را دارد
            - با سند جاسازیکننده متقاطع-خاستگاه است و هدر CORP ندارد که اجازه جاسازی در والد را بدهد.
        - `"worker initialization"`
          - : یک worker اختصاصی که توسط سندی با دستورهای COEP `require-corp` یا `credentialless` ایجاد شده است، تلاش می‌کند یک اسکریپت worker را بارگذاری کند بدون اینکه هیچ‌یک از این‌ها تنظیم شده باشند.
    - `blockedURL`
      - : رشته‌ای حاوی URL منبعی که به دلیل یک نقض COEP اعمال‌شده (enforced) از بارگذاری مسدود شده است.
    - `destination` {{non-standard_inline}}
      - : رشته‌ای که _مقصد_ منبع مسدودشده را نشان می‌دهد. این مقدار یکی از مقادیر [`Request.destination`](/en-US/docs/Web/API/Request/destination#value) را دارد.
    - `disposition`
      - : رشته‌ای که نشان می‌دهد نقض اعمال شده است یا فقط گزارش شده است. این مقدار یکی از مقادیر زیر را دارد:
        - `"enforce"`
          - : نقض باعث مسدود شدن بارگذاری منبع جاسازی‌شده شد. این مقدار برای نقض‌های خط‌مشی‌هایی تنظیم می‌شود که با {{httpheader("Cross-Origin-Embedder-Policy")}} تعیین شده‌اند.
        - `"reporting"`
          - : نقض بدون مسدود کردن بارگذاری منبع گزارش شد. این مقدار برای نقض‌های خط‌مشی‌هایی تنظیم می‌شود که با {{httpheader("Cross-Origin-Embedder-Policy-Report-Only")}} تعیین شده‌اند.
- `type`
  - : رشته `"coep"` که نشان می‌دهد این یک گزارش نقض COEP است.
- `url`
  - : رشته‌ای که URL سند تولیدکننده گزارش را نشان می‌دهد.

## توضیحات

خط‌مشی‌های یک سند برای بارگذاری و جاسازی منابع متقاطع-خاستگاه که در حالت `no-cors` درخواست می‌شوند، با استفاده از هدر HTTP {{httpheader("Cross-Origin-Embedder-Policy")}} پیکربندی و اعمال می‌شوند، و همچنین می‌توانند با استفاده از هدر {{httpheader("Cross-Origin-Embedder-Policy-Report-Only")}} گزارش شوند، اما اعمال نشوند.

نقض‌های خط‌مشی COEP ممکن است هر بار گزارش شوند که یک خط‌مشی تنظیم‌شده توسط آن هدرها بارگذاری یک منبع را مسدود کند (یا مسدود خواهد کرد).

می‌توانید گزارش‌های نقض COEP را در صفحه‌ای که خط‌مشی را تنظیم می‌کند با استفاده از [Reporting API](/en-US/docs/Web/API/Reporting_API) نظارت کنید. برای این کار یک شیء {{domxref("ReportingObserver")}} برای گوش دادن به گزارش‌ها ایجاد می‌کنید و یک متد callback و یک ویژگی (اختیاری) `options` که انواع گزارش‌هایی را که می‌خواهید دریافت کنید مشخص می‌کند، به آن پاس می‌دهید. سپس متد callback با گزارش‌های نوع درخواستی فراخوانی می‌شود و یک شیء گزارش به آن داده می‌شود. برای نقض‌های COEP، شیء یک `COEPViolationReport` خواهد بود (که ویژگی [`type`](#type) آن روی `"coep"` تنظیم شده است).

ساختار یک گزارش معمولی در زیر نشان داده شده است. توجه کنید که می‌توانیم URL صفحه‌ای که خط‌مشی آن نقض شده (`url`) و منبعی که از بارگذاری مسدود شده (`body.blockedURL`) را ببینیم. همچنین می‌توانیم ببینیم که گزارش توسط یک نقض `corp` ایجاد شده است، و از `body.disposition` متوجه می‌شویم که اعمال شده (و نه فقط گزارش شده).

```json
{
  "type": "coep",
  "url": "https://url-of-page-attempting-to-load-resource-in-violation",
  "body": {
    "type": "corp",
    "blockedURL": "https://url-of-blocked-resource",
    "destination": "image",
    "disposition": "enforce"
  }
}
```

گزارش‌های نقض همچنین ممکن است به عنوان یک شیء JSON در یک درخواست `POST` به یک [نقطه پایانی سرور گزارش‌دهی](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) پیکربندی‌شده ارسال شوند. نام نقطه پایانی سرور گزارش‌دهی در دستور خط‌مشی [`report-to`](/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Embedder-Policy#report-to_endpoint_name) هدر {{httpheader("Cross-Origin-Embedder-Policy")}} یا {{httpheader("Cross-Origin-Embedder-Policy-Report-Only")}} مشخص می‌شود. نام‌های نقطه پایانی معتبر و نگاشت آن‌ها به یک URL خاص با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تعریف می‌شوند.

ساختار گزارش سرور تقریباً دقیقاً مشابه `COEPViolationReport` است، با این تفاوت که به‌علاوه شامل فیلدهای `age` و `user_agent` می‌شود.

```json
[
  {
    "age": 967132,
    "body": {
      "blockedURL": "https://url-of-resource-that-was-blocked",
      "destination": "image",
      "disposition": "enforce",
      "type": "corp"
    },
    "type": "coep",
    "url": "https://url-of-document-that-generated-report",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/143.0.0.0 Safari/537.36"
  }
]
```

## مثال‌ها

### استفاده از رابط `ReportingObserver`

این مثال نشان می‌دهد چگونه می‌توانید گزارش‌های نقض COEP را با استفاده از {{domxref("ReportingObserver")}} دریافت کنید.

ابتدا حالتی را در نظر بگیرید که یک فایل HTML در خاستگاه `https://example.com` میزبان می‌شود، که شامل یک عنصر {{htmlelement("img")}} است که منبع (متقاطع-خاستگاه) `some-image.png` را به عنوان منبع خود تنظیم می‌کند. از آنجا که این عنصر ویژگی [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) را تنظیم نمی‌کند، در حالت `no-cors` درخواست داده می‌شود. به‌طور پیش‌فرض، اگر `some-image.png` با هدر {{httpheader("Cross-Origin-Embedder-Policy")}} سرو نشود، این درخواست موفق خواهد بود.

```html
<img src="https://another-example.com/some-image.png" />
```

برای اطمینان از اینکه سند فقط منابع متقاطع-خاستگاهی را بارگذاری می‌کند که نشان می‌دهند برای بارگذاری در خاستگاه سند ما ایمن هستند، می‌توانیم هدر {{httpheader("Cross-Origin-Embedder-Policy")}} را با دستور [`require-corp`](/en-US/docs/Web/HTTP/Reference/Headers/Cross-Origin-Embedder-Policy#require-corp) به صورت زیر تنظیم کنیم:

```http
Cross-Origin-Embedder-Policy: require-corp
```

این هدر الزام می‌کند که همه منابع باید با هدر {{HTTPHeader("Cross-Origin-Resource-Policy")}} و مقدار `cross-origin` سرو شوند تا بتوانند در خاستگاه سند (`https://example.com`) بارگذاری شوند. اگر سرور میزبان `some-image.png` این هدر را تنظیم نکند، برای ایجاد یک نقض COEP نیازی به کار دیگری نداریم.

برای مشاهده نقض‌ها در صفحه، یک شیء جدید {{domxref("ReportingObserver")}} می‌سازیم تا به گزارش‌هایی با نوع `"coep"` گوش دهد و یک callback به آن می‌دهیم که گزارش‌ها را دریافت و ثبت کند. این کد باید قبل از اسکریپتی که باعث نقض می‌شود بارگذاری شود:

```js
const options = {
  types: ["coep"],
  buffered: true,
};

const observer = new ReportingObserver((reports, observer) => {
  reports.forEach((violation) => {
    console.log(violation);
    console.log(JSON.stringify(violation));
  });
}, options);

observer.observe();
```

در بالا، هر شیء گزارش نقض و نسخه رشته‌ای JSON از شیء را ثبت می‌کنیم که ممکن است مشابه شیء زیر باشد. توجه کنید که `type` برابر `"coep"` است.

```json
{
  "type": "coep",
  "url": "https://example.com",
  "body": {
    "type": "corp",
    "blockedURL": "https://another-example.com/some-image.png",
    "destination": "image",
    "disposition": "enforce"
  }
}
```

همان گزارش می‌تواند با استفاده از {{httpheader("Cross-Origin-Embedder-Policy-Report-Only")}} تولید شود، با این تفاوت که [disposition](#disposition) به صورت `"reporting"` گزارش می‌شود.

### ارسال گزارش به یک نقطه پایانی گزارش‌دهی

پیکربندی یک صفحه وب برای ارسال گزارش COEP به یک [نقطه پایانی سرور گزارش‌دهی](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) تقریباً مانند مثال قبلی است. تنها تفاوت این است که باید یک نقطه پایانی گزارش‌دهی مشخص کنیم که می‌خواهیم گزارش‌ها به آنجا ارسال شوند، با استفاده از هدر پاسخ {{httpheader("Reporting-Endpoints")}}، و سپس هنگام تنظیم خط‌مشی به این‌ها در پارامتر `report-to` ارجاع دهیم.

این را در زیر می‌بینید، جایی که نقطه پایانی به نام `coep-endpoint` را تعریف می‌کنیم و سپس در خط‌مشی خود به آن ارجاع می‌دهیم:

```http
Reporting-Endpoints: coep-endpoint="https://some-example.com/coep"
Cross-Origin-Embedder-Policy: require-corp; report-to="coep-endpoint"
```

سپس گزارش نقض به عنوان یک شیء JSON در یک درخواست `POST` به نقطه پایانی ارجاع‌داده‌شده توسط `coep-endpoint` ارسال می‌شود.

شیء گزارش ساختاری مشابه با آنچه از callback `ReportingObserver` برمی‌گردد دارد، به‌جز افزودن ویژگی‌های `age` و `user_agent`.

```json
[
  {
    "age": 717139,
    "body": {
      "blockedURL": "https://another-example.com/some-image.png",
      "destination": "image",
      "disposition": "enforce",
      "type": "corp"
    },
    "type": "coep",
    "url": "https://example.com",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/143.0.0.0 Safari/537.36"
  }
]
```

همان گزارش تولید می‌شود اگر {{httpheader("Cross-Origin-Embedder-Policy-Report-Only")}} را به همان روش تنظیم کنیم، به‌جز اینکه [disposition](#disposition) روی `"reporting"` تنظیم می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ReportingObserver")}}
- {{httpheader("Cross-Origin-Embedder-Policy")}}
- {{httpheader("Cross-Origin-Embedder-Policy-Report-Only")}}
- {{HTTPHeader("Reporting-Endpoints")}}
- [Reporting API](/en-US/docs/Web/API/Reporting_API)
- [The Reporting API](https://developer.chrome.com/docs/capabilities/web-apis/reporting-api) (developer.chrome.com)