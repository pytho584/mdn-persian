---
title: "FileReader: readyState property"
short-title: readyState
slug: Web/API/FileReader/readyState
page-type: web-api-instance-property
browser-compat: api.FileReader.readyState
---

{{APIRef("File API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`readyState`** در رابط {{domxref("FileReader")}} وضعیت فعلی عملیات خواندن را ارائه می‌دهد. این مقدار یکی از حالت‌های `EMPTY`، `LOADING` یا `DONE` خواهد بود.

## مقدار

عددی که یکی از سه ثابت حالت ممکن تعریف‌شده در رابط {{domxref("FileReader")}} است:

- `FileReader.EMPTY` (0)
  - : شیء خوانده‌ساز (Reader) ایجاد شده است، اما هنوز هیچ‌کدام از متدهای خواندن فراخوانی نشده‌اند.
- `FileReader.LOADING` (1)
  - : یک متد خواندن فراخوانی شده است. یک {{domxref("File")}} یا {{domxref("Blob")}} در حال خوانده‌شدن است و هنوز خطایی رخ نداده است.
- `FileReader.DONE` (2)
  - : عملیات خواندن کامل شده است. این می‌تواند به این معنی باشد که: تمام {{domxref("File")}} یا {{domxref("Blob")}} در حافظه خوانده شده است، خطای خواندن فایل رخ داده است، یا {{domxref("FileReader.abort()", "abort()")}} فراخوانی شده و خواندن لغو شده است.

## مثال‌ها

```js
const reader = new FileReader();
console.log("EMPTY", reader.readyState); // readyState will be 0

reader.readAsText(blob);
console.log("LOADING", reader.readyState); // readyState will be 1

reader.onloadend = () => {
  console.log("DONE", reader.readyState); // readyState will be 2
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Blob")}}