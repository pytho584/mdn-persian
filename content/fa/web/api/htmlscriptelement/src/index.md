---
title: "HTMLScriptElement: src property"
short-title: src
slug: Web/API/HTMLScriptElement/src
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.src
---

{{APIRef("HTML DOM")}}

> [!WARNING]
> این ویژگی نمایانگر URI یک اسکریپت خارجی است که در عنصر اسکریپت بارگذاری می‌شود و بسته به {{domxref("HTMLScriptElement/type","type")}} اسکریپت ممکن است قابل اجرا باشد. APIهایی مانند این به عنوان [حفره‌های تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و به طور بالقوه بردار حملات [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند.
>
> می‌توانید این ریسک را با داشتن یک [خط‌مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) که مکان‌های بارگذاری اسکریپت‌ها را محدود می‌کند و با همیشه اختصاص دادن اشیاء {{domxref("TrustedScriptURL")}} به جای رشته‌ها و [اجباری کردن انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید. برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

ویژگی **`src`** از رابط {{domxref("HTMLScriptElement")}} یک رشته است که URL یک اسکریپت خارجی را نشان می‌دهد. این می‌تواند به عنوان جایگزینی برای جاسازی مستقیم یک اسکریپت در داخل یک سند استفاده شود.

این ویژگی منعکس‌کننده ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/script#src) عنصر {{HTMLElement("script")}} است.

## مقدار

خواندن ویژگی یک رشته شامل URI اسکریپت عنصر را برمی‌گرداند.

تنظیم ویژگی یا یک شیء {{domxref("TrustedScriptURL")}} یا یک رشته را می‌پذیرد.

### استثناها

- `TypeError`
  - : زمانی پرتاب می‌شود که ویژگی با یک رشته تنظیم شود در حالی که [انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP اجباری شده‌اند](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) و هیچ خط‌مشی پیش‌فرضی تعریف نشده باشد. همچنین اگر URL واکشی‌شده نتواند با موفقیت به عنوان نوع مشخص‌شده‌اش، مانند module یا importmap، تجزیه شود، پرتاب می‌شود.

## توضیحات

ویژگی **`src`** نمایانگر URL یک اسکریپت خارجی است. اگر تنظیم شود، اسکریپت‌های ارائه‌شده از طریق ویژگی‌های متنی {{domxref("HTMLScriptElement.text","text")}}، {{domxref("HTMLScriptElement.textContent","textContent")}} یا {{domxref("HTMLScriptElement.textContent","innerText")}} نادیده گرفته می‌شوند.

### ملاحظات امنیتی

ویژگی `src` برای بارگذاری و اجرای اسکریپت‌های خارجی استفاده می‌شود. اسکریپت واکشی‌شده در زمینه صفحه فعلی اجرا می‌شود و بنابراین می‌تواند هر کاری که کد وب‌سایت شما می‌تواند انجام دهد، انجام دهد (حتی اگر URL با سایت شما هم‌ریشه نباشد). اگر ورودی توسط کاربر ارائه شود، این یک بردار احتمالی برای حملات [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) است.

پذیرش و اجرای URLهای دلخواه از منابع غیرقابل اعتماد بسیار خطرناک است. یک وب‌سایت باید با استفاده از یک [خط‌مشی امنیت محتوا (CSP)](/en-US/docs/Web/HTTP/Guides/CSP) با دستور [`script-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/script-src) (یا یک بازگشت تعریف‌شده در [`default-src`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/default-src)) اسکریپت‌هایی را که مجاز به اجرا هستند کنترل کند. این می‌تواند اسکریپت‌ها را به اسکریپت‌های مبدأ فعلی، یا مجموعه خاصی از مبدأها، یا حتی فایل‌های خاص محدود کند.

اگر از این ویژگی استفاده می‌کنید و [انواع قابل اعتماد را اجباری می‌کنید](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) (با استفاده از دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for))، باید همیشه اشیاء {{domxref("TrustedScriptURL")}} را به جای رشته‌ها اختصاص دهید. این تضمین می‌کند که ورودی از یک تابع تبدیل عبور می‌کند که شانس رد یا اصلاح URL را قبل از تزریق دارد.

حتی اگر منبع توسط وب‌سایت شما قابل اعتماد باشد، ممکن است در یک [حمله زنجیره تأمین](/en-US/docs/Web/Security/Attacks/Supply_chain_attacks) به خطر بیفتد. برای کاهش این نوع حملات باید از ویژگی [یکپارچگی زیرمنبع](/en-US/docs/Web/Security/Attacks/Supply_chain_attacks#using_subresource_integrity) استفاده کنید.

## مثال‌ها

### استفاده از TrustedScriptURL

برای کاهش خطر XSS، باید همیشه نمونه‌های `TrustedScriptURL` را به ویژگی `src` اختصاص دهیم. همچنین اگر به دلایل دیگر انواع قابل اعتماد را اجباری می‌کنیم و می‌خواهیم برخی از منابع اسکریپت که مجاز شده‌اند (توسط `CSP: script-src`) را اجازه دهیم، باید این کار را انجام دهیم.

انواع قابل اعتماد هنوز در همه مرورگرها پشتیبانی نمی‌شوند، بنابراین ابتدا [tinyfill انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم. این به عنوان یک جایگزین شفاف برای API جاوااسکریپت انواع قابل اعتماد عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک {{domxref("TrustedTypePolicy")}} ایجاد می‌کنیم که یک متد {{domxref("TrustedTypePolicy/createScriptURL", "createScriptURL()")}} را برای تبدیل رشته‌های ورودی به نمونه‌های {{domxref("TrustedScriptURL")}} تعریف می‌کند.

برای هدف این مثال فرض می‌کنیم که می‌خواهیم مجموعه‌ای از پیش تعریف‌شده از URLها را در آرایه `scriptAllowList` مجاز کنیم و هر اسکریپت دیگری را ثبت کنیم.

```js
const scriptAllowList = [
  // Some list of allowed URLs
];
const policy = trustedTypes.createPolicy("script-url-policy", {
  createScriptURL(input) {
    if (scriptAllowList.includes(input)) {
      return input; // allow the script
    }
    console.log(`Script not in scriptAllowList: ${input}`);
    return ""; // Block the script
  },
});
```

سپس عنصر اسکریپت را که مقدار را به آن اختصاص می‌دهیم ایجاد کرده و یک دستگیره به عنصر می‌گیریم.

```html
<script id="el"></script>
```

```js
// Get the script element we're injecting the code into
const el = document.getElementById("el");
```

سپس از شیء `policy` برای ایجاد یک نمونه `trustedScriptURL` از رشته ورودی بالقوه مخرب استفاده می‌کنیم و نتیجه را به عنصر اختصاص می‌دهیم:

```js
// The potentially malicious string
// We won't be including untrustedScriptURL in our scriptAllowList array
const untrustedScriptURL = "https://evil.example.com/naughty.js";

// Create a TrustedScriptURL instance using the policy
const trustedScriptURL = policy.createScriptURL(untrustedScriptURL);

// Inject the TrustedScriptURL (which contains a trusted URL)
el.src = trustedScriptURL;
```

### خواندن ویژگی `src`

این مثال نشان می‌دهد که چگونه می‌توانید ویژگی `src` را برای دو عنصر اسکریپت زیر بخوانید، با فرض اینکه URL صفحه `https://example.com` است.

```html
<script id="script-with-src" type="module" src="/main.js"></script>
<script id="script-without-src" type="module"></script>
```

کد هر یک از عناصر اسکریپت را می‌خواند و خروجی ویژگی `src` را ثبت می‌کند.

```js
const scriptWithSrc = document.getElementById("script-with-src");
console.log(scriptWithSrc.src); // Output: "https://example.com/main.js"
const scriptWithoutSrc = document.getElementById("script-without-src");
console.log(scriptWithoutSrc.src); // Output: ""
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}