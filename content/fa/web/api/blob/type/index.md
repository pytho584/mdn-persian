---
title: "Blob: type property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Blob/type"
translated_by: "n8n + AI"
---

---
title: "Blob: type property"
short-title: type
slug: Web/API/Blob/type
page-type: web-api-instance-property
browser-compat: api.Blob.type
---

{{APIRef("File API")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`type`** از رابط {{domxref("Blob")}}، نوع {{Glossary("MIME type")}} فایل را برمی‌گرداند.

> [!NOTE]
> بر اساس پیاده‌سازی فعلی، مرورگرها در واقع جریان بایت فایل را برای تعیین نوع رسانه آن نمی‌خوانند.
> این مقدار بر اساس پسوند فایل فرض می‌شود؛ یک فایل تصویری PNG که به `.txt` تغییر نام داده شود، مقدار `"_text/plain_"` را برمی‌گرداند، نه `"_image/png_"`. علاوه بر این، `blob.type` معمولاً فقط برای انواع فایل‌های رایج مانند تصاویر، اسناد HTML، صدا و ویدئو قابل اعتماد است.
> پسوندهای فایل غیرمعمول یک رشته خالی برمی‌گردانند.
> پیکربندی کلاینت (برای مثال، رجیستری ویندوز) ممکن است حتی برای انواع رایج مقادیر غیرمنتظره‌ای ایجاد کند. **به توسعه‌دهندگان توصیه می‌شود که به این ویژگی به عنوان تنها طرح اعتبارسنجی تکیه نکنند.**

## مقدار

یک رشته شامل نوع MIME فایل، یا رشته‌ای خالی اگر نوع قابل تعیین نباشد.

## مثال‌ها

این مثال از کاربر می‌خواهد تعدادی فایل را انتخاب کند، سپس هر فایل را بررسی می‌کند تا مطمئن شود که یکی از مجموعه داده‌شده از انواع فایل‌های تصویری است.

### HTML

```html
<input type="file" id="input" multiple />
<output id="output">Choose image files…</output>
```

```css hidden
output {
  display: block;
  margin-top: 16px;
}
```

### JavaScript

```js
// Our application only allows GIF, PNG, and JPEG images
const allowedFileTypes = ["image/png", "image/jpeg", "image/gif"];

const input = document.getElementById("input");
const output = document.getElementById("output");

input.addEventListener("change", (event) => {
  const files = event.target.files;

  if (files.length === 0) {
    output.innerText = "Choose image files…";
    return;
  }

  const allAllowed = Array.from(files).every((file) =>
    allowedFileTypes.includes(file.type),
  );
  output.innerText = allAllowed
    ? "All files clear!"
    : "Please choose image files only.";
});
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Blob")}}
- [Using files from web applications](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)