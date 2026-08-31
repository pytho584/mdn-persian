---
title: "Clipboard: write() method"
short-title: write()
slug: Web/API/Clipboard/write
page-type: web-api-instance-method
browser-compat: api.Clipboard.write
---

{{APIRef("Clipboard API")}} {{securecontext_header}}

متد **`write()`** در رابط {{domxref("Clipboard")}} داده‌های دلخواه {{domxref("ClipboardItem")}} مانند تصاویر و متن را در کلیپ‌بورد می‌نویسد و پس از اتمام، {{jsxref("Promise")}} برگشتی را برآورده می‌کند. از این متد می‌توان برای پیاده‌سازی قابلیت برش و کپی استفاده کرد.

این متد از نظر تئوری می‌تواند داده‌های دلخواه را بنویسد (برخلاف {{domxref("Clipboard.writeText", "writeText()")}} که فقط می‌تواند متن بنویسد). مرورگرها معمولاً از نوشتن متن، HTML و داده‌های تصویر PNG پشتیبانی می‌کنند.

## Syntax

```js-nolint
write(data)
```

### Parameters

- `data`
  - : یک آرایه از اشیاء {{domxref("ClipboardItem")}} حاوی داده‌هایی که باید در کلیپ‌بورد نوشته شوند.

### Return value

یک {{jsxref("Promise")}} که وقتی داده‌ها در کلیپ‌بورد نوشته شدند، حل می‌شود. توجه داشته باشید که اگر سیستم‌عامل زیرین از چندین آیتم کلیپ‌بورد بومی روی کلیپ‌بورد سیستم پشتیبانی نکند، فقط اولین {{domxref("ClipboardItem")}} در آرایه نوشته می‌شود. اگر کلیپ‌بورد قادر به نوشتن نباشد، promise رد می‌شود.

### Exceptions

- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر نوشتن در کلیپ‌بورد مجاز نباشد، پرتاب می‌شود.

## Security considerations

نوشتن در کلیپ‌بورد فقط در یک [زمینه امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) قابل انجام است. الزامات امنیتی اضافی در بخش [ملاحظات امنیتی](/en-US/docs/Web/API/Clipboard_API#security_considerations) از مبحث نمای کلی API پوشش داده شده است.

## Examples

### Write text to the clipboard

این تابع نمونه، محتوای فعلی کلیپ‌بورد را با یک رشته مشخص وقتی دکمه‌ای فشار داده می‌شود جایگزین می‌کند. توجه داشته باشید که برای این مورد خاص، به راحتی می‌توانید از `Clipboard.writeText()` استفاده کنید.

```js
button.addEventListener("click", () => setClipboard("<empty clipboard>"));

async function setClipboard(text) {
  const type = "text/plain";
  const clipboardItemData = {
    [type]: text,
  };
  const clipboardItem = new ClipboardItem(clipboardItemData);
  await navigator.clipboard.write([clipboardItem]);
}
```

تابع `setClipboard()` یک نوع MIME `"text/plain"` را در ثابت `type` مشخص می‌کند، سپس یک شیء `clipboardItemData` با یک ویژگی واحد تعریف می‌کند – کلید آن نوع MIME است و مقدار آن متنی است که می‌خواهیم در کلیپ‌بورد بنویسیم. سپس یک شیء جدید {{domxref("ClipboardItem")}} می‌سازیم که شیء `clipboardItemData` به آن داده می‌شود.

در نهایت، `write()` با `await` فراخوانی می‌شود تا داده‌ها را در کلیپ‌بورد بنویسد.

### Write canvas contents to the clipboard

این مثال یک مستطیل آبی روی بوم (canvas) رسم می‌کند. می‌توانید روی مستطیل کلیک کنید تا محتوای بوم به عنوان یک تصویر در کلیپ‌بورد کپی شود، و سپس عنصر دیگری را انتخاب کرده و محتوا را از کلیپ‌بورد جای‌گذاری کنید.

#### HTML

HTML فقط عنصر `<canvas>` ما و عنصر `<div>` با id `target` را تعریف می‌کند که تصویر بوم در آن جای‌گذاری می‌شود.

```html
<canvas id="canvas" width="100" height="100"></canvas>

<div id="target">Paste here.</div>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 60px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

#### JavaScript

ابتدا یک تابع `async` برای کپی کردن بوم به یک blob تعریف می‌کنیم. این تابع، متد قدیمی مبتنی بر callback {{domxref("HTMLCanvasElement.toBlob()")}} را به یک تابع مبتنی بر `Promise` بصری‌تر تبدیل می‌کند.

```js
// Async/await method replacing toBlob() callback
async function getBlobFromCanvas(canvas) {
  return new Promise((resolve, reject) => {
    canvas.toBlob((blob) => {
      if (blob) {
        resolve(blob);
      } else {
        reject(new Error("Canvas toBlob failed"));
      }
    });
  });
}
```

سپس بوم خود را تنظیم کرده و یک شنونده رویداد برای رویداد `click` اضافه می‌کنیم.

وقتی روی مستطیل آبی کلیک می‌کنید، بوم نمایش‌دهنده مستطیل به یک blob کپی می‌شود، سپس blob به یک `ClipboardItem` اضافه شده و در کلیپ‌بورد نوشته می‌شود.

```js
const canvas = document.getElementById("canvas");

// Set up canvas
const ctx = canvas.getContext("2d");
ctx.fillStyle = "cornflowerblue";
ctx.fillRect(0, 0, 100, 100);

canvas.addEventListener("click", copyCanvasContentsToClipboard);
const target = document.getElementById("target");

async function copyCanvasContentsToClipboard() {
  // Copy canvas to blob
  try {
    const blob = await getBlobFromCanvas(canvas);
    // Create ClipboardItem with blob and it's type, and add to an array
    const data = [new ClipboardItem({ [blob.type]: blob })];
    // Write the data to the clipboard
    await navigator.clipboard.write(data);
    log("Copied");
  } catch (error) {
    log(error);
  }
}
```

توجه داشته باشید که اگر در حال دریافت یک نوع فایل کمتر رایج یا منبعی هستید که نوع آن را از قبل نمی‌دانید، ممکن است بخواهید از {{domxref("ClipboardItem.supports_static", "ClipboardItem.supports()")}} برای بررسی پشتیبانی از نوع فایل استفاده کنید و در صورت عدم پشتیبانی، یک پیام خطای مناسب به کاربر ارائه دهید.

سپس یک شنونده رویداد برای [`paste` events](/en-US/docs/Web/API/Element/paste_event) روی عنصری که می‌خواهیم محتوای کلیپ‌بورد را به عنوان تصویر نمایش دهیم، تعریف می‌کنیم. [FileReader API](/en-US/docs/Web/API/FileReader) به ما امکان می‌دهد blob را با استفاده از متد [`readAsDataUrl`](/en-US/docs/Web/API/FileReader/readAsDataURL) بخوانیم و یک عنصر `<img>` با محتوای بوم ایجاد کنیم:

```js
target.addEventListener("paste", (event) => {
  const items = (event.clipboardData || window.clipboardData).items;
  const blob = items[0].getAsFile();
  const reader = new FileReader();

  reader.addEventListener("load", (event) => {
    const img = new Image();
    img.src = event.target.result;
    target.appendChild(img);
  });

  reader.readAsDataURL(blob);
});
```

```css hidden
body {
  font-family: sans-serif;
}
#target {
  border: 2px solid;
  padding: 1rem;
  height: 150px;
}
img {
  margin: 0.5rem;
}
```

#### Result

نتیجه در زیر نشان داده شده است. ابتدا روی مربع آبی کلیک کنید، سپس متن "Paste here" را انتخاب کرده و از ترکیب‌های صفحه‌کلید مخصوص سیستم‌عامل خود برای جای‌گذاری از کلیپ‌بورد استفاده کنید (مانند `Ctrl+V` در ویندوز).

{{embedlivesample("write_canvas_contents_to_the_clipboard", "", "420", "", "", "", "clipboard-write")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Clipboard API](/en-US/docs/Web/API/Clipboard_API)
- [Image support for Async Clipboard article](https://web.dev/articles/async-clipboard)
- {{domxref("Clipboard.writeText()")}}
- {{domxref("Clipboard.read()")}}
- {{domxref("Clipboard.readText()")}}