---
title: "AbortSignal"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal"
translated_by: "n8n + AI"
---

# AbortSignal

رابط **`AbortSignal`** یک شیء سیگنال را نشان می‌دهد که به شما امکان می‌دهد با یک عملیات ناهمگام (مانند درخواست fetch) ارتباط برقرار کرده و در صورت نیاز با استفاده از یک شیء {{domxref("AbortController")}} آن را لغو کنید.

## ویژگی‌های نمونه

_همچنین ویژگی‌ها را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("AbortSignal.aborted")}} {{ReadOnlyInline}}
  - : یک مقدار {{Glossary("Boolean")}} که نشان می‌دهد درخواست(هایی) که سیگنال با آن‌ها در ارتباط است، لغو شده‌اند (`true`) یا خیر (`false`).
- {{domxref("AbortSignal.reason")}} {{ReadOnlyInline}}
  - : یک مقدار جاوااسکریپت که دلیل لغو را – پس از آن‌که سیگنال لغو شده باشد – ارائه می‌دهد.

## متدهای استاتیک

_همچنین متدها را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("AbortSignal/abort_static", "AbortSignal.abort()")}}
  - : یک نمونه از `AbortSignal` را برمی‌گرداند که از قبل به‌عنوان لغو شده تنظیم شده است.
- {{domxref("AbortSignal/any_static", "AbortSignal.any()")}}
  - : یک `AbortSignal` برمی‌گرداند که به محض لغو شدن هر یک از سیگنال‌های داده شده، لغو می‌شود.
- {{domxref("AbortSignal/timeout_static", "AbortSignal.timeout()")}}
  - : یک نمونه از `AbortSignal` برمی‌گرداند که به‌طور خودکار پس از مدت زمان مشخصی لغو خواهد شد.

## متدهای نمونه

_همچنین متدها را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("AbortSignal.throwIfAborted()")}}
  - : اگر سیگنال لغو شده باشد، {{domxref("AbortSignal.reason", "دلیل لغو")}} آن را به‌صورت خطا پرتاب می‌کند؛ در غیر این صورت کاری انجام نمی‌دهد.

## رویدادها

_همچنین رویدادها را از رابط والد خود، {{DOMxRef("EventTarget")}}، به ارث می‌برد._

با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با اختصاص یک شنونده رویداد به خصوصیت `oneventname` این رابط، به این رویداد گوش دهید.

- {{domxref("AbortSignal/abort_event", "abort")}}
  - : وقتی عملیات‌های ناهمگامی که سیگنال با آن‌ها در ارتباط است لغو می‌شوند، فراخوانی می‌شود.
    همچنین از طریق خصوصیت `onabort` نیز در دسترس است.

## مثال‌ها

### لغو یک عملیات fetch با استفاده از یک سیگنال مشخص

قطعه‌ کد زیر نشان می‌دهد چگونه می‌توان از یک سیگنال برای لغو دانلود یک ویدئو با استفاده از [Fetch API](/en-US/docs/Web/API/Fetch_API) استفاده کرد.

ابتدا یک متغیر برای `AbortController` خود تعریف می‌کنیم.

قبل از هر [درخواست fetch](/en-US/docs/Web/API/Window/fetch) یک کنترل‌کننده جدید با استفاده از سازنده {{domxref("AbortController.AbortController","AbortController()")}} می‌سازیم و سپس با استفاده از خصوصیت {{domxref("AbortController.signal")}} یک ارجاع به شیء `AbortSignal` مرتبط با آن می‌گیریم.

> [!NOTE]
> یک `AbortSignal` فقط یک‌بار قابل استفاده است. پس از لغو شدن، هر فراخوانی fetch که از همان سیگنال استفاده کند بلافاصله رد خواهد شد.

وقتی درخواست fetch آغاز می‌شود، `AbortSignal` را به‌عنوان یک گزینه درون شیء گزینه‌های درخواست (همان `{ signal }` در پایین) ارسال می‌کنیم. این کار سیگنال و کنترل‌کننده را با درخواست fetch مرتبط می‌کند و به ما اجازه می‌دهد با فراخوانی {{domxref("AbortController.abort()")}} آن را لغو کنیم، همان‌طور که در شنونده رویداد دوم نشان داده شده است.

وقتی `abort()` فراخوانی می‌شود، پرامیس `fetch()` با یک `DOMException` به نام `AbortError` رد می‌شود.

```js
let controller;
const url = "video.mp4";

const downloadBtn = document.querySelector(".download");
const abortBtn = document.querySelector(".abort");

downloadBtn.addEventListener("click", fetchVideo);

abortBtn.addEventListener("click", () => {
  if (controller) {
    controller.abort();
    console.log("Download aborted");
  }
});

async function fetchVideo() {
  controller = new AbortController();
  const signal = controller.signal;

  try {
    const response = await fetch(url, { signal });
    console.log("Download complete", response);
    // process response further
  } catch (err) {
    console.error(`Download error: ${err.message}`);
  }
}
```

اگر درخواست بعد از کامل شدن فراخوانی `fetch()` اما پیش از خوانده شدن بدنهٔ پاسخ لغو شود، تلاش برای خواندن بدنهٔ پاسخ با یک استثنای `AbortError` رد می‌شود.

```js
async function get() {
  const controller = new AbortController();
  const request = new Request("https://example.org/get", {
    signal: controller.signal,
  });

  const response = await fetch(request);
  controller.abort();
  // خط بعدی خطای `AbortError` را پرتاب می‌کند
  const text = await response.text();
  console.log(text);
}
```

می‌توانید یک [نمونهٔ کامل قابل اجرا در GitHub](https://github.com/mdn/dom-examples/tree/main/abort-api) را ببینید؛ همین‌طور [نسخهٔ زندهٔ آن](https://mdn.github.io/dom-examples/abort-api/) نیز در دسترس است.

### لغو یک عملیات fetch با timeout

اگر نیاز دارید عملیات را در صورت timeout لغو کنید، می‌توانید از متد استاتیک `AbortSignal.timeout()` استفاده کنید. این متد یک `AbortSignal` برمی‌گرداند که به‌طور خودکار بعد از تعداد مشخصی میلی‌ثانیه timeout می‌شود.

قطعه کد زیر نشان می‌دهد که چطور یا یک فایل را با موفقیت دانلود کنید، یا بعد از ۵ ثانیه خطای timeout را مدیریت کنید. توجه کنید که وقتی timeout رخ دهد، promise مربوط به `fetch()` با یک `DOMException` از نوع `TimeoutError` رد می‌شود. این موضوع به کد اجازه می‌دهد بین timeoutها (که معمولاً نیاز به اطلاع‌رسانی به کاربر دارند) و لغو توسط کاربر تمایز قائل شود.

```js
const url = "video.mp4";

try {
  const res = await fetch(url, { signal: AbortSignal.timeout(5000) });
  const result = await res.blob();
  // …
} catch (err) {
  if (err.name === "TimeoutError") {
    console.error("Timeout: دریافت نتیجه بیشتر از ۵ ثانیه طول کشید!");
  } else if (err.name === "AbortError") {
    console.error(
      "Fetch توسط کاربر لغو شد (دکمهٔ توقف مرورگر، بستن تب و غیره).",
    );
  } else {
    // خطای شبکه یا مشکلی دیگر.
    console.error(`Error: type: ${err.name}, message: ${err.message}`);
  }
}
```

### لغو fetch با timeout یا لغو صریح

اگر بخواهید از چندین signal برای لغو استفاده کنید، می‌توانید با `AbortSignal.any()` آن‌ها را در یک signal واحد ترکیب کنید. مثال زیر این کار را با استفاده از `fetch()` نشان می‌دهد:

```js
try {
  const controller = new AbortController();
  const timeoutSignal = AbortSignal.timeout(5000);
  const res = await fetch(url, {
    // در صورت لغو هر یک از signalها، fetch لغو می‌شود
    signal: AbortSignal.any([controller.signal, timeoutSignal]),
  });
  const body = await res.json();
} catch (e) {
  if (e.name === "AbortError") {
    // به کاربر اطلاع دهید که لغو شده است.
  } else if (e.name === "TimeoutError") {
    // به کاربر در مورد timeout اطلاع دهید.
  } else {
    // خطای شبکه یا مشکلی دیگر.
    console.log(`Type: ${e.name}, Message: ${e.message}`);
  }
}
```

> [!NOTE]
> برخلاف استفاده از `AbortSignal.timeout()`، هیچ راهی برای تشخیص اینکه لغو نهایی ناشی از timeout بوده وجود ندارد.

### پیاده‌سازی یک API قابل لغو

یک API که نیاز به پشتیبانی از لغو دارد می‌تواند یک شیء `AbortSignal` دریافت کند و از وضعیت آن برای راه‌اندازی مدیریت سیگنال لغو در مواقع نیاز استفاده کند.

یک API مبتنی بر `Promise` باید به سیگنال لغو این‌گونه پاسخ دهد: هر promiseای که هنوز تسویه نشده را با `reason` (دلیل) لغو مربوط به `AbortSignal` رد کند.
برای نمونه، `myCoolPromiseAPI` زیر را در نظر بگیرید که یک signal دریافت می‌کند و یک promise برمی‌گرداند. اگر signal از قبل لغو شده باشد یا رویداد لغو تشخیص داده شود، promise بلافاصله رد می‌شود. در غیر این صورت عملیات به‌طور عادی کامل شده و promise حل می‌شود.

```js
function myCoolPromiseAPI(/* …, */ { signal }) {
  return new Promise((resolve, reject) => {
    // اگر signal از قبل لغو شده باشد، بلافاصله خطا پرتاب کن تا promise رد شود.
    signal.throwIfAborted();

    // هدف اصلی API را انجام بده
    // وقتی کار تمام شد resolve(result) را صدا بزن.
  });
}
```

```js
    // گوش دادن به سیگنال 'abort'
    // استفاده از `once: true` باعث می‌شود Promise بعد از فراخوانی abort قابل جمع‌آوری توسط زباله‌روب (garbage collected) شود
    signal.addEventListener(
      "abort",
      () => {
        // توقف عملیات اصلی
        // رد کردن promise با دلیل لغو.
        reject(signal.reason);
      },
      { once: true },
    );
  });
}
```

در ادامه نحوهٔ استفاده از API نشان داده شده است.  
توجه کنید که برای لغو عملیات، {{domxref("AbortController.abort()")}} فراخوانی می‌شود.

```js
const controller = new AbortController();
const signal = controller.signal;

startSpinner();

myCoolPromiseAPI({ /* …, */ signal })
  .then((result) => {})
  .catch((err) => {
    if (err.name === "AbortError") return;
    showUserErrorMessage();
  })
  .then(() => stopSpinner());

controller.abort();
```

APIهایی که promise برنمی‌گردانند نیز ممکن است به شیوه‌ای مشابه واکنش نشان دهند.  
در برخی موارد منطقی است که سیگنال را جذب (absorb) کنید.

## همچنین ببینید

- [Fetch API](/en-US/docs/Web/API/Fetch_API)
- [Abortable Fetch](https://developer.chrome.com/blog/abortable-fetch/) نوشتهٔ Jake Archibald