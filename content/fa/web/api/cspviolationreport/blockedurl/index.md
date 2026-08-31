---
title: "CSPViolationReport: blockedURL property"
short-title: blockedURL
slug: Web/API/CSPViolationReport/blockedURL
page-type: web-api-instance-property
browser-compat: api.ReportingObserver.ReportingObserver.options_parameter.types_property.csp-violation
---

{{APIRef("Reporting API")}}

ویژگی **`blockedURL`** از دیکشنری {{domxref("CSPViolationReport")}} یک مقدار رشته‌ای است که منبعی را نشان می‌دهد که به دلیل نقض [سیاست امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) مسدود شده است.

## مقدار

یک رشته شامل یک مقدار یا URL که منبع ناقض سیاست را نشان می‌دهد.

اگر مقدار URL یک منبع نباشد، باید یکی از رشته‌های زیر باشد:

- `inline`
  - : یک منبع درون‌خطی (inline).
    به عنوان مثال، یک اسکریپت درون‌خطی که زمانی استفاده شده است که [`'unsafe-inline'`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#unsafe-inline) در CSP مشخص نشده بود.
- `eval`
  - : یک `eval()`.
    به عنوان مثال، `eval()` استفاده شده اما [`'unsafe-eval'`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#unsafe-eval) در CSP مشخص نشده بود.
- `wasm-eval`
  - : یک ارزیابی Wasm.
    به عنوان مثال، `eval()` استفاده شده اما [`'wasm-unsafe-eval'`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy#wasm-unsafe-eval) در CSP مشخص نشده بود.
- `trusted-types-policy`
  - : منبعی که دستور CSP [`trusted-types`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/trusted-types) را نقض کرده است.
    به عنوان مثال، یک {{domxref("TrustedTypePolicy")}} با استفاده از {{domxref("TrustedTypePolicyFactory/createPolicy", "window.trustedTypes.createPolicy()")}} با نامی ایجاد شده که در دستور CSP `trusted-types` فهرست نشده بود.
- `trusted-types-sink`
  - : منبعی که دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/trusted-types) را نقض کرده است.
    به عنوان مثال، دستور روی `script` تنظیم شده بود اما سند از یک {{domxref("TrustedTypePolicy")}} برای پالایش داده‌ها قبل از ارسال به یک sink مانند {{domxref("Element.innerHTML")}} استفاده نکرد.

## مثال‌ها

مثال‌های زیر HTMLهایی را نشان می‌دهند که منجر به برخی از مقادیر `blockedURL` ذکر شده در بالا می‌شوند.

این مثال‌ها فرض می‌کنند که شما یک فایل جاوااسکریپت به نام `main.js` از همان دامنه به اسکریپت خود وارد کرده‌اید. اسکریپت، که در زیر نشان داده شده است، یک {{domxref("ReportingObserver")}} جدید برای مشاهده گزارش‌های نقض محتوا از نوع `"csp-violation"` ایجاد می‌کند. هر بار که تابع callback فراخوانی می‌شود، `blockedURL` را در اولین ورودی آرایه گزارش‌ها ثبت می‌کنیم.

```js
const observer = new ReportingObserver(
  (reports, observer) => {
    console.log(`blockedURL: ${reports[0].body.blockedURL}`);
  },
  {
    types: ["csp-violation"],
    buffered: true,
  },
);

observer.observe();
```

توجه داشته باشید که اگرچه ممکن است چندین گزارش در آرایه برگشتی وجود داشته باشد، اما برای اختصار فقط URL مسدود شده اولین گزارش را ثبت می‌کنیم.

### blockedURL برای یک منبع خارجی

HTML زیر یک سیاست با مقدار `Content-Security-Policy: default-src 'self'` تنظیم می‌کند که فقط بارگیری منابع از همان سایت را مجاز می‌داند و سپس سعی می‌کند یک اسکریپت از سایت خارجی `https://apis.google.com` بارگیری کند.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'" />
    <script src="main.js"></script>
  </head>
  <body>
    <!-- This should generate a CSP violation -->
    <script src="https://apis.google.com/js/platform.js"></script>
  </body>
</html>
```

نتیجه ثبت `blockedURL` به صورت زیر خواهد بود:

```plain
blockedURL: https://apis.google.com/js/platform.js
```

### blockedURL برای منابع unsafe-inline

HTML زیر شرایطی را نشان می‌دهد که منجر به `blockedURL` با مقدار `inline` می‌شود. این یک سیاست با مقدار `Content-Security-Policy: default-src 'self'` تنظیم می‌کند که اجازه اجرای اسکریپت‌های درون‌خطی را نمی‌دهد و باعث نقض می‌شود زیرا صفحه شامل یک اسکریپت درون‌خطی است.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'" />
    <script src="main.js"></script>
  </head>
  <body>
    <script>
      const int = 4;
    </script>
  </body>
</html>
```

نتیجه ثبت `blockedURL` به صورت زیر خواهد بود:

```plain
blockedURL: inline
```

### blockedURL برای منابع trusted-types-policy

HTML زیر شرایطی را نشان می‌دهد که منجر به `blockedURL` با مقدار `trusted-types-policy` می‌شود. ابتدا یک سیاست تعریف می‌کند که اسکریپت‌های `'unsafe-inline'` را مجاز می‌داند تا بتوانیم یک {{domxref("TrustedTypePolicy")}} ایجاد کنیم که باعث نقض شود. این سیاست همچنین از دستور `trusted-types` استفاده می‌کند تا مشخص کند ایجاد یک {{domxref("TrustedTypePolicy")}} با نام `myPolicy` مجاز است.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta
      http-equiv="Content-Security-Policy"
      content="default-src 'self' 'report-sample' 'unsafe-inline'; trusted-types myPolicy" />
    <script src="main.js"></script>
  </head>

  <body>
    <script>
      const policy = trustedTypes.createPolicy("somePolicy", {
        // Some (insufficient) sanitization code
        createHTML: (string) => string.replace(/</g, "&lt;"),
      });
    </script>
  </body>
</html>
```

در اسکریپت، یک سیاست با نام `somePolicy` ایجاد می‌شود.

> [!NOTE]
> سیاست خاصی که در بالا تعریف کردیم، سیاست خیلی خوبی نیست.
> هدف از استفاده از انواع مورد اعتماد (trusted types) اعمال یک سیاست _خاص_ نیست، بلکه الزام به اعمال یک سیاست و اطمینان از این است که کد پالایش در یک مکان قرار دارد و به راحتی قابل بررسی است.

از آنجایی که این نام در دستور `trusted-types` فهرست نشده است، نقض CSP محسوب می‌شود و خروجی لاگ زیر را مشاهده می‌کنیم:

```plain
blockedURL: trusted-types-policy
```

اگر نام سیاست مجاز را به `somePolicy` تغییر دهیم، صفحه دیگر در وضعیت نقض نخواهد بود.

### blockedURL برای منابع trusted-types-sink

HTML زیر شرایطی را نشان می‌دهد که منجر به `blockedURL` با مقدار `trusted-types-sink` می‌شود. ابتدا یک سیاست تعریف می‌کند که اسکریپت‌های `'unsafe-inline'` را مجاز می‌داند و مانند مثال قبلی از دستور `trusted-types` استفاده می‌کند تا مشخص کند ایجاد یک {{domxref("TrustedTypePolicy")}} با نام `myPolicy` مجاز است.

علاوه بر این، دستور `require-trusted-types-for 'script'` را مشخص می‌کند که الزام می‌کند sinks فقط باید محتوایی را دریافت کنند که با استفاده از یک نوع مورد اعتماد پالایش شده است.

```html
<!doctype html>
<html lang="en">
  <head>
    <meta
      http-equiv="Content-Security-Policy"
      content="default-src 'self' 'report-sample' 'unsafe-inline'; trusted-types 'myPolicy'; require-trusted-types-for 'script'" />
    <script src="main.js"></script>
  </head>
  <body>
    <input type="text" id="userInput" />
    <button>Update Content</button>
    <div id="content"></div>

    <script>
      function updateContent() {
        const userInput = document.getElementById("userInput").value;

        // Passing unsanitized content - a violation of the policy
        document.getElementById("content").innerHTML = userInput;
      }

      document.querySelector("button").addEventListener("click", updateContent);
    </script>
  </body>
</html>
```

متد `updateContent()` محتوای پالایش نشده را به ویژگی `innerHTML` عنصر منتقل می‌کند که باعث نقض CSP می‌شود. خروجی لاگ زیر را مشاهده می‌کنیم:

```plain
blockedURL: trusted-types-sink
```

برای جلوگیری از نقض، باید اسکریپت را به‌روزرسانی کنیم تا یک سیاست نوع مورد اعتماد تعریف کرده و از آن برای پالایش ورودی ارسالی به عنصر استفاده کنیم:

```js
const policy = trustedTypes.createPolicy("myPolicy", {
  // Some (insufficient) sanitization code
  createHTML: (string) => string.replace(/</g, "&lt;"),
});

function updateContent() {
  const userInput = document.getElementById("userInput").value;
  const sanitizedInput = policy.createHTML(userInput);
  document.getElementById("content").innerHTML = sanitizedInput;
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("SecurityPolicyViolationEvent.blockedURI")}}