---
title: "FileReader: readAsBinaryString() method"
short-title: readAsBinaryString()
slug: Web/API/FileReader/readAsBinaryString
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.FileReader.readAsBinaryString
---

{{APIRef("File API")}}{{AvailableInWorkers}}{{Deprecated_Header}}

> [!NOTE]
> این متد به نفع {{DOMxRef("FileReader.readAsArrayBuffer","readAsArrayBuffer()")}} منسوخ شده است.

متد **`readAsBinaryString()`** از رابط {{domxref("FileReader")}} برای شروع خواندن محتویات {{domxref("Blob")}} یا {{domxref("File")}} مشخص‌شده استفاده می‌شود. وقتی عملیات خواندن به پایان برسد، خاصیت {{domxref("FileReader.readyState","readyState")}} برابر با `DONE` می‌شود و رویداد {{domxref("FileReader/loadend_event", "loadend")}} فعال می‌گردد. در آن زمان، خاصیت {{domxref("FileReader.result","result")}} شامل داده‌های خام دودوییِ خوانده‌شده از فایل است.

توجه داشته باشید که این متد زمانی از مشخصات File API حذف شده بود، اما برای سازگاری با نسخه‌های قبلی دوباره معرفی شد. استفاده از {{domxref("FileReader.readAsArrayBuffer()")}} توصیه می‌شود.

## سینتکس

```js-nolint
readAsBinaryString(blob)
```

### پارامترها

- `blob`
  - : {{domxref("Blob")}} یا {{domxref("File")}}ای که قرار است از آن خوانده شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

```js
const canvas = document.createElement("canvas");
const height = 200;
const width = 200;

canvas.width = width;
canvas.height = height;

const ctx = canvas.getContext("2d");

ctx.strokeStyle = "#009900";
ctx.beginPath();
ctx.arc(width / 2, height / 2, width / 2 - width / 10, 0, Math.PI * 2);
ctx.stroke();

canvas.toBlob((blob) => {
  const reader = new FileReader();

  reader.onload = () => {
    console.log(reader.result);
  };

  reader.readAsBinaryString(blob);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("FileReader")}}