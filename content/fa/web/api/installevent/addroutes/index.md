---
title: "InstallEvent: addRoutes() method"
short-title: addRoutes()
slug: Web/API/InstallEvent/addRoutes
page-type: web-api-instance-method
browser-compat: api.InstallEvent.addRoutes
---

{{APIRef("Service Workers API")}}

متد **`addRoutes()`** از رابط {{domxref("InstallEvent")}} یک یا چند مسیر ایستا (static route) را مشخص می‌کند؛ این مسیرها قوانینی را برای واکشی منابع مشخص تعریف می‌کنند که حتی پیش از راه‌اندازی service worker استفاده خواهند شد. این امکان را به شما می‌دهد تا برای مثال در مواردی که همیشه می‌خواهید منبعی را از شبکه یا از {{domxref("Cache")}} مرورگر واکشی کنید، service worker را دور بزنید و از سربار عملکرد ناشی از چرخه‌های غیرضروری service worker جلوگیری کنید.

## Syntax

```js-nolint
addRoutes(routerRules)
```

### Parameters

- `routerRules`
  - : یک شیء منفرد، یا آرایه‌ای از یک یا چند شیء، که قوانینی را برای نحوه واکشی منابع مشخص نشان می‌دهد. هر شیء `routerRules` شامل ویژگی‌های زیر است:
    - `condition`
      - : شیئی که یک یا چند شرط را تعریف می‌کند و مشخص می‌کند کدام منابع باید با این قانون مطابقت داشته باشند. ویژگی‌های زیر می‌توانند گنجانده شوند؛ اگر چند ویژگی استفاده شود، یک منبع باید همه شرایط مشخص‌شده را داشته باشد تا با قانون مطابقت کند.
        - `not` {{optional_inline}}
          - : یک شیء `condition` که شرایطی را تعریف می‌کند که برای مطابقت با قانون، به‌وضوح **نباید** برقرار باشند. شرایط تعریف‌شده درون یک شرط `not` با سایر شرایط متقابلاً انحصاری هستند.
        - `or` {{optional_inline}}
          - : آرایه‌ای از شیءهای `condition`. برای مطابقت با قانون، یکی از مجموعه‌های این شرایط تعریف‌شده باید برقرار باشد. شرایط تعریف‌شده درون یک شرط `or` با سایر شرایط متقابلاً انحصاری هستند.
        - `requestMethod` {{optional_inline}}
          - : رشته‌ای که [متد HTTP](/en-US/docs/Web/HTTP/Reference/Methods) را نشان می‌دهد که یک درخواست باید با آن ارسال شود تا با قانون مطابقت کند، مانند `"get"`, `"put"` یا `"head"`.
        - `requestMode` {{optional_inline}}
          - : رشته‌ای که [mode](/en-US/docs/Web/API/Request/mode) یک درخواست را نشان می‌دهد که باید داشته باشد تا با قانون مطابقت کند، برای مثال `"same-origin"`, `"no-cors"` یا `"cors"`.
        - `requestDestination` {{optional_inline}}
          - : رشته‌ای که [destination](/en-US/docs/Web/API/Request/destination) یک درخواست را نشان می‌دهد، یعنی چه نوع محتوایی باید درخواست شود، تا با قانون مطابقت کند. مثال‌ها شامل `"audio"`, `"document"`, `"script"` و `"worker"` هستند.
        - `runningStatus` {{optional_inline}}
          - : یک مقدار شمارشی (enumerated) که وضعیت اجرای لازم service worker را برای مطابقت یک درخواست با قانون نشان می‌دهد. مقادیر می‌توانند `"running"` یا `"not-running"` باشند.
        - `urlPattern` {{optional_inline}}
          - : یک نمونه {{domxref("URLPattern")}}، یا یک الگوی [`input`](/en-US/docs/Web/API/URLPattern/URLPattern#input) از سازنده `URLPattern()` که URLهای منطبق با قانون را نشان می‌دهد. گروه‌های ضبط عبارت باقاعده (regular expression capturing groups) مجاز نیستند، بنابراین {{domxref("URLPattern.hasRegExpGroups")}} باید `false` باشد.
    - `source`
      - : یک مقدار شمارشی یا یک شیء که منبع بارگذاری منابع منطبق را مشخص می‌کند. مقادیر شمارشی ممکن عبارتند از:
        - `"cache"`
          - : منابع از {{domxref("Cache")}} مرورگر بارگذاری خواهند شد.
        - `"fetch-event"`
          - : منابع از طریق کنترل‌کننده رویداد {{DOMxRef("ServiceWorkerGlobalScope.fetch_event", "fetch")}} مربوط به service worker بارگذاری خواهند شد. این مقدار را می‌توان با شرط `"runningStatus"` ترکیب کرد تا اگر service worker در حال اجرا بود، منابع از آن بارگذاری شوند و اگر در حال اجرا نبود، به یک مسیر ایستا در شبکه بازگردد (fall back).
        - `"network"`
          - : منابع از شبکه بارگذاری خواهند شد.
        - `"race-network-and-fetch-handler"`
          - : تلاش می‌شود منابع به‌طور همزمان از شبکه و از کنترل‌کننده رویداد {{DOMxRef("ServiceWorkerGlobalScope.fetch_event", "fetch")}} مربوط به service worker بارگذاری شوند. هر کدام که زودتر کامل شود استفاده می‌شود.

        مقدار `source` همچنین می‌تواند به یک شیء حاوی یک ویژگی واحد به نام `cacheName` تنظیم شود که مقدار آن رشته‌ای است نشان‌دهنده نام یک {{domxref("Cache")}} مرورگر. در صورت وجود، منابع منطبق از این حافظه نهان نامدار خاص بارگذاری خواهند شد.

### Return value

یک {{jsxref("Promise")}} که با `undefined` تکمیل می‌شود.

### Exceptions

- `TypeError` {{domxref("DOMException")}}
  - : در صورتی پرتاب می‌شود که یک یا چند شیء قانون درون `routerRules` نامعتبر باشد، یا دارای مقدار `"fetch-event"` برای `source` باشد در حالی که service worker مرتبط دارای کنترل‌کننده رویداد {{DOMxRef("ServiceWorkerGlobalScope.fetch_event", "fetch")}} نباشد. همچنین اگر بخواهید `or` را با نوع شرط دیگری ترکیب کنید، پرتاب می‌شود.

## Examples

### Route specific requests to the network if the service worker is not running

در مثال زیر، URLهایی که با `/articles` شروع می‌شوند، اگر service worker در حال حاضر در حال اجرا نباشد، به شبکه مسیریابی می‌شوند:

```js
addEventListener("install", (event) => {
  event.addRoutes({
    condition: {
      urlPattern: "/articles/*",
      runningStatus: "not-running",
    },
    source: "network",
  });
});
```

### Route form post requests to the network

در مثال زیر، درخواست‌های [`POST`](/en-US/docs/Web/HTTP/Reference/Methods/POST) به یک فرم مستقیماً به شبکه ارسال می‌شوند و service worker را دور می‌زنند:

```js
addEventListener("install", (event) => {
  event.addRoutes({
    condition: {
      urlPattern: "/form/*",
      requestMethod: "post",
    },
    source: "network",
  });
});
```

### Route certain image type requests to a named cache

در مثال زیر، {{domxref("Cache")}} مرورگر با نام `"pictures"` برای واکشی فایل‌های با پسوند `.png` یا `.jpg` استفاده می‌شود:

```js
addEventListener("install", (event) => {
  event.addRoutes({
    condition: {
      or: [{ urlPattern: "*.png" }, { urlPattern: "*.jpg" }],
    },
    source: {
      cacheName: "pictures",
    },
  });
});
```

> [!NOTE]
> اگر حافظه نهان وجود نداشته باشد، مرورگر به‌طور پیش‌فرض از شبکه استفاده می‌کند تا در صورت در دسترس بودن شبکه، منابع درخواستی همچنان قابل دریافت باشند.

نمی‌توانید `or` را با شرط دیگری ترکیب کنید — این کار به `TypeError` منجر می‌شود. برای مثال، اگر بخواهید فایل‌هایی با پسوند `.png` یا `.jpg` را فقط زمانی مطابقت دهید که `requestMethod` برابر با `get` باشد، باید دو شرط جداگانه مشخص کنید:

```js
addEventListener("install", (event) => {
  event.addRoutes(
    {
      condition: {
        urlPattern: "*.png",
        requestMethod: "get",
      },
      source: {
        cacheName: "pictures",
      },
    },
    {
      condition: {
        urlPattern: "*.jpg",
        requestMethod: "get",
      },
      source: {
        cacheName: "pictures",
      },
    },
  );
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("InstallEvent")}}
- رویداد [`install`](/en-US/docs/Web/API/ServiceWorkerGlobalScope/install_event)
- [Service Worker API](/en-US/docs/Web/API/Service_Worker_API)
- [استفاده از Service Worker Static Routing API برای دور زدن service worker در مسیرهای خاص](https://developer.chrome.com/blog/service-worker-static-routing) در `developer.chrome.com` (2024)