---
title: "File: name property"
short-title: name
slug: Web/API/File/name
page-type: web-api-instance-property
browser-compat: api.File.name
---

{{APIRef("File API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`name`** در رابط {{domxref("File")}} نام فایلی را که توسط یک شیء {{domxref("File")}} نمایش داده می‌شود، برمی‌گرداند. به دلایل امنیتی، مسیر فایل در این ویژگی لحاظ نمی‌شود.

## مقدار

یک رشته که شامل نام فایل بدون مسیر است، مانند «My Resume.rtf».

## مثال‌ها

### HTML

```html
<input type="file" id="file-picker" multiple />
<div>
  <p>List of selected files:</p>
  <ul id="output"></ul>
</div>
```

### JavaScript

```js
const output = document.getElementById("output");
const filePicker = document.getElementById("file-picker");

filePicker.addEventListener("change", (event) => {
  const files = event.target.files;
  output.textContent = "";

  for (const file of files) {
    const li = document.createElement("li");
    li.textContent = file.name;
    output.appendChild(li);
  }
});
```

### نتیجه

{{EmbedLiveSample('Examples')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)