---
title: "Permissions: query() method"
short-title: query()
slug: Web/API/Permissions/query
page-type: web-api-instance-method
browser-compat: api.Permissions.query
---

{{APIRef("Permissions API")}}{{AvailableInWorkers}}

متد **`query()`** از رابط {{domxref("Permissions")}} وضعیتِ مجوز یک کاربر را در حوزهٔ سراسری (global scope) برمی‌گرداند.

نام مجوزها در مشخصات (specifications) مربوط به هر ویژگی تعریف شده‌اند.
فهرست مجوزهایی که نسخه‌های مختلف مرورگر از آن‌ها پشتیبانی می‌کنند، در [داده‌های سازگاری رابط `Permissions`](/en-US/docs/Web/API/Permissions#browser_compatibility) آمده است (همچنین به کد منبع مرتبط برای [مقادیر Firefox](https://searchfox.org/firefox-main/source/dom/webidl/Permissions.webidl#10)، [مقادیر Chromium](https://chromium.googlesource.com/chromium/src/+/refs/heads/main/third_party/blink/renderer/modules/permissions/permission_descriptor.idl) و [مقادیر WebKit](https://github.com/WebKit/WebKit/blob/main/Source/WebCore/Modules/permissions/PermissionName.idl) مراجعه کنید).

APIهایی که دسترسی به آن‌ها توسط هر مجوز کنترل می‌شود، در بخش [APIهای مبتنی بر مجوز (Permission-aware APIs)](/en-US/docs/Web/API/Permissions_API#permission-aware_apis) از نمای کلی [Permissions API](/en-US/docs/Web/API/Permissions_API) فهرست شده‌اند.

## سینتکس

```js-nolint
query(permissionDescriptor)
```

### پارامترها

- `permissionDescriptor`
  - : شیئی که گزینه‌های عملیات `query` را تنظیم می‌کند.
    گزینه‌های موجود برای این توصیف‌گر به نوع مجوز بستگی دارند.

    همهٔ مجوزها دارای یک `name` هستند:
    - `name`
      - : رشته‌ای شامل نامِ APIای که می‌خواهید وضعیت مجوز آن را بررسی کنید، مانند `camera`، `bluetooth`، `microphone`، `geolocation` (برای فهرست کامل‌تر به [`Permissions`](/en-US/docs/Web/API/Permissions#browser_compatibility) مراجعه کنید).
        اگر نام مجوز توسط مرورگر پشتیبانی نشود، {{jsxref("Promise")}} بازگشتی با یک {{jsxref("TypeError")}} رد (reject) می‌شود.

    برای مجوزهای `push` نیز می‌توانید گزینهٔ زیر را مشخص کنید:
    - `userVisibleOnly` {{optional_inline}}
      - : (فقط برای Push است و در Firefox پشتیبانی نمی‌شود — به بخش «سازگاری مرورگر» در پایین مراجعه کنید.) مشخص می‌کند که آیا می‌خواهید برای هر پیام یک اعلان نمایش دهید یا بتوانید اعلان‌های فشاری بی‌صدا ارسال کنید. مقدار پیش‌فرض `false` است.

    برای مجوز `midi` نیز می‌توانید گزینهٔ زیر را مشخص کنید:
    - `sysex` {{optional_inline}}
      - : مشخص می‌کند که آیا به پیام‌های System Exclusive نیاز دارید و/یا آن‌ها را دریافت می‌کنید. مقدار پیش‌فرض `false` است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک شیء {{domxref("PermissionStatus")}} حل می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر متد `query()` در یک زمینهٔ مرور (browsing context) فراخوانی شود و سند مرتبط با آن به‌طور کامل فعال (fully active) نباشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر دریافت اطلاعات `PermissionDescriptor` به هر شکل با شکست مواجه شود، یا مجوز وجود نداشته باشد یا توسط عامل کاربر (user agent) پشتیبانی نشود، پرتاب می‌شود.

## مثال‌ها

### نمایش اخبار بر اساس مجوز موقعیت جغرافیایی

این مثال نشان می‌دهد که اگر مجوز `geolocation` صادر شده باشد، چگونه می‌توانید اخبار مرتبط با موقعیت کنونی را نمایش دهید؛ در غیر این صورت، از کاربر خواسته می‌شود تا دسترسی به موقعیت را فعال کند.

```js
navigator.permissions.query({ name: "geolocation" }).then((result) => {
  if (result.state === "granted") {
    showLocalNewsWithGeolocation();
  } else if (result.state === "prompt") {
    showButtonToEnableLocalNews();
  }
  // Don't do anything if the permission was denied.
});
```

### بررسی پشتیبانی از مجوزهای گوناگون

این مثال نتیجهٔ پرس‌وجوی هر یک از مجوزها را نشان می‌دهد.

کد با استفاده از `navigator.permissions.query()` هر مجوز را پرس‌وجو می‌کند و یا وضعیت مجوز را در گزارش (log) ثبت می‌کند یا این واقعیت را که مجوز در مرورگر پشتیبانی نمی‌شود.
توجه داشته باشید که `query()` درون یک بلوک `try...catch` فراخوانی می‌شود، زیرا اگر مجوز پشتیبانی نشود، {{jsxref("Promise")}} مربوطه رد خواهد شد.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 320px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js
// Array of permissions
const permissions = [
  "accelerometer",
  "accessibility-events",
  "ambient-light-sensor",
  "background-sync",
  "camera",
  "clipboard-read",
  "clipboard-write",
  "geolocation",
  "gyroscope",
  "local-fonts",
  "magnetometer",
  "microphone",
  "midi",
  "notifications",
  "payment-handler",
  "persistent-storage",
  "push",
  "screen-wake-lock",
  "storage-access",
  "top-level-storage-access",
  "window-management",
];

processPermissions();

// Iterate through the permissions and log the result
async function processPermissions() {
  for (const permission of permissions) {
    const result = await getPermission(permission);
    log(result);
  }
}

// Query a single permission in a try...catch block and return result
async function getPermission(permission) {
  try {
    let result;
    if (permission === "top-level-storage-access") {
      result = await navigator.permissions.query({
        name: permission,
        requestedOrigin: window.location.origin,
      });
    } else {
      result = await navigator.permissions.query({ name: permission });
    }
    return `${permission}: ${result.state}`;
  } catch (error) {
    return `${permission} (not supported)`;
  }
}
```

خروجی اجرای کد در ادامه نمایش داده شده است:

{{EmbedLiveSample('Test support for various permissions',"100%", "370px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}