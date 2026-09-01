---
title: "FileSystemFileHandle: createWritable() method"
short-title: createWritable()
slug: Web/API/FileSystemFileHandle/createWritable
page-type: web-api-instance-method
browser-compat: api.FileSystemFileHandle.createWritable
---

{{securecontext_header}}{{APIRef("File System API")}}{{AvailableInWorkers}}

متد **`createWritable()`** از رابط {{domxref("FileSystemFileHandle")}} یک {{domxref('FileSystemWritableFileStream')}} ایجاد می‌کند که می‌توان از آن برای نوشتن در یک فایل استفاده کرد. این متد یک {{jsxref('Promise')}} برمی‌گرداند که به این استریم ایجاد شده حل می‌شود.

هر تغییری که از طریق استریم اعمال شود تا زمانی که استریم بسته نشده است در فایل نمایش‌داده‌شده توسط دسته‌فایل منعکس نخواهد شد. این معمولاً با نوشتن داده‌ها در یک فایل موقت پیاده‌سازی می‌شود و تنها زمانی که استریم فایل قابل‌نوشتن بسته می‌شود، فایل نمایش‌داده‌شده توسط دسته‌فایل با فایل موقت جایگزین می‌گردد.

## نحو

```js-nolint
createWritable()
createWritable(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شی با ویژگی‌های زیر:
    - `keepExistingData` {{optional_inline}}
      - : یک {{jsxref('Boolean')}} است. پیش‌فرض `false`. اگر روی `true` تنظیم شود و فایل وجود داشته باشد، فایل موجود ابتدا به فایل موقت کپی می‌شود. در غیر این صورت فایل موقت خالی شروع می‌شود.
    - `mode` {{optional_inline}} {{non-standard_inline}}
      - : یک رشته که حالت قفل‌گذاری را برای استریم فایل قابل‌نوشتن مشخص می‌کند. مقدار پیش‌فرض `"siloed"` است. مقادیر ممکن:
        - `"exclusive"`
          - : فقط یک نویسنده `FileSystemWritableFileStream` می‌تواند باز شود. تلاش برای باز کردن نویسندگان بعدی قبل از بسته شدن اولین نویسنده باعث ایجاد استثنای `NoModificationAllowedError` می‌شود.
        - `"siloed"`
          - : چندین نویسنده `FileSystemWritableFileStream` می‌توانند همزمان باز شوند، هر کدام با فایل مبادله‌ای خود، مثلاً هنگام استفاده از همان برنامه در چند زبانه. آخرین نویسنده باز شده داده‌های خود را می‌نویسد، زیرا داده‌ها هنگام بسته شدن هر نویسنده تخلیه می‌شوند.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که به یک شی {{domxref('FileSystemWritableFileStream')}} حل می‌شود.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref('PermissionStatus.state')}} برای دسته‌فایل در حالت `readwrite` برابر `'granted'` نباشد، پرتاب می‌شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر ورودی جاری یافت نشود، پرتاب می‌شود.
- `NoModificationAllowedError` {{domxref("DOMException")}}
  - : اگر مرورگر نتواند روی فایل مرتبط با دسته‌فایل قفل بگیرد، پرتاب می‌شود. این می‌تواند به دلیل تنظیم `mode` روی `exclusive` و تلاش برای باز کردن همزمان چند نویسنده باشد.
- `AbortError` {{domxref("DOMException")}}
  - : اگر اسکن‌های بدافزار و بررسی‌های امنیتی تعریف‌شده توسط پیاده‌سازی ناموفق باشد، پرتاب می‌شود.

## مثال‌ها

### استفاده پایه

تابع ناهمگام زیر محتوای داده شده را در دسته‌فایل می‌نویسد و در نتیجه روی دیسک ذخیره می‌کند.

```js
async function writeFile(fileHandle, contents) {
  // Create a FileSystemWritableFileStream to write to.
  const writable = await fileHandle.createWritable();

  // Write the contents of the file to the stream.
  await writable.write(contents);

  // Close the file and write the contents to disk.
  await writable.close();
}
```

### استفاده گسترده با گزینه‌ها

مثال [آزمون حالت `createWritable()`](https://mdn.github.io/dom-examples/file-system-api/createwritable-mode/) (کد منبع را [اینجا](https://github.com/mdn/dom-examples/tree/main/file-system-api/createwritable-mode) ببینید) یک {{htmlelement("button")}} برای انتخاب فایل برای نوشتن، یک فیلد متنی {{htmlelement("input")}} برای وارد کردن متن برای نوشتن در فایل، و یک دکمه `<button>` دوم برای نوشتن متن در فایل ارائه می‌دهد.

در دموی بالا، سعی کنید یک فایل متنی از سیستم فایل خود انتخاب کنید (یا یک نام فایل جدید وارد کنید)، متنی را در فیلد ورودی وارد کنید و متن را در فایل بنویسید. فایل را در سیستم فایل خود باز کنید تا بررسی کنید نوشتن موفقیت‌آمیز بوده است.

همچنین، سعی کنید صفحه را در دو زبانه مرورگر به طور همزمان باز کنید. در زبانه اول یک فایل برای نوشتن انتخاب کنید و سپس بلافاصله سعی کنید همان فایل را در زبانه دوم انتخاب کنید. باید یک پیام خطا دریافت کنید زیرا در فراخوانی `createWritable()` از `mode: "exclusive"` استفاده کرده‌ایم.

در ادامه کد را بررسی می‌کنیم.

#### HTML

دو عنصر {{htmlelement("button")}} و فیلد متنی {{htmlelement("input")}} به این شکل هستند:

```html
<ol>
  <li>
    Select a file to write to: <button class="select">Select file</button>
  </li>
  <li>
    <label for="file-text">Enter text to write to the file:</label>
    <input type="text" id="file-text" name="file-text" disabled />
  </li>
  <li>
    Write your text to the file:
    <button class="write" disabled>Write text</button>
  </li>
</ol>
```

فیلد ورودی متن و دکمه نوشتن متن ابتدا با ویژگی [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled) غیرفعال شده‌اند — تا زمانی که کاربر فایلی را برای نوشتن انتخاب نکرده باشد نباید قابل استفاده باشند.

```css hidden
li {
  margin-bottom: 10px;
}
```

#### JavaScript

ابتدا ارجاع‌هایی به دکمه انتخاب فایل، دکمه نوشتن متن و فیلد ورودی متن می‌گیریم. همچنین یک متغیر سراسری `writableStream` اعلام می‌کنیم که پس از ایجاد، ارجاعی به استریم قابل‌نوشتن برای نوشتن متن در فایل ذخیره می‌کند. در ابتدا آن را روی `null` تنظیم می‌کنیم.

```js
const selectBtn = document.querySelector(".select");
const writeBtn = document.querySelector(".write");
const fileText = document.querySelector("#file-text");

let writableStream = null;
```

سپس یک تابع ناهمگام به نام `selectFile()` ایجاد می‌کنیم که وقتی دکمه انتخاب فشرده می‌شود فراخوانی می‌شود. این تابع از متد {{domxref("Window.showSaveFilePicker()")}} برای نمایش یک دیالوگ انتخاب فایل به کاربر و ایجاد یک دسته‌فایل برای فایل انتخابی استفاده می‌کند. روی آن دسته، متد `createWritable()` را فراخوانی می‌کنیم تا یک استریم برای نوشتن متن در فایل انتخاب شده ایجاد کند. اگر فراخوانی ناموفق باشد، خطا را در کنسول ثبت می‌کنیم.

یک شی گزینه شامل گزینه‌های زیر به `createWritable()` ارسال می‌کنیم:

- `keepExistingData: true`: اگر فایل انتخاب شده از قبل وجود داشته باشد، داده‌های موجود در آن قبل از شروع نوشتن به فایل موقت کپی می‌شوند.
- `mode: "exclusive"`: بیان می‌کند که فقط یک نویسنده می‌تواند همزمان روی دسته‌فایل باز باشد. اگر کاربر دوم مثال را بارگذاری کند و سعی کند فایلی را انتخاب کند، خطا دریافت می‌کند.

در نهایت، فیلد ورودی و دکمه نوشتن متن را فعال می‌کنیم (چون برای مرحله بعد نیاز هستند) و دکمه انتخاب فایل را غیرفعال می‌کنیم (در حال حاضر به آن نیاز نیست).

```js
async function selectFile() {
  // Create a new handle
  const handle = await window.showSaveFilePicker();

  // Create a FileSystemWritableFileStream to write to
  try {
    writableStream = await handle.createWritable({
      keepExistingData: true,
      mode: "exclusive",
    });
  } catch (e) {
    if (e.name === "NoModificationAllowedError") {
      console.log(
        `You can't access that file right now; someone else is trying to modify it. Try again later.`,
      );
    } else {
      console.log(e.message);
    }
  }

  // Enable text field and write button, disable select button
  fileText.disabled = false;
  writeBtn.disabled = false;
  selectBtn.disabled = true;
}
```

تابع بعدی ما، `writeFile()`، متن وارد شده در فیلد ورودی را با استفاده از {{domxref("FileSystemWritableFileStream.write()")}} در فایل انتخاب شده می‌نویسد، سپس فیلد ورودی را خالی می‌کند. سپس استریم قابل‌نوشتن را با استفاده از {{domxref("WritableStream.close()")}} می‌بندیم و دمو را به حالت اولیه بازنشانی می‌کنیم تا بتوان دوباره اجرا کرد — وضعیت `disabled` کنترل‌ها به حالت اولیه برمی‌گردد و متغیر `writableStream` دوباره روی `null` تنظیم می‌شود.

```js
async function writeFile() {
  // Write text to our file and empty out the text field
  await writableStream.write(fileText.value);
  fileText.value = "";

  // Close the file and write the contents to disk.
  await writableStream.close();

  // Disable text field and write button, enable select button
  fileText.disabled = true;
  writeBtn.disabled = true;
  selectBtn.disabled = false;

  // Set writableStream back to null
  writableStream = null;
}
```

برای اجرای دمو، شنوندگان رویداد را روی دکمه‌ها تنظیم می‌کنیم تا هنگام کلیک روی هر کدام، تابع مربوطه اجرا شود.

```js
selectBtn.addEventListener("click", selectFile);
writeBtn.addEventListener("click", writeFile);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [File System API](/en-US/docs/Web/API/File_System_API)
- [The File System Access API: simplifying access to local files](https://developer.chrome.com/docs/capabilities/web-apis/file-system-access)