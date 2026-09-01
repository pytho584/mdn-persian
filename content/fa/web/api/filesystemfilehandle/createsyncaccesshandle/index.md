---
title: "FileSystemFileHandle: createSyncAccessHandle() method"
short-title: createSyncAccessHandle()
slug: Web/API/FileSystemFileHandle/createSyncAccessHandle
page-type: web-api-instance-method
browser-compat: api.FileSystemFileHandle.createSyncAccessHandle
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers("dedicated")}}

متد **`createSyncAccessHandle()`** در رابط {{domxref("FileSystemFileHandle")}} یک {{jsxref('Promise')}} برمی‌گرداند که به یک شیء {{domxref('FileSystemSyncAccessHandle')}} حل می‌شود و می‌توان از آن برای خواندن و نوشتن همزمان (synchronous) در یک فایل استفاده کرد. ماهیت همزمان این متد مزیت‌های عملکردی به همراه دارد، اما فقط در [Web Workers](/en-US/docs/Web/API/Web_Workers_API) اختصاصی (dedicated) و برای فایل‌های داخل [سیستم فایل خصوصی مبدأ](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) قابل استفاده است.

ایجاد یک {{domxref('FileSystemSyncAccessHandle')}} یک قفل انحصاری روی فایل مرتبط با هندل فایل اعمال می‌کند. این کار از ایجاد {{domxref('FileSystemSyncAccessHandle')}}های بیشتر یا {{domxref('FileSystemWritableFileStream')}}های جدید برای آن فایل تا زمانی که هندل دسترسی موجود بسته نشود، جلوگیری می‌کند.

## نحو (Syntax)

```js-nolint
createSyncAccessHandle()
createSyncAccessHandle(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء با ویژگی‌های زیر:
    - `mode` {{optional_inline}} {{non-standard_inline}}
      - : رشته‌ای که حالت قفل را برای هندل دسترسی مشخص می‌کند. مقدار پیش‌فرض `"readwrite"` است.
        مقادیر ممکن عبارتند از:
        - `"read-only"`
          - : چندین شیء `FileSystemSyncAccessHandle` می‌توانند به طور همزمان روی یک فایل باز شوند (مثلاً هنگام استفاده از یک برنامه در چند تب)، به شرطی که همه آن‌ها در حالت `"read-only"` باز شده باشند. پس از باز شدن، می‌توان متدهای شبیه به خواندن را روی هندل‌ها فراخوانی کرد — {{domxref("FileSystemSyncAccessHandle.read", "read()")}}، {{domxref("FileSystemSyncAccessHandle.getSize", "getSize()")}} و {{domxref("FileSystemSyncAccessHandle.close", "close()")}}.
        - `"readwrite"`
          - : فقط یک شیء `FileSystemSyncAccessHandle` می‌تواند روی یک فایل باز شود. تلاش برای باز کردن هندل‌های بعدی قبل از بسته شدن هندل اول، منجر به پرتاب استثنای `NoModificationAllowedError` می‌شود. پس از باز شدن، می‌توان هر متد موجود را روی هندل فراخوانی کرد.
        - `"readwrite-unsafe"`
          - : چندین شیء `FileSystemSyncAccessHandle` می‌توانند به طور همزمان روی یک فایل باز شوند، به شرطی که همه آن‌ها در حالت `"readwrite-unsafe"` باز شده باشند. پس از باز شدن، می‌توان هر متد موجود را روی هندل‌ها فراخوانی کرد.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که به یک شیء {{domxref('FileSystemSyncAccessHandle')}} حل می‌شود.

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برای هندل در حالت `readwrite` برابر با `granted` نباشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر شیء {{domxref('FileSystemSyncAccessHandle')}} نمایانگر یک فایل در [سیستم فایل خصوصی مبدأ](/en-US/docs/Web/API/File_System_API/Origin_private_file_system) نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی فعلی یافت نشود، پرتاب می‌شود.
- `NoModificationAllowedError` {{domxref("DOMException")}}
  - : اگر مرورگر نتواند قفلی روی فایل مرتبط با هندل فایل به دست آورد، پرتاب می‌شود. این می‌تواند به این دلیل باشد که `mode` روی `readwrite` تنظیم شده و تلاش برای باز کردن همزمان چند هندل انجام می‌شود.

## مثال‌ها

### استفاده پایه

تابع رویداد ناهمگام زیر درون یک Web Worker قرار دارد. قطعه کد داخل آن یک هندل دسترسی همزمان به فایل ایجاد می‌کند.

```js
onmessage = async (e) => {
  // Retrieve message sent to work from main script
  const message = e.data;

  // Get handle to draft file
  const root = await navigator.storage.getDirectory();
  const draftHandle = await root.getFileHandle("draft.txt", { create: true });
  // Get sync access handle
  const accessHandle = await draftHandle.createSyncAccessHandle();

  // …

  // Always close FileSystemSyncAccessHandle if done.
  accessHandle.close();
};
```

### مثال کامل با گزینه `mode`

مثال [آزمون `createSyncAccessHandle()` با حالت mode](https://mdn.github.io/dom-examples/file-system-api/createsyncaccesshandle-mode/) (مشاهده [کد منبع](https://github.com/mdn/dom-examples/tree/main/file-system-api/createsyncaccesshandle-mode)) یک فیلد {{htmlelement("input")}} برای وارد کردن متن و دو دکمه فراهم می‌کند — یکی برای نوشتن متن وارد شده در انتهای یک فایل در سیستم فایل خصوصی مبدأ، و یکی برای خالی کردن فایل وقتی بیش از حد پر می‌شود.

نمایان بالا را با کنسول توسعه‌دهنده مرورگر باز امتحان کنید تا ببینید چه اتفاقی می‌افتد. اگر بخواهید دمو را در چند تب مرورگر باز کنید، خواهید دید که می‌توان چند هندل را به طور همزمان برای نوشتن در فایل باز کرد. این به این دلیل است که `mode: "readwrite-unsafe"` روی فراخوانی‌های `createSyncAccessHandle()` تنظیم شده است.

در ادامه کد را بررسی می‌کنیم.

#### HTML

دو عنصر {{htmlelement("button")}} و فیلد متنی {{htmlelement("input")}} به این شکل هستند:

```html
<ol>
  <li>
    <label for="file-text">Enter text to write to the file:</label>
    <input type="text" id="file-text" name="file-text" />
  </li>
  <li>
    Write your text to the file: <button class="write">Write text</button>
  </li>
  <li>
    Empty the file if it gets too full:
    <button class="empty">Empty file</button>
  </li>
</ol>
```

#### جاوااسکریپت اصلی

جاوااسکریپت ترد اصلی داخل فایل HTML در زیر نشان داده شده است. ما ارجاع‌هایی به دکمه نوشتن متن، دکمه خالی کردن فایل و فیلد ورودی متن می‌گیریم، سپس یک web worker جدید با استفاده از سازنده {{domxref("Worker.Worker", "Worker()")}} ایجاد می‌کنیم. سپس دو تابع تعریف کرده و آن‌ها را به عنوان مدیریت‌کننده رویداد روی دکمه‌ها تنظیم می‌کنیم:

- `writeToOPFS()` وقتی کلیک می‌شود که دکمه نوشتن متن کلیک شود. این تابع مقدار وارد شده در فیلد متنی را درون یک شیء با استفاده از متد {{domxref("Worker.postMessage()")}} به worker ارسال می‌کند و سپس فیلد متنی را خالی می‌کند تا برای افزودن بعدی آماده باشد. توجه کنید که شیء ارسال‌شده همچنین شامل یک ویژگی `command: "write"` است تا مشخص شود با این پیام می‌خواهیم عملیات نوشتن انجام دهیم.
- `emptyOPFS()` وقتی اجرا می‌شود که دکمه خالی کردن فایل کلیک شود. این تابع یک شیء حاوی ویژگی `command: "empty"` به worker ارسال می‌کند و مشخص می‌کند که فایل باید خالی شود.

```js
const writeBtn = document.querySelector(".write");
const emptyBtn = document.querySelector(".empty");
const fileText = document.querySelector("#file-text");

const opfsWorker = new Worker("worker.js");

function writeToOPFS() {
  opfsWorker.postMessage({
    command: "write",
    content: fileText.value,
  });
  console.log("Main script: Text posted to worker");
  fileText.value = "";
}

function emptyOPFS() {
  opfsWorker.postMessage({
    command: "empty",
  });
}

writeBtn.addEventListener("click", writeToOPFS);
emptyBtn.addEventListener("click", emptyOPFS);
```

#### جاوااسکریپت worker

جاوااسکریپت worker در زیر نشان داده شده است.

ابتدا تابعی به نام `initOPFS()` را اجرا می‌کنیم که با استفاده از {{domxref("StorageManager.getDirectory()")}} یک ارجاع به ریشه OPFS می‌گیرد، با استفاده از {{domxref("FileSystemDirectoryHandle.getFileHandle()")}} یک فایل ایجاد کرده و هندل آن را برمی‌گرداند، و سپس با استفاده از `createSyncAccessHandle()` یک {{domxref("FileSystemSyncAccessHandle")}} برمی‌گرداند. این فراخوانی شامل ویژگی `mode: "readwrite-unsafe"` است که به چند هندل اجازه می‌دهد به طور همزمان به همان فایل دسترسی داشته باشند.

```js
let accessHandle;

async function initOPFS() {
  const opfsRoot = await navigator.storage.getDirectory();
  const fileHandle = await opfsRoot.getFileHandle("file.txt", { create: true });
  accessHandle = await fileHandle.createSyncAccessHandle({
    mode: "readwrite-unsafe",
  });
}

initOPFS();
```

در داخل تابع مدیریت‌کننده [رویداد پیام](/en-US/docs/Web/API/Worker/message_event) worker، ابتدا اندازه فایل را با استفاده از {{domxref("FileSystemSyncAccessHandle.getSize", "getSize()")}} می‌گیریم. سپس بررسی می‌کنیم که آیا داده ارسال‌شده در پیام شامل یک ویژگی `command` با مقدار `"empty"` است یا خیر. اگر چنین باشد، فایل را با استفاده از {{domxref("FileSystemSyncAccessHandle.truncate", "truncate()")}} با مقدار `0` خالی می‌کنیم و اندازه فایل ذخیره‌شده در متغیر `size` را به‌روزرسانی می‌کنیم.

اگر داده پیام چیز دیگری باشد،:

- یک {{domxref("TextEncoder")}} و {{domxref("TextDecoder")}} جدید ایجاد می‌کنیم تا بعداً رمزگذاری و رمزگشایی محتوای متنی را مدیریت کنند.
- داده پیام را رمزگذاری کرده و نتیجه را با استفاده از {{domxref("FileSystemSyncAccessHandle.write", "write()")}} در انتهای فایل می‌نویسیم، سپس اندازه فایل ذخیره‌شده در متغیر `size` را به‌روزرسانی می‌کنیم.
- یک {{jsxref("DataView")}} برای نگهداری محتویات فایل ایجاد می‌کنیم و محتوا را با استفاده از {{domxref("FileSystemSyncAccessHandle.read", "read()")}} در آن می‌خوانیم.
- محتویات `DataView` را رمزگشایی کرده و در کنسول ثبت می‌کنیم.

```js
onmessage = function (e) {
  console.log("Worker: Message received from main script");

  // Get the current size of the file
  let size = accessHandle.getSize();

  if (e.data.command === "empty") {
    // Truncate the file to 0 bytes
    accessHandle.truncate(0);

    // Get the current size of the file
    size = accessHandle.getSize();
  } else {
    const textEncoder = new TextEncoder();
    const textDecoder = new TextDecoder();

    // Encode content to write to the file
    const content = textEncoder.encode(e.data.content);
    // Write the content at the end of the file
    accessHandle.write(content, { at: size });

    // Get the current size of the file
    size = accessHandle.getSize();

    // Prepare a data view of the length of the file
    const dataView = new DataView(new ArrayBuffer(size));

    // Read the entire file into the data view
    accessHandle.read(dataView, { at: 0 });

    // Log the current file contents to the console
    console.log(`File contents: ${textDecoder.decode(dataView)}`);

    // Flush the changes
    accessHandle.flush();
  }

  // Log the size of the file to the console
  console.log(`Size: ${size}`);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)