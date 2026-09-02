---
title: "InterventionReport"
---

---
title: InterventionReport
slug: Web/API/InterventionReport
page-type: web-api-interface
status:
  - experimental
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.intervention
---

{{APIRef("Reporting API")}}{{SeeCompatTable}}

دیکشنری `InterventionReport` از [Reporting API](/en-US/docs/Web/API/Reporting_API) یک گزارش مداخله را نشان می‌دهد.

یک گزارش مداخله ممکن است زمانی تولید شود که استفاده از یک قابلیت در یک سند وب توسط مرورگر به دلایلی مانند امنیت، کارایی یا آزار کاربر مسدود شده باشد. این نوع گزارش‌ها را می‌توان از داخل یک صفحه با استفاده از {{domxref("ReportingObserver")}} مشاهده کرد و یک نسخه سریال‌سازی‌شده را می‌توان به [نقطه پایان سرور گزارش‌گیری](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) ارسال کرد.

## ویژگی‌های نمونه

- `body`
  - : بدنه گزارش.
    این یک شیء با ویژگی‌های زیر است:
    - `columnNumber` {{experimental_inline}}
      - : یک رشته که موقعیت کاراکتر را در خط فایل منبع که مداخله در آن رخ داده است نشان می‌دهد، در صورت مشخص بودن، یا در غیر این صورت `null`.

    - `id` {{experimental_inline}}
      - : یک رشته که نشان‌دهنده مداخله‌ای است که گزارش را تولید کرده است. این مقدار می‌تواند برای گروه‌بندی گزارش‌ها استفاده شود.

    - `lineNumber` {{experimental_inline}}
      - : یک رشته که خط فایل منبع را که مداخله در آن رخ داده است نشان می‌دهد، در صورت مشخص بودن، یا در غیر این صورت `null`.

    - `message` {{experimental_inline}}
      - : یک رشته حاوی توصیف قابل‌خواندن برای انسان از مداخله، از جمله اطلاعاتی مانند اینکه چگونه می‌توان از مداخله اجتناب کرد. این مقدار معمولاً با پیامی که مرورگر در کنسول DevTools خود هنگام اعمال مداخله نمایش می‌دهد، در صورت وجود، مطابقت دارد.

    - `sourceFile` {{experimental_inline}}
      - : یک رشته حاوی مسیر فایل منبع که ابتدا از API مشخص‌شده استفاده کرده (و باعث مداخله شده است)، در صورت مشخص بودن، یا در غیر این صورت `null`.

- `type`
  - : رشته `"intervention"` که نشان می‌دهد این یک گزارش مداخله است.

- `url`
  - : یک رشته که URL سندی که گزارش را تولید کرده است نشان می‌دهد.

## توضیحات

یک گزارش مداخله ممکن است زمانی تولید شود که استفاده از یک قابلیت در یک سند وب توسط مرورگر به دلایلی مانند امنیت، کارایی یا آزار کاربر مسدود شده باشد. برای مثال، یک تبلیغ می‌تواند [Heavy Ad Intervention](https://developer.chrome.com/docs/web-platform/heavy-ads-intervention) را (developer.chrome.com) فعال کند اگر سرعت پاسخ‌دهی صفحه را کاهش دهد یا به نحوی دیگر تجربه کاربری را تحت تأثیر قرار دهد.

می‌توانید گزارش‌های مداخله را در همان صفحه‌ای که فعال شده‌اند با استفاده از [Reporting API](/en-US/docs/Web/API/Reporting_API) پایش کنید. برای این کار یک شیء {{domxref("ReportingObserver")}} می‌سازید تا به گزارش‌ها گوش دهد و یک متد callback و یک ویژگی (اختیاری) options که انواع گزارش‌هایی را که می‌خواهید دریافت کنید مشخص می‌کند، به آن منتقل می‌کنید. سپس متد callback با گزارش‌های نوع‌های درخواست‌شده فراخوانی می‌شود و یک شیء گزارش به آن داده می‌شود. برای گزارش‌های مداخله، این شیء یک نمونه `InterventionReport` خواهد بود (که ویژگی [`type`](#type) آن روی `"intervention"` تنظیم شده است).

یک گزارش مداخله معمولی در زیر نشان داده شده است (کپی شده از مشخصات). توجه کنید که `url` صفحه اصلی بارگذاری‌شده را نشان می‌دهد، در حالی که `body.sourceFile`، `body.lineNumber` و `body.columnNumber` مکان دقیق فراخوانی API را که باعث مداخله شده است مشخص می‌کنند.

```json
{
  "type": "intervention",
  "url": "https://example.com/",
  "body": {
    "id": "audio-no-gesture",
    "message": "A request to play audio was blocked because it was not triggered by user activation (such as a click).",
    "sourceFile": "https://example.com/index.js",
    "lineNumber": 1234,
    "columnNumber": 42
  }
}
```

گزارش‌های مداخله همچنین به صورت یک شیء JSON در یک درخواست {{httpmethod("POST")}} به [نقطه پایان سرور گزارش‌گیری](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) به نام `"default"` ارسال می‌شوند، در صورتی که تعریف شده باشد. نقطه پایان سرور گزارش‌گیری و نگاشت آن به یک URL خاص با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تنظیم می‌شود.

ساختار گزارش سرور تقریباً دقیقاً مشابه `InterventionReport` است، با این تفاوت که به‌علاوه شامل فیلدهای `age` و `user_agent` است.

```json
{
  "type": "intervention",
  "age": 27,
  "url": "https://example.com/",
  "user_agent": "Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0",
  "body": {
    "id": "audio-no-gesture",
    "message": "A request to play audio was blocked because it was not triggered by user activation (such as a click).",
    "sourceFile": "https://example.com/index.js",
    "lineNumber": 1234,
    "columnNumber": 42
  }
}
```

## مثال‌ها

### استفاده از رابط `ReportingObserver`

برای مشاهده گزارش‌های مداخله در داخل صفحه، یک شیء جدید {{domxref("ReportingObserver")}} می‌سازیم تا به گزارش‌هایی با نوع `"intervention"` گوش دهد و یک callback به آن منتقل می‌کنیم که گزارش‌ها را دریافت و ثبت (log) می‌کند. این کد باید قبل از اسکریپتی که باعث تخلف می‌شود بارگذاری شود:

```js
const options = {
  types: ["intervention"],
  buffered: true,
};

const observer = new ReportingObserver((reports, observer) => {
  reports.forEach((report) => {
    console.log(report);
    console.log(JSON.stringify(report));
  });
}, options);

// Start the observer
observer.observe();
```

نسخه رشته‌شده (stringified) گزارش ممکن است مشابه شیء زیر باشد. توجه کنید که `type` برابر با `"intervention"` است.

```json
{
  "type": "intervention",
  "url": "https://example.com/",
  "body": {
    "id": "audio-no-gesture",
    "message": "A request to play audio was blocked because it was not triggered by user activation (such as a click).",
    "sourceFile": "https://example.com/index.js",
    "lineNumber": 1234,
    "columnNumber": 42
  }
}
```

### ارسال گزارش به یک نقطه پایان گزارش‌گیری

پیکربندی یک صفحه وب برای ارسال گزارش مداخله مستلزم این است که یک [نقطه پایان سرور گزارش‌گیری](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) به نام "default" با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تنظیم کنید. در زیر، نقطه پایان `default` را روی `https://example.com/intervention` تنظیم می‌کنیم:

گزارش سپس به صورت یک شیء JSON در یک درخواست {{httpmethod("POST")}} به نقطه پایان ارسال می‌شود هر زمان که مداخله‌ای رخ دهد. ساختار آن همان ساختار `InterventionReport` است، به‌جز افزوده شدن ویژگی‌های `age` و `user_agent`.

```json
[
  {
    "type": "intervention",
    "age": 27,
    "url": "https://example.com/",
    "user_agent": "Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0",
    "body": {
      "id": "audio-no-gesture",
      "message": "A request to play audio was blocked because it was not triggered by user activation (such as a click).",
      "sourceFile": "https://example.com/index.js",
      "lineNumber": 1234,
      "columnNumber": 42
    }
  }
]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ReportingObserver")}}
- {{HTTPHeader("Reporting-Endpoints")}}
- [Reporting API](/en-US/docs/Web/API/Reporting_API)
- [The Reporting API](https://developer.chrome.com/docs/capabilities/web-apis/reporting-api) (developer.chrome.com)