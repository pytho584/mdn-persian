---
title: "FileReader: readAsText() method"
short-title: readAsText()
slug: Web/API/FileReader/readAsText
page-type: web-api-instance-method
browser-compat: api.FileReader.readAsText
---

{{APIRef("File API")}}{{AvailableInWorkers}}

**`readAsText()`** متدی از رابط {{domxref("FileReader")}} است که برای خواندن محتوای {{domxref("Blob")}} یا {{domxref("File")}} مشخص‌شده استفاده می‌شود.
هنگامی که عملیات خواندن کامل می‌شود، ویژگی {{domxref("FileReader.readyState","readyState")}} به `DONE` تغییر می‌کند،
رویداد {{domxref("FileReader/loadend_event", "loadend")}} فعال می‌شود و ویژگی {{domxref("FileReader.result","result")}} حاوی محتوای فایل به‌صورت یک رشته متنی خواهد بود.

> [!NOTE]
> متد {{domxref("Blob.text()")}} یک API مبتنی بر Promise جدیدتر برای خواندن یک فایل به‌صورت متن است.

> [!NOTE]
> این متد کل محتوای فایل را در حافظه بارگذاری می‌کند و برای فایل‌های بزرگ مناسب نیست. برای فایل‌های بزرگ، {{domxref("FileReader.readAsArrayBuffer", "readAsArrayBuffer()")}} را ترجیح دهید.

## نحو

```js-nolint
readAsText(blob)
readAsText(blob, encoding)
```

### پارامترها

- `blob`
  - : {{domxref("Blob")}} یا {{domxref("File")}} که باید از آن خوانده شود.
- `encoding` {{optional_inline}}
  - : رشته‌ای که مشخص می‌کند از چه رمزگذاری برای داده‌های برگشتی استفاده شود. به‌طور پیش‌فرض، اگر این پارامتر مشخص نشود، UTF-8 در نظر گرفته می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### HTML

```html
<input type="file" /><br />
<p class="content"></p>
```

### JavaScript

```js
const content = document.querySelector(".content");
const fileInput = document.querySelector("input[type=file]");

fileInput.addEventListener("change", previewFile);

function previewFile() {
  const file = fileInput.files[0];
  const reader = new FileReader();

  reader.addEventListener("load", () => {
    // this will then display a text file
    content.innerText = reader.result;
  });

  if (file) {
    reader.readAsText(file);
  }
}
```

### نتیجه

{{EmbedLiveSample("Examples", "100%", 240)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("FileReader")}}