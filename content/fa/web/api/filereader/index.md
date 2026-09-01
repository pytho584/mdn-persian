---
title: FileReader
slug: Web/API/FileReader
page-type: web-api-interface
browser-compat: api.FileReader
---

{{APIRef("File API")}}{{AvailableInWorkers}}

رابط **`FileReader`** به برنامه‌های وب اجازه می‌دهد تا محتویات فایل‌ها (یا بافرهای داده خام) ذخیره‌شده در رایانه کاربر را به‌صورت ناهمگام (asynchronous) بخوانند، با استفاده از اشیاء {{domxref("File")}} یا {{domxref("Blob")}} برای مشخص‌کردن فایل یا داده موردنظر برای خواندن.

اشیاء File ممکن است از یک شیء {{domxref("FileList")}} به‌دست آیند که در نتیجه انتخاب فایل توسط کاربر از طریق عنصر `<input type="file">` بازگردانده می‌شود، یا از شیء {{domxref("DataTransfer")}} یک عملیات کشیدن و رها کردن (drag and drop). `FileReader` فقط می‌تواند به محتویات فایل‌هایی دسترسی پیدا کند که کاربر به‌صراحت انتخاب کرده است؛ نمی‌توان از آن برای خواندن یک فایل بر اساس مسیر (pathname) از سیستم فایل کاربر استفاده کرد. برای خواندن فایل‌ها در سیستم فایل سمت کلاینت بر اساس مسیر، از [File System Access API](/en-US/docs/Web/API/File_System_API) استفاده کنید. برای خواندن فایل‌های سمت سرور، از {{domxref("Window/fetch", "fetch()")}} استفاده کنید، در صورت خواندن از مبدأ دیگر (cross-origin) با مجوز [CORS](/en-US/docs/Web/HTTP/Guides/CORS).

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("FileReader.FileReader", "FileReader()")}}
  - : یک شیء `FileReader` جدید بازمی‌گرداند.

برای جزئیات و مثال‌ها، [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications) را ببینید.

## ویژگی‌های نمونه (Instance properties)

- {{domxref("FileReader.error")}} {{ReadOnlyInline}}
  - : یک {{domxref("DOMException")}} که خطای رخ‌داده در هنگام خواندن فایل را نشان می‌دهد.
- {{domxref("FileReader.readyState")}} {{ReadOnlyInline}}
  - : عددی که وضعیت `FileReader` را نشان می‌دهد. یکی از مقادیر زیر است:

    | نام        | مقدار | توضیح                                |
    | ---------- | ----- | ------------------------------------ |
    | `EMPTY`    | `0`   | هنوز داده‌ای بارگذاری نشده است.      |
    | `LOADING`  | `1`   | در حال بارگذاری داده است.            |
    | `DONE`     | `2`   | کل درخواست خواندن تکمیل شده است.     |

- {{domxref("FileReader.result")}} {{ReadOnlyInline}}
  - : محتویات فایل. این ویژگی فقط پس از تکمیل عملیات خواندن معتبر است و قالب داده به روشی بستگی دارد که برای شروع عملیات خواندن استفاده شده است.

## روش‌های نمونه (Instance methods)

- {{domxref("FileReader.abort()")}}
  - : عملیات خواندن را لغو می‌کند. پس از بازگشت، `readyState` برابر با `DONE` خواهد بود.
- {{domxref("FileReader.readAsArrayBuffer()")}}
  - : خواندن محتویات {{domxref("Blob")}} مشخص‌شده را آغاز می‌کند؛ پس از اتمام، ویژگی `result` حاوی یک {{jsxref("ArrayBuffer")}} است که داده‌های فایل را نشان می‌دهد.
- {{domxref("FileReader.readAsBinaryString()")}} {{deprecated_inline}}
  - : خواندن محتویات {{domxref("Blob")}} مشخص‌شده را آغاز می‌کند؛ پس از اتمام، ویژگی `result` حاوی داده‌های باینری خام فایل به‌صورت یک رشته (string) است.
- {{domxref("FileReader.readAsDataURL()")}}
  - : خواندن محتویات {{domxref("Blob")}} مشخص‌شده را آغاز می‌کند؛ پس از اتمام، ویژگی `result` حاوی یک URL با طرح `data:` است که داده‌های فایل را نشان می‌دهد.
- {{domxref("FileReader.readAsText()")}}
  - : خواندن محتویات {{domxref("Blob")}} مشخص‌شده را آغاز می‌کند؛ پس از اتمام، ویژگی `result` حاوی محتویات فایل به‌صورت یک رشته متنی است. می‌توان یک نام encoding اختیاری نیز مشخص کرد.

## رویدادها (Events)

به این رویدادها با استفاده از {{domxref("EventTarget/addEventListener", "addEventListener()")}} گوش دهید یا با اختصاص یک شنونده رویداد به ویژگی `oneventname` این رابط. پس از پایان استفاده از `FileReader`، شنونده‌های رویداد را با {{domxref("EventTarget.removeEventListener", "removeEventListener()")}} حذف کنید تا از نشت حافظه (memory leaks) جلوگیری شود.

- {{domxref("FileReader/abort_event", "abort")}}
  - : زمانی رخ می‌دهد که یک خواندن لغو شده است، مثلاً به این دلیل که برنامه متد {{domxref("FileReader.abort()")}} را فراخوانی کرده است.
- {{domxref("FileReader/error_event", "error")}}
  - : زمانی رخ می‌دهد که خواندن به دلیل یک خطا ناموفق بوده است.
- {{domxref("FileReader/load_event", "load")}}
  - : زمانی رخ می‌دهد که یک خواندن با موفقیت کامل شده است.
- {{domxref("FileReader/loadend_event", "loadend")}}
  - : زمانی رخ می‌دهد که یک خواندن کامل شده است، چه موفق و چه ناموفق.
- {{domxref("FileReader/loadstart_event", "loadstart")}}
  - : زمانی رخ می‌دهد که یک خواندن شروع شده است.
- {{domxref("FileReader/progress_event", "progress")}}
  - : به‌طور دوره‌ای در حین خواندن داده رخ می‌دهد.

## مثال‌ها

### استفاده از FileReader

این مثال محتویات یک فایل متنی را مستقیماً در مرورگر می‌خواند و نمایش می‌دهد.

#### HTML

```html
<h1>File Reader</h1>
<input type="file" id="file-input" />
<div id="message"></div>
<pre id="file-content"></pre>
```

#### JavaScript

```js
const fileInput = document.getElementById("file-input");
const fileContentDisplay = document.getElementById("file-content");
const messageDisplay = document.getElementById("message");

fileInput.addEventListener("change", handleFileSelection);

function handleFileSelection(event) {
  const file = event.target.files[0];
  fileContentDisplay.textContent = ""; // Clear previous file content
  messageDisplay.textContent = ""; // Clear previous messages

  // Validate file existence and type
  if (!file) {
    showMessage("No file selected. Please choose a file.", "error");
    return;
  }

  if (!file.type.startsWith("text")) {
    showMessage("Unsupported file type. Please select a text file.", "error");
    return;
  }

  // Read the file
  const reader = new FileReader();
  reader.onload = () => {
    fileContentDisplay.textContent = reader.result;
  };
  reader.onerror = () => {
    showMessage("Error reading the file. Please try again.", "error");
  };
  reader.readAsText(file);
}

// Displays a message to the user
function showMessage(message, type) {
  messageDisplay.textContent = message;
  messageDisplay.style.color = type === "error" ? "red" : "green";
}
```

### نتیجه

{{EmbedLiveSample("Using FileReader", 640, 300)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)
- {{domxref("File")}}
- {{domxref("Blob")}}
- {{domxref("FileReaderSync")}}