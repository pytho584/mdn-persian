---
title: "HTMLScriptElement: attributionSrc property"
short-title: attributionSrc
slug: Web/API/HTMLScriptElement/attributionSrc
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.HTMLScriptElement.attributionSrc
---

{{APIRef("Attribution Reporting API")}}{{securecontext_header}}{{deprecated_header}}{{non-standard_header}}

خاصیت **`attributionSrc`** در رابط {{domxref("HTMLScriptElement")}}، ویژگی [`attributionsrc`](/en-US/docs/Web/HTML/Reference/Elements/script#attributionsrc) را روی یک عنصر {{htmlelement("script")}} بهصورت برنامهنویسی تنظیم یا دریافت میکند و مقدار آن ویژگی را منعکس میکند. `attributionsrc` مشخص میکند که میخواهید مرورگر هدر {{httpheader("Attribution-Reporting-Eligible")}} را بههمراه درخواست منبع اسکریپت ارسال کند.

در سمت سرور، این هدر برای ایجاد پاسخ حاوی هدر {{httpheader("Attribution-Reporting-Register-Source")}} یا {{httpheader("Attribution-Reporting-Register-Trigger")}} استفاده میشود تا به ترتیب یک [منبع انتساب](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#javascript-based_event_sources) یا [محرک انتساب](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_triggers#javascript-based_attribution_triggers) مبتنی بر جاوااسکریپت ثبت شود. اینکه کدام هدر پاسخ باید برگردانده شود، به مقدار هدر `Attribution-Reporting-Eligible` بستگی دارد که ثبت را فعال کرده است.

> [!NOTE]
> بهعنوان جایگزین، منابع یا محرکهای انتساب مبتنی بر جاوااسکریپت را میتوان با ارسال درخواست {{domxref("Window/fetch", "fetch()")}} حاوی گزینه `attributionReporting` (چه بهطور مستقیم روی فراخوانی `fetch()` تنظیم شود و چه روی یک شیء {{domxref("Request")}} که به فراخوانی `fetch()` منتقل میشود) یا با ارسال یک {{domxref("XMLHttpRequest")}} که روی شیء آن متد {{domxref("XMLHttpRequest.setAttributionReporting", "setAttributionReporting()")}} فراخوانی شده باشد، ثبت کرد.

برای جزئیات بیشتر به [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API) مراجعه کنید.

## مقدار

یک رشته (string). دو نسخه از این خاصیت وجود دارد که میتوانید آنها را دریافت و تنظیم کنید:

- رشته خالی، برای مثال `scriptElem.attributionSrc=""`. این مشخص میکند که میخواهید هدر {{httpheader("Attribution-Reporting-Eligible")}} به همان سروری که ویژگی `src` به آن اشاره دارد ارسال شود. این کار زمانی مناسب است که ثبت منبع یا محرک انتساب را روی همان سرور مدیریت میکنید. هنگام ثبت یک محرک انتساب، تنظیم این خاصیت اختیاری است و اگر حذف شود، مقدار رشته خالی استفاده خواهد شد.
- مقدار حاوی یک یا چند URL، برای مثال:

  ```js
  scriptElem.attributionSrc =
    "https://a.example/register-source https://b.example/register-source";
  ```

  این در مواردی مفید است که منبع درخواستشده روی سروری قرار ندارد که شما آن را کنترل میکنید، یا فقط میخواهید ثبت منبع انتساب را روی سرور دیگری مدیریت کنید. در این حالت میتوانید یک یا چند URL را بهعنوان مقدار `attributionSrc` مشخص کنید. وقتی درخواست منبع رخ میدهد، هدر {{httpheader("Attribution-Reporting-Eligible")}} علاوه بر مبدأ منبع، به URL(های) مشخصشده در `attributionSrc` نیز ارسال میشود. آن URLها سپس میتوانند با هدر {{httpheader("Attribution-Reporting-Register-Source")}} یا {{httpheader("Attribution-Reporting-Register-Trigger")}} پاسخ دهند تا ثبت کامل شود.

  > [!NOTE]
  > مشخص کردن چند URL به این معنی است که میتوان چند منبع انتساب را برای یک ویژگی (feature) ثبت کرد. برای مثال، ممکن است کمپینهای مختلفی داشته باشید که میخواهید موفقیت آنها را اندازهگیری کنید، و این کمپینها شامل تولید گزارشهای متفاوت روی دادههای مختلف میشوند.

## مثالها

### تنظیم یک attributionSrc خالی

```html
<script src="advertising-script.js"></script>
```

```js
const scriptElem = document.querySelector("script");
scriptElem.attributionSrc = "";
```

### تنظیم یک attributionSrc شامل URLها

```html
<script src="advertising-script.js"></script>
```

```js
// برای جلوگیری از تفسیر نادرست کاراکترهای ویژه
// مانند '='، URLها را کدگذاری کنید.
const encodedUrlA = encodeURIComponent("https://a.example/register-source");
const encodedUrlB = encodeURIComponent("https://b.example/register-source");

const scriptElem = document.querySelector("script");
scriptElem.attributionSrc = `${encodedUrlA} ${encodedUrlB}`;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API).