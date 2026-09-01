---
title: DirectoryReaderSync
slug: Web/API/DirectoryReaderSync
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.DirectoryReaderSync
---

{{APIRef("File and Directory Entries API")}}{{Non-standard_Header}}{{Deprecated_Header}}

رابط `DirectoryReaderSync` به شما امکان خواندن ورودی‌های یک دایرکتوری را می‌دهد.

> [!WARNING]
> این رابط منسوخ شده است و دیگر در مسیر استاندارد قرار ندارد.
> _از آن استفاده نکنید._ به جای آن از [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API) استفاده کنید.

## مفاهیم پایه

پیش از فراخوانی تنها متد این رابط، یعنی [`readEntries()`](#readentries)، شیء [`DirectoryEntrySync`](/en-US/docs/Web/API/DirectoryEntrySync) را ایجاد کنید. اما DirectoryEntrySync (و همچنین [`FileEntrySync`](/en-US/docs/Web/API/FileEntrySync)) یک نوع داده نیست که بتوانید بین یک برنامهٔ فراخوان و یک رشتهٔ Web Worker جابه‌جا کنید. این مسئله مشکل بزرگی نیست، زیرا واقعاً نیازی ندارید که برنامهٔ اصلی و رشتهٔ worker همان شیء جاوااسکریپت را ببینند؛ فقط باید به همان فایل‌ها دسترسی داشته باشند. می‌توانید با ارسال فهرستی از URLهای `filesystem:` (که فقط رشته هستند) به جای فهرستی از ورودی‌ها، این کار را انجام دهید. همچنین می‌توانید از URL `filesystem:` برای جستجوی ورودی با `resolveLocalFileSystemURL()` استفاده کنید. این کار شما را به یک شیء DirectoryEntrySync (و همچنین FileEntrySync) بازمی‌گرداند.

### مثال

در قطعه کد زیر از [HTML5Rocks (web.dev)](https://web.dev/articles/filesystem-sync)، Web Worker ایجاد می‌کنیم و داده را از آن به برنامهٔ اصلی ارسال می‌کنیم.

```js
// Taking care of the browser-specific prefixes.
window.resolveLocalFileSystemURL =
  window.resolveLocalFileSystemURL || window.webkitResolveLocalFileSystemURL;

// Create web workers
const worker = new Worker("worker.js");
worker.onmessage = (e) => {
  const urls = e.data.entries;
  urls.forEach((url) => {
    window.resolveLocalFileSystemURL(url, (fileEntry) => {
      // Print out file's name.
      console.log(fileEntry.name);
    });
  });
};

worker.postMessage({ cmd: "list" });
```

در ادامه کد `worker.js` است که محتویات دایرکتوری را دریافت می‌کند.

```js
// worker.js

// Taking care of the browser-specific prefixes.
self.requestFileSystemSync =
  self.webkitRequestFileSystemSync || self.requestFileSystemSync;

// Global for holding the list of entry file system URLs.
const paths = [];

function getAllEntries(dirReader) {
  const entries = dirReader.readEntries();

  for (const entry of entries) {
    // Stash this entry's filesystem in URL
    paths.push(entry.toURL());

    // If this is a directory, traverse.
    if (entry.isDirectory) {
      getAllEntries(entry.createReader());
    }
  }
}

// Forward the error to main app.
function onError(e) {
  postMessage(`ERROR: ${e.toString()}`);
}

self.onmessage = (e) => {
  const cmd = e.data.cmd;

  // Ignore everything else except our 'list' command.
  if (!cmd || cmd !== "list") {
    return;
  }

  try {
    const fs = requestFileSystemSync(TEMPORARY, 1024 * 1024 /* 1MB */);

    getAllEntries(fs.root.createReader());

    self.postMessage({ entries: paths });
  } catch (e) {
    onError(e);
  }
};
```

## متد

### readEntries()

یک فهرست از ورودی‌های یک دایرکتوری خاص را بازمی‌گرداند. این متد را تا زمانی که یک آرایهٔ خالی بازگردانده شود، فراخوانی کنید.

#### نحو

```js-nolint
readEntries()
```

##### پارامترها

هیچ.

##### مقدار بازگشتی

آرایه‌ای شامل [`FileEntrySync`](/en-US/docs/Web/API/FileEntrySync) و [`DirectoryEntrySync`](/en-US/docs/Web/API/DirectoryEntrySync).

##### استثناها

این متد می‌تواند یک [`DOMException`](/en-US/docs/Web/API/DOMException) با کدهای زیر ایجاد کند:

| استثنا               | توضیحات                                                                        |
| -------------------- | ------------------------------------------------------------------------------ |
| `NOT_FOUND_ERR`      | دایرکتوری وجود ندارد.                                                          |
| `INVALID_STATE_ERR`  | دایرکتوری از زمان اولین فراخوانی readEntries تغییر کرده است.                    |
| `SECURITY_ERR`       | مرورگر تشخیص داده است که جستجوی فراداده (metadata) ایمن نیست.                  |

## مشخصات

این ویژگی دیگر بخشی از هیچ مشخصاتی نیست. در مسیر تبدیل شدن به یک استاندارد قرار ندارد.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)