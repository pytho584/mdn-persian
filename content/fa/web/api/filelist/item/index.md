---
title: "FileList: item() method"
short-title: item()
slug: Web/API/FileList/item
page-type: web-api-instance-method
browser-compat: api.FileList.item
---

{{APIRef("File API")}}{{AvailableInWorkers}}

متد **`item()`** از رابط {{domxref("FileList")}} یک شی {{domxref("File")}} را برمی‌گرداند که نمایانگر فایل در اندیس مشخص‌شده در فهرست فایل‌ها است.

## سینتکس

```js-nolint
item(index)
```

### پارامترها

- `index`
  - اندیس مبتنی بر صفر فایلی که باید از فهرست دریافت شود.

### مقدار بازگشتی

یک شی {{domxref("File")}} که نمایانگر فایل درخواستی است.

## مثال‌ها

### چاپ نام یک فایل

در این مثال، از `item()` برای انتخاب اولین آیتم در `FileList` استفاده می‌کنیم.

#### HTML

```html
<input type="file" />
<div class="output"></div>
```

#### جاوااسکریپت

```js
const fileInput = document.querySelector("input[type=file]");
const output = document.querySelector(".output");

fileInput.addEventListener("change", () => {
  const fileList = fileInput.files;
  if (fileList.length > 0) {
    const file = fileList.item(0);
    output.textContent = `You selected: ${file.name}`;
  }
});
```

#### نتیجه

{{EmbedLiveSample("Printing the name of a file")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}