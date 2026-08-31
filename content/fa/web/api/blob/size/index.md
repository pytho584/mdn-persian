---
title: "Blob: size property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob/size"
translated_by: "n8n + AI"
---

---
title: "Blob: size property"
short-title: size
slug: Web/API/Blob/size
page-type: web-api-instance-property
browser-compat: api.Blob.size
---

{{APIRef("File API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`size`** از رابط {{domxref("Blob")}} اندازه {{domxref("Blob")}} یا {{domxref("File")}} را بر حسب بایت برمی‌گرداند.

## مقدار

تعداد بایت‌های داده موجود درون `Blob` (یا شیء مبتنی بر `Blob`، مانند {{domxref("File")}}).

## مثال‌ها

این مثال از یک عنصر {{HTMLElement("input")}} از نوع `file` استفاده می‌کند تا از کاربر یک گروه از فایل‌ها را درخواست کند، سپس روی آن فایل‌ها تکرار کرده و نام و اندازه آن‌ها را بر حسب بایت نمایش می‌دهد.

### HTML

```html
<input type="file" id="input" multiple />
<output id="output">Choose files…</output>
```

```css hidden
output {
  display: block;
  margin-top: 16px;
}
```

### JavaScript

```js
const input = document.getElementById("input");
const output = document.getElementById("output");

input.addEventListener("change", (event) => {
  output.innerText = "";

  for (const file of event.target.files) {
    output.innerText += `${file.name} has a size of ${file.size} bytes.\n`;
  }
});
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Blob")}}
- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)