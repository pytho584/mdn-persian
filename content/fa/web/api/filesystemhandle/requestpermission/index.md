---
title: "FileSystemHandle: requestPermission() method"
---

---
title: "FileSystemHandle: requestPermission() method"
short-title: requestPermission()
slug: Web/API/FileSystemHandle/requestPermission
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.FileSystemHandle.requestPermission
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

متد **`requestPermission()`** از رابط {{domxref("FileSystemHandle")}} برای دسته (handle) فایل، مجوز خواندن یا خواندن/نوشتن درخواست می‌کند.

## نحو

```js-nolint
requestPermission(descriptor)
```

### پارامترها

- `descriptor` {{optional_inline}}
  - : شیئی که حالت مجوزی که باید پرس‌وجو شود را مشخص می‌کند. گزینه‌ها به شرح زیر هستند:
    - `'mode'` {{optional_inline}}
      - : می‌تواند یکی از `'read'`، `'write'` یا `'readwrite'` باشد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{domxref('PermissionStatus.state')}} (وضعیت مجوز) حل می‌شود که یکی از مقادیر `'granted'`، `'denied'` یا `'prompt'` است. همچنین ممکن است با یکی از استثناهای زیر رد (reject) شود.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر پارامتری مشخص نشود یا `mode` یکی از مقادیر `'read'`، `'write'` یا `'readwrite'` نباشد، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : در یکی از موارد زیر پرتاب می‌شود:
    - متد در زمینه‌ای فراخوانی شود که [هم‌ریشه](/en-US/docs/Web/Security/Defenses/Same-origin_policy) با زمینه سطح بالا نیست (مثلاً iframeهای متقاطع‌ریشه (cross-origin)).
    - فعال‌سازی کاربر گذرا (transient user activation) مانند فشردن دکمه وجود نداشته باشد. این شامل حالتی است که دسته در زمینه‌ای غیر از Window قرار دارد که نمی‌تواند فعال‌سازی کاربر را مصرف کند، مانند یک worker.

## امنیت

[فعال‌سازی کاربر گذرا](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است. برای کارکرد این ویژگی، کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند.

## مثال‌ها

تابع ناهمگام (async) زیر در صورت عدم اعطای مجوز، آن را درخواست می‌کند.

```js
// fileHandle is a FileSystemFileHandle
// withWrite is a boolean set to true if write

async function verifyPermission(fileHandle, withWrite) {
  const opts = {};
  if (withWrite) {
    opts.mode = "readwrite";
  }

  // Check if we already have permission, if so, return true.
  if ((await fileHandle.queryPermission(opts)) === "granted") {
    return true;
  }

  // Request permission to the file, if the user grants permission, return true.
  if ((await fileHandle.requestPermission(opts)) === "granted") {
    return true;
  }

  // The user did not grant permission, return false.
  return false;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [File System Access API: ساده‌سازی دسترسی به فایل‌های محلی](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)