---
title: "accept HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/accept"
translated_by: "n8n + AI"
---

ویژگی **`accept`** مقداری به صورت فهرستی جدا شده با کاما از یک یا چند نوع فایل یا [شناسه‌های یکتای نوع فایل](#unique_file_type_specifiers) می‌گیرد که تعیین می‌کند کدام نوع فایل‌ها مجاز هستند.

```html interactive-example
<label for="movie">Choose a movie to upload:</label>

<input type="file" id="movie" name="movie" accept="video/*" />

<label for="poster">Choose a poster:</label>

<input type="file" id="poster" name="poster" accept="image/png, image/jpeg" />
```

```css interactive-example
label {
  display: block;
  margin-top: 1rem;
}

input {
  margin-bottom: 1rem;
}
```

## بررسی اجمالی

ویژگی `accept` یک attribute از عنصر `<input>` با نوع `file` است. قبلاً روی عنصر `<form>` پشتیبانی می‌شد، اما به نفع `<input>` با نوع `file` حذف شد.

چون ممکن است یک نوع فایل به چند روش شناسایی شود، بهتر است وقتی به فایل‌هایی از نوع خاصی نیاز دارید، مجموعه‌ای کامل از نوع‌ها را مشخص کنید، یا از wild card استفاده کنید تا نشان دهید هر فرمتی از آن نوع پذیرفته است.

برای مثال، فایل‌های Microsoft Word را می‌توان به چند روش شناسایی کرد؛ بنابراین سایتی که فایل Word می‌پذیرد ممکن است از `<input>` زیر استفاده کند:

```html
<input
  type="file"
  id="docpicker"
  accept=".doc,.docx,application/msword,application/vnd.openxmlformats-officedocument.wordprocessingml.document" />
```

در حالی که اگر می‌خواهید یک فایل رسانه‌ای بپذیرید، ممکن است بخواهید هر فرمتی از آن نوع رسانه را شامل شوید:

```html
<input type="file" id="soundFile" accept="audio/*" />
<input type="file" id="videoFile" accept="video/*" />
<input type="file" id="imageFile" accept="image/*" />
```

ویژگی `accept` نوع فایل‌های انتخاب‌شده را اعتبارسنجی نمی‌کند؛ این ویژگی فقط به مرورگرها راهنمایی (hint) می‌دهد تا کاربران را به سمت انتخاب فایل‌های درست هدایت کند. همچنان در بیشتر موارد کاربران می‌توانند گزینه‌ای را در انتخابگر فایل فعال کنند که این محدودیت را نادیده بگیرد و هر فایلی را انتخاب کنند، حتی نوع نادرست.

به همین دلیل باید مطمئن شوید که الزامات مورد انتظار در سمت سرور اعتبارسنجی می‌شوند.

## مثال‌ها

وقتی `accept` روی یک ورودی نوع `file` تنظیم شود، انتخابگر فایل بومی که باز می‌شود باید فقط انتخاب فایل‌هایی با نوع صحیح را فعال کند. بیشتر سیستم‌عامل‌ها فایل‌هایی را که با معیارها مطابقت ندارند کمرنگ و غیرقابل انتخاب می‌کنند.

```html
<p>
  <label for="soundFile">Select an audio file:</label>
  <input type="file" id="soundFile" accept="audio/*" />
</p>
<p>
  <label for="videoFile">Select a video file:</label>
  <input type="file" id="videoFile" accept="video/*" />
</p>
<p>
  <label for="imageFile">Select some images:</label>
  <input type="file" id="imageFile" accept="image/*" multiple />
</p>
```

توجه کنید که مثال آخر به شما امکان انتخاب چند تصویر را می‌دهد. برای اطلاعات بیشتر به ویژگی [`multiple`](/en-US/docs/Web/HTML/Reference/Elements/input#multiple) مراجعه کنید.

## شناسه‌های یکتای نوع فایل {#unique_file_type_specifiers}

یک **شناسه یکتای نوع فایل** (unique file type specifier) رشته‌ای است که نوع فایلی را توضیح می‌دهد که کاربر می‌تواند در عنصر `<input>` از نوع `file` انتخاب کند. هر شناسه یکتای نوع فایل می‌تواند یکی از شکل‌های زیر باشد:

- یک پسوند نام فایل معتبر که به بزرگی یا کوچکی حروف حساس نیست و با نقطه (".") شروع می‌شود؛ برای مثال `.jpg`, `.pdf`, یا `.doc`.
- یک رشته MIME type معتبر، بدون پسوند.
- رشته `audio/*` به معنای «هر فایل صوتی».
- رشته `video/*` به معنای «هر فایل ویدیویی».
- رشته `image/*` به معنای «هر فایل تصویری».

attribute «accept» به عنوان مقدار خود یک string می‌گیرد که شامل یک یا چند مشخصهٔ نوع فایل (file type specifier) است؛ این مشخصه‌ها با کاما از هم جدا می‌شوند. برای مثال، یک file picker که به محتوایی نیاز دارد که بتواند به صورت تصویر نمایش داده شود — از جمله فرمت‌های استاندارد تصویر و فایل‌های PDF — می‌تواند به شکل زیر باشد:

```html
<input type="file" accept="image/*,.pdf" />
```

## استفاده از input های فایل

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

خروجی کد بالا به شکل زیر است:

> [!NOTE]
> این مثال را می‌توانید در GitHub هم ببینید — [source code](https://github.com/mdn/learning-area/blob/main/html/forms/file-examples/simple-file.html) و همچنین [see it running live](https://mdn.github.io/learning-area/html/forms/file-examples/simple-file.html).

صرف‌نظر از دستگاه یا سیستم‌عامل کاربر، input فایل یک دکمه در اختیار می‌گذارد که دیالوگ انتخاب فایل (file picker dialog) را باز می‌کند و به کاربر اجازه می‌دهد فایلش را انتخاب کند.

همان‌طور که در بالا دیده می‌شود، اضافه کردن attribute ای به نام [`multiple`](/en-US/docs/Web/HTML/Reference/Elements/input#multiple) مشخص می‌کند که چند فایل بتوانند هم‌زمان انتخاب شوند. کاربر می‌تواند به هر شکلی که پلتفرمش اجازه می‌دهد، چند فایل را از file picker انتخاب کند (مثلاً با نگه‌داشتن <kbd>Shift</kbd> یا <kbd>Control</kbd> و سپس کلیک کردن). اگر می‌خواهید کاربر فقط یک فایل را در هر `<input>` انتخاب کند، attribute ی `multiple` را حذف کنید.

### محدود کردن انواع فایل‌های مجاز

اغلب نمی‌خواهید کاربر بتواند هر نوع فایل دلخواهی را انتخاب کند؛ بلکه می‌خواهید فایل‌هایی با یک یا چند نوع خاص انتخاب شوند. مثلاً اگر input فایل شما به کاربران اجازه می‌دهد تصویر پروفایل آپلود کنند، احتمالاً می‌خواهید فرمت‌های تصویری سازگار با وب مثل JPEG یا PNG را انتخاب کنند.

انواع فایل‌های مجاز را می‌توان با attribute ای به نام [`accept`](/en-US/docs/Web/HTML/Reference/Elements/input/file#accept) مشخص کرد. این attribute یک فهرست جداشده با کاما از پسوندهای فایل مجاز یا MIME type های مجاز می‌گیرد. چند مثال:

- `accept="image/png"` یا `accept=".png"` — فایل‌های PNG را می‌پذیرد.
- `accept="image/png, image/jpeg"` یا `accept=".png, .jpg, .jpeg"` — فایل‌های PNG یا JPEG را می‌پذیرد.
- `accept="image/*"` — هر فایلی با MIME type ای به شکل `image/*` را می‌پذیرد. (بسیاری از دستگاه‌های موبایل در این حالت به کاربر اجازه می‌دهند با دوربین عکس بگیرند.)
- `accept=".doc,.docx,.xml,application/msword,application/vnd.openxmlformats-officedocument.wordprocessingml.document"` — هر چیزی که شبیه سند Word باشد را می‌پذیرد.

بیایید یک مثال کامل‌تر را ببینیم:

```html
<form method="post" enctype="multipart/form-data">
  <div>
    <label for="profile_pic">Choose file to upload</label>
    <input
      type="file"
      id="profile_pic"
      name="profile_pic"
      accept=".jpg, .jpeg, .png" />
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

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- [Using files from web applications](/en-US/docs/Web/API/File_API/Using_files_from_web_applications)
- [File API](/en-US/docs/Web/API/File)