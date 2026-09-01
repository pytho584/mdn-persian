---
title: "File: webkitRelativePath property"
short-title: webkitRelativePath
slug: Web/API/File/webkitRelativePath
page-type: web-api-instance-property
browser-compat: api.File.webkitRelativePath
---

{{APIRef("File and Directory Entries API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`webkitRelativePath`** در واسط {{domxref("File")}} شامل رشته‌ای است که مسیر فایل را نسبت به پوشه‌ای که کاربر در یک عنصر {{HTMLElement("input")}} با ویژگی
[`webkitdirectory`](/en-US/docs/Web/HTML/Reference/Elements/input#webkitdirectory) انتخاب کرده است، مشخص می‌کند.

## مقدار

رشته‌ای شامل مسیر فایل نسبت به پوشهٔ والد (ancestor directory) که کاربر انتخاب کرده است.

## مثال

در این مثال، یک انتخاب‌گر پوشه ارائه شده است که به کاربر امکان می‌دهد یک یا چند پوشه را انتخاب کند. وقتی رویداد {{domxref("HTMLElement/change_event", "change")}} رخ می‌دهد، فهرستی از همه فایل‌های موجود در سلسله‌مراتب پوشه‌های انتخاب‌شده تولید و نمایش داده می‌شود.

### HTML

```html
<input type="file" id="file-picker" name="fileList" webkitdirectory multiple />
<output id="output"></output>
```

```css hidden
output {
  display: block;
  white-space: pre-wrap;
}
```

### JavaScript

```js
const output = document.getElementById("output");
const filePicker = document.getElementById("file-picker");

filePicker.addEventListener("change", (event) => {
  const files = event.target.files;

  for (const file of files) {
    output.textContent += `${file.webkitRelativePath}\n`;
  }
});
```

### نتیجه

{{EmbedLiveSample('Example')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("HTMLInputElement.webkitEntries")}}
- {{domxref("HTMLInputElement.webkitdirectory")}}