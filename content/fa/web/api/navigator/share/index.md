```
---
title: "Navigator: share() method"
---

---
title: "Navigator: share() method"
short-title: share()
slug: Web/API/Navigator/share
page-type: web-api-instance-method
browser-compat: api.Navigator.share
---

{{APIRef("Web Share API")}}{{securecontext_header}}

متد **`share()`** از رابط {{domxref("Navigator")}}، سازوکار اشتراک‌گذاری بومی دستگاه را برای به اشتراک‌گذاری داده‌هایی مانند متن، URL یا فایل‌ها فرامی‌خواند. *مقصدهای اشتراک‌گذاری* موجود به دستگاه بستگی دارند و ممکن است شامل کلیپ‌بورد، برنامه‌های مخاطبان و ایمیل، وب‌سایت‌ها، بلوتوث و غیره باشند.

این متد یک {{jsxref("Promise")}} را با مقدار `undefined` حل می‌کند. در ویندوز این اتفاق هنگام نمایش پنجرهٔ اشتراک‌گذاری رخ می‌دهد، در حالی که در اندروید، Promise پس از انتقال موفق داده‌ها به *مقصد اشتراک‌گذاری* حل می‌شود.

[Web Share API](/en-US/docs/Web/API/Web_Share_API) توسط سیاستِ مجوزِ [web-share](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/web-share) محدود می‌شود. اگر این مجوز پشتیبانی شود اما اعطا نشده باشد، متد `share()` استثنا پرتاب خواهد کرد.

## نحو

```js-nolint
share(data)
```

### پارامترها

- `data` {{optional_inline}}
  - : شیئی حاوی داده‌های قابل اشتراک‌گذاری.

    ویژگی‌هایی که برای عامل کاربر (user agent) ناشناخته هستند نادیده گرفته می‌شوند؛ داده‌های اشتراک‌گذاری فقط بر اساس ویژگی‌هایی ارزیابی می‌شوند که عامل کاربر آن‌ها را درک می‌کند.
    همهٔ ویژگی‌ها اختیاری هستند، اما باید حداقل یک ویژگی شناخته‌شده مشخص شده باشد.

    مقادیر ممکن عبارت‌اند از:

    - `url` {{optional_inline}}
      - : رشته‌ای که یک URL برای به اشتراک‌گذاری را نشان می‌دهد. رشتهٔ خالی (`""`) به URL صفحهٔ فعلی اشاره می‌کند.
    - `text` {{optional_inline}}
      - : رشته‌ای که متنی برای به اشتراک‌گذاری را نشان می‌دهد.
    - `title` {{optional_inline}}
      - : رشته‌ای که عنوانی برای به اشتراک‌گذاری را نشان می‌دهد. ممکن است توسط مقصد نادیده گرفته شود.
    - `files` {{optional_inline}}
      - : آرایه‌ای از اشیاء {{domxref("File")}} که فایل‌های مورد اشتراک‌گذاری را نشان می‌دهد. برای انواع فایل‌های قابل اشتراک‌گذاری به [بخش پایین](#shareable_file_types) مراجعه کنید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با `undefined` حل می‌شود، یا با یکی از [استثناهای](#exceptions) زیر رد می‌شود.

### استثناها

ممکن است {{jsxref("Promise")}} با یکی از مقادیر `DOMException` زیر رد شود:

- `InvalidStateError` {{domxref("DOMException")}}
  - : سند کاملاً فعال نیست یا عملیات اشتراک‌گذاری دیگری در حال انجام است.
- `NotAllowedError` {{domxref("DOMException")}}
  - : یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) از نوع `web-share` برای مسدود کردن استفاده از این قابلیت به‌کار رفته باشد، پنجره فاقد {{Glossary("transient activation")}} باشد، یا به دلایل امنیتی اشتراک‌گذاری فایل مسدود شده باشد.
- {{jsxref("TypeError")}}
  - : داده‌های اشتراک‌گذاری مشخص‌شده قابل اعتبارسنجی نیستند. دلایل احتمالی عبارت‌اند از:
    - پارامتر `data` به‌طور کامل حذف شده باشد یا فقط شامل ویژگی‌هایی با مقادیر ناشناخته باشد. توجه داشته باشید که هر ویژگی‌ای که توسط عامل کاربر شناسایی نشود نادیده گرفته می‌شود.
    - یک URL به‌درستی قالب‌بندی نشده باشد.
    - فایل‌هایی مشخص شده باشند اما پیاده‌سازی از اشتراک‌گذاری فایل پشتیبانی نکند.
    - اشتراک‌گذاری دادهٔ مشخص‌شده توسط عامل کاربر به‌عنوان یک «اشتراک‌گذاری خصمانه» تلقی شود.
- `AbortError` {{domxref("DOMException")}}
  - : کاربر عملیات اشتراک‌گذاری را لغو کرده باشد یا هیچ مقصد اشتراک‌گذاری در دسترس نباشد.
- `DataError` {{domxref("DOMException")}}
  - : در راه‌اندازی مقصد اشتراک‌گذاری یا انتقال داده‌ها مشکلی به وجود آمده باشد.

## انواع فایل‌های قابل اشتراک‌گذاری

در ادامه فهرستی از انواع فایل‌هایی آورده شده است که معمولاً قابل اشتراک‌گذاری هستند. با این حال، برای اطمینان از موفقیت اشتراک‌گذاری همیشه باید با {{domxref("navigator.canShare()")}} بررسی کنید.

- برنامه (Application)
  - `.pdf` - `application/pdf`
- صوت (Audio)
  - `.flac` - `audio/flac`
  - `.m4a` - `audio/x-m4a`
  - `.mp3` - `audio/mpeg` (همچنین `audio/mp3` را می‌پذیرد)
  - `.oga` - `audio/ogg`
  - `.ogg` - `audio/ogg`
  - `.opus` - `audio/ogg`
  - `.wav` - `audio/wav`
  - `.weba` - `audio/webm`
- تصویر (Image)
  - `.avif` - `image/avif`
  - `.bmp` - `image/bmp`
  - `.gif` - `image/gif`
  - `.ico` - `image/x-icon`
  - `.jfif` - `image/jpeg`
  - `.jpeg` - `image/jpeg`
  - `.jpg` - `image/jpeg`
  - `.pjp` - `image/jpeg`
  - `.pjpeg` - `image/jpeg`
  - `.png` - `image/png`
  - `.svg` - `image/svg+xml`
  - `.svgz` - `image/svg+xml`
  - `.tif` - `image/tiff`
  - `.tiff` - `image/tiff`
  - `.webp` - `image/webp`
  - `.xbm` - `image/x-xbitmap`
- متن (Text)
  - `.css` - `text/css`
  - `.csv` - `text/csv`
  - `.ehtml` - `text/html`
  - `.htm` - `text/html`
  - `.html` - `text/html`
  - `.shtm` - `text/html`
  - `.shtml` - `text/html`
  - `.text` - `text/plain`
  - `.txt` - `text/plain`
- ویدئو (Video)
  - `.m4v` - `video/mp4`
  - `.mp4` - `video/mp4`
  - `.mpeg` - `video/mpeg`
  - `.mpg` - `video/mpeg`
  - `.ogm` - `video/ogg`
  - `.ogv` - `video/ogg`
  - `.webm` - `video/webm`

## امنیت

این متد مستلزم آن است که سندِ فعلی، سیاستِ مجوز [web-share](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/web-share) و {{Glossary("transient activation")}} را داشته باشد. (باید از یک رویداد رابط کاربری مانند کلیک روی دکمه ناشی شود و اسکریپت نمی‌تواند آن را در نقاط دلخواه فراخوانی کند.) علاوه بر این، متد باید دادهٔ معتبری را مشخص کند که توسط پیاده‌سازی بومی برای اشتراک‌گذاری پشتیبانی می‌شود.

## مثال‌ها

### اشتراک‌گذاری یک URL

مثال زیر کلیک روی یک دکمه را نشان می‌دهد که با استفاده از Web Share API، نشانی MDN را به اشتراک می‌گذارد. این مثال از [آزمون Web share](https://mdn.github.io/dom-examples/web-share/) ما گرفته شده است ([مشاهدهٔ کد منبع](https://github.com/mdn/dom-examples/blob/main/web-share/index.html)).

#### HTML

HTML فقط یک دکمه برای آغاز اشتراک‌گذاری و یک پاراگراف برای نمایش نتیجهٔ آزمون ایجاد می‌کند.

```html
<p><button>Share MDN!</button></p>
<p class="result"></p>
```

#### JavaScript

```js
const shareData = {
  title: "MDN",
  text: "Learn web development on MDN!",
  url: "https://developer.mozilla.org",
};

const btn = document.querySelector("button");
const resultPara = document.querySelector(".result");

// Share must be triggered by "user activation"
btn.addEventListener("click", async () => {
  try {
    await navigator.share(shareData);
    resultPara.textContent = "MDN shared successfully";
  } catch (err) {
    resultPara.textContent = `Error: ${err}`;
  }
});
```

#### نتیجه

برای باز کردن گفت‌وگوی اشتراک‌گذاری در دستگاه خود روی دکمه کلیک کنید. در زیر دکمه متنی ظاهر می‌شود که نشان می‌دهد اشتراک‌گذاری موفق بوده است یا کد خطا را ارائه می‌دهد.

{{EmbedLiveSample('Sharing a URL','','','','','','web-share')}}

### اشتراک‌گذاری فایل‌ها

برای به اشتراک‌گذاری فایل‌ها، ابتدا {{domxref("navigator.canShare()")}} را بررسی کنید و آن را فراخوانی کنید. سپس فهرست فایل‌ها را در فراخوانی `navigator.share()` قرار دهید.

#### HTML

```html
<div>
  <label for="files">Select images to share:</label>
  <input id="files" type="file" accept="image/*" multiple />
</div>
<button id="share" type="button">Share your images!</button>
<output id="output"></output>
```

#### JavaScript

توجه داشته باشید که شیء داده ارسال‌شده به `navigator.canShare()` فقط شامل ویژگی `files` است؛ زیرا `title` و `text` نباید تأثیری داشته باشند.

```js
const input = document.getElementById("files");
const output = document.getElementById("output");

document.getElementById("share").addEventListener("click", async () => {
  const files = input.files;

  if (files.length === 0) {
    output.textContent = "No files selected.";
    return;
  }

  // feature detecting navigator.canShare() also implies
  // the same for the navigator.share()
  if (!navigator.canShare) {
    output.textContent = `Your browser doesn't support the Web Share API.`;
    return;
  }

  if (navigator.canShare({ files })) {
    try {
      await navigator.share({
        files,
        title: "Images",
        text: "Beautiful images",
      });
      output.textContent = "Shared!";
    } catch (error) {
      output.textContent = `Error: ${error.message}`;
    }
  } else {
    output.textContent = `Your system doesn't support sharing these files.`;
  }
});
```

#### نتیجه

{{EmbedLiveSample('Sharing files','','','','','','web-share')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("navigator.canShare()")}}
- <https://wpt.live/web-share/> (web platform tests)
```