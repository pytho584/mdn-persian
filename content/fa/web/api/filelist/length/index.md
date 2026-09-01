---
title: "FileList: length property"
short-title: length
slug: Web/API/FileList/length
page-type: web-api-instance-property
browser-compat: api.FileList.length
---

{{APIRef("File API")}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`length`** در رابط {{domxref("FileList")}} تعداد فایل‌های موجود در `FileList` را بازمی‌گرداند.

## مقدار

یک عدد که تعداد فایل‌های موجود در لیست را نشان می‌دهد.

## نمونه‌ها

### چاپ تعداد فایل‌های انتخاب‌شده

در این مثال، از `length` برای یافتن تعداد آیتم‌های موجود در `FileList` استفاده می‌کنیم.

#### HTML

```html
<input type="file" multiple />
<div class="output"></div>
```

#### JavaScript

```js
const fileInput = document.querySelector("input[type=file]");
const output = document.querySelector(".output");

fileInput.addEventListener("change", () => {
  const fileList = fileInput.files;
  output.textContent = `You've selected: ${fileList.length} file(s)`;
});
```

#### نتیجه

{{EmbedLiveSample("Printing the number of files selected")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}