---
title: "HTMLInputElement: webkitEntries property"
---

---
title: "HTMLInputElement: webkitEntries property"
short-title: webkitEntries
slug: Web/API/HTMLInputElement/webkitEntries
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.webkitEntries
---

{{APIRef("File and Directory Entries API")}}

ویژگی فقط‌خواندنیِ **`webkitEntries`** در واسط {{domxref("HTMLInputElement")}} شامل آرایه‌ای از ورودی‌های سیستم فایل (به شکل آبجکت‌هایی مبتنی بر {{domxref("FileSystemEntry")}}) است که فایل‌ها و/یا پوشه‌های انتخاب‌شده توسط کاربر را با استفاده از یک عنصر {{HTMLElement("input")}} از نوع `file` نشان می‌دهد؛ اما فقط اگر این انتخاب از طریق کشیدن و رها کردن (drag-and-drop) انجام شده باشد. انتخاب یک فایل در کادر محاوره‌ای، این ویژگی را خالی باقی می‌گذارد.

این آرایه فقط زمانی می‌تواند شامل پوشه‌ها باشد که ویژگی {{domxref("HTMLInputElement.webkitdirectory", "webkitdirectory")}} مقدار `true` داشته باشد. این یعنی عنصر `<input>` به‌گونه‌ای پیکربندی شده است که به کاربر اجازه دهد پوشه‌ها را انتخاب کند.

> [!NOTE]
> این ویژگی در مشخصات (specification) به دلیل منشأ خود که یک API مخصوص گوگل کروم بوده، `webkitEntries` نامیده می‌شود. احتمال دارد روزی تغییر نام دهد.

## مقدار

آرایه‌ای از آبجکت‌های مبتنی بر {{domxref("FileSystemEntry")}}؛ هر کدام نمایانگر یک فایل انتخاب‌شده در عنصر {{HTMLElement("input")}} است. به‌طور دقیق‌تر، فایل‌ها با آبجکت‌های {{domxref("FileSystemFileEntry")}} و در صورت مجاز بودن، پوشه‌ها با آبجکت‌های {{domxref("FileSystemDirectoryEntry")}} نمایش داده می‌شوند.

## مثال‌ها

این مثال نشان می‌دهد چگونه یک عنصر `<input>` برای انتخاب فایل بسازیم و فایل‌های انتخاب‌شده را پردازش کنیم.

### HTML

```html
<input id="files" type="file" multiple />
```

### JavaScript

```js
document.getElementById("files").addEventListener("change", (event) => {
  event.target.webkitEntries.forEach((entry) => {
    /* do stuff with the entry */
  });
});
```

هر بار که رویداد {{domxref("HTMLElement/change_event", "change")}} رخ دهد، این کد روی فایل‌های انتخاب‌شده پیمایش می‌کند، آبجکت‌های مبتنی بر {{domxref("FileSystemEntry")}} آن‌ها را به دست می‌آورد و روی آن‌ها عملیات انجام می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("HTMLInputElement")}}
- {{domxref("FileSystemEntry")}}
- {{domxref("FileSystem")}}