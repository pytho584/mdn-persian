---
title: "Document: requestStorageAccessFor() method"
short-title: requestStorageAccessFor()
slug: Web/API/Document/requestStorageAccessFor
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Document.requestStorageAccessFor
---

{{APIRef("Storage Access API")}}{{deprecated_header}}{{non-standard_header}}

متد **`requestStorageAccessFor()`** از رابط {{domxref("Document")}} به سایت‌های سطح بالا (top-level) اجازه می‌دهد تا از طرف محتوای تعبیه‌شده که از سایتی دیگر در همان [مجموعه وب‌سایت‌های مرتبط](https://privacysandbox.google.com/cookies/related-website-sets-integration) است، دسترسی به کوکی‌های شخص ثالث را درخواست کنند. این متد یک {{jsxref("Promise")}} برمی‌گرداند که در صورت اعطای دسترسی حل می‌شود و در صورت رد شدن، رد می‌شود.

## نحو (Syntax)

```js-nolint
requestStorageAccessFor(requestedOrigin)
```

### پارامترها

- `requestedOrigin`
  - : رشته‌ای که URL مبدأ را که برای آن دسترسی به کوکی‌های شخص ثالث درخواست می‌کنید، مشخص می‌کند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که اگر دسترسی به کوکی‌های شخص ثالث اعطا شود، با `undefined` fulfilled می‌شود و اگر دسترسی رد شود، rejected می‌شود.

درخواست‌های `requestStorageAccessFor()` به‌طور خودکار رد می‌شوند مگر اینکه محتوای سطح بالا در حال حاضر یک ژست کاربری (user gesture) مانند ضربه یا کلیک را پردازش کند ({{Glossary("transient activation")}})، یا اینکه قبلاً اجازه داده شده باشد. اگر قبلاً اجازه داده نشده باشد، باید در یک event handler مبتنی بر ژست کاربری اجرا شوند. رفتار ژست کاربری به وضعیت promise بستگی دارد:

- اگر promise حل شود (یعنی اجازه اعطا شده باشد)، ژست کاربری مصرف نشده است، بنابراین اسکریپت می‌تواند پس از آن APIهایی را که نیاز به ژست کاربری دارند فراخوانی کند.
- اگر promise رد شود (یعنی اجازه اعطا نشده باشد)، ژست کاربری مصرف شده است، بنابراین اسکریپت نمی‌تواند کاری را که نیاز به ژست دارد انجام دهد. این کار از فراخوانی مجدد `requestStorageAccessFor()` در صورت رد شدن اجازه توسط اسکریپت جلوگیری می‌کند.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} فعلی هنوز فعال نباشد، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - پنجره سند یک [زمینه امن (secure context)](/en-US/docs/Web/Security/Defenses/Secure_Contexts) نباشد.
    - سند، سند سطح بالا نباشد.
    - سند دارای مبدأ `null` باشد.
    - `requestedOrigin` ارائه‌شده [مات (opaque)](https://html.spec.whatwg.org/multipage/browsers.html#concept-origin-opaque) باشد.
    - سایت سطح بالا و سایت تعبیه‌شده در یک [مجموعه وب‌سایت‌های مرتبط](https://privacysandbox.google.com/cookies/related-website-sets-integration) نباشند.
    - {{htmlelement("iframe")}} حاوی محتوا sandbox شده باشد و توکن `allow-storage-access-by-user-activation` تنظیم نشده باشد.
    - استفاده توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) با هدر {{httpheader("Permissions-Policy/storage-access", "storage-access")}} مسدود شده باشد.
    - استفاده توسط درخواست اجازه‌ی user agent برای استفاده از API رد شده باشد.
- `TypeError`
  - : اگر `requestedOrigin` یک URL معتبر نباشد، پرتاب می‌شود.

## توضیحات

متد `requestStorageAccessFor()` چالش‌های موجود در پذیرش Storage Access API در سایت‌های سطح بالایی که از تصاویر یا اسکریپت‌های متقابل-سایت (cross-site) نیازمند کوکی استفاده می‌کنند را برطرف می‌کند. این متد برای user agentهایی که به‌طور پیش‌فرض دسترسی به کوکی‌های [شخص ثالث](/en-US/docs/Web/Privacy/Guides/Third-party_cookies) و [بخش‌بندی‌نشده (unpartitioned)](/en-US/docs/Web/API/Storage_Access_API#unpartitioned_versus_partitioned_cookies) را برای بهبود حریم خصوصی (مثلاً برای جلوگیری از ردیابی) مسدود می‌کنند، مرتبط است و به‌عنوان یک افزونه پیشنهادی برای [Storage Access API](/en-US/docs/Web/API/Storage_Access_API) مطرح شده است.

`requestStorageAccessFor()` می‌تواند دسترسی به کوکی‌های شخص ثالث را برای منابع متقابل-سایتی که مستقیماً در یک سایت سطح بالا تعبیه شده‌اند و خودشان قادر به درخواست دسترسی به حافظه نیستند، مانند عناصر {{htmlelement("img")}}، فراهم کند. محتوای متقابل-سایت تعبیه‌شده در `<iframe>`ها که منطق و منابع خاص خود را دارد و به کوکی‌های شخص ثالث نیاز دارد، باید از طریق {{domxref("Document.requestStorageAccess()")}} دسترسی به حافظه را درخواست کند.

برای بررسی اینکه آیا قبلاً از طریق `requestStorageAccessFor()` اجازه دسترسی به کوکی‌های شخص ثالث اعطا شده است یا خیر، می‌توانید با تعیین نام ویژگی `"top-level-storage-access"` متد {{domxref("Permissions.query()")}} را فراخوانی کنید. این با نام ویژگی‌ای که برای متد معمولی {{domxref("Document.requestStorageAccess()")}} استفاده می‌شود، یعنی `"storage-access"`، متفاوت است.

فراخوانی `Permissions.query()` باید مبدأ تعبیه‌شده را مشخص کند؛ به عنوان مثال:

```js
navigator.permissions.query({
  name: "top-level-storage-access",
  requestedOrigin: "https://www.example.com",
});
```

> [!NOTE]
> استفاده از این ویژگی ممکن است توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) با هدر {{httpheader("Permissions-Policy/storage-access", "storage-access")}} که روی سرور شما تنظیم شده است (همان هدری که بقیه Storage Access API را کنترل می‌کند) مسدود شود. علاوه بر این، سند باید بررسی‌های اضافی مخصوص مرورگر مانند فهرست‌های مجاز، فهرست‌های مسدود، طبقه‌بندی روی دستگاه، تنظیمات کاربر، یا روش‌های اکتشافی ضد [clickjacking](/en-US/docs/Web/Security/Attacks/Clickjacking) را پشت سر بگذارد.

## مثال‌ها

```js
function rSAFor() {
  if ("requestStorageAccessFor" in document) {
    document.requestStorageAccessFor("https://example.com").then(
      (res) => {
        // Use storage access
        doThingsWithCookies();
      },
      (err) => {
        // Handle errors
      },
    );
  }
}
```

پس از یک فراخوانی موفق `requestStorageAccessFor()`، درخواست‌های متقابل-سایت شامل کوکی‌ها خواهند بود اگر شامل [CORS](/en-US/docs/Web/HTTP/Guides/CORS) / [`crossorigin`](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) باشند؛ بنابراین سایت‌ها ممکن است بخواهند قبل از شروع یک درخواست صبر کنند. چنین درخواست‌هایی باید از گزینه [`credentials: "include"`](/en-US/docs/Web/API/RequestInit#credentials) استفاده کنند و منابع باید ویژگی `crossorigin="use-credentials"` را داشته باشند.

به عنوان مثال:

```js
function checkCookie() {
  fetch("https://example.com/getcookies.json", {
    method: "GET",
    credentials: "include",
  })
    .then((response) => response.json())
    .then((json) => {
      // Do something
    });
}
```

> [!NOTE]
> برای یک مثال کامل‌تر به [استفاده از Storage Access API](/en-US/docs/Web/API/Storage_Access_API/Using) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.hasStorageAccess()")}}، {{domxref("Document.hasUnpartitionedCookieAccess()")}}، {{domxref("Document.requestStorageAccess()")}}
- [استفاده از Storage Access API](/en-US/docs/Web/API/Storage_Access_API/Using)
- [معرفی Storage Access API](https://webkit.org/blog/8124/introducing-storage-access-api/) (وبلاگ WebKit)