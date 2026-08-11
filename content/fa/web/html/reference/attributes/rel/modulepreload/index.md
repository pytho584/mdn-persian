---
title: "rel=\"modulepreload\" HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel/modulepreload"
translated_by: "n8n + AI"
---

کلمه کلیدی **`modulepreload`** برای ویژگی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) در عنصر `<link>`، روشی اعلانی (declarative) برای واکشی (fetch) پیش‌دستانهٔ اسکریپت ماژول (module script) فراهم می‌کند؛ به این صورت که ماژول دریافت، تجزیه و کامپایل شده و در module map سند ذخیره می‌شود تا بعداً اجرا شود.

Preload کردن باعث می‌شود ماژول‌ها و وابستگی‌هایشان زودتر دانلود شوند و می‌تواند زمان کل دانلود و پردازش را به‌طور قابل‌توجهی کاهش دهد. این کار به صفحات اجازه می‌دهد ماژول‌ها را به‌صورت موازی واکشی کنند، نه به‌صورت ترتیبی که معمولاً هنگام پردازش هر ماژول و کشف وابستگی‌هایش رخ می‌دهد. با این حال، نمی‌توان همه‌چیز را preload کرد! انتخاب اینکه چه چیزی را preload کنید باید با سایر عملیات‌ها متعادل باشد؛ در غیر این صورت ممکن است برخی عملیات منابع کافی دریافت نکنند و تجربهٔ کاربری بد شود.

لینک‌های با `rel="modulepreload"` مشابه لینک‌های با [`rel="preload"`](/en-US/docs/Web/HTML/Reference/Attributes/rel/preload) هستند. تفاوت اصلی این است که `preload` فقط فایل را دانلود و در کش ذخیره می‌کند، در حالی که `modulepreload` ماژول را دریافت کرده، آن را تجزیه و کامپایل می‌کند و نتایج را در module map قرار می‌دهد تا آمادهٔ اجرا باشد.

هنگام استفاده از `modulepreload`، حالت درخواست واکشی همیشه [`cors`](/en-US/docs/Web/API/Request/mode#cors) است و ویژگی [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) تعیین می‌کند که حالت اعتبار (credential mode) درخواست چه باشد. اگر `crossorigin` روی [`anonymous`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin#anonymous) یا [`""`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin#sect) (مقدار پیش‌فرض) تنظیم شود، حالت اعتبار [`same-origin`](/en-US/docs/Web/API/Request/credentials#same-origin) خواهد بود؛ یعنی اعتبارهای کاربر مانند کوکی‌ها و اطلاعات احراز هویت فقط برای درخواست‌های هم‌خاستگاه ارسال می‌شوند. اگر `crossorigin` روی [`use-credentials`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin#use-credentials) تنظیم شود، حالت اعتبار [`include`](/en-US/docs/Web/API/Request/credentials#include) می‌شود و اعتبارهای کاربر برای درخواست‌های هم‌خاستگاه و غیر هم‌خاستگاه ارسال می‌شود.

ویژگی [`as`](/en-US/docs/Web/HTML/Reference/Elements/link#as) برای لینک‌های با `rel="modulepreload"` اختیاری است و به‌طور پیش‌فرض برابر `"script"` است. می‌توان آن را روی `"script"`، `"style"`، `"json"`، `"text"` یا هر مقصد script-مانند دیگری مثل `"audioworklet"`، `"paintworklet"`، `"serviceworker"`، `"sharedworker"` یا `"worker"` تنظیم کرد. مجموعهٔ کامل مقادیر مجاز در نگاشت [module preload destination](https://html.spec.whatwg.org/multipage/links.html#module-preload-destination) در مشخصات HTML تعریف شده است. برای فهرست مقصدهای script-مانند، به [Fetch spec](https://fetch.spec.whatwg.org/#request-destination-script-like) مراجعه کنید. اگر مقصد دیگری استفاده شود، یک [`رویداد`](/en-US/docs/Web/API/Event/Event) به نام `"error"` روی عنصر فعال می‌شود.

مرورگر ممکن است به‌عنوان بهینه‌سازی، به‌طور خودکار وابستگی‌های منبع ماژول را نیز واکشی کند. اما توجه داشته باشید که این یک بهینه‌سازی مختص مرورگر است؛ تنها راهی که مطمئن شوید همه مرورگرها تلاش می‌کنند وابستگی‌های یک ماژول را preload کنند، مشخص کردن تک‌به‌تک آن‌هاست. علاوه بر این، رویدادهای `load` و `error` بلافاصله پس از موفقیت یا شکست در بارگذاری _منابع مشخص‌شده_ فعال می‌شوند. اگر وابستگی‌ها به‌صورت خودکار واکشی شوند، رویداد اضافی‌ای در thread اصلی فعال نمی‌شود (البته ممکن است درخواست‌های اضافی را در service worker یا سمت سرور نظارت کنید).

## Examples

مثال [basic-modules](https://github.com/mdn/js-examples/tree/main/module-examples/basic-modules) (نسخهٔ زنده [live version](https://mdn.github.io/js-examples/module-examples/basic-modules/)) را در نظر بگیرید که در راهنمای [ماژول‌های جاوااسکریپت](/en-US/docs/Web/JavaScript/Guide/Modules#basic_example_structure) معرفی شده است.

این مثال ساختار فایلی به صورت زیر دارد که شامل یک ماژول سطح بالا به نام `main.js` است. `main.js` با استفاده از [`import statement`](/en-US/docs/Web/JavaScript/Reference/Statements/import) دو ماژول وابسته یعنی `modules/canvas.js` و `modules/square.js` را به صورت ایستا (statically) وارد می‌کند.

```plain
index.html
main.js
modules/
    canvas.js
    square.js
```

کد HTML زیر نشان می‌دهد که `main.js` چگونه در یک عنصر `<script>` بارگذاری می‌شود. مرورگر تنها پس از بارگذاری کامل `main.js`، دو ماژول وابسته را شناسایی و دریافت می‌کند.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <title>Basic JavaScript module example</title>
    <script type="module" src="main.js"></script>
  </head>
  <body></body>
</html>
```

در کد HTML زیر، مثال به‌روزرسانی شده تا از عناصر `<link>` با ویژگی `rel="modulepreload"` برای فایل اصلی و هر یک از ماژول‌های وابسته استفاده کند. این روش بسیار سریع‌تر است زیرا هر سه ماژول پیش از نیاز، به صورت ناهمگام (asynchronous) و موازی (parallel) شروع به دانلود می‌کنند. زمانی که `main.js` تجزیه (parsed) شد و وابستگی‌های آن مشخص شد، آن وابستگی‌ها از قبل دریافت و دانلود شده‌اند.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <title>Basic JavaScript module example</title>
    <link rel="modulepreload" href="main.js" />
    <link rel="modulepreload" href="modules/canvas.js" />
    <link rel="modulepreload" href="modules/square.js" />
    <script type="module" src="main.js"></script>
  </head>
  <body></body>
</html>
```

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- [بارگذاری پیش‌بینی‌شده (Speculative loading)](/en-US/docs/Web/Performance/Guides/Speculative_loading) برای مقایسهٔ `<link rel="modulepreload">` با سایر ویژگی‌های مشابه بهبود عملکرد.
- [پیش‌بارگذاری ماژول‌ها (Preloading modules)](https://web.dev/articles/modulepreload) در web.dev