---
title: "Document: requestStorageAccess() method"
short-title: requestStorageAccess()
slug: Web/API/Document/requestStorageAccess
page-type: web-api-instance-method
browser-compat: api.Document.requestStorageAccess
---

{{APIRef("Storage Access API")}}

متد **`requestStorageAccess()`** از رابط {{domxref("Document")}} به محتوایی که درون یک زمینه شخص ثالث (third-party context) بارگذاری شده است (یعنی درون یک {{htmlelement("iframe")}}) اجازه می‌دهد تا دسترسی به [کوئکی‌های شخص ثالث (third-party cookies)](/en-US/docs/Web/Privacy/Guides/Third-party_cookies) و [وضعیت تفکیک‌نشده (unpartitioned state)](/en-US/docs/Web/Privacy/Guides/State_Partitioning#state_partitioning) را درخواست کند. این موضوع برای عامل‌های کاربری (user agents) که به‌طور پیش‌فرض دسترسی به کوئکی‌های شخص ثالث و تفکیک‌نشده را برای بهبود حریم خصوصی (مثلاً جلوگیری از ردیابی) مسدود می‌کنند، مرتبط است و بخشی از [Storage Access API](/en-US/docs/Web/API/Storage_Access_API) محسوب می‌شود.

برای بررسی اینکه آیا مجوز دسترسی به کوئکی‌های شخص ثالث قبلاً اعطا شده است، می‌توانید با مشخص کردن نام ویژگی `"storage-access"`، متد {{domxref("Permissions.query()")}} را فراخوانی کنید.

پس از اینکه یک عنصر جاسازی‌شده (embed) مجوز `storage-access` را از طریق `requestStorageAccess()` فعال کرد، باید خود را دوباره بارگذاری کند. مرورگر منبع را با کوئکی‌های شخص ثالث تفکیک‌نشده دوباره درخواست کرده و پس از بارگذاری، آن‌ها را در دسترس منبع جاسازی‌شده قرار می‌دهد.

کوئکی‌های شخص ثالث فقط با درخواست‌هایی به مبدأ دقیق (exact origin) منبع جاسازی‌شده ارسال می‌شوند. سایر مبدأهای داخل همان سایت که می‌خواهند به کوئکی‌های شخص ثالث خود دسترسی داشته باشند، باید مجوز اعطاشده `storage-access` را _فعال_ کنند. برای فعال‌سازی یک مجوز `storage-access` اعطاشده باید از [هدرهای دسترسی به ذخیره‌سازی (storage access headers)](/en-US/docs/Web/API/Storage_Access_API#storage_access_headers) استفاده کرد. توجه داشته باشید که این هدرها می‌توانند یک مجوز اعطاشده را برای هر منبع جاسازی‌شده، مانند تصاویر دارای اعتبار (credentialed images)، فعال کنند، نه فقط کدهای جاسازی‌شده درون یک {{htmlelement("iframe")}}.

همچنین امکان فعال‌سازی یک مجوز اعطاشده برای یک نقطه پایانی (endpoint) با مبدأ متفاوت اما همان سایت (cross-origin, same-site) با فراخوانی `requestStorageAccess()` وجود دارد (این بار بدون نیاز به فعال‌سازی موقت - transient activation). با این حال، این روش فقط برای فعال‌سازی مجوز برای کدهای جاسازی‌شده کار می‌کند. همچنین نسبت به استفاده از هدرها کارایی کمتری دارد، زیرا برای فعال‌سازی مجوز باید منبع بارگذاری شود.

> [!NOTE]
> استفاده از این ویژگی ممکن است توسط یک {{httpheader("Permissions-Policy/storage-access", "storage-access")}} [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) که روی سرور شما تنظیم شده است مسدود شود. علاوه بر این، سند باید بررسی‌های خاص مرورگر دیگری مانند لیست‌های مجاز (allowlists)، لیست‌های مسدود (blocklists)، طبقه‌بندی روی دستگاه (on-device classification)، تنظیمات کاربر، اکتشافات ضد [کلیک‌جکینگ (clickjacking)](/en-US/docs/Web/Security/Attacks/Clickjacking) یا درخواست مجوز صریح از کاربر را پشت سر بگذارد.

## نحو (Syntax)

```js-nolint
requestStorageAccess()
requestStorageAccess(types)
```

### پارامترها

- `types` {{optional_inline}}
  - : یک شی حاوی ویژگی‌هایی که مشخص می‌کند چه وضعیت تفکیک‌نشده‌ای قابل دسترسی شود. اگر مشخص نشود، مقدار پیش‌فرض ویژگی `false` است. ویژگی‌های موجود به شرح زیر هستند:
    - `all`
      - : یک بولی (boolean) که مشخص می‌کند همه وضعیت‌های تفکیک‌نشده ممکن باید قابل دسترسی شوند.
    - `cookies`
      - : یک بولی که مشخص می‌کند کوئکی‌های شخص ثالث باید قابل دسترسی شوند.
    - `sessionStorage`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.sessionStorage")}} باید قابل دسترسی شود.
    - `localStorage`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.localStorage")}} باید قابل دسترسی شود.
    - `indexedDB`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.indexedDB")}} باید قابل دسترسی شود.
    - `locks`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.locks")}} باید قابل دسترسی شود.
    - `caches`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.caches")}} باید قابل دسترسی شود.
    - `getDirectory`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.getDirectory()")}} باید قابل دسترسی شود.
    - `estimate`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.estimate()")}} باید قابل دسترسی شود.
    - `createObjectURL`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.createObjectURL()")}} باید قابل دسترسی شود.
    - `revokeObjectURL`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.revokeObjectURL()")}} باید قابل دسترسی شود.
    - `BroadcastChannel`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.BroadcastChannel()")}} باید قابل دسترسی شود.
    - `SharedWorker`
      - : یک بولی که مشخص می‌کند {{domxref("StorageAccessHandle.SharedWorker()")}} باید قابل دسترسی شود.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که در صورت اعطای دسترسی به کوئکی‌های شخص ثالث و عدم ارائه پارامتر `types`، با `undefined` fulfilled می‌شود، در صورت ارائه پارامتر `types` و اعطای دسترسی به وضعیت تفکیک‌نشده درخواست‌شده، با {{domxref("StorageAccessHandle")}} fulfilled می‌شود، و در صورت رد دسترسی rejected می‌شود.

درخواست‌های `requestStorageAccess()` به‌طور خودکار رد می‌شوند مگر اینکه محتوای جاسازی‌شده در حال پردازش یک ژست کاربری (user gesture) مانند ضربه زدن یا کلیک کردن ({{Glossary("transient activation")}}) باشد، یا اینکه مجوز قبلاً اعطا شده باشد. اگر مجوز قبلاً اعطا نشده باشد، باید درون یک مدیریت‌کننده رویداد مبتنی بر ژست کاربری اجرا شوند. رفتار ژست کاربری به وضعیت promise بستگی دارد:

- اگر promise resolve شود (یعنی مجوز اعطا شد)، ژست کاربری مصرف نشده است، بنابراین اسکریپت می‌تواند بعداً APIهایی را که نیاز به ژست کاربری دارند فراخوانی کند.
- اگر promise reject شود (یعنی مجوز اعطا نشد)، ژست کاربری مصرف شده است، بنابراین اسکریپت نمی‌تواند کاری را که نیاز به ژست دارد انجام دهد. این یک محافظت عمدی در برابر سوءاستفاده است – از فراخوانی مکرر `requestStorageAccess()` در یک حلقه تا زمانی که کاربر اعلان را بپذیرد جلوگیری می‌کند.

### استثناها (Exceptions)

- `InvalidStateError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - {{domxref("Document")}} فعلی هنوز فعال نیست.
    - پارامتر `types` ارائه شده است و همه ویژگی‌های آن `false` هستند.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - پنجره سند یک [زمینه امن (secure context)](/en-US/docs/Web/Security/Defenses/Secure_Contexts) نیست.
    - استفاده توسط یک {{httpheader("Permissions-Policy/storage-access", "storage-access")}} [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.
    - سند یا سند سطح بالا دارای مبدأ `null` است.
    - {{htmlelement("iframe")}} جاساز sandbox شده است و توکن `allow-storage-access-by-user-activation` تنظیم نشده است.
    - استفاده توسط درخواست مجوز عامل کاربر برای استفاده از API رد شده است.

## مثال‌ها

### استفاده پایه

```js
document.requestStorageAccess().then(
  () => {
    console.log("cookie access granted");
  },
  () => {
    console.log("cookie access denied");
  },
);

document.requestStorageAccess({ localStorage: true }).then(
  (handle) => {
    console.log("localStorage access granted");
    handle.localStorage.setItem("foo", "bar");
  },
  () => {
    console.log("localStorage access denied");
  },
);
```

> [!NOTE]
> برای یک مثال کامل‌تر به [استفاده از Storage Access API](/en-US/docs/Web/API/Storage_Access_API/Using) مراجعه کنید.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- {{domxref("Document.hasStorageAccess()")}}, {{domxref("Document.hasUnpartitionedCookieAccess()")}}, {{domxref("Document.requestStorageAccessFor()")}}
- [استفاده از Storage Access API](/en-US/docs/Web/API/Storage_Access_API/Using)
- [معرفی Storage Access API](https://webkit.org/blog/8124/introducing-storage-access-api/) (وبلاگ WebKit)