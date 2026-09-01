---
title: "File System API"
slug: Web/API/File_System_API
page-type: web-api-overview
browser-compat:
  - api.FileSystemHandle
  - api.FileSystemFileHandle
  - api.FileSystemDirectoryHandle
  - api.FileSystemWritableFileStream
  - api.FileSystemSyncAccessHandle
spec-urls:
  - https://fs.spec.whatwg.org/
  - https://wicg.github.io/file-system-access/
---

{{securecontext_header}}{{DefaultAPISidebar("File System API")}}{{AvailableInWorkers}}

**File System API** — با افزونه‌هایی که از طریق [**File System Access API**](https://wicg.github.io/file-system-access/) برای دسترسی به فایل‌های سیستم فایل دستگاه ارائه می‌شود — قابلیت‌های خواندن، نوشتن و مدیریت فایل را فراهم می‌کند.

برای مقایسه بین این API، [File and Directory Entries API](/en-US/docs/Web/API/File_and_Directory_Entries_API) و [File API](/en-US/docs/Web/API/File_API)، به [رابطه با سایر APIهای مرتبط با فایل](/en-US/docs/Web/API/File_API#relationship_to_other_file-related_apis) مراجعه کنید.

## مفاهیم و کاربرد

این API امکان تعامل با فایل‌های موجود در دستگاه محلی کاربر یا سیستم فایل شبکه‌ای قابل دسترس برای کاربر را فراهم می‌کند. عملکرد اصلی این API شامل خواندن فایل‌ها، نوشتن یا ذخیره فایل‌ها و دسترسی به ساختار دایرکتوری است.

بیشتر تعامل با فایل‌ها و دایرکتوری‌ها از طریق دسته‌ها (handles) انجام می‌شود. کلاس والد {{domxref('FileSystemHandle')}} به تعریف دو کلاس فرزند کمک می‌کند: {{domxref('FileSystemFileHandle')}} و {{domxref('FileSystemDirectoryHandle')}} به ترتیب برای فایل‌ها و دایرکتوری‌ها.

دسته‌ها یک فایل یا دایرکتوری را در سیستم کاربر نشان می‌دهند. ابتدا می‌توانید با نمایش یک انتخاب‌گر فایل یا دایرکتوری به کاربر، با استفاده از روش‌هایی مانند {{domxref('window.showOpenFilePicker()')}} و {{domxref('window.showDirectoryPicker()')}} به آن‌ها دسترسی پیدا کنید. پس از فراخوانی این روش‌ها، انتخاب‌گر فایل نمایش داده می‌شود و کاربر یک فایل یا دایرکتوری را انتخاب می‌کند. پس از انجام موفقیت‌آمیز این کار، یک دسته (handle) بازگردانده می‌شود.

همچنین می‌توانید از طریق موارد زیر به دسته‌های فایل دسترسی پیدا کنید:

- روش {{domxref('DataTransferItem.getAsFileSystemHandle()')}} از [HTML Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API).
- [File Handling API](https://developer.chrome.com/docs/capabilities/web-apis/file-handling).

هر دسته عملکرد خاص خود را ارائه می‌دهد و بسته به اینکه از کدام یک استفاده می‌کنید، تفاوت‌های کمی وجود دارد (برای جزئیات خاص به بخش [رابط‌ها](#interfaces) مراجعه کنید). سپس می‌توانید به داده‌های فایل یا اطلاعات (از جمله فرزندان) دایرکتوری انتخاب‌شده دسترسی پیدا کنید. این API قابلیت‌های بالقوه‌ای را که وب فاقد آن بود باز می‌کند. با این حال، امنیت در طراحی این API از اهمیت بالایی برخوردار بوده است و دسترسی به داده‌های فایل/دایرکتوری مجاز نیست مگر اینکه کاربر صریحاً اجازه دهد (توجه داشته باشید که این مورد در مورد [سیستم فایل خصوصی مبدأ](#origin_private_file_system) صدق نمی‌کند، زیرا برای کاربر قابل مشاهده نیست).

> [!NOTE]
> استثناهای مختلفی که هنگام استفاده از ویژگی‌های این API ممکن است رخ دهند، در صفحات مربوطه طبق مشخصات فهرست شده‌اند. با این حال، وضعیت به دلیل تعامل API و سیستم عامل زیرین پیچیده‌تر می‌شود. پیشنهادی برای [فهرست کردن نگاشت خطاها در مشخصات](https://github.com/whatwg/fs/issues/57) ارائه شده است که شامل اطلاعات مفید مرتبط است.

> [!NOTE]
> اشیاء مبتنی بر {{domxref("FileSystemHandle")}} می‌توانند در یک نمونه پایگاه داده {{domxref("IndexedDB API", "IndexedDB", "", "nocode")}} سریال‌سازی شوند یا از طریق {{domxref("window.postMessage", "postMessage()")}} منتقل شوند.

### سیستم فایل خصوصی مبدأ

سیستم فایل خصوصی مبدأ (OPFS) یک نقطه پایانی ذخیره‌سازی است که به عنوان بخشی از File System API ارائه می‌شود و برای مبدأ صفحه خصوصی است و مانند سیستم فایل معمولی برای کاربر قابل مشاهده نیست. این سیستم دسترسی به نوع خاصی از فایل را فراهم می‌کند که برای عملکرد بهینه‌سازی شده است و دسترسی نوشتن درجا به محتوای آن ارائه می‌دهد.

برخی از موارد استفاده احتمالی عبارتند از:

- برنامه‌های دارای آپلودکننده پایدار
  - وقتی فایل یا دایرکتوری برای آپلود انتخاب می‌شود، می‌توانید فایل را در یک محیط sandbox محلی کپی کرده و بخش به بخش آپلود کنید.
  - برنامه می‌تواند پس از وقفه، مانند بسته شدن یا خراب شدن مرورگر، قطع شدن اتصال یا خاموش شدن رایانه، آپلود را از سر بگیرد.

- بازی‌های ویدیویی یا سایر برنامه‌های دارای دارایی‌های رسانه‌ای زیاد
  - برنامه یک یا چند tarball بزرگ دانلود کرده و آن‌ها را به صورت محلی در یک ساختار دایرکتوری گسترش می‌دهد.
  - برنامه دارایی‌ها را در پس‌زمینه از پیش دریافت می‌کند، بنابراین کاربر می‌تواند بدون انتظار برای دانلود، به مرحله بعد یا سطح بازی برود.

- ویرایشگر صوتی یا عکس با دسترسی آفلاین یا حافظه پنهان محلی (بسیار عالی برای عملکرد و سرعت)
  - برنامه می‌تواند درجا در فایل‌ها بنویسد (مثلاً فقط تگ‌های ID3/EXIF را بازنویسی کند و نه کل فایل را).

- نمایش‌دهنده ویدیوی آفلاین
  - برنامه می‌تواند فایل‌های بزرگ (بیش از ۱ گیگابایت) را برای مشاهده بعدی دانلود کند.
  - برنامه می‌تواند به فایل‌های نیمه‌دانلودشده دسترسی داشته باشد (تا بتوانید فصل اول DVD خود را تماشا کنید، حتی اگر برنامه همچنان در حال دانلود بقیه محتوا باشد یا اگر دانلود به دلیل عجله شما برای رسیدن به قطار کامل نشده باشد).

- سرویس‌گیرنده ایمیل وب آفلاین
  - سرویس گیرنده پیوست‌ها را دانلود کرده و آن‌ها را به صورت محلی ذخیره می‌کند.
  - سرویس گیرنده پیوست‌ها را برای آپلود بعدی ذخیره می‌کند.

برای دستورالعمل‌های استفاده از آن، [سیستم فایل خصوصی مبدأ](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) ما را بخوانید.

### ذخیره فایل‌ها

- در مورد دسته‌های ناهمگام، از رابط {{domxref('FileSystemWritableFileStream')}} استفاده کنید. وقتی داده‌هایی که می‌خواهید ذخیره کنید در قالب {{domxref('Blob')}}، شیء {{jsxref("String")}}، رشته‌ی متنی یا {{jsxref('ArrayBuffer', 'buffer')}} قرار دارند، می‌توانید یک جریان باز کرده و داده‌ها را در یک فایل ذخیره کنید. این فایل می‌تواند فایل موجود یا یک فایل جدید باشد.
- در مورد {{domxref('FileSystemSyncAccessHandle')}} همگام، تغییرات را با استفاده از روش {{domxref('FileSystemSyncAccessHandle.write', 'write()')}} در یک فایل می‌نویسید. در صورت نیاز به ثبت تغییرات بر روی دیسک در زمان مشخص، می‌توانید به صورت اختیاری {{domxref('FileSystemSyncAccessHandle.flush', 'flush()')}} را نیز فراخوانی کنید (در غیر این صورت می‌توانید به سیستم عامل زیرین اجازه دهید تا در زمان مناسب خودش مدیریت کند، که در بیشتر موارد باید کافی باشد).

## رابط‌ها

- {{domxref("FileSystemChangeRecord")}} {{experimental_inline}}
  - : حاوی جزئیات یک تغییر مشاهده‌شده توسط {{domxref("FileSystemObserver")}} است.
- {{domxref("FileSystemHandle")}}
  - : شیءای که یک ورودی فایل یا دایرکتوری را نشان می‌دهد. چندین دسته می‌توانند همان ورودی را نشان دهند. در بیشتر موارد مستقیماً با `FileSystemHandle` کار نمی‌کنید، بلکه با رابط‌های فرزند آن یعنی {{domxref('FileSystemFileHandle')}} و {{domxref('FileSystemDirectoryHandle')}} کار می‌کنید.
- {{domxref("FileSystemFileHandle")}}
  - : یک دسته به یک ورودی سیستم فایل ارائه می‌دهد.
- {{domxref("FileSystemDirectoryHandle")}}
  - : یک دسته به یک دایرکتوری سیستم فایل ارائه می‌دهد.
- {{domxref("FileSystemObserver")}} {{experimental_inline}}
  - : مکانیزمی برای مشاهده تغییرات در فایل‌ها یا دایرکتوری‌های انتخاب‌شده فراهم می‌کند.
- {{domxref("FileSystemSyncAccessHandle")}}
  - : یک دسته همگام به یک ورودی سیستم فایل ارائه می‌دهد که به صورت درجا روی یک فایل واحد روی دیسک عمل می‌کند. ماهیت همگام خواندن و نوشتن فایل، عملکرد بالاتری را برای روش‌های حیاتی در زمینه‌هایی که عملیات ناهمگام سربار بالایی دارند، مانند [WebAssembly](/en-US/docs/WebAssembly)، فراهم می‌کند. این کلاس فقط در [Web Workers](/en-US/docs/Web/API/Web_Workers_API) اختصاصی برای فایل‌های داخل [سیستم فایل خصوصی مبدأ](#origin_private_file_system) قابل دسترسی است.
- {{domxref("FileSystemWritableFileStream")}}
  - : یک شیء {{domxref('WritableStream')}} با روش‌های راحتی اضافی که روی یک فایل واحد روی دیسک عمل می‌کند.

### افزونه‌های رابط‌های دیگر

- {{domxref("Window.showDirectoryPicker()")}}
  - : یک انتخاب‌گر دایرکتوری نمایش می‌دهد که به کاربر اجازه می‌دهد یک دایرکتوری را انتخاب کند.
- {{domxref("Window.showOpenFilePicker()")}}
  - : یک انتخاب‌گر فایل نشان می‌دهد که به کاربر اجازه می‌دهد یک یا چند فایل را انتخاب کند.
- {{domxref("Window.showSaveFilePicker()")}}
  - : یک انتخاب‌گر فایل نشان می‌دهد که به کاربر اجازه می‌دهد یک فایل را ذخیره کند.
- {{domxref("DataTransferItem.getAsFileSystemHandle()")}}
  - : یک {{jsxref('Promise')}} برمی‌گرداند که اگر مورد کشیده‌شده یک فایل باشد با یک {{domxref('FileSystemFileHandle')}} و اگر مورد کشیده‌شده یک دایرکتوری باشد با یک {{domxref('FileSystemDirectoryHandle')}} محقق می‌شود.
- {{domxref("StorageManager.getDirectory()")}}
  - : برای به دست آوردن ارجاع به یک شیء {{domxref("FileSystemDirectoryHandle")}} استفاده می‌شود که امکان دسترسی به یک دایرکتوری و محتویات آن را فراهم می‌کند و در [سیستم فایل خصوصی مبدأ](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) ذخیره شده است. یک {{jsxref('Promise')}} برمی‌گرداند که با یک شیء {{domxref("FileSystemDirectoryHandle")}} محقق می‌شود.

## مثال‌ها

### دسترسی به فایل‌ها

کد زیر به کاربر اجازه می‌دهد یک فایل را از انتخاب‌گر فایل انتخاب کند.

```js
async function getFile() {
  // Open file picker and destructure the result the first handle
  const [fileHandle] = await window.showOpenFilePicker();
  const file = await fileHandle.getFile();
  return file;
}
```

تابع ناهمگام زیر یک انتخاب‌گر فایل ارائه می‌دهد و پس از انتخاب فایل، از روش `getFile()` برای بازیابی محتوا استفاده می‌کند.

```js
const pickerOpts = {
  types: [
    {
      description: "Images",
      accept: {
        "image/*": [".png", ".gif", ".jpeg", ".jpg"],
      },
    },
  ],
  excludeAcceptAllOption: true,
  multiple: false,
};

async function getTheFile() {
  // Open file picker and destructure the result the first handle
  const [fileHandle] = await window.showOpenFilePicker(pickerOpts);

  // get file contents
  const fileData = await fileHandle.getFile();
}
```

### دسترسی به دایرکتوری‌ها

مثال زیر یک دسته دایرکتوری با نام مشخص‌شده برمی‌گرداند. اگر دایرکتوری وجود نداشته باشد، ایجاد می‌شود.

```js
const dirName = "directoryToGetName";

// assuming we have a directory handle: 'currentDirHandle'
const subDir = await currentDirHandle.getDirectoryHandle(dirName, {
  create: true,
});
```

تابع ناهمگام زیر از `resolve()` برای یافتن مسیر فایل انتخاب‌شده نسبت به یک دسته دایرکتوری مشخص استفاده می‌کند.

```js
async function returnPathDirectories(directoryHandle) {
  // Get a file handle by showing a file picker:
  const [handle] = await self.showOpenFilePicker();
  if (!handle) {
    // User cancelled, or otherwise failed to open a file.
    return;
  }

  // Check if handle exists inside our directory handle
  const relativePaths = await directoryHandle.resolve(handle);

  if (relativePaths === null) {
    // Not inside directory handle
  } else {
    // relativePaths is an array of names, giving the relative path

    for (const name of relativePaths) {
      // log each entry
      console.log(name);
    }
  }
}
```

### نوشتن در فایل‌ها

تابع ناهمگام زیر انتخاب‌گر ذخیره فایل را باز می‌کند که پس از انتخاب فایل، یک {{domxref('FileSystemFileHandle')}} برمی‌گرداند. سپس با استفاده از روش {{domxref('FileSystemFileHandle.createWritable()')}} یک جریان قابل نوشتن ایجاد می‌شود.

یک {{domxref('Blob')}} تعریف‌شده توسط کاربر سپس در جریان نوشته می‌شود که در ادامه بسته می‌شود.

```js
async function saveFile() {
  // create a new handle
  const newHandle = await window.showSaveFilePicker();

  // create a FileSystemWritableFileStream to write to
  const writableStream = await newHandle.createWritable();

  // write our file
  await writableStream.write(imgBlob);

  // close the file and write the contents to disk.
  await writableStream.close();
}
```

در زیر نمونه‌های مختلفی از گزینه‌هایی که می‌توان به روش `write()` منتقل کرد نشان داده شده است.

```js
// just pass in the data (no options)
writableStream.write(data);

// writes the data to the stream from the determined position
writableStream.write({ type: "write", position, data });

// updates the current file cursor offset to the position specified
writableStream.write({ type: "seek", position });

// resizes the file to be size bytes long
writableStream.write({ type: "truncate", size });
```

### خواندن و نوشتن همگام فایل‌ها در OPFS

این مثال به صورت همگام یک فایل را در [سیستم فایل خصوصی مبدأ](#origin_private_file_system) می‌خواند و می‌نویسد.

تابع مدیریت رویداد ناهمگام زیر در یک Web Worker قرار دارد. پس از دریافت پیام از رشته اصلی:

- یک دسته دسترسی همگام به فایل ایجاد می‌کند.
- اندازه فایل را به دست می‌آورد و یک {{jsxref("ArrayBuffer")}} برای نگهداری آن ایجاد می‌کند.
- محتوای فایل را در بافر می‌خواند.
- پیام را کدگذاری کرده و در انتهای فایل می‌نویسد.
- تغییرات را روی دیس