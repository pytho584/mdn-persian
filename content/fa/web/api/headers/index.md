---
title: Headers
slug: Web/API/Headers
page-type: web-api-interface
browser-compat: api.Headers
---

{{APIRef("Fetch API")}} {{AvailableInWorkers}}

رابط‌های **`Headers`** در [API Fetch](/en-US/docs/Web/API/Fetch_API) به شما امکان می‌دهد تا عملیات مختلفی روی [سرآیندهای درخواست و پاسخ HTTP](/en-US/docs/Web/HTTP/Reference/Headers) انجام دهید. این عملیات شامل بازیابی، تنظیم، افزودن و حذف سرآیندها از فهرست سرآیندهای درخواست می‌شود.

می‌توانید یک شیء `Headers` را از طریق ویژگی‌های {{domxref("Request.headers")}} و {{domxref("Response.headers")}} دریافت کنید و با استفاده از سازنده {{domxref("Headers.Headers", "Headers()")}} یک شیء `Headers` جدید ایجاد کنید. در مقایسه با استفاده از اشیاء ساده، استفاده از اشیاء `Headers` برای ارسال درخواست‌ها، پالایش ورودی بیشتری را فراهم می‌کند. به عنوان مثال، نام سرآیندها را به حروف کوچک تبدیل می‌کند، فاصله‌های ابتدا و انتهای مقادیر سرآیند را حذف می‌کند و از تنظیم برخی سرآیندهای خاص جلوگیری می‌کند.

> [!NOTE]
> می‌توانید اطلاعات بیشتری درباره سرآیندهای موجود با مطالعه مرجع [HTTP headers](/en-US/docs/Web/HTTP/Reference/Headers) ما به دست آورید.

## توضیحات

یک شیء `Headers` دارای یک لیست سرآیند مرتبط است که در ابتدا خالی بوده و از صفر یا چند جفت نام و مقدار تشکیل شده است. می‌توانید با استفاده از روش‌هایی مانند {{domxref("Headers.append","append()")}} (به [نمونه‌ها](#examples) مراجعه کنید) به آن اضافه کنید. در تمام روش‌های این رابط، نام سرآیندها با تطابق نادیده‌گیرنده حروف بزرگ/کوچک (case-insensitive) مقایسه می‌شوند.

یک شیء که `Headers` را پیاده‌سازی می‌کند، می‌تواند مستقیماً در ساختار {{jsxref("Statements/for...of", "for...of")}} به جای {{domxref('Headers.entries()', 'entries()')}} استفاده شود: `for (const p of myHeaders)` معادل است با `for (const p of myHeaders.entries())`.

### محدودیت‌های تغییر

برخی از اشیاء `Headers` در مورد اینکه آیا روش‌های {{domxref("Headers.set","set()")}}، {{domxref("Headers.delete","delete()")}} و {{domxref("Headers.append","append()")}} می‌توانند سرآیند را تغییر دهند، محدودیت دارند. این محدودیت‌ها بسته به نحوه ایجاد شیء `Headers` تعیین می‌شوند.

- برای سرآیندهای ایجاد شده با سازنده {{domxref("Headers.Headers","Headers()")}}، هیچ محدودیت تغییری وجود ندارد.
- برای سرآیندهای اشیاء {{domxref("Request")}}:
  - اگر {{domxref("Request.mode","mode")}} درخواست `no-cors` باشد، می‌توانید هر نام/مقدار {{Glossary("CORS-safelisted request header")}} را تغییر دهید.
  - در غیر این صورت، می‌توانید هر نام/مقدار {{Glossary("forbidden request header", "non-forbidden request header")}} را تغییر دهید.
- برای سرآیندهای اشیاء {{domxref("Response")}}:
  - اگر پاسخ با استفاده از {{domxref("Response.error_static", "Response.error()")}} یا {{domxref("Response.redirect_static", "Response.redirect()")}} ایجاد شده باشد، یا از فراخوانی {{domxref("Window/fetch", "fetch()")}} دریافت شده باشد، سرآیندها غیرقابل تغییر (immutable) بوده و نمی‌توان آنها را تغییر داد.
  - در غیر این صورت، اگر پاسخ با استفاده از {{domxref("Response.Response","Response()")}} یا {{domxref("Response.json_static","Response.json()")}} ایجاد شده باشد، می‌توانید هر نام/مقدار {{Glossary("forbidden response header name", "non-forbidden response header")}} را تغییر دهید.

همه روش‌های Headers اگر سعی کنید به نامی که [یک نام سرآیند HTTP معتبر](https://fetch.spec.whatwg.org/#concept-header-name) نیست، ارجاع دهید، یک {{jsxref("TypeError")}} پرتاب می‌کنند. اگر سرآیند غیرقابل تغییر باشد، عملیات تغییر یک `TypeError` پرتاب می‌کند. در هر مورد دیگر شکست، آنها بی‌صدا شکست می‌خورند.

## سازنده

- {{domxref("Headers.Headers()", "Headers()")}}
  - : یک شیء `Headers` جدید ایجاد می‌کند.

## روش‌های نمونه

- {{domxref("Headers.append()")}}
  - : یک مقدار جدید به یک سرآیند موجود در یک شیء `Headers` اضافه می‌کند، یا اگر سرآیند وجود نداشته باشد، آن را اضافه می‌کند.
- {{domxref("Headers.delete()")}}
  - : یک سرآیند را از یک شیء `Headers` حذف می‌کند.
- {{domxref("Headers.entries()")}}
  - : یک {{jsxref("Iteration_protocols","iterator")}} برمی‌گرداند که امکان پیمایش تمام جفت‌های کلید/مقدار موجود در این شیء را فراهم می‌کند.
- {{domxref("Headers.forEach()")}}
  - : یک تابع ارائه شده را یک بار برای هر جفت کلید/مقدار در این شیء `Headers` اجرا می‌کند.
- {{domxref("Headers.get()")}}
  - : یک دنباله {{jsxref("String")}} از تمام مقادیر یک سرآیند در یک شیء `Headers` با یک نام مشخص برمی‌گرداند.
- {{domxref("Headers.getSetCookie()")}}
  - : یک آرایه حاوی مقادیر تمام سرآیندهای {{httpheader("Set-Cookie")}} مرتبط با یک پاسخ برمی‌گرداند.
- {{domxref("Headers.has()")}}
  - : یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا یک شیء `Headers` حاوی یک سرآیند خاص است یا خیر.
- {{domxref("Headers.keys()")}}
  - : یک {{jsxref("Iteration_protocols", "iterator")}} برمی‌گرداند که به شما امکان می‌دهد تمام کلیدهای جفت‌های کلید/مقدار موجود در این شیء را پیمایش کنید.
- {{domxref("Headers.set()")}}
  - : یک مقدار جدید برای یک سرآیند موجود در یک شیء `Headers` تنظیم می‌کند، یا اگر سرآیند وجود نداشته باشد، آن را اضافه می‌کند.
- {{domxref("Headers.values()")}}
  - : یک {{jsxref("Iteration_protocols", "iterator")}} برمی‌گرداند که به شما امکان می‌دهد تمام مقادیر جفت‌های کلید/مقدار موجود در این شیء را پیمایش کنید.

> [!NOTE]
> برای روشن شدن، تفاوت بین {{domxref("Headers.set()")}} و {{domxref("Headers.append()")}} این است که اگر سرآیند مشخص شده از قبل وجود داشته باشد و مقادیر متعدد را بپذیرد، {{domxref("Headers.set()")}} مقدار موجود را با مقدار جدید بازنویسی می‌کند، در حالی که {{domxref("Headers.append()")}} مقدار جدید را به انتهای مجموعه مقادیر اضافه می‌کند. برای کد نمونه به صفحات اختصاصی آنها مراجعه کنید.

> [!NOTE]
> هنگامی که مقادیر سرآیند پیمایش می‌شوند، به طور خودکار به ترتیب لغت‌نامه‌ای (lexicographical) مرتب می‌شوند و مقادیر نام‌های سرآیند تکراری با هم ترکیب می‌شوند.

## نمونه‌ها

در قطعه کد زیر، ما یک سرآیند جدید با استفاده از سازنده `Headers()` ایجاد می‌کنیم، یک سرآیند جدید با استفاده از `append()` به آن اضافه می‌کنیم، و سپس آن مقدار سرآیند را با استفاده از `get()` برمی‌گردانیم:

```js
const myHeaders = new Headers();

myHeaders.append("Content-Type", "text/xml");
myHeaders.get("Content-Type"); // should return 'text/xml'
```

همین کار را می‌توان با ارسال یک آرایه از آرایه‌ها یا یک شیء literal به سازنده انجام داد:

```js
let myHeaders = new Headers({
  "Content-Type": "text/xml",
});

// or, using an array of arrays:
myHeaders = new Headers([["Content-Type", "text/xml"]]);

myHeaders.get("Content-Type"); // should return 'text/xml'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API Service Worker](/en-US/docs/Web/API/Service_Worker_API)
- [کنترل دسترسی HTTP (CORS)](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)