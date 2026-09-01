---
title: "FileReaderSync: FileReaderSync() constructor"
short-title: FileReaderSync()
slug: Web/API/FileReaderSync/FileReaderSync
page-type: web-api-constructor
browser-compat: api.FileReaderSync.FileReaderSync
---

{{APIRef("File API")}} {{AvailableInWorkers("worker_except_service")}}

سازنده‌ی **`FileReaderSync()`** یک شیء جدید از {{domxref("FileReaderSync")}} ایجاد می‌کند.

## نحو

```js-nolint
new FileReaderSync()
```

### پارامترها

هیچ‌کدام.

## مثال‌ها

قطعه کد زیر نحوه ایجاد یک شیء [`FileReaderSync`](/en-US/docs/Web/API/FileReaderSync) با استفاده از سازنده‌ی `FileReaderSync()` و استفاده‌ی بعدی از آن را نشان می‌دهد:

```js
function readFile(blob) {
  const reader = new FileReaderSync();
  postMessage(reader.readAsDataURL(blob));
}
```

> [!NOTE]
> این قطعه کد باید درون یک {{domxref("Worker")}} استفاده شود، زیرا رابط‌های همزمان (synchronous) نمی‌توانند در نخ اصلی استفاده شوند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}