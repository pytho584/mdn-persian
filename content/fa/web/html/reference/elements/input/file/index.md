---
title: "<input type=\"file\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/file"
translated_by: "n8n + AI"
---

عنصر `<input>` با **`type="file"`** به کاربر اجازه می‌دهد یک یا چند فایل را از حافظه دستگاهش انتخاب کند. پس از انتخاب، فایل‌ها را می‌توان با [ارسال فرم](/en-US/docs/Learn_web_development/Extensions/Forms) به سرور آپلود کرد، یا با کد جاوااسکریپت و [File API](/en-US/docs/Web/API/File_API/Using_files_from_web_applications) دستکاری کرد.

```html interactive-example
<label for="avatar">Choose a profile picture:</label>

<input type="file" id="avatar" name="avatar" accept="image/png, image/jpeg" />
```

```css interactive-example
label {
  display: block;
  font:
    1rem "Fira Sans",
    sans-serif;
}

input,
label {
  margin: 0.4rem 0;
}
```

## مقدار

ویژگی (attribute) [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) در ورودی فایل، رشته‌ای است که مسیر فایل‌های انتخاب‌شده را نمایش می‌دهد. اگر هنوز فایلی انتخاب نشده باشد، مقدار آن رشتهٔ خالی (`""`) است. وقتی کاربر چند فایل را انتخاب کرده باشد، `value` اولین فایل از فهرست فایل‌های انتخابی را نشان می‌دهد. فایل‌های دیگر را می‌توان با استفاده از [ویژگی `HTMLInputElement.files` ورودی](/en-US/docs/Web/API/File_API/Using_files_from_web_applications#getting_information_about_selected_files) شناسایی کرد.

> **نکته:**
> مقدار [همیشه نام فایل با پیشوند `C:\fakepath\`](https://html.spec.whatwg.org/multipage/input.html#fakepath-srsly) است و مسیر واقعی فایل نیست. این کار برای جلوگیری از حدس زدن ساختار فایل کاربر توسط نرم‌افزارهای مخرب انجام می‌شود.

## ویژگی‌های اضافی

علاوه بر ویژگی‌های مشترکی که همهٔ عناصر `<input>` دارند، ورودی‌های نوع `file` از ویژگی‌های زیر نیز پشتیبانی می‌کنند.

### ویژگی `accept`

مقدار ویژگی [`accept`](/en-US/docs/Web/HTML/Reference/Attributes/accept) رشته‌ای است که نوع فایل‌هایی را مشخص می‌کند که ورودی فایل باید بپذیرد. این رشته فهرستی است از **[شناسه‌های منحصربه‌فرد نوع فایل](#unique_file_type_specifiers)** که با کاما از هم جدا شده‌اند. از آنجا که ممکن است یک نوع فایل به چند روش شناسایی شود، بهتر است وقتی به فایل‌هایی با فرمت مشخص نیاز دارید، مجموعهٔ کاملی از این شناسه‌ها را ارائه دهید.

مثلاً فایل‌های Microsoft Word را می‌توان به چند روش شناسایی کرد؛ بنابراین سایتی که فایل‌های Word می‌پذیرد ممکن است از `<input>` ای شبیه به این استفاده کند:

```html
<input
  type="file"
  id="docpicker"
  accept=".doc,.docx,.xml,application/msword,application/vnd.openxmlformats-officedocument.wordprocessingml.document" />
```

### ویژگی `capture`

مقدار ویژگی [`capture`](/en-US/docs/Web/HTML/Reference/Attributes/capture) رشته‌ای است که مشخص می‌کند برای ضبط دادهٔ تصویری یا ویدیویی از کدام دوربین استفاده شود، در صورتی که ویژگی [`accept`](/en-US/docs/Web/HTML/Reference/Attributes/accept) نشان دهد ورودی باید از یکی از این نوع‌ها باشد. مقدار `user` یعنی دوربین و/یا میکروفون روبه‌رو (سمت کاربر) باید استفاده شود. مقدار `environment` یعنی دوربین و/یا میکروفون پشتی (رو به بیرون) باید استفاده شود. اگر این ویژگی وجود نداشته باشد، عامل کاربر (user agent) مختار است خودش تصمیم بگیرد. اگر حالت دوربین درخواست‌شده در دسترس نباشد، عامل کاربر می‌تواند به حالت پیش‌فرض ترجیحی خود بازگردد.

> **نکته:**
> `capture` قبلاً یک ویژگی Boolean بود که در صورت وجود، درخواست می‌کرد به‌جای ورودی فایل، از دستگاه‌های ضبط رسانه‌ای مانند دوربین یا میکروفون استفاده شود.

### ویژگی `multiple`

وقتی ویژگی Boolean [`multiple`](/en-US/docs/Web/HTML/Reference/Attributes/multiple) مشخص شده باشد، ورودی فایل به کاربر اجازه می‌دهد بیش از یک فایل را انتخاب کند.

## ویژگی‌های غیراستاندارد

علاوه بر attributeهای فهرست‌شده در بالا، attributeهای غیراستاندارد زیر نیز در برخی browserها در دسترس هستند. بهتر است تا حد امکان از استفاده از آن‌ها خودداری کنید، زیرا این کار توانایی کد شما را برای کار در browserهایی که این attributeها را پیاده‌سازی نکرده‌اند محدود می‌کند.

### `webkitdirectory`

attribute بولین `webkitdirectory` در صورت وجود، نشان می‌دهد که در رابط انتخاب فایل، فقط پوشه‌ها باید برای انتخاب توسط کاربر در دسترس باشند. برای جزئیات و مثال‌های بیشتر به `HTMLInputElement.webkitdirectory` مراجعه کنید.

## مشخص‌کننده‌های یکتای نوع فایل

یک «مشخص‌کنندهٔ یکتای نوع فایل» (unique file type specifier) رشته‌ای است که نوع فایلی را توصیف می‌کند که کاربر می‌تواند در یک element از نوع `<input type="file">` انتخاب کند. هر مشخص‌کنندهٔ یکتای نوع فایل می‌تواند یکی از اشکال زیر را داشته باشد:

- یک پسوند نام فایل معتبر که به بزرگی/کوچکی حروف حساس نیست و با نقطه (".") شروع می‌شود. به عنوان مثال: `.jpg`، `.pdf` یا `.doc`.
- یک رشته MIME type معتبر، بدون پسوند.
- رشته `audio/*` به معنای «هر فایل صوتی».
- رشته `video/*` به معنای «هر فایل ویدیویی».
- رشته `image/*` به معنای «هر فایل تصویری».

attribute `accept` یک رشته شامل یک یا چند مورد از این مشخص‌کننده‌های نوع فایل یکتا را به عنوان مقدار خود می‌پذیرد که با کاما از هم جدا شده‌اند. به عنوان مثال، یک انتخاب‌گر فایل که به محتوایی نیاز دارد که بتواند به عنوان تصویر نمایش داده شود، از جمله هر دو فرمت استاندارد تصویر و فایل‌های PDF، ممکن است به این شکل باشد:

```html
<input type="file" accept="image/*,.pdf" />
```

## استفاده از ورودی‌های فایل

### یک مثال ساده

```html
<form method="post" enctype="multipart/form-data">
  <div>
    <label for="file">Choose file to upload</label>
    <input type="file" id="file" name="file" multiple />
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

```css hidden
div {
  margin-bottom: 10px;
}
```

خروجی به این صورت است:

> [!NOTE]
> این مثال را می‌توانید در GitHub هم ببینید — [کد منبع](https://github.com/mdn/learning-area/blob/main/html/forms/file-examples/simple-file.html) و همچنین [مشاهده اجرای زنده](https://mdn.github.io/learning-area/html/forms/file-examples/simple-file.html).

صرف‌نظر از دستگاه یا سیستم‌عامل کاربر، ورودی فایل (file input) دکمه‌ای را فراهم می‌کند که یک کادر محاوره‌ای انتخاب فایل را باز می‌کند و به کاربر اجازه می‌دهد فایلی را انتخاب کند.

قرار دادن attribute [`multiple`](#multiple)، همان‌طور که در بالا نشان داده شده است، مشخص می‌کند که چندین فایل می‌توانند همزمان انتخاب شوند. کاربر می‌تواند در انتخاب‌گر فایل، به هر شکلی که پلتفرم موردنظرش اجازه می‌دهد (مثلاً با نگه داشتن <kbd>Shift</kbd> یا <kbd>Control</kbd> و سپس کلیک کردن)، چند فایل را انتخاب کند. اگر فقط می‌خواهید کاربر در هر `<input>` یک فایل انتخاب کند، attribute `multiple` را حذف کنید.

### دریافت اطلاعات درباره فایل‌های انتخاب‌شده

فایل‌های انتخاب‌شده توسط property `HTMLInputElement.files` مربوط به همان element برگردانده می‌شوند؛ این property یک شیء `FileList` حاوی فهرستی از اشیاء `File` است. `FileList` مانند یک آرایه رفتار می‌کند، بنابراین می‌توانید property `length` آن را بررسی کنید تا تعداد فایل‌های انتخاب‌شده را به دست آورید.

هر شیء `File` اطلاعات زیر را شامل می‌شود:

- `name`
  - : نام فایل.
- `lastModified`
  - : عددی که تاریخ و زمان آخرین تغییر فایل را مشخص می‌کند، به میلی‌ثانیه از مبدأ UNIX (نیمه‌شب ۱ ژانویه ۱۹۷۰).
- `lastModifiedDate` (منسوخ شده)
  - : یک شیء `Date` که تاریخ و زمان آخرین تغییر فایل را نشان می‌دهد. _این property منسوخ شده و نباید استفاده شود. به جای آن از `lastModified` استفاده کنید._
- `size`
  - : اندازه فایل بر حسب بایت.
- `type`
  - : [MIME type](/en-US/docs/Web/HTTP/Guides/MIME_types) فایل.
- `webkitRelativePath` (غیراستاندارد)
  - : رشته‌ای که مسیر فایل را نسبت به دایرکتوری پایه انتخاب‌شده در یک انتخاب‌گر دایرکتوری (یعنی یک انتخاب‌گر فایل که در آن attribute [`webkitdirectory`](#webkitdirectory) تنظیم شده است) مشخص می‌کند. _این property غیراستاندارد است و باید با احتیاط استفاده شود._

### محدود کردن انواع فایل‌های مجاز

معمولاً نمی‌خواهید کاربر بتواند هر نوع فایلی را انتخاب کند؛ بلکه می‌خواهید او فقط فایل‌هایی با نوع یا انواع خاصی انتخاب کند. مثلاً اگر ورودی فایل برای آپلود عکس پروفایل است، احتمالاً می‌خواهید کاربر فقط فرمت‌های تصویری سازگار با وب مثل JPEG یا PNG را انتخاب کند.

انواع فایل‌های مجاز را می‌توان با ویژگی [`accept`](#accept) مشخص کرد. این ویژگی یک لیست جدا شده با کاما از پسوندهای مجاز یا MIME type‌ها می‌گیرد. چند مثال:

- `accept="image/png"` یا `accept=".png"` — فقط فایل‌های PNG مجاز هستند.
- `accept="image/png, image/jpeg"` یا `accept=".png, .jpg, .jpeg"` — فایل‌های PNG یا JPEG مجاز هستند.
- `accept="image/*"` — هر فایلی با MIME type از نوع `image/*` مجاز است. (در بسیاری از دستگاه‌های موبایل، با این مقدار کاربر می‌تواند مستقیماً با دوربین عکس بگیرد.)
- `accept=".doc,.docx,.xml,application/msword,application/vnd.openxmlformats-officedocument.wordprocessingml.document"` — هر چیزی که شبیه سند MS Word باشد مجاز است.

بیایید یک مثال کامل‌تر ببینیم:

```html
<form method="post" enctype="multipart/form-data">
  <div>
    <label for="profile_pic">انتخاب فایل برای آپلود</label>
    <input
      type="file"
      id="profile_pic"
      name="profile_pic"
      accept=".jpg, .jpeg, .png" />
  </div>
  <div>
    <button>ارسال</button>
  </div>
</form>
```

```css hidden
div {
  margin-bottom: 10px;
}
```

خروجی این کد شبیه مثال قبلی است (بدون نمایش تعاملی).

> [!NOTE]
> می‌توانید این مثال را در GitHub هم ببینید — [کد منبع](https://github.com/mdn/learning-area/blob/main/html/forms/file-examples/file-with-accept.html) و [نمایش زنده](https://mdn.github.io/learning-area/html/forms/file-examples/file-with-accept.html).

اگرچه ظاهر آن مشابه است، اما وقتی فایلی را انتخاب کنید، می‌بینید که انتخاب‌گر فایل فقط به شما اجازه می‌دهد انواعی را انتخاب کنید که در `accept` مشخص شده‌اند (رابط دقیق آن در مرورگرها و سیستم‌عامل‌های مختلف متفاوت است).

ویژگی `accept` نوع فایل‌های انتخاب شده را اعتبارسنجی نمی‌کند؛ فقط به مرورگر راهنمایی می‌دهد تا کاربر را به سمت انتخاب نوع صحیح هدایت کند. در بیشتر موارد، کاربر می‌تواند با تغییر یک گزینه در انتخاب‌گر فایل، این محدودیت را دور بزند و هر فایلی را انتخاب کند – حتی نوع نادرست.

به همین دلیل، باید مطمئن شوید که ویژگی `accept` با اعتبارسنجی مناسب در سمت سرور پشتیبانی می‌شود.

### تشخیص لغو شدن

وقتی کاربر انتخاب خود را تغییر ندهد و دوباره همان فایل‌های قبلی را انتخاب کند، رویداد `cancel` فعال می‌شود. همچنین وقتی پنجره انتخاب فایل با دکمه «لغو» یا کلید <kbd>Escape</kbd> بسته یا لغو شود، رویداد `cancel` فعال می‌شود.

مثال: کد زیر در کنسول پیامی چاپ می‌کند اگر کاربر پاپ‌آپ را بدون انتخاب فایل ببندد:

```js
const elem = document.createElement("input");
elem.type = "file";
elem.addEventListener("cancel", () => {
  console.log("لغو شد.");
});
elem.addEventListener("change", () => {
  if (elem.files.length === 1) {
    console.log("فایل انتخاب شد: ", elem.files[0]);
  }
});
elem.click();
```

### نکات

1. نمی‌توانید مقدار یک انتخاب‌گر فایل را از طریق اسکریپت تنظیم کنید. کاری مثل کد زیر اثری ندارد:

   ```js
   const input = document.querySelector("input[type=file]");
   input.value = "foo";
   ```

2. وقتی یک فایل با `<input type="file">` انتخاب می‌شود، مسیر واقعی فایل به دلایل امنیتی واضح در ویژگی `value` نمایش داده نمی‌شود. در عوض، فقط نام فایل نشان داده می‌شود و `C:\fakepath\` به ابتدای آن اضافه می‌شود. این رفتار دلایل تاریخی دارد، اما در همه مرورگرهای مدرن پشتیبانی می‌شود و در واقع [در مشخصات استاندارد تعریف شده است](https://html.spec.whatwg.org/multipage/forms.html#fakepath-srsly).

در این مثال، یک انتخابگر فایل کمی پیشرفته‌تر را نشان می‌دهیم که از اطلاعات فایل موجود در خاصیت `HTMLInputElement.files` استفاده می‌کند و چند ترفند هوشمندانه را هم به نمایش می‌گذارد.

> [!NOTE]
> می‌توانید کد منبع کامل این مثال را در GitHub ببینید — [file-example.html](https://github.com/mdn/learning-area/blob/main/html/forms/file-examples/file-example.html) ([نسخهٔ زنده](https://mdn.github.io/learning-area/html/forms/file-examples/file-example.html)). CSS را توضیح نمی‌دهیم؛ تمرکز اصلی روی JavaScript است.

اول از همه، بیایید نگاهی به HTML بیندازیم:

```html
<form method="post" enctype="multipart/form-data">
  <div>
    <label for="image_uploads">Choose images to upload (PNG, JPG)</label>
    <input
      type="file"
      id="image_uploads"
      name="image_uploads"
      accept=".jpg, .jpeg, .png"
      multiple />
  </div>
  <div class="preview">
    <p>No files currently selected for upload</p>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

```css hidden
html {
  font-family: sans-serif;
}

form {
  background: #cccccc;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid black;
}

form ol {
  padding-left: 0;
}

form li,
div > p {
  background: #eeeeee;
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  list-style-type: none;
  border: 1px solid black;
}

form img {
  height: 64px;
  order: 1;
}

form p {
  line-height: 32px;
  padding-left: 10px;
}

form label,
form button {
  background-color: #7f9ccb;
  padding: 5px 10px;
  border-radius: 5px;
  border: 1px ridge black;
  font-size: 0.8rem;
  height: auto;
}

form label:hover,
form button:hover {
  background-color: #2d5ba3;
  color: white;
}

form label:active,
form button:active {
  background-color: #0d3f8f;
  color: white;
}
```

این شبیه به چیزهایی است که قبلاً دیده‌ایم — نکتهٔ خاصی برای توضیح ندارد.

در ادامه، قدم‌به‌قدم JavaScript را بررسی می‌کنیم.

در خطوط ابتدایی اسکریپت، به خود input فرم و عنصر `<div>` با کلاس `.preview` ارجاع می‌دهیم. سپس عنصر `<input>` را مخفی می‌کنیم — این کار را انجام می‌دهیم چون inputهای فایل معمولاً ظاهر زشتی دارند، استایل‌دهی به آنها سخت است و طراحی آنها در مرورگرهای مختلف یکسان نیست. با کلیک روی `<label>` مربوطه می‌توانید عنصر `input` را فعال کنید، بنابراین بهتر است `input` را به‌صورت بصری مخفی کنیم و `label` را مثل یک دکمه استایل دهیم تا کاربر بداند برای آپلود فایل باید با آن تعامل کند.

```js
const input = document.querySelector("input");
const preview = document.querySelector(".preview");

input.style.opacity = 0;
```

> [!NOTE]
> برای مخفی کردن input فایل از `opacity` استفاده می‌شود به جای `visibility: hidden` یا `display: none`، چون فناوری‌های کمکی دو حالت آخر را به این معنا تفسیر می‌کنند که input فایل تعاملی نیست.

در مرحله بعد، یک [event listener](/en-US/docs/Web/API/EventTarget/addEventListener) به input اضافه می‌کنیم تا تغییرات مقدار انتخاب‌شده را بشنود (در این مورد، وقتی فایل‌ها انتخاب می‌شوند). این event listener تابع سفارشی `updateImageDisplay()` را فراخوانی می‌کند.

هر زمان که تابع `updateImageDisplay()` فراخوانی شود، ما:

- از یک حلقهٔ `while` استفاده کن تا محتوای قبلی داخل `<div>` پیشنمایش را خالی کنی.
- آبجکت `FileList` را که اطلاعات همهٔ فایل‌های انتخاب‌شده را دارد بگیر و آن را در متغیری به نام `curFiles` ذخیره کن.
- بررسی کن که آیا هیچ فایلی انتخاب نشده است؛ یعنی `curFiles.length` برابر با 0 باشد. اگر چنین بود، در `<div>` پیشنمایش پیامی چاپ کن که می‌گوید هیچ فایلی انتخاب نشده است.
- اگر فایلی _انتخاب شده باشد_، روی تک‌به‌تک آن‌ها حلقه می‌زنیم و اطلاعات هرکدام را داخل `<div>` پیشنمایش چاپ می‌کنیم. چند نکته در اینجا وجود دارد:
- از تابع سفارشی `validFileType()` استفاده می‌کنیم تا بررسی کنیم فایل از نوع درست است یا نه (مثلاً انواع تصویری که در attribute `accept` مشخص شده‌اند).
- اگر درست بود:
  - نام و اندازهٔ فایل را در یک آیتم فهرست داخل همان `<div>` قبلی چاپ می‌کنیم (این مقادیر از `file.name` و `file.size` به دست می‌آیند). تابع سفارشی `returnFileSize()` نسخهٔ خوش‌فرمت‌شده‌ای از اندازه را بر حسب bytes/KB/MB برمی‌گرداند (به‌طور پیش‌فرض مرورگر اندازه را بر حسب بایت مطلق گزارش می‌کند).
  - پیش‌نمایش بندانگشتی تصویر را با فراخوانی `URL.createObjectURL(file)` می‌سازیم. سپس با ساخت یک `<img>` جدید و تنظیم [`src`](/en-US/docs/Web/HTML/Reference/Elements/img#src) آن روی همان تصویر، تصویر را هم به آیتم فهرست اضافه می‌کنیم.
- اگر نوع فایل نامعتبر باشد، در یک آیتم فهرست پیامی نمایش می‌دهیم که به کاربر می‌گوید باید نوع فایل دیگری انتخاب کند.

```js
function updateImageDisplay() {
  while (preview.firstChild) {
    preview.removeChild(preview.firstChild);
  }

  const curFiles = input.files;
  if (curFiles.length === 0) {
    const para = document.createElement("p");
    para.textContent = "No files currently selected for upload";
    preview.appendChild(para);
  } else {
    const list = document.createElement("ol");
    preview.appendChild(list);

    for (const file of curFiles) {
      const listItem = document.createElement("li");
      const para = document.createElement("p");
      if (validFileType(file)) {
        para.textContent = `File name ${file.name}, file size ${returnFileSize(
          file.size,
        )}.`;
        const image = document.createElement("img");
        image.src = URL.createObjectURL(file);
        image.alt = image.title = file.name;

        listItem.appendChild(image);
        listItem.appendChild(para);
      } else {
        para.textContent = `File name ${file.name}: Not a valid file type. Update your selection.`;
        listItem.appendChild(para);
      }

      list.appendChild(listItem);
    }
  }
}
```

تابع سفارشی `validFileType()` یک آبجکت `File` را به‌عنوان پارامتر می‌گیرد، سپس با استفاده از `Array.prototype.includes()` بررسی می‌کند که آیا مقداری در `fileTypes` با property نوع فایل (یعنی `file.type`) مطابقت دارد. اگر مطابقت پیدا شود، تابع `true` را برمی‌گرداند. اگر مطابقتی نباشد، `false` برمی‌گرداند.

```js
// https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Formats/Image_types
const fileTypes = [
  "image/apng",
  "image/bmp",
  "image/gif",
  "image/jpeg",
  "image/pjpeg",
  "image/png",
  "image/svg+xml",
  "image/tiff",
  "image/webp",
  "image/x-icon",
];

function validFileType(file) {
  return fileTypes.includes(file.type);
}
```

تابع `returnFileSize()` یک عدد (تعداد بایت‌ها، که از property اندازهٔ فایل جاری یعنی `size` گرفته می‌شود) دریافت می‌کند و آن را به اندازه‌ای خوش‌فرمت بر حسب bytes/KB/MB تبدیل می‌کند.

```js
function returnFileSize(number) {
  if (number < 1e3) {
    return `${number} bytes`;
  } else if (number >= 1e3 && number < 1e6) {
    return `${(number / 1e3).toFixed(1)} KB`;
  }
  return `${(number / 1e6).toFixed(1)} MB`;
}
```

> [!NOTE]
> واحدهای "KB" و "MB" در اینجا از قرارداد پیشوند SI (SI prefix) استفاده می‌کنند که 1KB = 1000B است، مشابه macOS. سیستم‌های مختلف اندازه فایل را متفاوت نمایش می‌دهند - مثلاً اوبونتو از پیشوندهای IEC استفاده می‌کند که در آن 1KiB = 1024B است، در حالی که مشخصات RAM معمولاً از پیشوند SI برای نمایش توان‌های دو (1KB = 1024B) استفاده می‌کنند. به همین دلیل، ما به جای `1024` و `1048576` از `1e3` (1000) و `1e6` (100000) استفاده کردیم. در برنامهٔ خودتان، اگر اندازهٔ دقیق مهم است، باید سیستم واحد را به وضوح به کاربران توضیح دهید.

```js hidden
const button = document.querySelector("form button");
button.addEventListener("click", (e) => {
  e.preventDefault();
  const para = document.createElement("p");
  para.append("Image uploaded!");
  preview.replaceChildren(para);
});
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">مقدار (Value)</a></strong></td>
      <td>
        رشته‌ای که مسیر فایل انتخاب‌شده را نشان می‌دهد.
      </td>
    </tr>
    <tr>
      <td><strong>رویدادها (Events)</strong></td>
      <td>
        <code>change</code>، <code>input</code> و <code>cancel</code>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های معمول پشتیبانی‌شده (Supported common attributes)</strong></td>
      <td><a href="/en-US/docs/Web/HTML/Reference/Elements/input#required"><code>required</code></a></td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های اضافی (Additional Attributes)</strong></td>
      <td>
        <a href="#accept"><code>accept</code></a>،
        <a href="#capture"><code>capture</code></a>،
        <a href="#multiple"><code>multiple</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های IDL</strong></td>
      <td><code>files</code> و <code>value</code></td>
    </tr>
    <tr>
      <td><strong>رابط DOM</strong></td>
      <td>{{domxref("HTMLInputElement")}}</td>
    </tr>
    <tr>
      <td><strong>نقش ARIA ضمنی (Implicit ARIA Role)</strong></td>
      <td><a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a></td>
    </tr>
  </tbody>
</table>

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگرها (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- [استفاده از فایل‌ها در برنامه‌های وب](/en-US/docs/Web/API/File_API/Using_files_from_web_applications) — شامل مثال‌های مفید دیگری دربارهٔ `<input type="file">` و [File API](/en-US/docs/Web/API/File) است.