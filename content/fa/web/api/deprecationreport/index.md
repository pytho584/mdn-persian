---
title: DeprecationReport
slug: Web/API/DeprecationReport
page-type: web-api-interface
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.deprecation
---

{{APIRef("Reporting API")}}

دیکشنری `DeprecationReport` از [Reporting API](/en-US/docs/Web/API/Reporting_API) یک گزارش منسوخ‌شدگی (deprecation report) را نمایش می‌دهد.

یک گزارش منسوخ‌شدگی ممکن است هنگامی که یک ویژگی منسوخ‌شده (مثلاً یک متد API منسوخ‌شده) در یک سند استفاده می‌شود، تولید شود. توجه داشته باشید که دریافت گزارش‌های منسوخ‌شدگی مفید به این بستگی دارد که فروشندگان مرورگر این هشدارها را برای ویژگی‌های منسوخ‌شده اضافه کنند.

گزارش‌های این نوع را می‌توان با استفاده از یک {{domxref("ReportingObserver")}} درون یک صفحه مشاهده کرد، و یک نسخه سریال‌شده (serialized) را می‌توان به [نقطه پایانی سرور گزارش‌دهی پیش‌فرض](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) ارسال کرد.

## ویژگی‌های نمونه (Instance properties)

- `body`
  - : بدنه گزارش. این یک شیء با ویژگی‌های زیر است:
    - `id` {{experimental_inline}}
      - : یک رشته (string) که نشان‌دهنده ویژگی یا API منسوخ‌شده است، برای مثال `NavigatorGetUserMedia`. می‌توان از آن برای گروه‌بندی گزارش‌ها بر اساس ویژگی منسوخ‌شده استفاده کرد.
    - `anticipatedRemoval` {{Experimental_Inline}}
      - : یک شیء {{jsxref("Date")}} (که به صورت رشته نمایش داده می‌شود) که تاریخ مورد انتظار حذف ویژگی از مرورگر فعلی را نشان می‌دهد. اگر تاریخ مشخص نباشد، این ویژگی `null` برمی‌گرداند. این مقدار می‌تواند برای اولویت‌بندی هشدارها استفاده شود. اگر این ویژگی به دلیل نامشخص بودن تاریخ `null` برگرداند، باید منسوخ‌شدگی را با اولویت پایین در نظر گرفت.
    - `message` {{experimental_inline}}
      - : یک رشته حاوی توضیح قابل خواندن برای انسان از منسوخ‌شدگی، شامل اطلاعاتی مانند اینکه کدام ویژگی جدیدتر جایگزین آن شده است (در صورت وجود). این معمولاً با پیامی مطابقت دارد که مرورگر در کنسول DevTools خود هنگام استفاده از یک ویژگی منسوخ‌شده نمایش می‌دهد، در صورت وجود.
    - `sourceFile` {{experimental_inline}}
      - : یک رشته حاوی مسیر فایل منبعی که ویژگی منسوخ‌شده در آن استفاده شده است، در صورت مشخص بودن، یا در غیر این صورت `null`.
    - `lineNumber` {{experimental_inline}}
      - : یک عدد که نشان‌دهنده خط در فایل منبعی است که ویژگی منسوخ‌شده در آن استفاده شده است، در صورت مشخص بودن، یا در غیر این صورت `null`.
    - `columnNumber` {{experimental_inline}}
      - : یک عدد که نشان‌دهنده موقعیت کاراکتر در خط فایل منبعی است که ویژگی منسوخ‌شده برای اولین بار در آن استفاده شده است، در صورت مشخص بودن، یا در غیر این صورت `null`.
- `type`
  - : رشته `"deprecation"` که نشان می‌دهد این یک گزارش منسوخ‌شدگی است.
- `url`
  - : رشته‌ای که URL سندی را که گزارش را تولید کرده است نشان می‌دهد.

## توضیحات

یک گزارش منسوخ‌شدگی ممکن است هنگامی که یک ویژگی منسوخ‌شده (مثلاً یک متد API منسوخ‌شده) در یک سند استفاده می‌شود، تولید شود.

می‌توانید گزارش‌های منسوخ‌شدگی را در صفحه‌ای که در آن فعال می‌شوند با استفاده از [Reporting API](/en-US/docs/Web/API/Reporting_API) نظارت کنید. برای این کار یک شیء {{domxref("ReportingObserver")}} برای گوش دادن به گزارش‌ها ایجاد می‌کنید، یک متد بازخورد (callback) و به صورت اختیاری یک ویژگی `options` که انواع گزارش‌هایی را که می‌خواهید گزارش دهید مشخص می‌کند، ارسال می‌کنید. سپس متد بازخورد با گزارش‌های انواع درخواست‌شده فراخوانی می‌شود و یک شیء گزارش را ارسال می‌کند. برای گزارش‌های منسوخ‌شدگی، شیء یک نمونه `DeprecationReport` خواهد بود (که ویژگی [`type`](#type) آن روی `"deprecation"` تنظیم شده است).

یک گزارش منسوخ‌شدگی معمولی در زیر نشان داده شده است. توجه داشته باشید که `url` نمایانگر صفحه اصلی است که بارگذاری شده است، در حالی که `body.sourceFile`، `body.lineNumber` و `body.columnNumber` مکان خاص فراخوانی API را که باعث مداخله (intervention) شده است نشان می‌دهند (در این مثال آنها فایل یکسانی هستند).

```json
{
  "type": "deprecation",
  "url": "https://example.com/",
  "body": {
    "sourceFile": "https://example.com/",
    "lineNumber": 54,
    "columnNumber": 11,
    "id": "XMLHttpRequestSynchronousInNonWorkerOutsideBeforeUnload",
    "message": "Synchronous `XMLHttpRequest` on the main thread is deprecated because of its detrimental effects to the end user's experience. For more help, check https://xhr.spec.whatwg.org/.",
    "anticipatedRemoval": null
  }
}
```

گزارش‌های منسوخ‌شدگی همچنین به عنوان یک شیء JSON در یک درخواست {{httpmethod("POST")}} به [نقطه پایانی سرور گزارش‌دهی](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) به نام `"default"` ارسال می‌شوند، در صورت تعریف شدن. نقطه پایانی سرور گزارش‌دهی و نگاشت آن به یک URL خاص با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تنظیم می‌شود.

ساختار گزارش سرور تقریباً دقیقاً مشابه `DeprecationReport` است، با این تفاوت که به طور اضافی فیلدهای `age` و `user_agent` را شامل می‌شود.

```json
{
  "type": "deprecation",
  "age": 27,
  "url": "https://example.com/",
  "user_agent": "Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0",
  "body": {
    "sourceFile": "https://example.com/",
    "lineNumber": 54,
    "columnNumber": 11,
    "id": "XMLHttpRequestSynchronousInNonWorkerOutsideBeforeUnload",
    "message": "Synchronous `XMLHttpRequest` on the main thread is deprecated because of its detrimental effects to the end user's experience. For more help, check https://xhr.spec.whatwg.org/.",
    "anticipatedRemoval": null
  }
}
```

## مثال‌ها

### استفاده از رابط `ReportingObserver`

این مثال نشان می‌دهد که چگونه گزارش‌های `"deprecation"` را در صفحه‌ای که آنها را فعال می‌کند مشاهده کنید.

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 200px;
  margin: 10px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### JavaScript

ابتدا یک شیء جدید {{domxref("ReportingObserver")}} می‌سازیم تا به گزارش‌هایی با نوع `"deprecation"` گوش دهد، و یک بازخورد (callback) ارسال می‌کنیم که گزارش‌ها را دریافت کرده و ثبت (log) می‌کند.

```js
const options = {
  types: ["deprecation"],
  buffered: true,
};

const observer = new ReportingObserver((reports, observer) => {
  reports.forEach((report) => {
    log(JSON.stringify(report, null, 2));
  });
}, options);

// شروع observer
observer.observe();
```

سپس کد زیر را فراخوانی می‌کنیم که از XHR همزمان (synchronous) (API منسوخ‌شده) استفاده می‌کند. توجه داشته باشید که این کد پس از تعریف observer تعریف شده است و پس از اجرای observer فعال می‌شود.

```js
const xhr = new XMLHttpRequest();
xhr.open("GET", "/", false); // false = synchronous (deprecated)
xhr.send();
```

#### نتایج

در مرورگرهایی که از گزارش‌های منسوخ‌شدگی پشتیبانی می‌کنند، یک گزارش در زیر نمایش داده می‌شود. توجه داشته باشید که `type` برابر با `"deprecation"` است.

{{EmbedLiveSample("Using the `ReportingObserver` interface", "100%", "280px")}}

### ارسال گزارش به یک نقطه پایانی گزارش‌دهی

پیکربندی یک صفحه وب برای ارسال گزارش منسوخ‌شدگی نیاز دارد که یک [نقطه پایانی سرور گزارش‌دهی](/en-US/docs/Web/API/Reporting_API#reporting_server_endpoints) به نام "default" با استفاده از هدر {{httpheader("Reporting-Endpoints")}} تنظیم کنید. در زیر نقطه پایانی `default` را به `https://example.com/deprecation` تنظیم می‌کنیم:

سپس گزارش به عنوان یک شیء JSON در یک درخواست {{httpmethod("POST")}} به نقطه پایانی ارسال می‌شود هرگاه یک API منسوخ‌شده استفاده شود. این ساختار مشابه `DeprecationReport` دارد، به جز اضافه شدن ویژگی‌های `age` و `user_agent`.

```json
[
  {
    "type": "deprecation",
    "age": 27,
    "url": "https://example.com/",
    "user_agent": "Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0",
    "body": {
      "sourceFile": "https://example.com/",
      "lineNumber": 54,
      "columnNumber": 11,
      "id": "XMLHttpRequestSynchronousInNonWorkerOutsideBeforeUnload",
      "message": "Synchronous `XMLHttpRequest` on the main thread is deprecated because of its detrimental effects to the end user's experience. For more help, check https://xhr.spec.whatwg.org/.",
      "anticipatedRemoval": null
    }
  }
]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ReportingObserver")}}
- {{HTTPHeader("Reporting-Endpoints")}}
- [Reporting API](/en-US/docs/Web/API/Reporting_API)
- [The Reporting API](https://developer.chrome.com/docs/capabilities/web-apis/reporting-api) (developer.chrome.com)