---
title: "DataTransferItem: getAsFileSystemHandle() method"
---

---
title: "DataTransferItem: getAsFileSystemHandle() method"
short-title: getAsFileSystemHandle()
slug: Web/API/DataTransferItem/getAsFileSystemHandle
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.DataTransferItem.getAsFileSystemHandle
---

{{securecontext_header}}{{APIRef("File System API")}}{{SeeCompatTable}}

متد **`getAsFileSystemHandle()`** از رابط {{domxref("DataTransferItem")}} یک {{jsxref('Promise')}} برمی‌گرداند؛ اگر آیتمِ کشیده‌شده یک فایل باشد، این Promise با یک {{domxref('FileSystemFileHandle')}} برآورده می‌شود و اگر آیتمِ کشیده‌شده یک پوشه باشد، با یک {{domxref('FileSystemDirectoryHandle')}} برآورده می‌شود.

## سینتکس

```js-nolint
getAsFileSystemHandle()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{jsxref('Promise')}}.

اگر ویژگی {{domxref("DataTransferItem.kind", "kind")}} آیتم برابر با `"file"` باشد و به این آیتم در هندلرهای رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} یا {{domxref("HTMLElement/drop_event", "drop")}} دسترسی داشته باشیم، آنگاه اگر آیتمِ کشیده‌شده یک فایل باشد، Promise بازگشت‌شده با یک {{domxref('FileSystemFileHandle')}} برآورده می‌شود و اگر آیتمِ کشیده‌شده یک پوشه باشد، با یک {{domxref('FileSystemDirectoryHandle')}} برآورده می‌شود.

در غیر این صورت، Promise با `null` برآورده می‌شود.

### استثناها

هیچ‌کدام.

## مثال‌ها

این مثال از متد `getAsFileSystemHandle()` برای بازگرداندن {{domxref('FileSystemHandle', 'file handles', '', 'nocode')}} مربوط به آیتم‌های رهاشده استفاده می‌کند.

> [!NOTE]
> زیرا `getAsFileSystemHandle()` تنها در همان تیکی که هندلر رویداد `drop` اجرا می‌شود می‌تواند هندلِ آن ورودی را بازیابی کند، نباید هیچ `await`ای قبل از آن وجود داشته باشد. به همین دلیل است که ابتدا `getAsFileSystemHandle()` را برای همه آیتم‌ها به‌صورت همگام فراخوانی می‌کنیم و سپس به‌طور همزمان منتظر نتیجه‌های آن‌ها می‌مانیم.

```js
elem.addEventListener("dragover", (e) => {
  // Prevent navigation.
  e.preventDefault();
});
elem.addEventListener("drop", async (e) => {
  // Prevent navigation.
  e.preventDefault();
  const handlesPromises = [...e.dataTransfer.items]
    // kind will be 'file' for file/directory entries.
    .filter((x) => x.kind === "file")
    .map((x) => x.getAsFileSystemHandle());
  const handles = await Promise.all(handlesPromises);

  // Process all of the items.
  for (const handle of handles) {
    if (handle.kind === "file") {
      // run code for if handle is a file
    } else if (handle.kind === "directory") {
      // run code for is handle is a directory
    }
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)