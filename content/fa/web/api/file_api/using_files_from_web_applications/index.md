---
title: "استفاده از فایل‌ها در برنامه‌های تحت وب"
slug: Web/API/File_API/Using_files_from_web_applications
page-type: guide
---

{{DefaultAPISidebar("File API")}}{{AvailableInWorkers}}

با استفاده از File API، محتوای وب می‌تواند از کاربر بخواهد فایل‌های محلی را انتخاب کند و سپس محتوای آن فایل‌ها را بخواند. این انتخاب می‌تواند با استفاده از یک عنصر HTML `{{HTMLElement("input/file", '&lt;input type="file"&gt;')}}` یا با کشیدن و رها کردن (drag and drop) انجام شود.

## دسترسی به فایل(های) انتخاب شده

این HTML را در نظر بگیرید:

```html
<input type="file" id="input" multiple />
```

File API امکان دسترسی به یک {{DOMxRef("FileList")}} شامل اشیاء {{DOMxRef("File")}} را فراهم می‌کند که نشان‌دهنده فایل‌های انتخاب شده توسط کاربر هستند.

ویژگی `multiple` در عنصر `input` به کاربر اجازه می‌دهد چندین فایل را انتخاب کند.

دسترسی به اولین فایل انتخاب شده با استفاده از یک انتخاب‌گر DOM کلاسیک:

```js
const selectedFile = document.getElementById("input").files[0];
```

### دسترسی به فایل(های) انتخاب شده در رویداد change

همچنین امکان دسترسی به {{DOMxRef("FileList")}} از طریق رویداد `change` وجود دارد (اما اجباری نیست). باید از {{DOMxRef("EventTarget.addEventListener()")}} برای افزودن شنونده رویداد `change` استفاده کنید، مانند این:

```js
const inputElement = document.getElementById("input");
inputElement.addEventListener("change", handleFiles);
function handleFiles() {
  const fileList = this.files; /* اکنون می‌توانید با لیست فایل‌ها کار کنید */
}
```

## دریافت اطلاعات درباره فایل(های) انتخاب شده

شی {{DOMxRef("FileList")}} که توسط DOM ارائه می‌شود، تمام فایل‌های انتخاب شده توسط کاربر را فهرست می‌کند که هر کدام به عنوان یک شی {{DOMxRef("File")}} مشخص شده‌اند. می‌توانید با بررسی مقدار ویژگی `length` لیست فایل، تعداد فایل‌های انتخاب شده توسط کاربر را تعیین کنید:

```js
const numFiles = fileList.length;
```

اشیاء {{DOMxRef("File")}} را می‌توان با دسترسی به لیست به عنوان یک آرایه بازیابی کرد.

سه ویژگی توسط شی {{DOMxRef("File")}} ارائه می‌شود که حاوی اطلاعات مفیدی درباره فایل هستند.

- `name`
  - : نام فایل به صورت یک رشته فقط خواندنی. این فقط نام فایل است و شامل اطلاعات مسیر نمی‌شود.
- `size`
  - : اندازه فایل بر حسب بایت به صورت یک عدد صحیح ۶۴ بیتی فقط خواندنی.
- `type`
  - : نوع MIME فایل به صورت یک رشته فقط خواندنی یا `""` اگر نوع قابل تعیین نباشد.

### مثال: نمایش اندازه فایل(ها)

مثال زیر یک استفاده احتمالی از ویژگی `size` را نشان می‌دهد:

```html
<form name="uploadForm">
  <div>
    <input id="uploadInput" type="file" multiple />
    <label for="fileNum">فایل‌های انتخاب شده:</label>
    <output id="fileNum">0</output>;
    <label for="fileSize">حجم کل:</label>
    <output id="fileSize">0</output>
  </div>
  <div><input type="submit" value="ارسال فایل" /></div>
</form>
```

```js
const uploadInput = document.getElementById("uploadInput");
uploadInput.addEventListener("change", () => {
  // محاسبه حجم کل
  let numberOfBytes = 0;
  for (const file of uploadInput.files) {
    numberOfBytes += file.size;
  }

  // تقریب به نزدیک‌ترین واحد پیشوندی
  const units = ["B", "KiB", "MiB", "GiB", "TiB", "PiB", "EiB", "ZiB", "YiB"];
  const exponent = Math.min(
    Math.floor(Math.log(numberOfBytes) / Math.log(1024)),
    units.length - 1,
  );
  const approx = numberOfBytes / 1024 ** exponent;
  const output =
    exponent === 0
      ? `${numberOfBytes} bytes`
      : `${approx.toFixed(3)} ${units[exponent]} (${numberOfBytes} bytes)`;

  document.getElementById("fileNum").textContent = uploadInput.files.length;
  document.getElementById("fileSize").textContent = output;
});
```

## استفاده از عناصر ورودی فایل مخفی با روش click()

می‌توانید عنصر زشت فایل {{HTMLElement("input")}} را مخفی کنید و رابط کاربری خود را برای باز کردن انتخاب‌گر فایل و نمایش فایل(های) انتخاب شده توسط کاربر ارائه دهید. این کار را می‌توانید با استایل دادن به عنصر ورودی با `display:none` و فراخوانی متد {{DOMxRef("HTMLElement.click","click()")}} روی عنصر {{HTMLElement("input")}} انجام دهید.

این HTML را در نظر بگیرید:

```html
<input type="file" id="fileElem" multiple accept="image/*" />
<button id="fileSelect" type="button">انتخاب چند فایل</button>
```

```css
#fileElem {
  display: none;
}
```

کدی که رویداد `click` را مدیریت می‌کند می‌تواند به این شکل باشد:

```js
const fileSelect = document.getElementById("fileSelect");
const fileElem = document.getElementById("fileElem");

fileSelect.addEventListener("click", (e) => {
  if (fileElem) {
    fileElem.click();
  }
});
```

می‌توانید {{HTMLElement("button")}} را هر طور که می‌خواهید استایل دهید.

## استفاده از عنصر label برای فعال کردن عنصر ورودی فایل مخفی

برای باز کردن انتخاب‌گر فایل بدون استفاده از جاوااسکریپت (متد click())، می‌توان از یک عنصر {{HTMLElement("label")}} استفاده کرد. توجه داشته باشید که در این حالت عنصر ورودی نباید با `display: none` (یا `visibility: hidden`) مخفی شود، در غیر این صورت برچسب برای صفحه‌کلید قابل دسترس نخواهد بود. در عوض از [تکنیک visually-hidden](https://www.a11yproject.com/posts/how-to-hide-content/) استفاده کنید.

این HTML را در نظر بگیرید:

```html
<input
  type="file"
  id="fileElem"
  multiple
  accept="image/*"
  class="visually-hidden" />
<label for="fileElem">انتخاب چند فایل</label>
```

و این CSS:

```css
.visually-hidden {
  clip: rect(0 0 0 0);
  clip-path: inset(50%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}

input.visually-hidden:is(:focus, :focus-within) + label {
  outline: thin dotted;
}
```

نیازی به اضافه کردن کد جاوااسکریپت برای فراخوانی `fileElem.click()` نیست. همچنین در این حالت می‌توانید عنصر label را هر طور که می‌خواهید استایل دهید. باید یک نشانه بصری برای وضعیت فوکوس فیلد ورودی مخفی روی برچسب آن ارائه دهید، خواه یک outline مانند بالا، یا background-color یا box-shadow. (در زمان نگارش، فایرفاکس این نشانه بصری را برای عناصر `<input type="file">` نشان نمی‌دهد.)

## انتخاب فایل‌ها با استفاده از کشیدن و رها کردن

همچنین می‌توانید به کاربر اجازه دهید فایل‌ها را به برنامه وب شما بکشد و رها کند.

اولین قدم ایجاد یک منطقه رها (drop zone) است. اینکه دقیقاً کدام بخش از محتوای شما رها شدن را بپذیرد ممکن است بسته به طراحی برنامه شما متفاوت باشد، اما آسان است که یک عنصر رویدادهای drop را دریافت کند:

```js
let dropbox;

dropbox = document.getElementById("dropbox");
dropbox.addEventListener("dragenter", dragenter);
dropbox.addEventListener("dragover", dragover);
dropbox.addEventListener("drop", drop);
```

در این مثال، عنصر با شناسه `dropbox` را به منطقه رها خود تبدیل می‌کنیم. این کار با اضافه کردن شنونده‌هایی برای رویدادهای {{domxref("HTMLElement/dragenter_event", "dragenter")}}، {{domxref("HTMLElement/dragover_event", "dragover")}} و {{domxref("HTMLElement/drop_event", "drop")}} انجام می‌شود.

در واقع نیازی به انجام کاری با رویدادهای `dragenter` و `dragover` در مورد ما نیست، بنابراین این توابع هر دو ساده هستند. آنها فقط انتشار رویداد را متوقف می‌کنند و از انجام عمل پیش‌فرض جلوگیری می‌کنند:

```js
function dragenter(e) {
  e.stopPropagation();
  e.preventDefault();
}

function dragover(e) {
  e.stopPropagation();
  e.preventDefault();
}
```

جادوی واقعی در تابع `drop()` اتفاق می‌افتد:

```js
function drop(e) {
  e.stopPropagation();
  e.preventDefault();

  const dt = e.dataTransfer;
  const files = dt.files;

  handleFiles(files);
}
```

در اینجا، فیلد `dataTransfer` را از رویداد دریافت می‌کنیم، لیست فایل‌ها را از آن استخراج می‌کنیم و سپس آن را به `handleFiles()` می‌دهیم. از این نقطه به بعد، مدیریت فایل‌ها چه کاربر از عنصر `input` استفاده کرده باشد و چه از کشیدن و رها کردن، یکسان است.

## مثال: نمایش تصاویر بندانگشتی از تصاویر انتخاب شده توسط کاربر

فرض کنید در حال توسعه سایت بزرگ بعدی اشتراک‌گذاری عکس هستید و می‌خواهید از HTML برای نمایش پیش‌نمایش‌های بندانگشتی تصاویر قبل از اینکه کاربر واقعاً آنها را آپلود کند استفاده کنید. می‌توانید عنصر ورودی یا منطقه رها خود را همانطور که قبلاً بحث شد ایجاد کنید و از آنها بخواهید تابعی مانند `handleFiles()` زیر را فراخوانی کنند.

```js
function handleFiles(files) {
  for (const file of files) {
    if (!file.type.startsWith("image/")) {
      continue;
    }

    const img = document.createElement("img");
    img.classList.add("obj");
    img.file = file;
    preview.appendChild(img); // فرض می‌کنیم "preview" همان div خروجی است که محتوا در آن نمایش داده می‌شود.

    const reader = new FileReader();
    reader.onload = (e) => {
      img.src = e.target.result;
    };
    reader.readAsDataURL(file);
  }
}
```

در اینجا حلقه ما که فایل‌های انتخاب شده توسط کاربر را مدیریت می‌کند، ویژگی `type` هر فایل را بررسی می‌کند تا ببیند آیا نوع MIME آن با `image/` شروع می‌شود یا خیر. برای هر فایلی که تصویر است، یک عنصر `img` جدید ایجاد می‌کنیم. از CSS می‌توان برای ایجاد هر گونه حاشیه یا سایه زیبا و مشخص کردن اندازه تصویر استفاده کرد، بنابراین نیازی به انجام این کار در اینجا نیست.

هر تصویر دارای کلاس CSS `obj` است که به آن اضافه می‌شود و پیدا کردن آن را در درخت DOM آسان می‌کند. همچنین یک ویژگی `file` به هر تصویر اضافه می‌کنیم که {{DOMxRef("File")}} مربوط به تصویر را مشخص می‌کند؛ این به ما امکان می‌دهد بعداً تصاویر را برای آپلود واقعی بازیابی کنیم. از {{DOMxRef("Node.appendChild()")}} برای اضافه کردن بندانگشتی جدید به منطقه پیش‌نمایش سند خود استفاده می‌کنیم.

سپس، {{DOMxRef("FileReader")}} را برای مدیریت بارگیری ناهمزمان تصویر و پیوست کردن آن به عنصر `img` ایجاد می‌کنیم. پس از ایجاد شی جدید `FileReader`، تابع `onload` آن را تنظیم می‌کنیم و سپس `readAsDataURL()` را برای شروع عملیات خواندن در پس‌زمینه فراخوانی می‌کنیم. هنگامی که کل محتوای فایل تصویر بارگیری شد، به یک URL از نوع `data:` تبدیل می‌شود که به回调 `onload` ارسال می‌شود. پیاده‌سازی ما از این روال، ویژگی `src` عنصر `img` را به تصویر بارگیری شده تنظیم می‌کند که باعث می‌شود تصویر در بندانگشتی روی صفحه کاربر ظاهر شود.

## استفاده از URLهای شیء

متدهای {{DOMxref("URL.createObjectURL_static", "URL.createObjectURL()")}} و {{DOMxref("URL.revokeObjectURL_static", "URL.revokeObjectURL()")}} در DOM به شما اجازه می‌دهند رشته‌های URL ساده‌ای ایجاد کنید که می‌توان از آنها برای ارجاع به هر داده‌ای که می‌توان با استفاده از یک شی {{DOMxRef("File")}} DOM به آن اشاره کرد، از جمله فایل‌های محلی روی رایانه کاربر، استفاده کرد.

هنگامی که یک شی {{DOMxRef("File")}} دارید که می‌خواهید با URL از HTML به آن ارجاع دهید، می‌توانید یک URL شیء برای آن به این شکل ایجاد کنید:

```js
const objectURL = window.URL.createObjectURL(fileObj);
```

URL شیء یک رشته است که شی {{DOMxRef("File")}} را شناسایی می‌کند. هر بار که {{DOMxref("URL.createObjectURL_static", "URL.createObjectURL()")}} را فراخوانی می‌کنید، یک URL شیء منحصر به فرد ایجاد می‌شود، حتی اگر قبلاً برای آن فایل یک URL شیء ایجاد کرده باشید. هر یک از اینها باید آزاد شوند. در حالی که آنها به طور خودکار هنگام تخلیه سند آزاد می‌شوند، اگر صفحه شما به صورت پویا از آنها استفاده می‌کند، باید به صراحت با فراخوانی {{DOMxref("URL.revokeObjectURL_static", "URL.revokeObjectURL()")}} آنها را آزاد کنید:

```js
URL.revokeObjectURL(objectURL);
```

## مثال: استفاده از URLهای شیء برای نمایش تصاویر

این مثال از URLهای شیء برای نمایش تصاویر بندانگشتی استفاده می‌کند. علاوه بر این، اطلاعات دیگر فایل از جمله نام و اندازه آنها را نمایش می‌دهد.

HTML که رابط را ارائه می‌دهد به این شکل است:

```html
<input type="file" id="fileElem" multiple accept="image/*" />
<a href="#" id="fileSelect">انتخاب چند فایل</a>
<div id="fileList">
  <p>هیچ فایلی انتخاب نشده است!</p>
</div>
```

```css
#fileElem {
  display: none;
}
```

این کار عنصر {{HTMLElement("input")}} فایل ما و همچنین یک پیوند که انتخاب‌گر فایل را فراخوانی می‌کند (زیرا ورودی فایل را مخفی نگه می‌داریم تا از نمایش آن رابط کاربری نازیبا جلوگیری کنیم) ایجاد می‌کند. این موضوع در بخش [استفاده از عناصر ورودی فایل مخفی با روش click()](#using_hidden_file_input_elements_using_the_click_method) توضیح داده شده است، و همچنین روشی که انتخاب‌گر فایل را فراخوانی می‌کند.

متد `handleFiles()` به شرح زیر است:

```js
const fileSelect = document.getElementById("fileSelect"),
  fileElem = document.getElementById("fileElem"),
  fileList = document.getElementById("fileList");

fileSelect.addEventListener("click", (e) => {
  if (fileElem) {
    fileElem.click();
  }
  e.preventDefault(); // جلوگیری از پیمایش به "#"
});

fileElem.addEventListener("change", handleFiles);

function handleFiles() {
  fileList.textContent = "";
  if (!this.files.length) {
    const p = document.createElement("p");
    p.textContent = "هیچ فایلی انتخاب نشده است!";
    fileList.appendChild(p);
  } else {
    const list = document.createElement("ul");
    fileList.appendChild(list);
    for (const file of this.files) {
      const li = document.createElement("li");
      list.appendChild(li);

      const img = document.createElement("img");
      img.src = URL.createObjectURL(file);
      img.height = 60;
      li.appendChild(img);
      const info = document.createElement("span");
      info.textContent = `${file.name}: ${file.size} bytes`;
      li.appendChild(info);
    }
  }
}
```

این کار با دریافت URL {{HTMLElement("div")}} با شناسه `fileList` شروع می‌شود. این بلوکی است که لیست فایل‌های خود را از جمله بندانگشتی‌ها در آن وارد می‌کنیم.

اگر شی {{DOMxRef("FileList")}} که به `handleFiles()` ارسال شده خالی باشد، HTML داخلی بلوک را طوری تنظیم می‌کنیم که "هیچ فایلی انتخاب نشده است!" را نمایش دهد. در غیر این صورت، شروع به ساختن لیست فایل خود می‌کنیم، به شرح زیر:

1. یک عنصر لیست نامرتب جدید ({{HTMLElement("ul")}}) ایجاد می‌شود.
2. عنصر لیست جدید با فراخوانی متد {{DOMxRef("Node.appendChild()")}} آن در بلوک {{HTMLElement("div")}} قرار می‌گیرد.
3. برای هر {{DOMxRef("File")}} در {{DOMxRef("FileList")}} که توسط `files` نشان داده می‌شود:
   1. یک عنصر آیتم لیست جدید ({{HTMLElement("li")}}) ایجاد کنید و آن را در لیست قرار دهید.
   2. یک عنصر تصویر جدید ({{HTMLElement("img")}}) ایجاد کنید.
   3. منبع تصویر را به یک URL شیء جدید که نشان‌دهنده فایل است، با استفاده از {{DOMxref("URL.createObjectURL_static", "URL.createObjectURL()")}} برای ایجاد URL blob تنظیم کنید.
   4. ارتفاع تصویر را به ۶۰ پیکسل تنظیم کنید.
   5. آیتم لیست جدید را به لیست اضافه کنید.

در اینجا یک نمایش زنده از کد بالا آمده است:

{{EmbedLiveSample('Example_Using_object_URLs_to_display_images', '100%', '300px')}}

توجه داشته باشید که بلافاصله پس از بارگیری تصویر، URL شیء را لغو نمی‌کنیم، زیرا این کار باعث می‌شود تصویر برای تعاملات کاربر (مانند کلیک راست برای ذخیره تصویر یا باز کردن آن در یک تب جدید) غیرقابل استفاده شود. برای برنامه‌های طولانی مدت، باید URLهای شیء را زمانی که دیگر مورد نیاز نیستند لغو کنید (مانند زمانی که تصویر از DOM حذف می‌شود) تا با فراخوانی متد {{DOMxref("URL.revokeObjectURL_static", "URL.revokeObjectURL()")}} و ارسال رشته URL شیء، حافظه آزاد شود.

## مثال: آپلود یک فایل انتخاب شده توسط کاربر

این مثال نشان می‌دهد که چگونه به کاربر اجازه دهیم فایل‌ها (مانند تصاویر انتخاب شده با استفاده از مثال قبلی) را به یک سرور آپلود کند.

> [!NOTE]
> معمولاً ترجیح داده می‌شود درخواست‌های HTTP با استفاده از [Fetch API](/en-US/docs/Web/API/Fetch_API) به جای {{domxref("XMLHttpRequest")}} انجام شود. با این حال، در این مورد می‌خواهیم پیشرفت آپلود را به کاربر نشان دهیم و این ویژگی هنوز توسط Fetch API پشتیبانی نمی‌شود، بنابراین مثال از `XMLHttpRequest` استفاده می‌کند.
>
> کار برای ردیابی استانداردسازی اعلان‌های پیشرفت با استفاده از Fetch API در <https://github.com/whatwg/fetch/issues/607> انجام می‌شود.

### ایجاد وظایف آپلود

با ادامه کدی که بندانگشتی‌ها را در مثال قبلی ساخت، به یاد بیاورید که هر تصویر بندانگشتی در کلاس CSS `obj` با {{DOMxRef("File")}} مربوطه که در یک ویژگی `file` ضمیمه شده است، قرار دارد. این به ما اجازه می‌دهد تمام تصاویری را که کاربر برای آپلود انتخاب کرده است با استفاده از {{DOMxRef("Document.querySelectorAll()")}} انتخاب کنیم، مانند این:

```js
function sendFiles() {
  const imgs = document.querySelectorAll(".obj");

  for (const img of imgs) {
    new FileUpload(img, img.file);
  }
}
```

`document.querySelectorAll` یک {{DOMxRef("NodeList")}} از تمام عناصر در سند با کلاس CSS `obj` را دریافت می‌کند. در مورد ما، اینها همه تصاویر بندانگشتی خواهند بود. هنگامی که آن لیست را داریم، به راحتی می‌توان از آن عبور کرد و برای هر کدام یک نمونه جدید `FileUpload` ایجاد کرد. هر یک از اینها آپلود فایل مربوطه را مدیریت می‌کند.

### مدیریت فرآیند آپلود برای یک فایل

تابع `FileUpload` دو ورودی دریافت می‌کند: یک عنصر تصویر و یک فایل که از آن داده‌های تصویر خوانده شود.

```js
function FileUpload(img, file) {
  const reader = new FileReader();
  this.ctrl = createThrobber(img);
  const xhr = new XMLHttpRequest();
  this.xhr = xhr;

  this.xhr.upload.addEventListener("progress", (e) => {
    if (e.lengthComputable) {
      const percentage = Math.round((e.loaded * 100) / e.total);
      this.ctrl.update(percentage);
    }
  });

  xhr.upload.addEventListener("load", (e) => {
    this.ctrl.update(100);
    const canvas = this.ctrl.ctx.canvas;
    canvas.parentNode.removeChild(canvas);
  });
  xhr.open(
    "POST",
    "https://demos.hacks.mozilla.org/paul/demos/resources/webservices/devnull.php",
  );
  xhr.overrideMimeType("text/plain; charset=x-user-defined-binary");
  reader.onload = (evt) => {
    xhr.send(evt.target.result);
  };
  reader.readAsBinaryString(file);
}

function createThrobber(img) {
  const throbberWidth = 64;
  const throbberHeight = 6;
  const throbber = document.createElement("canvas");
  throbber.classList.add("upload-progress");
  throbber.setAttribute("width", throbberWidth);
  throbber.setAttribute("height", throbberHeight);
  img.parentNode.appendChild(throbber);
  throbber.ctx = throbber.getContext("2d");
  throbber.ctx.fillStyle = "orange";
  throbber.update = (percent) => {
    throbber.ctx.fillRect(
      0,
      0,
      (throbberWidth * percent) / 100,
      throbberHeight,
    );
    if (percent === 100) {
      throbber.ctx.fillStyle = "green";
    }
  };
  throbber.update(0);
  return throbber;
}
```

تابع `FileUpload()` که در بالا نشان داده شده است یک throber (نشان‌دهنده پیشرفت) ایجاد می‌کند که برای نمایش اطلاعات پیشرفت استفاده می‌شود و سپس یک {{DOMxRef("XMLHttpRequest")}} برای مدیریت آپلود داده‌ها ایجاد می‌کند.

قبل از انتقال واقعی داده‌ها، چندین مرحله مقدماتی انجام می‌شود:

1. شنونده `progress` آپلود `XMLHttpRequest` تنظیم می‌شود تا throber را با اطلاعات درصد جدید به‌روز کند، به طوری که با پیشرفت آپلود، throber بر اساس آخرین اطلاعات به‌روز شود.
2. کنترل‌کننده رویداد `load` آپلود `XMLHttpRequest` تنظیم می‌شود تا اطلاعات پیشرفت throber را به ۱۰۰٪ به‌روز کند تا اطمینان حاصل شود که نشان‌دهنده پیشرفت واقعاً به ۱۰۰٪ می‌رسد (در صورت وجود مشکلات دانه‌بندی در طول فرآیند). سپس throber را حذف می‌کند زیرا دیگر نیازی نیست. این باعث می‌شود throber پس از اتمام آپلود ناپدید شود.
3. درخواست برای آپلود فایل تصویر با فراخوانی متد `open()` `XMLHttpRequest` برای شروع تولید یک درخواست POST باز می‌شود.
4. نوع MIME برای آپلود با فراخوانی تابع `overrideMimeType()` `XMLHttpRequest` تنظیم می‌شود. در این مورد، ما از یک نوع MIME عمومی استفاده می‌کنیم؛ بسته به مورد استفاده شما ممکن است اصلاً نیازی به تنظیم نوع MIME نداشته باشید.
5. از شی `FileReader` برای تبدیل فایل به یک رشته باینری استفاده می‌شود.
6. در نهایت، هنگامی که محتوا بارگیری شد، تابع `send()` `XMLHttpRequest` برای آپلود محتوای فایل فراخوانی می‌شود.

### مدیریت ناهمزمان فرآیند آپلود فایل

این مثال که از PHP در سمت سرور و جاوااسکریپت در سمت کلاینت استفاده می‌کند، آپلود ناهمزمان یک فایل را نشان می‌دهد.

```php
<?php
if (isset($_FILES["myFile"])) {
  // مثال:
  move_uploaded_file($_FILES["myFile"]["tmp_name"], "uploads/" . $_FILES["myFile"]["name"]);
  exit;
}
?><!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>dnd binary upload</title>
  </head>
  <body>
    <div>
      <div
        id="dropzone"
        style="margin:30px; width:500px; height:300px; border:1px dotted grey;">
        فایل خود را اینجا بکشید و رها کنید
      </div>
    </div>
    <script>
      function sendFile(file) {
        const uri = "/index.php";
        const xhr = new XMLHttpRequest();
        const fd = new FormData();

        xhr.open("POST", uri, true);
        xhr.onreadystatechange = () => {
          if (xhr.readyState === 4 && xhr.status === 200) {
            alert(xhr.responseText); // مدیریت پاسخ.
          }
        };
        fd.append("myFile", file);
        // شروع یک آپلود multipart/form-data
        xhr.send(fd);
      }

      const dropzone = document.getElementById("dropzone");
      dropzone.addEventListener("dragover", (event) => {
        event.stopPropagation();
        event.preventDefault();
      });

      dropzone.addEventListener("drop", (event) => {
        event.preventDefault();

        const filesArray = event.dataTransfer.files;
        for (let i = 0; i < filesArray.length; i++) {
          sendFile(filesArray[i]);
        }
      });
    </script>
  </body>
</html>
```

## مثال: استفاده از URLهای شیء برای نمایش PDF

URLهای شیء را می‌توان برای چیزهای دیگری غیر از تصاویر نیز استفاده کرد! آنها را می‌توان برای نمایش فایل‌های PDF جاسازی شده یا هر منبع دیگری که توسط مرورگر قابل نمایش است استفاده کرد.

در فایرفاکس، برای اینکه PDF به صورت جاسازی شده در iframe ظاهر شود (به جای اینکه به عنوان یک فایل دانلودی پیشنهاد شود)، باید تنظیمات `pdfjs.disabled` روی `false` تنظیم شود.

```html
<iframe id="viewer"></iframe>
```

و در اینجا تغییر ویژگی `src` آمده است:

```js
const objURL = URL.createObjectURL(blob);
const iframe = document.getElementById("viewer");
iframe.setAttribute("src", objURL);

// بعداً:
URL.revokeObjectURL(objURL);
```

## مثال: استفاده از URLهای شیء با انواع دیگر فایل‌ها

می‌توانید فایل‌های با فرمت‌های دیگر را به همان روش دستکاری کنید. در اینجا نحوه پیش‌نمایش ویدیوی آپلود شده آمده است:

```js
const video = document.getElementById("video");
const objURL = URL.createObjectURL(blob);
video.src = objURL;
video.play();

// بعداً:
URL.revokeObjectURL(objURL);
```

## همچنین ببینید

- {{DOMxRef("File")}}
- {{DOMxRef("FileList")}}
- {{DOMxRef("FileReader")}}
- {{DOMxRef("URL")}}
- {{DOMxRef("XMLHttpRequest")}}
- [استفاده از XMLHttpRequest](/en-US/docs/Web/API/XMLHttpRequest_API/Using_XMLHttpRequest)