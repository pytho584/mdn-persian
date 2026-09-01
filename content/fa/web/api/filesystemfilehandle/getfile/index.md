---
title: "FileSystemFileHandle: getFile() method"
short-title: getFile()
slug: Web/API/FileSystemFileHandle/getFile
page-type: web-api-instance-method
browser-compat: api.FileSystemFileHandle.getFile
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`getFile()`** در رابط {{domxref("FileSystemFileHandle")}} یک {{jsxref('Promise')}} برمی‌گرداند که به یک شیء {{domxref('File')}} تبدیل می‌شود. این شیء نمایانگر وضعیت فعلی ورودی‌ای است که این هندل (handle) به آن اشاره می‌کند، در دیسک.

اگر فایل موجود در دیسک پس از فراخوانی این متد تغییر کند یا حذف شود، احتمالاً شیء {{domxref('File')}} برگشتی دیگر قابل خواندن نخواهد بود.

## Syntax

```js-nolint
getFile()
```

### Parameters

هیچ‌کدام.

### Return value

یک {{jsxref('Promise')}} که به یک شیء {{domxref('File')}} تبدیل می‌شود.

### Exceptions

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} در حالت `read` برابر با `granted` نباشد، این خطا پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی جاری یافت نشود، این خطا پرتاب می‌شود.

## Examples

تابع ناهمگام زیر یک انتخاب‌گر فایل را نمایش می‌دهد و پس از انتخاب فایل، با استفاده از متد `getFile()` محتوا را بازیابی می‌کند.

```js
async function getTheFile() {
  // open file picker
  const [fileHandle] = await window.showOpenFilePicker(pickerOpts);

  // get file contents
  const fileData = await fileHandle.getFile();
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)