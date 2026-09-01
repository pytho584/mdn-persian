---
title: "FileReader: FileReader() constructor"
short-title: FileReader()
slug: Web/API/FileReader/FileReader
page-type: web-api-constructor
browser-compat: api.FileReader.FileReader
---

{{APIRef("File API")}}{{AvailableInWorkers}}

سازندهٔ **`FileReader()`** یک شیء `FileReader` جدید ایجاد می‌کند.

برای جزئیات بیشتر دربارهٔ نحوهٔ استفاده از `FileReader`، [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications) را ببینید.

## سینتکس

```js-nolint
new FileReader()
```

### پارامترها

هیچ.

## مثال‌ها

قطعه‌کد زیر، ایجاد یک شیء {{domxref("FileReader")}} را با استفاده از سازندهٔ `FileReader()` و سپس استفاده از آن شیء را نشان می‌دهد:

```js
function printFile(file) {
  const reader = new FileReader();
  reader.onload = (evt) => {
    console.log(evt.target.result);
  };
  reader.readAsText(file);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)