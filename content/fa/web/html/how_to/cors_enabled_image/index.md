---
title: "Use cross-origin images in a canvas"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/How_to/CORS_enabled_image"
translated_by: "n8n + AI"
---

HTML این امکان را فراهم می‌کند که با استفاده از ویژگی [`crossorigin`](/en-US/docs/Web/HTML/Reference/Elements/img#crossorigin) روی تصاویر، همراه با هدر مناسب {{Glossary("CORS")}}، تصاویر بارگذاری‌شده از originهای خارجی را درون یک {{HTMLElement("canvas")}} به‌کار ببری، انگار که از همین origin بار شده‌اند.

برای جزئیات بیشتر در مورد نحوه‌ی استفاده از ویژگی `crossorigin`، به [ویژگی‌های تنظیمات CORS](/en-US/docs/Web/HTML/Reference/Attributes/crossorigin) مراجعه کن.

## امنیت و canvasهای آلوده (tainted)

چون پیکسل‌های بیت‌مپ یک canvas می‌توانند از منابع مختلفی (مثل تصاویر یا ویدیوهای گرفته‌شده از میزبان‌های دیگر) بیایند، بروز مشکلات امنیتی اجتناب‌ناپذیر است.

به محض اینکه هر داده‌ای که از یک origin دیگر بدون تأیید CORS بارگذاری شده را درون یک canvas رسم کنی، آن canvas **آلوده (tainted)** می‌شود. یک canvas آلوده دیگر امن محسوب نمی‌شود و هر تلاشی برای دریافت داده‌های تصویری از آن باعث پرتاب یک استثنا خواهد شد.

اگر منبع محتوای خارجی یک عنصر HTML {{HTMLElement("img")}} یا SVG {{SVGElement("svg")}} باشد، تلاش برای دریافت محتویات canvas مجاز نیست.

اگر محتوای خارجی از تصویری بیاید که از یک {{domxref("HTMLCanvasElement")}} یا {{domxref("ImageBitMap")}} به دست آمده باشد، و منبع تصویر با قوانین **same-origin** مطابقت نداشته باشد، تلاش برای خواندن محتویات canvas مسدود می‌شود.

فراخوانی هر یک از موارد زیر روی یک canvas آلوده باعث خطا می‌شود:

- فراخوانی {{domxref("CanvasRenderingContext2D.getImageData", "getImageData()")}} روی context canvas
- فراخوانی {{domxref("HTMLCanvasElement.toBlob", "toBlob()")}}، {{domxref("HTMLCanvasElement.toDataURL", "toDataURL()")}} یا {{domxref("HTMLCanvasElement.captureStream", "captureStream()")}} روی خود عنصر {{HTMLElement("canvas")}}

هر کدام از این عملیات‌ها روی یک canvas آلوده باعث پرتاب خطای `SecurityError` می‌شود. این کار از کاربران در برابر افشای داده‌های خصوصی با استفاده از تصاویری که داده‌ها را از وب‌سایت‌های راه دور بدون اجازه بیرون می‌کشند، محافظت می‌کند.

## ذخیره‌سازی یک تصویر از یک origin خارجی

در این مثال می‌خواهیم اجازه دهیم تصاویر از originهای خارجی دریافت و در حافظه‌ی محلی (local storage) ذخیره شوند. پیاده‌سازی این کار نیاز به پیکربندی سرور و همچنین نوشتن کد برای خود وب‌سایت دارد.

### پیکربندی سرور وب

اولین چیزی که نیاز داریم یک سرور است که به‌گونه‌ای پیکربندی شده باشد که تصاویر را با هدر {{HTTPHeader("Access-Control-Allow-Origin")}} سرو کند تا دسترسی cross-origin به فایل‌های تصویری مجاز باشد.

فرض کنیم که سایت خود را با [Apache](https://httpd.apache.org/) سرو می‌کنیم. فایل پیکربندی سرور Apache برای CORS تصاویر از HTML5 Boilerplate در زیر آورده شده است:

```apacheconf
<IfModule mod_setenvif.c>
  <IfModule mod_headers.c>
    <FilesMatch "\.(avifs?|bmp|cur|gif|ico|jpe?g|jxl|a?png|svgz?|webp)$">
      SetEnvIf Origin ":" IS_CORS
      Header set Access-Control-Allow-Origin "*" env=IS_CORS
    </FilesMatch>
  </IfModule>
</IfModule>
```

به طور خلاصه، این پیکربندی به سرور اجازه می‌دهد که فایل‌های گرافیکی (با پسوندهای ".bmp"، ".cur"، ".gif"، ".ico"، ".jpg"، ".jpeg"، ".png"، ".svg"، ".svgz" و ".webp") را به صورت cross-origin از هر جایی در اینترنت در دسترس قرار دهد.

### پیاده‌سازی قابلیت ذخیره‌سازی

حالا که سرور برای دریافت تصاویر به صورت cross-origin پیکربندی شده است، می‌توانیم کدی بنویسیم که به کاربران اجازه دهد این تصاویر را در [حافظه‌ی محلی (local storage)](/en-US/docs/Web/API/Web_Storage_API) ذخیره کنند، درست مثل اینکه از همان دامنه‌ای که کد در آن اجرا می‌شود سرو می‌شدند.

کلید کار استفاده از ویژگی [`crossorigin`](/en-US/docs/Web/HTML/Reference/Elements/img#crossorigin) است، با تنظیم `crossOrigin` روی عنصر `HTMLImageElement` که تصویر در آن بارگذاری می‌شود. این کار به مرورگر می‌گوید هنگام دانلود داده‌های تصویر، دسترسی cross-origin را درخواست کند.

#### شروع دانلود

کدی که دانلود را آغاز می‌کند (مثلاً وقتی کاربر روی دکمه «دانلود» کلیک می‌کند) به این شکل است:

```js
function startDownload() {
  let imageURL = "https://mdn.github.io/shared-assets/images/examples/mdn.svg";
  let imageDescription = "Logo of a dinosaur in front of a map";

  downloadedImg = new Image();
  downloadedImg.crossOrigin = "anonymous";
  downloadedImg.addEventListener("load", imageReceived);
  downloadedImg.alt = imageDescription;
  downloadedImg.src = imageURL;
}
```

در اینجا از یک URL ثابت (`imageURL`) و متن توصیفی متناظر (`imageDescription`) استفاده کرده‌ایم، اما این مقادیر می‌توانند از هر جایی بیایند. برای شروع دانلود تصویر، یک شیء جدید `HTMLImageElement` با استفاده از سازنده `Image()` ایجاد می‌کنیم. سپس تصویر با تنظیم ویژگی `crossOrigin` روی `"anonymous"` (یعنی اجازه دانلود تصویر بدون احراز هویت cross-origin) برای دانلود cross-origin پیکربندی می‌شود. یک event listener به رویداد `load` روی عنصر تصویر اضافه می‌کنیم (که به معنی دریافت داده‌های تصویر است). متن جایگزین به تصویر اضافه می‌شود؛ اگرچه `<canvas>` از ویژگی `alt` پشتیبانی نمی‌کند، اما می‌توان از این مقدار برای تنظیم `aria-label` یا محتوای داخلی canvas استفاده کرد.

در نهایت، ویژگی `src` تصویر روی URL تصویر مورد نظر تنظیم می‌شود؛ این کار دانلود را آغاز می‌کند.

#### دریافت و ذخیره کردن تصویر

کدی که تصویر تازه دانلود شده را مدیریت می‌کند در متد `imageReceived()` قرار دارد:

```js
function imageReceived() {
  const canvas = document.createElement("canvas");
  const context = canvas.getContext("2d");

  canvas.width = downloadedImg.width;
  canvas.height = downloadedImg.height;
  canvas.innerText = downloadedImg.alt;

  context.drawImage(downloadedImg, 0, 0);
  imageBox.appendChild(canvas);

  try {
    localStorage.setItem("saved-image-example", canvas.toDataURL("image/png"));
  } catch (err) {
    console.error(`Error: ${err}`);
  }
}
```

`imageReceived()` برای مدیریت رویداد `load` روی `HTMLImageElement` که تصویر دانلود شده را دریافت می‌کند، فراخوانی می‌شود. این رویداد زمانی فعال می‌شود که تمام داده‌های دانلود شده در دسترس باشند. این تابع با ایجاد یک عنصر جدید `<canvas>` شروع می‌کند که برای تبدیل تصویر به یک data URL به کار می‌رود و سپس به بافت ترسیم دو بعدی canvas (`CanvasRenderingContext2D`) در متغیر `context` دسترسی پیدا می‌کند.

اندازه canvas با توجه به تصویر دریافتی تنظیم می‌شود، متن داخلی آن برابر با توضیحات تصویر قرار می‌گیرد، سپس تصویر با استفاده از `drawImage()` روی canvas کشیده می‌شود. در نهایت canvas به سند اضافه می‌شود تا تصویر قابل مشاهده باشد.

حالا نوبت ذخیره‌سازی محلی تصویر است. برای این کار از سازوکار ذخیره‌سازی محلی Web Storage API استفاده می‌کنیم که از طریق `localStorage` جهانی قابل دسترسی است. متد `toDataURL()` روی canvas برای تبدیل تصویر به یک data:// URL که نمایانگر یک تصویر PNG است به کار می‌رود و سپس با استفاده از `setItem()` در localStorage ذخیره می‌شود.

## همچنین ببینید

- [Using Cross-domain images in WebGL and Chrome 13](https://blog.chromium.org/2011/07/using-cross-domain-images-in-webgl-and.html)
- [HTML Specification - the `crossorigin` attribute](https://html.spec.whatwg.org/multipage/embedded-content.html#attr-img-crossorigin)
- [Web Storage API](/en-US/docs/Web/API/Web_Storage_API)