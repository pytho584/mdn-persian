---
title: "استفاده از Fetch API"
slug: Web/API/Fetch_API/Using_Fetch
page-type: guide
---

{{DefaultAPISidebar("Fetch API")}}

[Fetch API](/en-US/docs/Web/API/Fetch_API) یک رابط جاوااسکریپتی برای ارسال درخواست‌های HTTP و پردازش پاسخ‌ها فراهم می‌کند.

Fetch جایگزین مدرن {{domxref("XMLHttpRequest")}} است: برخلاف `XMLHttpRequest` که از callback استفاده می‌کند، Fetch مبتنی بر Promise بوده و با ویژگی‌های وب مدرن مانند [service workerها](/en-US/docs/Web/API/Service_Worker_API) و [اشتراک منابع بین‌منشأ (CORS)](/en-US/docs/Web/HTTP/Guides/CORS) یکپارچه شده است.

با Fetch API، با فراخوانی {{domxref("Window/fetch", "fetch()")}} که به عنوان یک تابع سراسری در هر دو زمینه {{domxref("Window", "window")}} و {{domxref("WorkerGlobalScope", "worker")}} در دسترس است، یک درخواست ارسال می‌کنید. شما یک شیء {{domxref("Request")}} یا یک رشته حاوی URL مورد نظر برای واکشی را به همراه یک آرگومان اختیاری برای پیکربندی درخواست به آن پاس می‌دهید.

تابع `fetch()` یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء {{domxref("Response")}} نشان‌دهنده پاسخ سرور، fulfilled می‌شود. سپس می‌توانید وضعیت درخواست را بررسی کرده و بدنه پاسخ را در قالب‌های مختلف از جمله متن و JSON با فراخوانی متد مناسب روی پاسخ استخراج کنید.

در ادامه یک تابع حداقلی که از `fetch()` برای دریافت داده‌های JSON از یک سرور استفاده می‌کند آمده است:

```js
async function getData() {
  const url = "https://example.org/products.json";
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }

    const result = await response.json();
    console.log(result);
  } catch (error) {
    console.error(error.message);
  }
}
```

ما یک رشته حاوی URL را اعلام کرده و سپس `fetch()` را با ارسال URL بدون گزینه اضافی فراخوانی می‌کنیم.

تابع `fetch()` در برخی خطاها Promise را رد می‌کند، اما اگر سرور با یک وضعیت خطا مانند {{httpstatus("404")}} پاسخ دهد این کار را نمی‌کند: بنابراین ما وضعیت پاسخ را نیز بررسی کرده و در صورت عدم OK بودن، خطا پرتاب می‌کنیم.

در غیر این صورت، محتوای بدنه پاسخ را به صورت {{glossary("JSON")}} با فراخوانی متد {{domxref("Response.json()", "json()")}} از `Response` دریافت کرده و یکی از مقادیر آن را ثبت می‌کنیم. توجه داشته باشید که مانند خود `fetch()`، `json()` نیز ناهمگام است، همانند سایر متدهای دسترسی به محتوای بدنه پاسخ.

در ادامه این صفحه، مراحل مختلف این فرآیند را با جزئیات بیشتری بررسی خواهیم کرد.

## ارسال یک درخواست

برای ارسال یک درخواست، `fetch()` را با ارسال موارد زیر فراخوانی کنید:

1. یک تعریف از منبعی که باید واکشی شود. این می‌تواند یکی از موارد زیر باشد:
   - یک رشته حاوی URL
   - یک شیء، مانند نمونه‌ای از {{domxref("URL")}}، که دارای یک {{glossary("stringifier")}} است که رشته‌ای حاوی URL تولید می‌کند
   - یک نمونه {{domxref("Request")}}
2. به صورت اختیاری، یک شیء حاوی گزینه‌هایی برای پیکربندی درخواست.

در این بخش، برخی از پرکاربردترین گزینه‌ها را بررسی می‌کنیم. برای مطالعه تمام گزینه‌های قابل ارائه، به صفحه مرجع [`fetch()`](/en-US/docs/Web/API/Window/fetch) مراجعه کنید.

### تنظیم متد

به طور پیش‌فرض، `fetch()` یک درخواست {{httpmethod("GET")}} ارسال می‌کند، اما می‌توانید از گزینه `method` برای استفاده از یک [متد درخواست](/en-US/docs/Web/HTTP/Reference/Methods) متفاوت استفاده کنید:

```js
const response = await fetch("https://example.org/post", {
  method: "POST",
  // …
});
```

اگر گزینه `mode` روی `no-cors` تنظیم شده باشد، آنگاه `method` باید یکی از `GET`، `POST` یا `HEAD` باشد.

### تنظیم یک بدنه

بدنه درخواست، بار (payload) درخواست است: چیزی است که کلاینت به سرور ارسال می‌کند. شما نمی‌توانید در درخواست‌های `GET` بدنه قرار دهید، اما برای درخواست‌هایی که محتوا را به سرور ارسال می‌کنند، مانند درخواست‌های {{httpmethod("POST")}} یا {{httpmethod("PUT")}} مفید است. برای مثال، اگر می‌خواهید یک فایل را به سرور آپلود کنید، می‌توانید یک درخواست `POST` ارسال کرده و فایل را به عنوان بدنه درخواست قرار دهید.

برای تنظیم یک بدنه درخواست، آن را به عنوان گزینه `body` پاس دهید:

```js
const response = await fetch("https://example.org/post", {
  method: "POST",
  body: JSON.stringify({ username: "example" }),
  // …
});
```

می‌توانید بدنه را به عنوان نمونه‌ای از هر یک از انواع زیر ارائه دهید:

- یک رشته
- {{jsxref("ArrayBuffer")}}
- {{jsxref("TypedArray")}}
- {{jsxref("DataView")}}
- {{domxref("Blob")}}
- {{domxref("File")}}
- {{domxref("URLSearchParams")}}
- {{domxref("FormData")}}
- {{domxref("ReadableStream")}}

سایر اشیاء با استفاده از متد `toString()` خود به رشته تبدیل می‌شوند. برای مثال، می‌توانید از یک شیء {{domxref("URLSearchParams")}} برای رمزگذاری داده‌های فرم استفاده کنید (برای اطلاعات بیشتر به [تنظیم هدرها](#setting_headers) مراجعه کنید):

```js
const response = await fetch("https://example.org/post", {
  method: "POST",
  headers: {
    "Content-Type": "application/x-www-form-urlencoded",
  },
  // به طور خودکار به "username=example&password=password" تبدیل می‌شود
  body: new URLSearchParams({ username: "example", password: "password" }),
  // …
});
```

توجه داشته باشید که مانند بدنه پاسخ‌ها، بدنه درخواست‌ها نیز stream هستند و ارسال درخواست باعث خواندن stream می‌شود، بنابراین اگر یک درخواست حاوی بدنه باشد، نمی‌توانید آن را دو بار ارسال کنید:

```js example-bad
const request = new Request("https://example.org/post", {
  method: "POST",
  body: JSON.stringify({ username: "example" }),
});

const response1 = await fetch(request);
console.log(response1.status);

// خطا: "Body has already been consumed."
const response2 = await fetch(request);
console.log(response2.status);
```

در عوض، باید قبل از ارسال درخواست، یک {{domxref("Request.clone()", "clone", "", "nocode"}} از آن ایجاد کنید:

```js
const request1 = new Request("https://example.org/post", {
  method: "POST",
  body: JSON.stringify({ username: "example" }),
});

const request2 = request1.clone();

const response1 = await fetch(request1);
console.log(response1.status);

const response2 = await fetch(request2);
console.log(response2.status);
```

برای اطلاعات بیشتر به [Streamهای قفل شده و مختل شده](#locked_and_disturbed_streams) مراجعه کنید.

### تنظیم هدرها

هدرهای درخواست اطلاعاتی درباره درخواست به سرور می‌دهند: برای مثال، در یک درخواست `POST`، هدر {{httpheader("Content-Type")}} فرمت بدنه درخواست را به سرور می‌گوید.

برای تنظیم هدرهای درخواست، آن‌ها را به گزینه `headers` اختصاص دهید.

می‌توانید در اینجا یک شیء literal با خصوصیات `header-name: header-value` پاس دهید:

```js
const response = await fetch("https://example.org/post", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({ username: "example" }),
  // …
});
```

متناوباً، می‌توانید یک شیء {{domxref("Headers")}} بسازید، هدرها را با استفاده از {{domxref("Headers.append()")}} به آن اضافه کنید، سپس شیء `Headers` را به گزینه `headers` اختصاص دهید:

```js
const myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

const response = await fetch("https://example.org/post", {
  method: "POST",
  headers: myHeaders,
  body: JSON.stringify({ username: "example" }),
  // …
});
```

در مقایسه با استفاده از اشیاء ساده، شیء `Headers` برخی پالایش‌های ورودی اضافی را فراهم می‌کند. برای مثال، نام هدرها را به حروف کوچک نرمال می‌کند، فاصله‌های ابتدا و انتهای مقادیر هدر را حذف می‌کند، و از تنظیم برخی هدرها جلوگیری می‌کند. بسیاری از هدرها به طور خودکار توسط مرورگر تنظیم می‌شوند و توسط اسکریپت قابل تنظیم نیستند: این هدرها {{glossary("Forbidden request header", "هدرهای درخواست ممنوعه")}} نامیده می‌شوند. اگر گزینه {{domxref("Request.mode", "mode")}} روی `no-cors` تنظیم شود، مجموعه هدرهای مجاز بیشتر محدود می‌شود.

### ارسال داده در یک درخواست GET

درخواست‌های `GET` بدنه ندارند، اما همچنان می‌توانید با افزودن داده به عنوان query string به URL، داده‌ها را به سرور ارسال کنید. این یک روش رایج برای ارسال داده‌های فرم به سرور است. می‌توانید این کار را با استفاده از {{domxref("URLSearchParams")}} برای رمزگذاری داده‌ها و سپس افزودن آن به URL انجام دهید:

```js
const params = new URLSearchParams();
params.append("username", "example");

// درخواست GET ارسال شده به https://example.org/login?username=example
const response = await fetch(`https://example.org/login?${params}`);
```

### ارسال درخواست‌های بین‌منشأ

اینکه آیا یک درخواست می‌تواند بین‌منشأ باشد یا خیر، با مقدار گزینه {{domxref("RequestInit", "", "mode")}} تعیین می‌شود. این گزینه می‌تواند یکی از سه مقدار `cors`، `same-origin` یا `no-cors` را داشته باشد.

- برای درخواست‌های fetch، مقدار پیش‌فرض `mode` `cors` است، به این معنی که اگر درخواست بین‌منشأ باشد، از مکانیزم [اشتراک منابع بین‌منشأ (CORS)](/en-US/docs/Web/HTTP/Guides/CORS) استفاده می‌کند. این به این معنی است که:
  - اگر درخواست یک [درخواست ساده](/en-US/docs/Web/HTTP/Guides/CORS#simple_requests) باشد، درخواست همیشه ارسال می‌شود، اما سرور باید با هدر صحیح {{httpheader("Access-Control-Allow-Origin")}} پاسخ دهد، در غیر این صورت مرورگر پاسخ را با فراخواننده به اشتراک نمی‌گذارد.
  - اگر درخواست ساده نباشد، مرورگر یک [درخواست پیش‌پرواز](/en-US/docs/Web/HTTP/Guides/CORS#preflighted_requests) ارسال می‌کند تا بررسی کند که سرور CORS را درک می‌کند و درخواست را مجاز می‌داند، و درخواست واقعی ارسال نخواهد شد مگر اینکه سرور با هدرهای CORS مناسب به درخواست پیش‌پرواز پاسخ دهد.

- تنظیم `mode` روی `same-origin` درخواست‌های بین‌منشأ را کاملاً غیرمجاز می‌کند.

- تنظیم `mode` روی `no-cors` CORS را برای درخواست‌های بین‌منشأ غیرفعال می‌کند. این کار هدرهای قابل تنظیم را محدود کرده و متدها را به GET، HEAD و POST محدود می‌کند. پاسخ _opaque_ است، به این معنی که هدرها و بدنه آن برای جاوااسکریپت در دسترس نیستند. بیشتر اوقات یک وب‌سایت نباید از `no-cors` استفاده کند: کاربرد اصلی آن برای برخی موارد استفاده از service worker است.

برای جزئیات بیشتر به مستندات مرجع {{domxref("RequestInit", "", "mode")}} مراجعه کنید.

### شامل کردن اعتبارنامه‌ها

در زمینه Fetch API، اعتبارنامه یک قطعه داده اضافی است که همراه با درخواست ارسال می‌شود و سرور ممکن است از آن برای احراز هویت کاربر استفاده کند. تمام موارد زیر به عنوان اعتبارنامه در نظر گرفته می‌شوند:

- کوکی‌های HTTP
- گواهینامه‌های کلاینت {{glossary("TLS")}}
- هدرهای {{httpheader("Authorization")}} و {{httpheader("Proxy-Authorization")}}

به طور پیش‌فرض، اعتبارنامه‌ها فقط در درخواست‌های هم‌منشأ گنجانده می‌شوند. برای سفارشی‌سازی این رفتار، و همچنین برای کنترل اینکه آیا مرورگر به هدرهای پاسخ **`Set-Cookie`** احترام می‌گذارد یا خیر، گزینه [`credentials`](/en-US/docs/Web/API/RequestInit#credentials) را تنظیم کنید که می‌تواند یکی از سه مقدار زیر را داشته باشد:

- `omit`: هرگز اعتبارنامه‌ها را در درخواست ارسال نکنید یا در پاسخ شامل نکنید.
- `same-origin` (پیش‌فرض): فقط برای درخواست‌های هم‌منشأ اعتبارنامه ارسال و شامل کنید.
- `include`: همیشه اعتبارنامه را شامل کنید، حتی بین‌منشأ.

توجه داشته باشید که اگر ویژگی [`SameSite`](/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie#samesitesamesite-value) یک کوکی روی `Strict` یا `Lax` تنظیم شده باشد، آن کوکی بین‌سایتی ارسال نخواهد شد، حتی اگر `credentials` روی `include` تنظیم شده باشد.

شامل کردن اعتبارنامه‌ها در درخواست‌های بین‌منشأ می‌تواند یک سایت را در برابر حملات {{glossary("CSRF")}} آسیب‌پذیر کند، بنابراین حتی اگر `credentials` روی `include` تنظیم شده باشد، سرور نیز باید با شامل کردن هدر {{httpheader("Access-Control-Allow-Credentials")}} در پاسخ خود با این کار موافقت کند. علاوه بر این، در این شرایط سرور باید مبدأ کلاینت را به صراحت در هدر پاسخ {{httpheader("Access-Control-Allow-Origin")}} مشخص کند (یعنی `*` مجاز نیست).

این بدان معناست که اگر `credentials` روی `include` تنظیم شده باشد و درخواست بین‌منشأ باشد، آنگاه:

- اگر درخواست یک [درخواست ساده](/en-US/docs/Web/HTTP/Guides/CORS#simple_requests) باشد، درخواست با اعتبارنامه ارسال می‌شود، اما سرور باید هدرهای پاسخ {{httpheader("Access-Control-Allow-Credentials")}} و {{httpheader("Access-Control-Allow-Origin")}} را تنظیم کند، در غیر این صورت مرورگر یک خطای شبکه به فراخواننده برمی‌گرداند. اگر سرور هدرهای صحیح را تنظیم کند، پاسخ شامل اعتبارنامه به فراخواننده تحویل داده می‌شود.

- اگر درخواست ساده نباشد، مرورگر یک [درخواست پیش‌پرواز](/en-US/docs/Web/HTTP/Guides/CORS#preflighted_requests) بدون اعتبارنامه ارسال می‌کند و سرور باید هدرهای پاسخ {{httpheader("Access-Control-Allow-Credentials")}} و {{httpheader("Access-Control-Allow-Origin")}} را تنظیم کند، در غیر این صورت مرورگر یک خطای شبکه به فراخواننده برمی‌گرداند. اگر سرور هدرهای صحیح را تنظیم کند، مرورگر درخواست واقعی را با اعتبارنامه دنبال کرده و پاسخ واقعی را شامل اعتبارنامه به فراخواننده تحویل می‌دهد.

### ایجاد یک شیء `Request`

سازنده {{domxref("Request.Request()", "Request()")}} همان آرگومان‌های خود `fetch()` را می‌گیرد. این بدان معناست که به جای پاس دادن گزینه‌ها به `fetch()`، می‌توانید همان گزینه‌ها را به سازنده `Request()` پاس دهید و سپس آن شیء را به `fetch()` ارسال کنید.

برای مثال، می‌توانیم یک درخواست POST با پاس دادن گزینه‌ها به `fetch()` با استفاده از کدی مانند زیر انجام دهیم:

```js
const myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

const response = await fetch("https://example.org/post", {
  method: "POST",
  body: JSON.stringify({ username: "example" }),
  headers: myHeaders,
});
```

با این حال، می‌توانیم این را بازنویسی کنیم تا همان آرگومان‌ها را به سازنده `Request()` پاس دهیم:

```js
const myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

const myRequest = new Request("https://example.org/post", {
  method: "POST",
  body: JSON.stringify({ username: "example" }),
  headers: myHeaders,
});

const response = await fetch(myRequest);
```

این همچنین به این معنی است که می‌توانید یک درخواست را از درخواست دیگر ایجاد کنید، در حالی که برخی از خصوصیات آن را با استفاده از آرگومان دوم تغییر دهید:

```js
async function post(request) {
  try {
    const response = await fetch(request);
    const result = await response.json();
    console.log("Success:", result);
  } catch (error) {
    console.error("Error:", error);
  }
}

const request1 = new Request("https://example.org/post", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({ username: "example1" }),
});

const request2 = new Request(request1, {
  body: JSON.stringify({ username: "example2" }),
});

post(request1);
post(request2);
```

## لغو یک درخواست

برای قابل لغو کردن یک درخواست، یک {{domxref("AbortController")}} ایجاد کرده و {{domxref("AbortSignal")}} آن را به خصوصیت `signal` درخواست اختصاص دهید.

برای لغو درخواست، متد {{domxref("AbortController.abort()", "abort()")}} کنترل‌کننده را فراخوانی کنید. فراخوانی `fetch()` Promise را با یک استثنای `AbortError` رد می‌کند.

```js
const controller = new AbortController();

const fetchButton = document.querySelector("#fetch");
fetchButton.addEventListener("click", async () => {
  try {
    console.log("Starting fetch");
    const response = await fetch("https://example.org/get", {
      signal: controller.signal,
    });
    console.log(`Response: ${response.status}`);
  } catch (e) {
    console.error(`Error: ${e}`);
  }
});

const cancelButton = document.querySelector("#cancel");
cancelButton.addEventListener("click", () => {
  controller.abort();
  console.log("Canceled fetch");
});
```

اگر درخواست پس از fulfilled شدن فراخوانی `fetch()` اما قبل از خوانده شدن بدنه پاسخ لغو شود، تلاش برای خواندن بدنه پاسخ با یک استثنای `AbortError` رد می‌شود.

```js
async function get() {
  const controller = new AbortController();
  const request = new Request("https://example.org/get", {
    signal: controller.signal,
  });

  const response = await fetch(request);
  controller.abort();
  // خط بعدی `AbortError` پرتاب می‌کند
  const text = await response.text();
  console.log(text);
}
```

## مدیریت پاسخ

به محض اینکه مرورگر وضعیت و هدرهای پاسخ را از سرور دریافت کرد (و احتمالاً قبل از دریافت خود بدنه پاسخ)، Promise بازگردانده شده توسط `fetch()` با یک شیء {{domxref("Response")}} fulfilled می‌شود.

### بررسی وضعیت پاسخ

Promise بازگردانده شده توسط `fetch()` در برخی خطاها مانند خطای شبکه یا طرح نامعتبر رد می‌شود. با این حال، اگر سرور با خطایی مانند {{httpstatus("404")}} پاسخ دهد، `fetch()` با یک `Response` fulfilled می‌شود، بنابراین باید قبل از خواندن بدنه پاسخ، وضعیت را بررسی کنیم.

خصوصیت {{domxref("Response.status")}} کد وضعیت عددی را به ما می‌گوید، و خصوصیت {{domxref("Response.ok")}} در صورتی که وضعیت در [محدوده 200](/en-US/docs/Web/HTTP/Reference/Status#successful_responses) باشد، `true` برمی‌گرداند.

یک الگوی رایج بررسی مقدار `ok` و پرتاب خطا در صورت `false` بودن است:

```js
async function getData() {
  const url = "https://example.org/products.json";
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }
    // …
  } catch (error) {
    console.error(error.message);
  }
}
```

### بررسی نوع پاسخ

پاسخ‌ها دارای یک خصوصیت {{domxref("Response.type", "type")}} هستند که می‌تواند یکی از موارد زیر باشد:

- `basic`: درخواست یک درخواست هم‌منشأ بود.
- `cors`: درخواست یک درخواست CORS بین‌منشأ بود.
- `opaque`: درخواست یک درخواست ساده بین‌منشأ بود که با حالت `no-cors` انجام شده است.
- `opaqueredirect`: درخواست گزینه `redirect` را روی `manual` تنظیم کرده بود و سرور یک [وضعیت تغییر مسیر](/en-US/docs/Web/HTTP/Reference/Status#redirection_messages) برگرداند.

نوع محتویات احتمالی پاسخ را به صورت زیر تعیین می‌کند:

- پاسخ‌های basic هدرهای پاسخ را از لیست {{glossary("Forbidden response header name", "نام هدرهای پاسخ ممنوعه")}} حذف می‌کنند.
- پاسخ‌های CORS فقط هدرهای پاسخ را از لیست {{glossary("CORS-safelisted response header", "هدرهای پاسخ ایمن CORS")}} شامل می‌شوند.
- پاسخ‌های opaque و پاسخ‌های تغییر مسیر opaque دارای `status` برابر `0`، لیست هدر خالی و بدنه `null` هستند.

### بررسی هدرها

مانند درخواست، پاسخ دارای یک خصوصیت {{domxref("Response.headers", "headers")}} است که یک شیء {{domxref("Headers")}} است و شامل هر هدر پاسخی است که در معرض اسکریپت‌ها قرار می‌گیرد، با توجه به استثناهای اعمال شده بر اساس نوع پاسخ.

یک مورد استفاده رایج برای این کار بررسی نوع محتوا قبل از تلاش برای خواندن بدنه است:

```js
async function fetchJSON(request) {
  try {
    const response = await fetch(request);
    const contentType = response.headers.get("content-type");
    if (!contentType || !contentType.includes("application/json")) {
      throw new TypeError("Oops, we haven't got JSON!");
    }
    // در غیر این صورت، می‌توانیم بدنه را به عنوان JSON بخوانیم
  } catch (error) {
    console.error("Error:", error);
  }
}
```

### خواندن بدنه پاسخ

رابط `Response` تعدادی متد برای بازیابی کل محتوای بدنه در قالب‌های مختلف ارائه می‌دهد:

- {{domxref("Response.arrayBuffer()")}}
- {{domxref("Response.blob()")}}
- {{domxref("Response.formData()")}}
- {{domxref("Response.json()")}}
- {{domxref("Response.text()")}}

همه اینها متدهای ناهمگام هستند و یک {{jsxref("Promise")}} برمی‌گردانند که با محتوای بدنه fulfilled می‌شود.

در این مثال، یک تصویر را واکشی کرده و به عنوان یک {{domxref("Blob")}} می‌خوانیم، که سپس می‌توانیم از آن برای ایجاد یک URL شیء استفاده کنیم:

```js
const image = document.querySelector("img");

const url = "flowers.jpg";

async function setImage() {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }
    const blob = await response.blob();
    const objectURL = URL.createObjectURL(blob);
    image.src = objectURL;
  } catch (e) {
    console.error(e);
  }
}
```

اگر بدنه پاسخ در قالب مناسب نباشد، متد یک استثنا پرتاب می‌کند: برای مثال، اگر `json()` را روی پاسخی که قابل تجزیه به JSON نیست فراخوانی کنید.

### استریم کردن بدنه پاسخ

بدنه درخواست‌ها و پاسخ‌ها در واقع اشیاء {{domxref("ReadableStream")}} هستند و هر زمان که آن‌ها را می‌خوانید، محتوا را استریم می‌کنید. این برای کارایی حافظه خوب است، زیرا مرورگر مجبور نیست کل پاسخ را قبل از بازیابی آن توسط فراخواننده با استفاده از متدی مانند `json()` در حافظه بافر کند.

این همچنین به این معنی است که فراخواننده می‌تواند محتوا را به صورت تدریجی در حین دریافت پردازش کند.

برای مثال، یک درخواست `GET` را در نظر بگیرید که یک فایل متنی بزرگ را واکشی کرده و به نوعی پردازش می‌کند، یا آن را به کاربر نمایش می‌دهد:

```js
const url = "https://www.example.org/a-large-file.txt";

async function fetchText(url) {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }

    const text = await response.text();
    console.log(text);
  } catch (e) {
    console.error(e);
  }
}
```

اگر از {{domxref("Response.text()")}} مانند بالا استفاده کنیم، باید تا دریافت کامل فایل صبر کنیم تا بتوانیم هر بخشی از آن را پردازش کنیم.

اگر به جای آن پاسخ را استریم کنیم، می‌توانیم تکه‌های بدنه را در حین دریافت از شبکه پردازش کنیم:

```js
const url = "https://www.example.org/a-large-file.txt";

async function fetchTextAsStream(url) {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }

    const stream = response.body.pipeThrough(new TextDecoderStream());
    for await (const value of stream) {
      console.log(value);
    }
  } catch (e) {
    console.error(e);
  }
}
```

در این مثال، ما {{jsxref("Statements/for-await...of", "به صورت ناهمگام روی stream پیمایش می‌کنیم", "", "nocode"}} و هر تکه را در زمان رسیدن پردازش می‌کنیم.

توجه داشته باشید که وقتی بدنه را مستقیماً به این صورت دسترسی می‌دهید، بایت‌های خام پاسخ را دریافت می‌کنید و باید خودتان آن را تبدیل کنید. در این مورد، {{domxref("ReadableStream.pipeThrough()")}} را فراخوانی می‌کنیم تا پاسخ را از طریق یک {{domxref("TextDecoderStream")}} عبور دهیم، که داده‌های بدنه رمزگذاری شده با UTF-8 را به عنوان متن رمزگشایی می‌کند.

### پردازش یک فایل متنی خط به خط

در مثال زیر، یک منبع متنی را واکشی کرده و آن را خط به خط با استفاده از یک عبارت منظم برای جستجوی انتهای خطوط پردازش می‌کنیم. برای سادگی، فرض می‌کنیم متن UTF-8 است و خطاهای fetch را مدیریت نمی‌کنیم:

```js
async function* makeTextFileLineIterator(fileURL) {
  const response = await fetch(fileURL);
  const reader = response.body.pipeThrough(new TextDecoderStream()).getReader();

  let { value: chunk = "", done: readerDone } = await reader.read();

  const newline = /\r?\n/g;
  let startIndex = 0;

  while (true) {
    const result = newline.exec(chunk);
    if (!result) {
      if (readerDone) break;
      const remainder = chunk.slice(startIndex);
      ({ value: chunk, done: readerDone } = await reader.read());
      chunk = remainder + (chunk || "");
      startIndex = newline.lastIndex = 0;
      continue;
    }
    yield chunk.substring(startIndex, result.index);
    startIndex = newline.lastIndex;
  }

  if (startIndex < chunk.length) {
    // آخرین خط با کاراکتر خط جدید خاتمه نیافته است
    yield chunk.substring(startIndex);
  }
}

async function run(urlOfFile) {
  for await (const line of makeTextFileLineIterator(urlOfFile)) {
    processLine(line);
  }
}

function processLine(line) {
  console.log(line);
}

run("https://www.example.org/a-large-file.txt");
```

### Streamهای قفل شده و مختل شده

پیامدهای stream بودن بدنه درخواست‌ها و پاسخ‌ها به شرح زیر است:

- اگر یک reader با استفاده از `ReadableStream.getReader()` به یک stream متصل شده باشد، stream _قفل_ است و هیچ چیز دیگری نمی‌تواند stream را بخواند.
- اگر هر محتوایی از stream خوانده شده باشد، stream _مختل_ است و هیچ چیز دیگری نمی‌تواند از stream بخواند.

این بدان معناست که نمی‌توان همان بدنه پاسخ (یا درخواست) را بیش از یک بار خواند:

```js example-bad
async function getData() {
  const url = "https://example.org/products.json";
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }

    const result1 = await response.json();
    const result2 = await response.json(); // خطا پرتاب می‌کند
  } catch (error) {
    console.error(error.message);
  }
}
```

اگر نیاز به خواندن بدنه بیش از یک بار دارید، باید قبل از خواندن بدنه، {{domxref("Response.clone()")}} را فراخوانی کنید:

```js
async function getData() {
  const url = "https://example.org/products.json";
  try {
    const response1 = await fetch(url);
    if (!response1.ok) {
      throw new Error(`Response status: ${response1.status}`);
    }

    const response2 = response1.clone();

    const result1 = await response1.json();
    const result2 = await response2.json();
  } catch (error) {
    console.error(error.message);
  }
}
```

این یک الگوی رایج در [پیاده‌سازی کش آفلاین با service workerها](/en-US/docs/Web/Progressive_web_apps/Guides/Caching) است. service worker می‌خواهد پاسخ را به برنامه برگرداند، اما همچنین پاسخ را ذخیره کند. بنابراین پاسخ را clone می‌کند، نسخه اصلی را برمی‌گرداند و clone را ذخیره می‌کند:

```js
async function cacheFirst(request) {
  const cachedResponse = await caches.match(request);
  if (cachedResponse) {
    return cachedResponse;
  }
  try {
    const networkResponse = await fetch(request);
    if (networkResponse.ok) {
      const cache = await caches.open("MyCache_1");
      cache.put(request, networkResponse.clone());
    }
    return networkResponse;
  } catch (error) {
    return Response.error();
  }
}

self.addEventListener("fetch", (event) => {
  if (precachedResources.includes(url.pathname)) {
    event.respondWith(cacheFirst(event.request));
  }
});
```

## جستارهای وابسته

- [Service Worker API](/en-US/docs/Web/API/Service_Worker_API)
- [Streams API](/en-US/docs/Web/API/Streams_API)
- [CORS](/en-US/docs/Web/HTTP/Guides/CORS)
- [HTTP](/en-US/docs/Web/HTTP)
- [نمونه‌های Fetch در GitHub](https://github.com/mdn/dom-examples/tree/main/fetch)