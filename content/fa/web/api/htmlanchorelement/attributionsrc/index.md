---
title: "HTMLAnchorElement: attributionSrc property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLAnchorElement/attributionSrc"
---

---
title: "HTMLAnchorElement: attributionSrc property"
short-title: attributionSrc
slug: Web/API/HTMLAnchorElement/attributionSrc
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.HTMLAnchorElement.attributionSrc
---

{{APIRef("Attribution Reporting API")}}{{securecontext_header}}{{deprecated_header}}{{non-standard_header}}

ویژگی **`attributionSrc`** در رابط {{domxref("HTMLAnchorElement")}}، ویژگی [`attributionsrc`](/en-US/docs/Web/HTML/Reference/Elements/a#attributionsrc) را روی یک عنصر {{htmlelement("a")}} به صورت برنامه‌نویسی‌شده دریافت و تنظیم می‌کند و مقدار آن ویژگی را بازتاب می‌دهد. `attributionsrc` مشخص می‌کند که می‌خواهید مرورگر هدر {{httpheader("Attribution-Reporting-Eligible")}} را ارسال کند. در سمت سرور، از این هدر برای فعال‌سازی ارسال هدر {{httpheader("Attribution-Reporting-Register-Source")}} در پاسخ استفاده می‌شود تا یک [منبع attribution مبتنی بر ناوبری](/en-US/docs/Web/API/Attribution_Reporting_API/Registering_sources#navigation-based_attribution_sources) ثبت شود.

مرورگر داده‌های منبع مرتبط با منبع attribution مبتنی بر ناوبری را (که در هدر پاسخ {{httpheader("Attribution-Reporting-Register-Source")}} ارائه شده است) هنگام دریافت پاسخ ناوبری ذخیره می‌کند.

برای جزئیات بیشتر، [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API) را ببینید.

> [!NOTE]
> عناصر `<a>` نمی‌توانند به عنوان «trigger» (محرک) attribution استفاده شوند؛ فقط می‌توانند «source» (منبع) باشند.

## مقدار

یک رشته. دو نسخه از این ویژگی وجود دارد که می‌توانید دریافت و تنظیم کنید:

- رشته خالی، یعنی `aElem.attributionSrc=""`. این مشخص می‌کند که می‌خواهید هدر {{httpheader("Attribution-Reporting-Eligible")}} به همان سروری که ویژگی `href` به آن اشاره می‌کند ارسال شود. این روش زمانی مناسب است که ثبت منبع attribution را روی همان سرور مدیریت می‌کنید.
- مقداری شامل یک یا چند URL، برای مثال:

  ```js
  aElem.attributionSrc =
    "https://a.example/register-source https://b.example/register-source";
  ```

  این روش در مواردی مفید است که منبع درخواستی روی سروری که کنترل آن را ندارید قرار دارد، یا صرفاً می‌خواهید ثبت منبع attribution را روی سرور دیگری مدیریت کنید. در این حالت، می‌توانید یک یا چند URL را به عنوان مقدار `attributionSrc` مشخص کنید. وقتی درخواست منبع انجام شود، هدر {{httpheader("Attribution-Reporting-Eligible")}} علاوه بر مبدأ منبع، به URL(های) مشخص‌شده در `attributionSrc` نیز ارسال می‌شود. این URLها می‌توانند با یک {{httpheader("Attribution-Reporting-Register-Source")}} پاسخ دهند تا منبع ثبت شود.

  > [!NOTE]
  > مشخص کردن چند URL به این معناست که چند منبع attribution می‌توانند روی یک ویژگی ثبت شوند. برای مثال، ممکن است کمپین‌های مختلفی داشته باشید که می‌خواهید موفقیت آن‌ها را اندازه‌گیری کنید و این کمپین‌ها شامل تولید گزارش‌های متفاوت روی داده‌های مختلف باشند.

## مثال‌ها

### تنظیم یک attributionSrc خالی

```html
<a href="https://shop.example"> برای بازدید از فروشگاه ما کلیک کنید </a>
```

```js
const aElem = document.querySelector("a");
aElem.attributionSrc = "";
```

### تنظیم attributionSrc حاوی URL

```html
<a href="https://ourshop.example"> برای بازدید از فروشگاه ما کلیک کنید </a>
```

```js
// URLها را کدگذاری کنید، در صورتی که شامل کاراکترهای خاصی
// مانند '=' باشند که ممکن است به درستی تجزیه نشوند.
const encodedUrlA = encodeURIComponent("https://a.example/register-source");
const encodedUrlB = encodeURIComponent("https://b.example/register-source");

const aElem = document.querySelector("a");
aElem.attributionSrc = `${encodedUrlA} ${encodedUrlB}`;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Attribution Reporting API](/en-US/docs/Web/API/Attribution_Reporting_API).