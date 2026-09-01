---
title: "DataTransferItem: webkitGetAsEntry() method"
short-title: webkitGetAsEntry()
slug: Web/API/DataTransferItem/webkitGetAsEntry
page-type: web-api-instance-method
browser-compat: api.DataTransferItem.webkitGetAsEntry
---

{{APIRef("HTML Drag and Drop API")}}

اگر آیتم توصیف‌شده توسط {{domxref("DataTransferItem")}} یک فایل باشد، `webkitGetAsEntry()` یک {{domxref("FileSystemFileEntry")}} یا {{domxref("FileSystemDirectoryEntry")}} متناظر با آن را بازمی‌گرداند. اگر آیتم فایل نباشد، مقدار `null` بازگردانده می‌شود.

> [!NOTE]
> این تابع هم‌اکنون در مرورگرهای غیر-WebKit از جمله Firefox با نام `webkitGetAsEntry()` پیاده‌سازی شده است؛ ممکن است در آینده به `getAsEntry()` تغییر نام دهد؛ بنابراین بهتر است کد خود را به‌صورت دفاعی بنویسید و هر دو حالت را پوشش دهید.

## Syntax

```js-nolint
webkitGetAsEntry()
```

### Parameters

هیچ‌کدام.

### Return value

یک شیء مبتنی بر {{domxref("FileSystemEntry")}} که آیتم رهاشده را توصیف می‌کند. این مقدار یا {{domxref("FileSystemFileEntry")}} خواهد بود یا {{domxref("FileSystemDirectoryEntry")}}. اگر آیتم رهاشده یک فایل نباشد، یا اگر شیء {{domxref("DataTransferItem")}} در حالت خواندن یا خواندن/نوشتن نباشد، متد کار خود را متوقف کرده و مقدار `null` را بازمی‌گرداند.

## Examples

در این مثال، یک ناحیه رهاسازی ایجاد می‌شود که به رویداد {{domxref("HTMLElement/drop_event", "drop")}} پاسخ می‌دهد و با اسکن فایل‌ها و پوشه‌های رهاشده، یک فهرست سلسله‌مراتبی از پوشه‌ها را به نمایش درمی‌آورد.

### HTML

بخش HTML، خودِ ناحیه رهاسازی را ایجاد می‌کند که یک عنصر {{HTMLElement("div")}} با شناسه `"dropzone"` است، و همچنین یک عنصر فهرست بدون ترتیب با شناسه `"listing"`.

```html
<p>Drag files and/or directories to the box below!</p>

<div id="dropzone">
  <div id="boxtitle">Drop Files Here</div>
</div>

<h2>Directory tree:</h2>

<ul id="listing"></ul>
```

### CSS

استایل‌های استفاده‌شده در این مثال در ادامه نشان داده شده‌اند.

```css
#dropzone {
  text-align: center;
  width: 300px;
  height: 100px;
  margin: 10px;
  padding: 10px;
  border: 4px dashed red;
  border-radius: 10px;
}

#boxtitle {
  display: table-cell;
  vertical-align: middle;
  text-align: center;
  color: black;
  font:
    bold 2em "Arial",
    sans-serif;
  width: 300px;
  height: 100px;
}

body {
  font:
    14px "Arial",
    sans-serif;
}
```

### JavaScript

ابتدا به تابع بازگشتی `scanFiles()` نگاه می‌کنیم. این تابع یک {{domxref("FileSystemEntry")}} را به‌عنوان ورودی می‌گیرد که نمایانگر یک ورودی در سیستم فایل است و باید اسکن و پردازش شود (پارامتر `item`)؛ همچنین یک عنصر دریافت می‌کند که فهرست محتویات باید در آن درج شود (پارامتر `container`).

> [!NOTE]
> برای خواندن همه فایل‌های موجود در یک پوشه، باید `readEntries` به‌طور مکرر فراخوانی شود تا زمانی که یک آرایه خالی بازگرداند. در مرورگرهای مبتنی بر Chromium، مثال زیر حداکثر ۱۰۰ ورودی را بازمی‌گرداند.

```js
let dropzone = document.getElementById("dropzone");
let listing = document.getElementById("listing");

function scanFiles(item, container) {
  let elem = document.createElement("li");
  elem.textContent = item.name;
  container.appendChild(elem);

  if (item.isDirectory) {
    let directoryReader = item.createReader();
    let directoryContainer = document.createElement("ul");
    container.appendChild(directoryContainer);
    directoryReader.readEntries((entries) => {
      entries.forEach((entry) => {
        scanFiles(entry, directoryContainer);
      });
    });
  }
}
```

تابع `scanFiles()` کار خود را با ایجاد یک عنصر جدید {{HTMLElement("li")}} برای نمایش آیتمِ در حال اسکن آغاز می‌کند، نام آیتم را به‌عنوان محتوای متنی آن قرار می‌دهد و سپس آن را به ظرف اضافه می‌کند. در این مثال، همان‌طور که به‌زودی خواهید دید، ظرف همیشه یک عنصر فهرست است.

پس از قرار گرفتن آیتم جاری در فهرست، ویژگی {{domxref("FileSystemEntry.isDirectory", "isDirectory")}} آیتم بررسی می‌شود. اگر آیتم یک پوشه باشد، باید به‌صورت بازگشتی وارد آن پوشه شویم. اولین قدم ایجاد یک {{domxref("FileSystemDirectoryReader")}} برای دریافت محتویات پوشه است. این کار با فراخوانی متد {{domxref("FileSystemDirectoryEntry.createReader", "createReader()")}} روی آیتم انجام می‌شود. سپس یک {{HTMLElement("ul")}} جدید ساخته شده و به فهرست والد اضافه می‌شود؛ این عنصر، محتویات پوشه را در سطح بعدی سلسله‌مراتب فهرست در بر خواهد گرفت.

پس از آن، {{domxref("FileSystemDirectoryReader.readEntries", "directoryReader.readEntries()")}} فراخوانی می‌شود تا همه ورودی‌های داخل پوشه خوانده شوند. سپس هر یک از این ورودی‌ها به نوبه خود در یک فراخوانی بازگشتی به `scanFiles()` برای پردازش ارسال می‌شوند. ورودی‌هایی که فایل هستند در فهرست درج می‌شوند؛ ورودی‌هایی که پوشه هستند نیز در فهرست درج شده و سطح جدیدی از سلسله‌مراتب فهرست در زیر آن‌ها افزوده می‌شود و همین روند ادامه می‌یابد.

سپس نوبت به مدیریت‌کننده‌های رویداد می‌رسد. ابتدا جلوگیری می‌کنیم تا رویداد {{domxref("HTMLElement/dragover_event", "dragover")}} توسط مدیریت‌کننده پیش‌فرض پردازش نشود؛ به این ترتیب ناحیه رهاسازی ما می‌تواند رویداد drop را دریافت کند:

```js
dropzone.addEventListener("dragover", (event) => {
  event.preventDefault();
});
```

البته مدیریت‌کننده‌ای که همه‌چیز را شروع می‌کند، مدیریت‌کننده رویداد {{domxref("HTMLElement/drop_event", "drop")}} است:

```js
dropzone.addEventListener("drop", (event) => {
  let items = event.dataTransfer.items;

  event.preventDefault();
  listing.textContent = "";

  for (const item of items) {
    const entry = item.webkitGetAsEntry();

    if (entry) {
      scanFiles(entry, listing);
    }
  }
});
```

این کد فهرست اشیاء {{domxref("DataTransferItem")}} را که نمایانگر آیتم‌های رهاشده هستند، از `event.dataTransfer.items` دریافت می‌کند. سپس {{domxref("Event.preventDefault()")}} را فراخوانی می‌کنیم تا رویداد پس از پایان کار ما بیشتر پردازش نشود.

حالا زمان شروع ساخت فهرست فرا رسیده است. ابتدا فهرست با خالی کردن مقدار {{domxref("Node.textContent", "listing.textContent")}} پاک می‌شود. در نتیجه یک {{HTMLElement("ul")}} خالی در اختیار داریم که می‌توانیم درج ورودی‌های پوشه را در آن آغاز کنیم.

سپس روی آیتم‌های موجود در فهرست آیتم‌های رهاشده پیمایش می‌کنیم. برای هر یک از آن‌ها، متد `webkitGetAsEntry()` را فراخوانی می‌کنیم تا یک {{domxref("FileSystemEntry")}} نمایانگر فایل به دست آوریم. اگر این فراخوانی موفق باشد، تابع `scanFiles()` را برای پردازش آیتم فراخوانی می‌کنیم — یا اگر صرفاً یک فایل است، آن را به فهرست اضافه می‌کنیم، و یا اگر پوشه است، آن را اضافه کرده و به داخل آن نیز می‌رویم.

### Result

می‌توانید عملکرد این مثال را با امتحان کردن آن در پایین مشاهده کنید. چند فایل و پوشه پیدا کنید و آن‌ها را به داخل این ناحیه بکشید و سپس خروجی حاصل را بررسی کنید.

{{EmbedLiveSample('Examples', 600, 400)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API)
- {{domxref("DataTransferItem")}}
- {{domxref("FileSystemEntry")}}، {{domxref("FileSystemFileEntry")}} و {{domxref("FileSystemDirectoryEntry")}}
- رویدادها: {{domxref("HTMLElement/dragover_event", "dragover")}} و {{domxref("HTMLElement/drop_event", "drop")}}