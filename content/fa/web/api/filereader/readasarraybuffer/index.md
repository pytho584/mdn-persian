---
title: "FileReader: readAsArrayBuffer() method"
short-title: readAsArrayBuffer()
slug: Web/API/FileReader/readAsArrayBuffer
page-type: web-api-instance-method
browser-compat: api.FileReader.readAsArrayBuffer
---

{{APIRef("File API")}}{{AvailableInWorkers}}

متد **`readAsArrayBuffer()`** در رابط {{domxref("FileReader")}} برای شروع خواندن محتوای یک {{domxref("Blob")}} یا {{domxref("File")}} مشخص استفاده می‌شود. وقتی عملیات خواندن به پایان برسد، خاصیت {{domxref("FileReader.readyState","readyState")}} به مقدار `DONE` تغییر می‌کند و رویداد {{domxref("FileReader/loadend_event", "loadend")}} فعال می‌شود. در آن زمان، خاصیت {{domxref("FileReader.result","result")}} شامل یک {{jsxref("ArrayBuffer")}} است که داده‌های فایل را نشان می‌دهد.

> [!NOTE]
> متد {{domxref("Blob.arrayBuffer()")}} یک API جدیدتر مبتنی بر Promise است که فایل را به صورت یک آرایه بافر (array buffer) می‌خواند.

## Syntax

```js-nolint
readAsArrayBuffer(blob)
```

### Parameters

- `blob`
  - : {{domxref("Blob")}} یا {{domxref("File")}} که قرار است از آن خوانده شود.

### Return value

هیچ مقداری ({{jsxref("undefined")}}).

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("FileReader")}}