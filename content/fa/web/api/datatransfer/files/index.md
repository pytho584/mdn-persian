---
title: "DataTransfer: files property"
short-title: files
slug: Web/API/DataTransfer/files
page-type: web-api-instance-property
browser-compat: api.DataTransfer.files
---

{{APIRef("HTML Drag and Drop API")}}

خاصیت **`files`** (فقط‌خواندنی) اشیاء [`DataTransfer`](/en-US/docs/Web/API/DataTransfer) فهرستی از [فایل‌ها](/en-US/docs/Web/API/FileList) در عملیات کشیدن (drag) است. اگر عملیات شامل هیچ فایلی نباشد، فهرست خالی است.

این قابلیت برای کشیدن فایل‌ها از دسکتاپ کاربر به داخل مرورگر استفاده می‌شود.

> [!NOTE]
> خاصیت `files` اشیاء [`DataTransfer`](/en-US/docs/Web/API/DataTransfer) فقط از داخل رویدادهای {{domxref("HTMLElement/drop_event", "drop")}} و {{domxref("Element/paste_event", "paste")}} قابل دسترسی است. برای همه رویدادهای دیگر، خاصیت `files` خالی خواهد بود — زیرا مخزن دادهٔ زیرین آن در [حالت محافظت‌شده](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store#protected_mode) قرار دارد.

## مقدار

یک {{domxref("FileList")}} شامل فایل‌های موجود در عملیات کشیدن، که به ازای هر فایل یک آیتم در آن وجود دارد. اگر عملیات کشیدن فایلی نداشته باشد، فهرست خالی است.

## مثال‌ها

### خواندن فهرست فایل‌ها

این مثال یک ناحیهٔ ساده می‌سازد که می‌توانید فایل‌ها را در آن رها کنید و برخی فراداده‌ها را نمایش می‌دهد.

```html
<pre id="output">Drop files here from your file system.</pre>
```

```css
#output {
  min-height: 200px;
  border: 1px solid black;
  padding: 1em;
}
```

```js
const output = document.getElementById("output");

function log(text) {
  output.innerText += text;
}

output.addEventListener("dragenter", (e) => {
  e.stopPropagation();
  e.preventDefault();
  output.textContent = "";
});
output.addEventListener("dragover", (e) => {
  e.stopPropagation();
  e.preventDefault();
});
output.addEventListener("drop", (e) => {
  e.stopPropagation();
  e.preventDefault();
  const files = event.dataTransfer.files;
  log(`File Count: ${files.length}\n`);

  for (const file of files) {
    log(`  File: ${file}, ${file.name}, ${file.size} bytes\n`);
  }
});
```

{{EmbedLiveSample("reading_the_files_list", "", "300")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}