---
title: "HTMLInputElement: webkitdirectory property"
---

---
title: "HTMLInputElement: webkitdirectory property"
short-title: webkitdirectory
slug: Web/API/HTMLInputElement/webkitdirectory
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.webkitdirectory
---

{{APIRef("File and Directory Entries API")}}

ویژگی **`webkitdirectory`** در رابط {{domxref("HTMLInputElement")}}، بازتاب‌دهندهٔ ویژگی HTML [`webkitdirectory`](/en-US/docs/Web/HTML/Reference/Elements/input/file#webkitdirectory) است که نشان می‌دهد عناصر [`<input type="file">`](/en-US/docs/Web/HTML/Reference/Elements/input/file) می‌توانند فقط پوشه‌ها را انتخاب کنند، نه فایل‌ها را.

هنگامی که یک پوشه انتخاب می‌شود، آن پوشه و کل سلسله‌مراتب محتویات آن در مجموعهٔ موارد انتخاب‌شده قرار می‌گیرند. ورودی‌های (entries) سیستم فایل انتخاب‌شده را می‌توان با استفاده از ویژگی {{domxref("HTMLInputElement.webkitEntries", "webkitEntries")}} به دست آورد.

> [!NOTE]
> این ویژگی در مشخصات «webkitdirectory» نامیده می‌شود، زیرا ریشه در یک API ویژهٔ Google Chrome دارد.

## مقدار

یک مقدار بولی (Boolean)؛ `true` اگر عنصر {{HTMLElement("input")}} باید فقط انتخاب پوشه‌ها را مجاز کند، و `false` اگر فقط فایل‌ها قابل انتخاب باشند.

## توضیحات

تنظیم `webkitdirectory` به `true` باعث می‌شود عنصر ورودی به‌جای فایل‌ها، پوشه‌هایی را برای انتخاب به کاربر ارائه دهد. پس از اینکه کاربر یک پوشه را انتخاب کرد، هر شیء {{domxref("File")}} در مجموعهٔ `files` بازگشت‌داده‌شده، ویژگی {{domxref("File.webkitRelativePath")}} را به مسیری نسبی نسبت به پوشهٔ والد انتخاب‌شده تنظیم کرده است. برای مثال، این سیستم فایل را در نظر بگیرید:

```plain
PhotoAlbums
├── Birthdays
│   ├── Jamie's 1st birthday
│   │   ├── PIC1000.jpg
│   │   └── PIC1044.jpg
│   └── Don's 40th birthday
│       ├── PIC2343.jpg
│       └── PIC2356.jpg
└── Vacations
    └── Mars
        ├── PIC5556.jpg
        ├── PIC5684.jpg
        └── PIC5712.jpg
```

اگر کاربر پوشهٔ `PhotoAlbums` را انتخاب کند، فهرست گزارش‌شده توسط `files` برای هر فایل یک شیء {{domxref("File")}} خواهد داشت. ورودی مربوط به `PIC2343.jpg` دارای `webkitRelativePath` به شکل `PhotoAlbums/Birthdays/Don's 40th birthday/PIC2343.jpg` خواهد بود. این کار تعیین سلسله‌مراتب پوشهٔ انتخاب‌شده را ممکن می‌سازد، حتی اگر {{domxref("FileList")}} تخت (flat) باشد.

> [!NOTE]
> رفتار `webkitRelativePath` در _Chromium < 72_ متفاوت است.
> برای جزئیات بیشتر به [این باگ](https://crbug.com/124187) مراجعه کنید.

## مثال‌ها

در این مثال، یک انتخاب‌گر پوشه نمایش داده می‌شود که به کاربر اجازه می‌دهد یک یا چند پوشه را انتخاب کند. هنگامی که رویداد {{domxref("HTMLElement/change_event", "change")}} رخ می‌دهد، فهرستی از همهٔ فایل‌های موجود در سلسله‌مراتب پوشه‌های انتخاب‌شده ایجاد و نمایش داده می‌شود.

### HTML

```html
<input type="file" id="file-picker" name="fileList" webkitdirectory multiple />
<ul id="listing"></ul>
```

### JavaScript

```js
document.getElementById("file-picker").addEventListener("change", (event) => {
  let output = document.getElementById("listing");
  for (const file of event.target.files) {
    let item = document.createElement("li");
    item.textContent = file.webkitRelativePath;
    output.appendChild(item);
  }
});
```

### نتیجه

{{EmbedLiveSample('Examples')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("HTMLInputElement.webkitEntries")}}
- {{domxref("File.webkitRelativePath")}}