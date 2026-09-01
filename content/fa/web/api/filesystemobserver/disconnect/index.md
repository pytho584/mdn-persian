---
title: "FileSystemObserver: disconnect() method"
short-title: disconnect()
slug: Web/API/FileSystemObserver/disconnect
page-type: web-api-instance-method
status:
  - experimental
  - non-standard
browser-compat: api.FileSystemObserver.disconnect
---

{{securecontext_header}}{{APIRef("File System API")}}{{SeeCompatTable}}{{non-standard_header}}

متد **`disconnect()`** از رابط {{domxref("FileSystemObserver")}} مشاهده‌گر را از مشاهدهٔ سیستم فایل متوقف می‌کند.

## نحو

```js-nolint
disconnect()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref('undefined')}}).

## مثال‌ها

### توقف مشاهدهٔ سیستم فایل

با فرض اینکه یک نمونه از `FileSystemObserver` در دسترس باشد، می‌توانید وقتی می‌خواهید مشاهدهٔ تغییرات ورودی سیستم فایل را متوقف کنید، متد `disconnect()` را روی آن صدا بزنید:

```js
observer.disconnect();
```

## مشخصات

در حال حاضر بخشی از هیچ مشخصاتی نیست. برای PR مربوط به مشخصات، به [https://github.com/whatwg/fs/pull/165](https://github.com/whatwg/fs/pull/165) مراجعه کنید.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [آزمایش origin برای File System Observer API](https://developer.chrome.com/blog/file-system-observer#stop-observing-the-file-system) در developer.chrome.com (2024)