---
title: "Picture-in-Picture API"
slug: Web/API/Picture-in-Picture_API
page-type: web-api-overview
browser-compat: api.PictureInPictureWindow
---

{{DefaultAPISidebar("Picture-in-Picture API")}}

**Picture-in-Picture API** به وب‌سایت‌ها امکان می‌دهد یک پنجره ویدئویی شناور و همیشه در بالای پنجره‌ها ایجاد کنند. این ویژگی به کاربران اجازه می‌دهد در حین تعامل با سایر سایت‌ها یا برنامه‌های روی دستگاه خود، به مصرف محتوای رسانه‌ای ادامه دهند.

> **توجه:** [Document Picture-in-Picture API](/en-US/docs/Web/API/Document_Picture-in-Picture_API) قابلیت‌های Picture-in-Picture API را گسترش می‌دهد تا پنجره همیشه در بالا بتواند با _هر_ محتوای HTML دلخواه (نه فقط یک ویدئو) پر شود.

> **توجه:** می‌توانید هنگام باز شدن برنامه‌نویسی شده پنجره همیشه در بالا، با استفاده از رویداد {{domxref("HTMLVideoElement.enterpictureinpicture_event", "enterpictureinpicture")}} کد را اجرا کنید. اما این رویداد زمانی که خود مرورگر (و نه کد شما) باعث انتقال محتوا به پنجره همیشه در بالا می‌شود، فعال نمی‌شود. این حالت می‌تواند به عنوان مثال در نتیجه پنهان شدن محتوا، تغییر برگه نمایش داده شده، یا انتخاب گزینه «تصویر در تصویر» توسط کاربر از منوی زمینه ویدئو یا کروم مرورگر رخ دهد.
>
> برای اجرای کد در پاسخ به چنین اقداماتی، یک کنترل‌کننده اکشن جلسه رسانه با استفاده از {{domxref("MediaSession.setActionHandler()")}} با `type` برابر با `enterpictureinpicture` تنظیم کنید.

## رابط‌ها

- {{DOMxRef("PictureInPictureWindow")}}
  - : نمایانگر پنجره ویدئویی شناور است؛ شامل ویژگی‌های {{domxref("PictureInPictureWindow/width", "width")}} و {{domxref("PictureInPictureWindow/height", "height")}} و یک ویژگی کنترل‌کننده رویداد {{domxref("PictureInPictureWindow/resize_event", "onresize")}} است.
- {{DOMxRef("PictureInPictureEvent")}}
  - : نمایانگر رویدادهای مرتبط با تصویر در تصویر، از جمله {{domxref("HTMLVideoElement/enterpictureinpicture_event", "enterpictureinpicture")}}، {{domxref("HTMLVideoElement/leavepictureinpicture_event", "leavepictureinpicture")}} و {{domxref("PictureInPictureWindow/resize_event", "resize")}} است.

## روش‌های نمونه

Picture-in-Picture API روش‌هایی را به رابط‌های {{DOMxRef("HTMLVideoElement")}} و {{DOMxRef("Document")}} اضافه می‌کند تا امکان جابجایی پنجره ویدئویی شناور فراهم شود.

### روش‌های نمونه در رابط HTMLVideoElement

- {{DOMxRef("HTMLVideoElement.requestPictureInPicture()")}}
  - : درخواست می‌کند که عامل کاربر ویدئو را به حالت تصویر در تصویر وارد کند.

### روش‌های نمونه در رابط Document

- {{DOMxRef("Document.exitPictureInPicture()")}}
  - : درخواست می‌کند که عامل کاربر عنصر موجود در حالت تصویر در تصویر را به جعبه اصلی خود بازگرداند.

## ویژگی‌های نمونه

Picture-in-Picture API رابط‌های {{DOMxRef("HTMLVideoElement")}}، {{DOMxRef("Document")}} و {{DOMxRef("ShadowRoot")}} را با ویژگی‌هایی گسترش می‌دهد که می‌توانند برای تعیین پشتیبانی و در دسترس بودن حالت پنجره ویدئویی شناور، فعال بودن حالت تصویر در تصویر در حال حاضر، و اینکه کدام ویدئو شناور است، استفاده شوند.

### ویژگی‌های نمونه در رابط HTMLVideoElement

- {{DOMxRef("HTMLVideoElement.disablePictureInPicture")}}
  - : ویژگی `disablePictureInPicture` به عامل کاربر راهنمایی می‌کند که تصویر در تصویر را به کاربران پیشنهاد ندهد یا به طور خودکار درخواست نکند.

### ویژگی‌های نمونه در رابط Document

- {{DOMxRef("Document.pictureInPictureEnabled")}}
  - : ویژگی `pictureInPictureEnabled` به شما می‌گوید که آیا امکان ورود به حالت تصویر در تصویر وجود دارد یا خیر. اگر حالت تصویر در تصویر به هر دلیلی در دسترس نباشد (مثلاً [`"picture-in-picture"` feature](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/picture-in-picture) غیرفعال شده باشد یا حالت تصویر در تصویر پشتیبانی نشود)، این مقدار `false` است.

### ویژگی‌های نمونه در رابط‌های Document یا ShadowRoot

- {{DOMxRef("Document.pictureInPictureElement")}} / {{DOMxRef("ShadowRoot.pictureInPictureElement")}}
  - : ویژگی `pictureInPictureElement` به شما می‌گوید کدام {{DOMxRef("Element")}} در حال حاضر در پنجره شناور (یا در DOM سایه‌ای) نمایش داده می‌شود. اگر این مقدار `null` باشد، سند (یا DOM سایه‌ای) هیچ گره‌ای در حالت تصویر در تصویر ندارد.

## رویدادها

_Picture-in-Picture API سه رویداد را تعریف می‌کند که می‌توان از آن‌ها برای تشخیص زمان جابجایی حالت تصویر در تصویر و تغییر اندازه پنجره ویدئویی شناور استفاده کرد._

- {{domxref("HTMLVideoElement.enterpictureinpicture_event", "enterpictureinpicture")}}
  - : به یک {{DOMxRef("HTMLVideoElement")}} هنگامی که وارد حالت تصویر در تصویر می‌شود، ارسال می‌شود.
- {{domxref("HTMLVideoElement.leavepictureinpicture_event", "leavepictureinpicture")}}
  - : به یک {{DOMxRef("HTMLVideoElement")}} هنگامی که از حالت تصویر در تصویر خارج می‌شود، ارسال می‌شود.
- {{domxref("PictureInPictureWindow.resize_event", "resize")}}
  - : به یک {{DOMxRef("PictureInPictureWindow")}} هنگامی که اندازه آن تغییر می‌کند، ارسال می‌شود.

## افزودن کنترل‌ها

اگر کنترل‌کننده‌های اکشن رسانه از طریق [Media Session API](/en-US/docs/Web/API/Media_Session_API) تنظیم شده باشند، مرورگر کنترل‌های مناسب برای آن اکشن‌ها را به پوشش تصویر در تصویر اضافه می‌کند. به عنوان مثال، اگر یک اکشن `"nexttrack"` تنظیم شده باشد، یک دکمه پرش به جلو ممکن است در نمای تصویر در تصویر نمایش داده شود. پشتیبانی از افزودن دکمه‌ها یا کنترل‌های HTML سفارشی وجود ندارد.

## کنترل سبک‌دهی

[شبه-کلاس](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-classes) {{cssxref(":picture-in-picture")}} [CSS](/en-US/docs/Web/CSS) با عنصر ویدئویی که در حال حاضر در حالت تصویر در تصویر است مطابقت دارد و به شما امکان می‌دهد شیوه‌نامه‌های خود را طوری پیکربندی کنید که به طور خودکار اندازه، سبک یا چیدمان محتوا را زمانی که یک ویدئو بین حالت تصویر در تصویر و حالت نمایش سنتی جابجا می‌شود، تنظیم کنند.

## کنترل دسترسی

در دسترس بودن حالت تصویر در تصویر می‌تواند با استفاده از [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) کنترل شود. ویژگی حالت تصویر در تصویر با رشته `"picture-in-picture"` شناسایی می‌شود و مقدار لیست مجاز پیش‌فرض آن `*` است، به این معنی که حالت تصویر در تصویر در زمینه‌های سند سطح بالا و همچنین در زمینه‌های مرور تودرتو که از همان مبدأ سند بالایی بارگذاری شده‌اند، مجاز است.

## مثال‌ها

### جابجایی حالت تصویر در تصویر

در این مثال، یک عنصر {{HTMLElement("video")}} در یک صفحه وب، یک {{HTMLElement("button")}} برای جابجایی تصویر در تصویر، و یک عنصر برای ثبت اطلاعات مرتبط با مثال داریم. عنصر {{HTMLElement("button")}} در ابتدا `disabled` است تا زمانی که پشتیبانی مرورگر را تعیین کنیم.

```html
<video
  src="/shared-assets/videos/friday.mp4"
  id="video"
  muted
  controls
  loop
  width="300"></video>

<button id="pip-button" disabled>Toggle PiP</button>
<pre id="log"></pre>
```

```css hidden
body {
  font:
    14px "Open Sans",
    sans-serif;
  padding: 0.5em;
}

button {
  display: block;
  margin-block: 1rem;
}
```

ابتدا با `document.pictureInPictureEnabled` بررسی می‌کنیم که آیا مرورگر از PiP پشتیبانی می‌کند یا خیر، و اگر پشتیبانی نمی‌کند، آن اطلاعات را در عنصر `<pre>` ثبت می‌کنیم. اگر در مرورگر در دسترس باشد، می‌توانیم دکمه جابجایی را برای ورود و خروج از PiP فعال کنیم.

برای کنترل‌ها، یک شنونده رویداد روی عنصر {{HTMLElement("button")}} تابع `togglePictureInPicture()` که تعریف کرده‌ایم را فراخوانی می‌کند. در `togglePictureInPicture()`، یک دستور `if` مقدار ویژگی `pictureInPictureElement` {{DOMxRef("Document", "document")}} را بررسی می‌کند.

- اگر مقدار `null` باشد، هیچ ویدئویی در پنجره شناور نیست، بنابراین می‌توانیم درخواست کنیم که ویدئو وارد حالت تصویر در تصویر شود. این کار را با فراخوانی {{DOMxRef("HTMLVideoElement.requestPictureInPicture()")}} روی عنصر {{HTMLElement("video")}} انجام می‌دهیم.
- اگر مقدار `null` نباشد، یک عنصر در حال حاضر در حالت تصویر در تصویر است. سپس می‌توانیم {{DOMxRef("Document.exitPictureInPicture", "document.exitPictureInPicture()")}} را فراخوانی کنیم تا ویدئو به جعبه اولیه خود بازگردد و از حالت تصویر در تصویر خارج شود.

```js
const video = document.getElementById("video");
const pipButton = document.getElementById("pip-button");
const log = document.getElementById("log");

if (document.pictureInPictureEnabled) {
  pipButton.removeAttribute("disabled");
} else {
  log.innerText = "PiP not supported. Check browser compatibility for details.";
}

function togglePictureInPicture() {
  if (document.pictureInPictureElement) {
    document.exitPictureInPicture();
  } else {
    video.requestPictureInPicture();
  }
}

pipButton.addEventListener("click", togglePictureInPicture);
```

```css
:picture-in-picture {
  outline: 5px dashed green;
}
```

با کلیک روی دکمه "Toggle PiP" کاربر می‌تواند بین پخش ویدئو در صفحه و در یک پنجره شناور جابجا شود:

{{embedlivesample("toggling_picture-in-picture", , "350")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("HTMLVideoElement.requestPictureInPicture()")}}
- {{DOMxRef("HTMLVideoElement.disablePictureInPicture")}}
- {{DOMxRef("Document.pictureInPictureEnabled")}}
- {{DOMxRef("Document.exitPictureInPicture()")}}
- {{DOMxRef("Document.pictureInPictureElement")}}
- {{CSSxRef(":picture-in-picture")}}
- [Document Picture-in-Picture API](/en-US/docs/Web/API/Document_Picture-in-Picture_API)