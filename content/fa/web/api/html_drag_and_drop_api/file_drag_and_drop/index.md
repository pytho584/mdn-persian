```
---
title: "File drag and drop"
---

---
title: File drag and drop
slug: Web/API/HTML_Drag_and_Drop_API/File_drag_and_drop
page-type: guide
---

{{DefaultAPISidebar("HTML Drag and Drop API")}}

همانطور که در [صفحهٔ اصلی](/en-US/docs/Web/API/HTML_Drag_and_Drop_API#concepts_and_usage) اشاره شد، Drag and Drop API به‌طور هم‌زمان سه مورد استفاده را مدل‌سازی می‌کند: کشیدن عناصر داخل یک صفحه، کشیدن داده‌ها به بیرون از صفحه، و کشیدن داده‌ها به داخل صفحه. این آموزش مورد سوم را نشان می‌دهد: کشیدن داده‌ها به داخل صفحه. ما یک ناحیهٔ رهاسازی پایه پیاده‌سازی خواهیم کرد که به کاربر اجازه می‌دهد فایل‌های تصویری را از کاوشگر فایل سیستم‌عامل کاربر بکشد و روی صفحه رها کند و آن‌ها را روی صفحه نمایش دهد. برای کاربرانی که نمی‌توانند یا نمی‌خواهند از کشیدن و رها کردن استفاده کنند، قابلیت جایگزین انتخاب فایل را نیز از طریق یک عنصر `<input>` فراهم می‌کنیم.

## چیدمان پایهٔ صفحه

از آنجا که می‌خواهیم انتخاب فایل معمولی با `<input>` نیز امکان‌پذیر باشد، منطقی است که ناحیهٔ رهاسازی توسط یک عنصر `<input>` پشتیبانی شود تا بتوانیم هم‌زمان فایل‌ها را به داخل آن بکشیم و روی آن کلیک کنیم. ما از یک ترفند رایج استفاده می‌کنیم: `<input>` را نامرئی می‌کنیم و از {{HTMLElement("label")}} مرتبط با آن برای تعامل با کاربر بهره می‌بریم، زیرا استایل‌دهی به عناصر `<label>` بسیار آسان‌تر است. همچنین عناصر پیش‌نمایش تصاویر رهاشده را اضافه می‌کنیم.

```html live-sample___file-dnd
<label id="drop-zone">
  Drop images here, or click to upload.
  <input type="file" id="file-input" multiple accept="image/*" />
</label>
<ul id="preview"></ul>
<button id="clear-btn">Clear</button>
```

ما عنصر `label` را طوری استایل می‌دهیم که به‌صورت بصری یک ناحیهٔ رهاسازی باشد و ورودی فایل را پنهان می‌کنیم.

```css live-sample___file-dnd
body {
  font-family: "Arial", sans-serif;
}

#drop-zone {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 500px;
  max-width: 100%;
  height: 200px;
  padding: 1em;
  border: 1px solid #cccccc;
  border-radius: 4px;
  color: slategray;
  cursor: pointer;
}

#file-input {
  display: none;
}

#preview {
  width: 500px;
  max-width: 100%;
  display: flex;
  flex-direction: column;
  gap: 0.5em;
  list-style: none;
  padding: 0;
}

#preview li {
  display: flex;
  align-items: center;
  gap: 0.5em;
  margin: 0;
  width: 100%;
  height: 100px;
}

#preview img {
  width: 100px;
  height: 100px;
  object-fit: cover;
}
```

به دلیل استفاده از عناصر `<label>` و `<input>`، برای پیاده‌سازی تجربهٔ کاربری انتخاب فایل به جاوااسکریپت اضافی نیاز نیست. اکنون روی رها کردن فایل و پردازش بعدی فایل‌های رهاشده تمرکز می‌کنیم.

## تعریف هدف رهاسازی

هدف رهاسازی ما عنصر `<label>` است. این عنصر به‌عنوان _عنصر هدف_، برای پردازش فایل رهاشده به رویداد {{domxref("HTMLElement/drop_event", "drop")}} گوش می‌دهد.

```js live-sample___file-dnd
const dropZone = document.getElementById("drop-zone");

dropZone.addEventListener("drop", dropHandler);
```

هنگام رها کردن فایل، مرورگر ممکن است آن‌ها را به‌صورت پیش‌فرض پردازش کند (مانند باز کردن یا دانلود فایل)، حتی وقتی فایل در یک هدف رهاسازی معتبر رها نشده باشد. برای جلوگیری از این رفتار، لازم است به رویداد `drop` روی `window` نیز گوش دهیم و آن را لغو کنیم. دقت می‌کنیم که رویداد را فقط زمانی مدیریت کنیم که یک فایل در حال کشیده‌شدن باشد؛ اگر چیز دیگری مانند یک پیوند باشد، همچنان از رفتار پیش‌فرض استفاده می‌کنیم. اگر آیتم کشیده‌شده یک فایل غیرتصویری باشد، باز هم رویداد را مدیریت می‌کنیم، اما بازخوردی به کاربر می‌دهیم که مجاز نیست.

```js live-sample___file-dnd
window.addEventListener("drop", (e) => {
  if ([...e.dataTransfer.items].some((item) => item.kind === "file")) {
    e.preventDefault();
  }
});
```

برای اینکه رویداد `drop` فعال شود، عنصر باید رویداد {{domxref("HTMLElement/dragover_event", "dragover")}} را نیز لغو کند. از آنجا که ما به رویداد `drop` روی `window` گوش می‌دهیم، لازم است رویداد `dragover` را برای کل `window` نیز لغو کنیم. همچنین اگر فایل تصویری نباشد یا به مکان درست کشیده نشده باشد، {{domxref("DataTransfer.dropEffect")}} را روی `none` تنظیم می‌کنیم.

```js live-sample___file-dnd
dropZone.addEventListener("dragover", (e) => {
  const fileItems = [...e.dataTransfer.items].filter(
    (item) => item.kind === "file",
  );
  if (fileItems.length > 0) {
    e.preventDefault();
    if (fileItems.some((item) => item.type.startsWith("image/"))) {
      e.dataTransfer.dropEffect = "copy";
    } else {
      e.dataTransfer.dropEffect = "none";
    }
  }
});

window.addEventListener("dragover", (e) => {
  const fileItems = [...e.dataTransfer.items].filter(
    (item) => item.kind === "file",
  );
  if (fileItems.length > 0) {
    e.preventDefault();
    if (!dropZone.contains(e.target)) {
      e.dataTransfer.dropEffect = "none";
    }
  }
});
```

> [!NOTE]
> رویدادهای {{domxref("HTMLElement/dragstart_event", "dragstart")}} و {{domxref("HTMLElement/dragend_event", "dragend")}} هنگام کشیدن فایل از سیستم‌عامل به داخل مرورگر فعال نمی‌شوند. برای تشخیص کشیده‌شدن فایل‌های سیستم‌عامل به داخل مرورگر، از {{domxref("HTMLElement/dragenter_event", "dragenter")}} و {{domxref("HTMLElement/dragleave_event", "dragleave")}} استفاده کنید.
> این بدان معناست که امکان استفاده از {{domxref("DataTransfer.setDragImage","setDragImage()")}} برای اعمال یک تصویر/نمایهٔ شناور سفارشی هنگام کشیدن فایل‌ها از سیستم‌عامل وجود ندارد — زیرا ذخیره‌گاه دادهٔ کشیدن فقط در رویداد {{domxref("HTMLElement/dragstart_event", "dragstart")}} قابل تغییر است. این موضوع در مورد {{domxref("DataTransfer.setData","setData()")}} نیز صدق می‌کند.

## پردازش رهاسازی

اکنون `dropHandler` را با استفاده از روش {{domxref("DataTransferItem.getAsFile","getAsFile()")}} برای دسترسی به هر فایل پیاده‌سازی می‌کنیم. سپس برنامهٔ شما می‌تواند تصمیم بگیرد که این فایل را چگونه با استفاده از [File API](/en-US/docs/Web/API/File_API) پردازش کند. در اینجا ما فقط آن‌ها را روی صفحه نمایش می‌دهیم؛ در عمل احتمالاً می‌خواهید در نهایت آن‌ها را به سرور نیز بارگذاری کنید.

```js live-sample___file-dnd
const preview = document.getElementById("preview");

function displayImages(files) {
  for (const file of files) {
    if (file.type.startsWith("image/")) {
      const li = document.createElement("li");
      const img = document.createElement("img");
      img.src = URL.createObjectURL(file);
      img.alt = file.name;
      li.appendChild(img);
      li.appendChild(document.createTextNode(file.name));
      preview.appendChild(li);
    }
  }
}

function dropHandler(ev) {
  ev.preventDefault();
  const files = [...ev.dataTransfer.items]
    .map((item) => item.getAsFile())
    .filter((file) => file);
  displayImages(files);
}
```

## افزودن همان رفتار به عنصر input

موارد بالا کل جریان داده برای کشیدن و رها کردن است؛ اکنون باید تابع `displayImages()` را به ورودی فایل نیز متصل کنیم.

```js live-sample___file-dnd
const fileInput = document.getElementById("file-input");
fileInput.addEventListener("change", (e) => {
  displayImages(e.target.files);
});
```

## دکمهٔ پاک کردن

در نهایت راهی برای پاک کردن ناحیهٔ پیش‌نمایش اضافه می‌کنیم. ما از {{domxref("URL.revokeObjectURL_static","URL.revokeObjectURL()")}} برای آزاد کردن حافظهٔ استفاده‌شده توسط اشیاء تصویر بهره می‌بریم.

```js live-sample___file-dnd
const clearBtn = document.getElementById("clear-btn");
clearBtn.addEventListener("click", () => {
  for (const img of preview.querySelectorAll("img")) {
    URL.revokeObjectURL(img.src);
  }
  preview.textContent = "";
});
```

## نتیجه

{{EmbedLiveSample("file-dnd", "", 500)}}

## همچنین ببینید

- [HTML Drag and Drop API](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
```