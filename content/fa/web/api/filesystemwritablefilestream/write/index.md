---
title: "FileSystemWritableFileStream: write() method"
short-title: write()
slug: Web/API/FileSystemWritableFileStream/write
page-type: web-api-instance-method
browser-compat: api.FileSystemWritableFileStream.write
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`write()`** در interface {{domxref("FileSystemWritableFileStream")}} محتوایی را در فایلی که متد روی آن فراخوانی شده است، در آفست فعلی مکان‌نمای فایل می‌نویسد.

هیچ تغییری در فایل واقعی روی دیسک نوشته نمی‌شود تا زمانی که stream بسته شود. تغییرات معمولاً به‌جای آن در یک فایل موقت نوشته می‌شوند. این متد همچنین می‌تواند برای جابجایی به یک نقطه بایتی خاص در stream و برش (truncate) برای تغییر تعداد کل بایت‌های فایل استفاده شود.

## Syntax

```js-nolint
write(data)
```

### Parameters

- `data`
  - : می‌تواند یکی از موارد زیر باشد:
    - داده‌های فایل برای نوشتن، در قالب یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}}، {{jsxref("DataView")}}، {{domxref('Blob')}}، یا string.
    - یک شیء شامل ویژگی‌های زیر:
      - `type`
        - : رشته‌ای که یکی از مقادیر `"write"`، `"seek"` یا `"truncate"` است.
      - `data`
        - : داده‌های فایل برای نوشتن. می‌تواند یک {{jsxref("ArrayBuffer")}}، {{jsxref("TypedArray")}}، {{jsxref("DataView")}}، {{domxref('Blob')}} یا string باشد. این ویژگی اگر `type` برابر با `"write"` باشد الزامی است.
      - `position`
        - : موقعیت بایتی که مکان‌نمای فعلی فایل باید به آن منتقل شود اگر نوع `"seek"` استفاده شود. همچنین می‌تواند اگر `type` برابر با `"write"` باشد تنظیم شود، در این صورت نوشتن از موقعیت مشخص‌شده شروع می‌شود.
      - `size`
        - : عددی که نشان‌دهنده تعداد بایت‌هایی است که stream باید شامل شود. این ویژگی اگر `type` برابر با `"truncate"` باشد الزامی است.

### Return value

یک {{jsxref('Promise')}} که به `undefined` برمی‌گردد.

### Exceptions

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برابر با `granted` نباشد پرتاب می‌شود.
- {{domxref("QuotaExceededError")}}
  - : اگر اندازه جدید فایل بزرگ‌تر از اندازه اصلی فایل باشد و از [سهمیه ذخیره‌سازی](/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) مرورگر فراتر رود، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر `data` تعریف‌نشده باشد، یا اگر `position` یا `size` معتبر نباشند، پرتاب می‌شود.

## Examples

تابع ناهمگام زیر انتخاب‌گر «ذخیره فایل» را باز می‌کند که پس از انتخاب یک فایل، یک {{domxref('FileSystemFileHandle')}} برمی‌گرداند. از این طریق، یک stream قابل نوشتن با استفاده از متد {{domxref('FileSystemFileHandle.createWritable()')}} ایجاد می‌شود.

سپس یک رشته متنی در stream نوشته می‌شود که متعاقباً بسته می‌شود.

```js
async function saveFile() {
  try {
    // create a new handle
    const newHandle = await window.showSaveFilePicker();

    // create a FileSystemWritableFileStream to write to
    const writableStream = await newHandle.createWritable();

    // write our file
    await writableStream.write("This is my file content");

    // close the file and write the contents to disk.
    await writableStream.close();
  } catch (err) {
    console.error(err.name, err.message);
  }
}
```

مثال‌های زیر گزینه‌های مختلفی را نشان می‌دهند که می‌توانند به متد `write()` ارسال شوند.

```js
// just pass in the data (no options)
writableStream.write(data);

// writes the data to the stream from the determined position
writableStream.write({ type: "write", position, data });

// updates the current file cursor offset to the position specified
writableStream.write({ type: "seek", position });

// resizes the file to be size bytes long
writableStream.write({ type: "truncate", size });
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)