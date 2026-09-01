---
title: FileSystemDirectoryHandle
slug: Web/API/FileSystemDirectoryHandle
page-type: web-api-interface
browser-compat: api.FileSystemDirectoryHandle
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

رابط کاربری **`FileSystemDirectoryHandle`** از {{domxref("File System API", "File System API", "", "nocode")}} یک دسته (handle) به یک دایرکتوری در سیستم فایل فراهم می‌کند.

این رابط از طریق متدهای {{domxref('window.showDirectoryPicker()')}}، {{domxref('StorageManager.getDirectory()')}}، {{domxref('DataTransferItem.getAsFileSystemHandle()')}} و {{domxref('FileSystemDirectoryHandle.getDirectoryHandle()')}} قابل دسترسی است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{DOMxRef("FileSystemHandle")}}، به ارث می‌برد._

## روش‌های نمونه

_روش‌ها را از والد خود، {{DOMxRef("FileSystemHandle")}}، به ارث می‌برد._

روش‌های عادی:

- {{domxref('FileSystemDirectoryHandle.getDirectoryHandle()')}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که با یک `FileSystemDirectoryHandle` برای زیرشاخه‌ای با نام مشخص‌شده در داخل دسته دایرکتوری که روش روی آن فراخوانی شده، تکمیل می‌شود.
- {{domxref('FileSystemDirectoryHandle.getFileHandle()')}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که با یک {{domxref('FileSystemFileHandle')}} برای فایلی با نام مشخص‌شده، در داخل دایرکتوری که روش روی آن فراخوانی شده، تکمیل می‌شود.
- {{domxref('FileSystemDirectoryHandle.removeEntry()')}}
  - : به‌صورت ناهمگام تلاش می‌کند یک ورودی را حذف کند، اگر دسته دایرکتوری شامل فایل یا دایرکتوری با نام مشخص‌شده باشد.
- {{domxref('FileSystemDirectoryHandle.resolve()')}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که با یک {{jsxref('Array')}} از نام دایرکتوری‌ها از دسته والد تا ورودی فرزند مشخص‌شده تکمیل می‌شود، به‌طوری‌که نام ورودی فرزند آخرین آیتم آرایه باشد.

روش‌های [تکرارگر ناهمگام](/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#the_async_iterator_and_async_iterable_protocols):

- {{domxref('FileSystemDirectoryHandle.entries()')}}
  - : یک _تکرارگر ناهمگام_ جدید از جفت‌های `[key, value]` ویژگی‌های قابل شمارش خود شیء برمی‌گرداند.
- {{domxref('FileSystemDirectoryHandle.keys()')}}
  - : یک _تکرارگر ناهمگام_ جدید حاوی کلیدهای هر آیتم در `FileSystemDirectoryHandle` برمی‌گرداند.
- {{domxref('FileSystemDirectoryHandle.values()')}}
  - : یک _تکرارگر ناهمگام_ جدید حاوی مقادیر هر ایندکس در شیء `FileSystemDirectoryHandle` برمی‌گرداند.
- `FileSystemDirectoryHandle[Symbol.asyncIterator]()`
  - : یک _تکرارگر ناهمگام_ جدید از جفت‌های `[key, value]` ویژگی‌های قابل شمارش خود شیء برمی‌گرداند.

## مثال‌ها

### برگرداندن دسته دایرکتوری

مثال زیر یک دسته دایرکتوری را با نام مشخص‌شده برمی‌گرداند؛ اگر دایرکتوری از قبل وجود نداشته باشد، ایجاد می‌شود.

```js
const dirName = "directoryToGetName";

// فرض کنید یک دسته دایرکتوری داریم: 'currentDirHandle'
const subDir = await currentDirHandle.getDirectoryHandle(dirName, {
  create: true,
});
```

### برگرداندن مسیر فایل

تابع ناهمگام زیر از `resolve()` برای یافتن مسیر یک فایل انتخابی، نسبی به یک دسته دایرکتوری مشخص، استفاده می‌کند.

```js
async function returnPathDirectories(directoryHandle) {
  // دریافت دسته فایل با نمایش انتخاب‌گر فایل:
  const handle = await self.showOpenFilePicker();
  if (!handle) {
    // کاربر لغو کرد، یا به هر دلیل دیگری فایل باز نشد.
    return;
  }

  // بررسی کنید که آیا دسته در داخل دسته دایرکتوری ما وجود دارد
  const relativePaths = await directoryHandle.resolve(handle);

  if (relativePaths === null) {
    // داخل دسته دایرکتوری نیست
  } else {
    // relativePath آرایه‌ای از نام‌ها است که مسیر نسبی را می‌دهد

    for (const name of relativePaths) {
      // هر ورودی را ثبت کنید
      console.log(name);
    }
  }
}
```

### برگرداندن دسته‌ها برای همه فایل‌های یک دایرکتوری

مثال زیر به‌صورت بازگشتی یک دایرکتوری را اسکن می‌کند تا شیءهای {{domxref('FileSystemFileHandle')}} را برای هر فایل در آن دایرکتوری برگرداند:

```js
async function* getFilesRecursively(entry) {
  if (entry.kind === "file") {
    const file = await entry.getFile();
    if (file !== null) {
      file.relativePath = getRelativePath(entry);
      yield file;
    }
  } else if (entry.kind === "directory") {
    for await (const handle of entry.values()) {
      yield* getFilesRecursively(handle);
    }
  }
}
for await (const fileHandle of getFilesRecursively(directoryHandle)) {
  console.log(fileHandle);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)