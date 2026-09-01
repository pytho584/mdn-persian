---
title: "FileReader: readAsDataURL() method"
short-title: readAsDataURL()
slug: Web/API/FileReader/readAsDataURL
page-type: web-api-instance-method
browser-compat: api.FileReader.readAsDataURL
---

{{APIRef("File API")}}{{AvailableInWorkers}}

از متد **`readAsDataURL()`** در رابط {{domxref("FileReader")}} برای خواندن محتوای {{domxref("Blob")}} یا {{domxref("File")}} مشخص شده استفاده می‌شود. وقتی عملیات خواندن به پایان می‌رسد، ویژگی {{domxref("FileReader.readyState","readyState")}} به `DONE` تغییر می‌کند و رویداد {{domxref("FileReader/loadend_event", "loadend")}} راه‌اندازی می‌شود. در آن زمان، ویژگی {{domxref("FileReader.result","result")}} حاوی داده‌ها به صورت یک [data: URL](/en-US/docs/Web/URI/Reference/Schemes/data) است که داده‌های فایل را به صورت یک رشته کدگذاری شده base64 نمایش می‌دهد.

> [!NOTE]
> نمی‌توان {{domxref("FileReader.result","result")}} مربوط به blob را مستقیماً به صورت Base64 رمزگشایی کرد بدون اینکه ابتدا اعلان Data-URL که قبل از داده‌های کدگذاری شده Base64 قرار دارد حذف شود. برای دریافت تنها رشته کدگذاری شده Base64، ابتدا `data:*/*;base64,` را از نتیجه حذف کنید.

## Syntax

```js-nolint
readAsDataURL(blob)
```

### پارامترها

- `blob`
  - : {{domxref("Blob")}} یا {{domxref("File")}} که باید از آن خوانده شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### خواندن یک فایل

#### HTML

```html
<input type="file" /><br />
<img src="" height="200" alt="پیش‌نمایش تصویر" />
```

#### JavaScript

```js
const preview = document.querySelector("img");
const fileInput = document.querySelector("input[type=file]");

fileInput.addEventListener("change", previewFile);

function previewFile() {
  const file = fileInput.files[0];
  const reader = new FileReader();

  reader.addEventListener("load", () => {
    // تبدیل فایل تصویر به رشته base64
    preview.src = reader.result;
  });

  if (file) {
    reader.readAsDataURL(file);
  }
}
```

#### نتیجه

{{EmbedLiveSample("Reading a single file", "100%", 240)}}

### خواندن چندین فایل

#### HTML

```html
<input id="browse" type="file" multiple />
<div id="preview"></div>
```

#### JavaScript

```js
function previewFiles() {
  const preview = document.querySelector("#preview");
  const files = document.querySelector("input[type=file]").files;

  function readAndPreview(file) {
    // اطمینان از اینکه `file.name` با معیارهای پسوند ما مطابقت دارد
    if (/\.(?:jpe?g|png|gif)$/i.test(file.name)) {
      const reader = new FileReader();

      reader.addEventListener("load", () => {
        const image = new Image();
        image.height = 100;
        image.title = file.name;
        image.src = reader.result;
        preview.appendChild(image);
      });

      reader.readAsDataURL(file);
    }
  }

  if (files) {
    Array.prototype.forEach.call(files, readAndPreview);
  }
}

const picker = document.querySelector("#browse");
picker.addEventListener("change", previewFiles);
```

#### نتیجه

{{EmbedLiveSample("Reading multiple files", "100%", 240)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("FileReader")}}
- {{domxref("URL.createObjectURL_static", "URL.createObjectURL()")}}