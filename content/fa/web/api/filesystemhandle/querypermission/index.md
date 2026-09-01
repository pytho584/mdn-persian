---
title: "FileSystemHandle: queryPermission() method"
short-title: queryPermission()
slug: Web/API/FileSystemHandle/queryPermission
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.FileSystemHandle.queryPermission
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

متد **`queryPermission()`** از رابط {{domxref("FileSystemHandle")}} وضعیت مجوز فعلیِ دسته‌ی جاری را بررسی می‌کند.

## نحو (Syntax)

```js-nolint
queryPermission(descriptor)
```

### پارامترها

- `descriptor` {{optional_inline}}
  - : شیئی که حالت مجوز مورد نظر برای بررسی را مشخص می‌کند. گزینه‌ها به شرح زیر هستند:
    - `'mode'` {{optional_inline}}
      - : می‌تواند یکی از مقادیر `'read'`، `'write'` یا `'readwrite'` باشد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{domxref('PermissionStatus.state')}} یکی از مقادیر `'granted'`، `'denied'` یا `'prompt'` حل می‌شود. همچنین ممکن است با یکی از استثناهای زیر رد شود.

اگر این Promise با مقدار "prompt" حل شود، وب‌سایت باید قبل از هرگونه عملیات روی دسته، متد `requestPermission()` را فراخوانی کند. اگر با "denied" حل شود، هر عملیاتی رد خواهد شد. معمولاً دسته‌هایی که توسط سازنده‌های دسته در سیستم فایل محلی بازگردانده می‌شوند، در ابتدا با حالت مجوز خواندن، مقدار "granted" را برمی‌گردانند. با این حال، به غیر از مواردی که کاربر مجوز را لغو کند، دسته‌ای که از IndexedDB بازیابی می‌شود نیز به احتمال زیاد با مقدار "prompt" حل می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `mode` با مقداری غیر از `'read'`، `'write'` یا `'readwrite'` مشخص شود، پرتاب می‌شود.

## مثال‌ها

تابع ناهمگام زیر مقدار `true` را برمی‌گرداند اگر کاربر مجوز خواندن یا خواندن/نوشتن را به دسته‌ی فایل داده باشد. در صورت نبود مجوز، درخواست مجوز داده می‌شود.

```js
// fileHandle یک FileSystemFileHandle است
// withWrite یک bool است که در صورت نیاز به نوشتن true می‌شود

async function verifyPermission(fileHandle, withWrite) {
  const opts = {};
  if (withWrite) {
    opts.mode = "readwrite";
  }

  // بررسی کنید که آیا از قبل مجوز داریم؛ اگر بله، true برگردانید.
  if ((await fileHandle.queryPermission(opts)) === "granted") {
    return true;
  }

  // درخواست مجوز برای فایل؛ اگر کاربر مجوز داد، true برگردانید.
  if ((await fileHandle.requestPermission(opts)) === "granted") {
    return true;
  }

  // کاربر مجوز نداد؛ false برگردانید.
  return false;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)