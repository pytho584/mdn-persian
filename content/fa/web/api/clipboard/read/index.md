---
title: "Clipboard: read() method"
short-title: read()
slug: Web/API/Clipboard/read
page-type: web-api-instance-method
browser-compat: api.Clipboard.read
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

متد **`read()`** در رابط {{domxref("Clipboard")}} درخواست یک کپی از محتویات کلیپبورد را ارسال میکند و {{jsxref("Promise")}} بازگشتی را با دادهها تکمیل میکند.

این متد در تئوری میتواند دادههای دلخواه را برگرداند (برخلاف {{domxref("Clipboard.readText", "readText()")}} که فقط متن برمیگرداند).
مرورگرها معمولاً از خواندن متن، HTML و دادههای تصویر PNG پشتیبانی میکنند.

## نحو (Syntax)

```js-nolint
read()
read(formats)
```

### پارامترها

- `formats` {{optional_inline}}
  - : یک شیء اختیاری با ویژگیهای زیر:
    - `unsanitized` {{optional_inline}}
      - : یک {{jsxref("Array")}} از رشتههای حاوی انواع MIME برای قالبهای دادهای که هنگام خواندن از کلیپبورد نباید پاکسازی (sanitize) شوند.

        برخی مرورگرها ممکن است دادههای کلیپبورد را هنگام خواندن پاکسازی کنند تا از چسباندن محتوای مخرب در سند جلوگیری شود. برای مثال، کروم (و سایر مرورگرهای مبتنی بر کرومیوم) دادههای HTML را با حذف تگهای `<script>` و سایر محتوای بالقوه خطرناک پاکسازی میکند. از آرایه `unsanitized` برای指定 فهرستی از انواع MIME که نباید پاکسازی شوند استفاده کنید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با آرایهای از اشیاء {{domxref("ClipboardItem")}} حاوی محتویات کلیپبورد حل میشود.

### استثناها (Exceptions)

- `NotAllowedError` {{domxref("DOMException")}}
  - : در صورتی که خواندن از کلیپبورد مجاز نباشد پرتاب میشود.

## ملاحظات امنیتی

خواندن از کلیپبورد فقط در [زمینه امن (secure context)](/en-US/docs/Web/Security/Defenses/Secure_Contexts) قابل انجام است.

ملزومات امنیتی اضافی در بخش [ملاحظات امنیتی](/en-US/docs/Web/API/Clipboard_API#security_considerations) در مبحث نمای کلی API پوشش داده شده است.

## مثال‌ها

### خواندن داده تصویر از کلیپبورد

این مثال از متد `read()` برای خواندن داده تصویر از کلیپبورد و چسباندن آن در یک عنصر {{HTMLElement("img")}} استفاده میکند.

#### HTML

```html
<img id="source" src="butterfly.jpg" alt="A butterfly" />
<img id="destination" src="" alt="Pasted image" />
<button id="reload" type="button">Reload</button>
<p id="log"></p>
```

#### CSS

```css
img {
  height: 100px;
  width: 100px;
  margin: 0 1rem;
  border: 1px solid black;
}
#reload {
  display: block;
  margin: 0 1rem;
}
```

#### JavaScript

این کد مکانیزمی برای ثبت هرگونه خطا در عنصر با شناسه `log` فراهم میکند.

```js
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `Error: ${text}`;
}
```

همچنین کدی برای بارگذاری مجدد و پاک کردن مثال هنگام فشردن دکمه «Reload» اضافه میکنیم.

```js
const reload = document.querySelector("#reload");

reload.addEventListener("click", () => {
  window.location.reload(true);
});
```

کد باقیمانده هنگام کلیک روی عنصر مقصد، کلیپبورد را میخواند و داده تصویر را در عنصر `destinationImage` کپی میکند.
در صورت عدم توانایی در استفاده از متد `read()` یا اینکه کلیپبورد حاوی داده با فرمت PNG نباشد، خطا ثبت میکند.

```js
const destinationImage = document.querySelector("#destination");
destinationImage.addEventListener("click", pasteImage);

async function pasteImage() {
  try {
    const clipboardContents = await navigator.clipboard.read();
    for (const item of clipboardContents) {
      if (!item.types.includes("image/png")) {
        throw new Error("Clipboard does not contain PNG image data.");
      }
      const blob = await item.getType("image/png");
      destinationImage.src = URL.createObjectURL(blob);
    }
  } catch (error) {
    log(error.message);
  }
}
```

#### نتیجه

تصویر پروانه در سمت چپ را با کلیک راست روی تصویر و انتخاب «Copy image» از منوی زمینه کپی کنید.
سپس روی قاب خالی در سمت راست کلیک کنید.
مثال داده تصویر را از کلیپبورد دریافت کرده و تصویر را در قاب خالی نمایش میدهد.

{{EmbedLiveSample("Reading image data from clipboard", "100%", "250", "", "", "", "clipboard-read")}}

> [!NOTE]
> در صورت درخواست، برای چسباندن تصویر اجازه دهید.

### خواندن داده از کلیپبورد

این مثال از متد `read()` برای خواندن داده از کلیپبورد و ثبت هر داده ذخیرهشده در کلیپبورد استفاده میکند.

این با نسخه قبلی تفاوت دارد زیرا اشیاء {{domxref("ClipboardItem")}} متنی، HTML و تصویری را نمایش میدهد (و نه فقط تصاویر).

#### HTML

```html
<img id="source_jpg" src="butterfly.jpg" alt="JPG butterfly image" />
<div id="destination">Click here to copy clipboard data.</div>
<button id="reload" type="button">Reload</button>
<p id="log"></p>
```

#### CSS

```css
img {
  height: 100px;
  width: 100px;
  margin: 0 1rem;
  border: 1px solid black;
}

#destination {
  min-height: 300px;
  min-width: 90%;
  margin: 0 1rem;
  border: 1px solid black;
}

#reload {
  display: block;
  margin: 0 1rem;
}
```

#### JavaScript

این کد مکانیزمی برای ثبت هرگونه خطا در عنصر با شناسه `log` فراهم میکند.

```js
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `Error: ${text}`;
}
```

همچنین کدی برای بارگذاری مجدد و پاک کردن مثال هنگام فشردن دکمه «Reload» اضافه میکنیم.

```js
const reload = document.querySelector("#reload");

reload.addEventListener("click", () => {
  window.location.reload(true);
});
```

کد باقیمانده هنگام کلیک روی عنصر مقصد، کلیپبورد را میخواند و هر عنصر {{domxref("ClipboardItem")}} را همراه با نوع MIME آن نمایش میدهد.
در صورت عدم توانایی در استفاده از متد `read()` یا وجود هر نوع MIME دیگر در کلیپبورد، خطا ثبت میکند.

```js
const destinationDiv = document.querySelector("#destination");
destinationDiv.addEventListener("click", pasteData);

async function pasteData() {
  destinationDiv.innerText = ""; // Clear inner text
  try {
    const clipboardContents = await navigator.clipboard.read();
    for (const item of clipboardContents) {
      for (const mimeType of item.types) {
        const mimeTypeElement = document.createElement("p");
        mimeTypeElement.innerText = `MIME type: ${mimeType}`;
        destinationDiv.appendChild(mimeTypeElement);
        if (mimeType === "image/png") {
          const pngImage = new Image();
          pngImage.alt = "PNG image from clipboard";
          const blob = await item.getType("image/png");
          pngImage.src = URL.createObjectURL(blob);
          destinationDiv.appendChild(pngImage);
        } else if (mimeType === "text/html") {
          const blob = await item.getType("text/html");
          const blobText = await blob.text();
          const clipHTML = document.createElement("pre");
          clipHTML.innerText = blobText;
          destinationDiv.appendChild(clipHTML);
        } else if (mimeType === "text/plain") {
          const blob = await item.getType("text/plain");
          const blobText = await blob.text();
          const clipPlain = document.createElement("pre");
          clipPlain.innerText = blobText;
          destinationDiv.appendChild(clipPlain);
        } else {
          throw new Error(`${mimeType} not supported.`);
        }
      }
    }
  } catch (error) {
    log(error.message);
  }
}
```

#### نتیجه

مقداری متن یا تصویر پروانه (JPG) زیر را کپی کنید (برای کپی تصاویر روی آنها کلیک راست کرده و سپس «Copy image» را از منوی زمینه انتخاب کنید).
قاب مشخصشده در زیر را انتخاب کنید تا این اطلاعات از کلیپبورد در قاب چسبانده شود.

{{EmbedLiveSample("Reading data from the clipboard", "100%", "500", "", "", "", "clipboard-read")}}

توجه:

- حتی اگر تصویر پروانه یک فایل JPG باشد، هنگام خواندن از کلیپبورد بهصورت PNG است.
- در صورت درخواست، برای چسباندن تصویر باید اجازه دهید.
- این ممکن است در مرورگرهای کرومیوم کار نکند زیرا قاب نمونه دارای مجوز [Permissions-Policy](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy) برای `clipboard-read` و `clipboard-write` نیست ([الزامی توسط مرورگرهای کرومیوم](/en-US/docs/Web/API/Clipboard_API#security_considerations)).

### خواندن HTML پاکسازینشده از کلیپبورد

این مثال از پارامتر `formats` برای خواندن داده HTML از کلیپبورد و دریافت کد به شکل اصلی آن، بدون پاکسازی قبلی مرورگر، استفاده میکند.

#### HTML

```html
<textarea id="source" rows="5">
  <style>h1 {color: red;} p {color: blue;}</style>
  <h1>Hello world!</h1>
  <p>This is a test.</p>
  <script>alert('Hello world!');</script>
</textarea>
<button id="copy">Copy HTML</button>
<button id="paste_normal">Paste HTML</button>
<button id="paste_unsanitized">Paste unsanitized HTML</button>
<textarea id="destination" rows="5"></textarea>
```

#### CSS

```css
body {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 5px;
}

textarea {
  grid-column: 1 / span 3;
}
```

#### JavaScript

```js
const copyButton = document.getElementById("copy");
const pasteButton = document.getElementById("paste_normal");
const pasteUnsanitizedButton = document.getElementById("paste_unsanitized");
const sourceTextarea = document.getElementById("source");
const destinationTextarea = document.getElementById("destination");

copyButton.addEventListener("click", async () => {
  const text = sourceTextarea.value;
  const type = "text/html";
  const blob = new Blob([text], { type });
  const data = [new ClipboardItem({ [type]: blob })];

  try {
    await navigator.clipboard.write(data);
  } catch (error) {
    destinationTextarea.value = `Clipboard write failed: ${error}`;
  }
});

async function getHTMLFromClipboardContents(clipboardContents) {
  for (const item of clipboardContents) {
    if (item.types.includes("text/html")) {
      const blob = await item.getType("text/html");
      const blobText = await blob.text();
      return blobText;
    }
  }

  return null;
}

pasteButton.addEventListener("click", async () => {
  try {
    const clipboardContents = await navigator.clipboard.read();
    const html = await getHTMLFromClipboardContents(clipboardContents);
    destinationTextarea.value =
      html || "Could not find HTML data in the clipboard.";
  } catch (error) {
    destinationTextarea.value = `Clipboard read failed: ${error}`;
  }
});

pasteUnsanitizedButton.addEventListener("click", async () => {
  try {
    const clipboardContents = await navigator.clipboard.read({
      unsanitized: ["text/html"],
    });
    const html = await getHTMLFromClipboardContents(clipboardContents);
    destinationTextarea.value =
      html || "Could not find HTML data in the clipboard.";
  } catch (error) {
    destinationTextarea.value = `Clipboard read failed: ${error}`;
  }
});
```

#### نتیجه

ابتدا دکمه «Copy HTML» را کلیک کنید تا کد HTML از اولین textarea در کلیپبورد نوشته شود. سپس یا دکمه «Paste HTML» یا دکمه «Paste unsanitized HTML» را کلیک کنید تا کد HTML پاکسازیشده یا پاکسازینشده در textarea دوم چسبانده شود.

{{EmbedLiveSample("Reading unsanitized HTML from the clipboard", "100%", "250", "", "", "", "clipboard-read; clipboard-write")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- [رفع انسداد دسترسی به کلیپبورد](https://web.dev/articles/async-clipboard) در web.dev
- [HTML پاکسازینشده در Async Clipboard API](https://developer.chrome.com/docs/web-platform/unsanitized-html-async-clipboard) در developer.chrome.com
- {{domxref("Clipboard.readText()")}}
- {{domxref("Clipboard.writeText()")}}
- {{domxref("Clipboard.write()")}}