---
title: "Navigator: getAutoplayPolicy() method"
short-title: getAutoplayPolicy()
slug: Web/API/Navigator/getAutoplayPolicy
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Navigator.getAutoplayPolicy
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

متد **`getAutoplayPolicy()`** از _Autoplay Policy Detection API_ اطلاعاتی در این مورد ارائه می‌دهد که آیا [پخش خودکار](/en-US/docs/Web/Media/Guides/Autoplay) عناصر رسانه‌ای و زمینه‌های صوتی (audio contexts) مجاز است، غیرمجاز است، یا فقط در صورتی مجاز است که صدا بی‌صدا (muted) باشد.

برنامه‌ها می‌توانند از این اطلاعات برای ارائه تجربه‌ی کاربری مناسب استفاده کنند.
برای مثال، اگر خط‌مشی (policy) عامل کاربر (user agent) فقط اجازه‌ی پخش خودکار محتوای بی‌صدا را بدهد، برنامه می‌تواند ویدیوها را بی‌صدا کند تا همچنان بتوانند به‌صورت خودکار پخش شوند.

از این متد می‌توان برای دریافت خط‌مشی کلی پخش خودکار برای همه‌ی موارد یک نوع خاص در سند، یا برای عناصر رسانه‌ای یا زمینه‌های صوتی خاص استفاده کرد.

## نحوه‌ی استفاده (Syntax)

```js-nolint
// بررسی خط‌مشی پخش خودکار برای یک ویژگی پخش رسانه‌ای خاص
getAutoplayPolicy(type)

// بررسی پشتیبانی از پخش خودکار برای یک عنصر یا زمینه‌ی خاص
getAutoplayPolicy(element)
getAutoplayPolicy(context)
```

### پارامترها

متد باید با یکی (و فقط یکی) از سه پارامتر زیر فراخوانی شود:

- `type` {{optional_inline}}
  - : رشته‌ای است که ویژگی پخش رسانه‌ای را مشخص می‌کند که خط‌مشی کلی پخش خودکار برای آن لازم است.

    مقادیر پشتیبانی‌شده عبارت‌اند از:
    - `mediaelement`
      - : دریافت خط‌مشی کلی پخش خودکار برای عناصر رسانه‌ای در سند.
        عناصر رسانه‌ای اشیاء مشتق‌شده از [`HTMLMediaElement`](/en-US/docs/Web/API/HTMLMediaElement) مانند [`HTMLAudioElement`](/en-US/docs/Web/API/HTMLAudioElement) و [`HTMLVideoElement`](/en-US/docs/Web/API/HTMLVideoElement) و همچنین تگ‌های متناظر آن‌ها {{HTMLElement("audio")}} و {{HTMLElement("video")}} هستند.

    - `audiocontext`
      - : دریافت خط‌مشی کلی پخش خودکار برای پخش‌کننده‌های [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) در سند.

- `element` {{optional_inline}}
  - : یک عنصر رسانه‌ای خاص.
    این باید یک [`HTMLMediaElement`](/en-US/docs/Web/API/HTMLMediaElement) باشد، از جمله عناصر مشتق‌شده مانند [`HTMLVideoElement`](/en-US/docs/Web/API/HTMLVideoElement) و [`HTMLAudioElement`](/en-US/docs/Web/API/HTMLAudioElement).

- `context` {{optional_inline}}
  - : یک [`AudioContext`](/en-US/docs/Web/API/AudioContext) خاص.

### مقدار بازگشتی

رشته‌ای که خط‌مشی پخش خودکار را برای نوع ویژگی، عنصر یا زمینه‌ی مشخص‌شده نشان می‌دهد.
این رشته یکی از مقادیر زیر را شامل می‌شود:

- `allowed`
  - : پخش خودکار مجاز است.
- `allowed-muted`
  - : پخش خودکار فقط برای رسانه‌ی بی‌صدا مجاز است.
    این شامل رسانه‌ای است که track صوتی ندارد یا صدای آن بی‌صدا شده است.
- `disallowed`
  - : پخش خودکار مجاز نیست.

توجه داشته باشید که خط‌مشی پخش خودکار بازگشت‌داده‌شده برای پارامتر `type`، خط‌مشی _کلی_ برای مواردی از نوع مشخص‌شده است.
در هنگام بارگذاری صفحه، همه‌ی موارد از یک نوع، همان خط‌مشی نوع را دارند.
پس از اینکه کاربر با صفحه/سایت تعامل کرد، در برخی مرورگرها ممکن است تک‌تک موارد خط‌مشی متفاوتی نسبت به نوع مربوطه داشته باشند.

### استثناها (Exceptions)

- `TypeError`
  - : شیء ارسال‌شده به متد از نوع مجاز نیست.
    انواع مجاز شامل [`HTMLMediaElement`](/en-US/docs/Web/API/HTMLMediaElement) (یا عنصر مشتق‌شده مانند [`HTMLVideoElement`](/en-US/docs/Web/API/HTMLVideoElement) و [`HTMLAudioElement`](/en-US/docs/Web/API/HTMLAudioElement)) یا [`AudioContext`](/en-US/docs/Web/API/AudioContext) است.

## توضیحات

«پخش خودکار» (Autoplay) به هر ویژگی‌ای اشاره دارد که باعث شود محتوا بدون درخواست صریح کاربر برای شروع پخش، شروع به پخش کند.
این شامل ویژگی `autoplay` در عناصر HTML [`<video>`](/en-US/docs/Web/HTML/Reference/Elements/video#autoplay) و [`<audio>`](/en-US/docs/Web/HTML/Reference/Elements/audio#autoplay) و همچنین استفاده از کد جاوااسکریپت برای شروع پخش بدون هیچ تعامل کاربری می‌شود.

عامل‌های کاربر معمولاً پخش خودکار را مسدود می‌کنند یا فقط اجازه‌ی پخش خودکار محتوای بی‌صدا را می‌دهند، زیرا صداهای غیرمنتظره هنگام بارگذاری اولیه‌ی صفحه می‌تواند تجربه‌ی کاربری ناخوشایند و آزاردهنده‌ای ایجاد کند.
سازوکارهای مورد استفاده برای تعیین اینکه آیا محتوا می‌تواند پخش خودکار شود یا نه، یا فقط برای محتوای بی‌صدا پخش شود، در عامل‌های کاربر متفاوت است.

متد **`getAutoplayPolicy()`** یک سازوکار استاندارد برای تعیین خط‌مشی یک عامل کاربر خاص برای پخش خودکار یک نوع یا مورد خاص از محتوا فراهم می‌کند.
این امر سفارشی‌سازی برنامه را ممکن می‌سازد، مانند بی‌صدا کردن خودکار ویدیو در سایت‌هایی که پخش خودکار محتوای دارای صدا مجاز نیست، یا اصلاح برنامه برای رفتار بدون پخش خودکار.

استفاده‌ی توصیه‌شده از این متد این است که آن را _هنگام بارگذاری صفحه_ (یا قبل از ایجاد عناصر پخش‌کننده‌ی محتوا) فراخوانی کنید و نوع ویژگی مورد بررسی را مشخص کنید و سپس پخش خودکار عناصر رسانه‌ای را بر اساس نتیجه پیکربندی کنید.
برای مثال، اگر برنامه می‌خواهد عناصر ویدیویی که track صوتی دارند را به‌صورت خودکار پخش کند، می‌توانید از کد زیر برای بی‌صدا کردن ویدیو در صورت مجاز بودن فقط محتوای بی‌صدا استفاده کنید.

```js
if (navigator.getAutoplayPolicy("mediaelement") === "allowed") {
  // کاری نکنید. محتوا می‌تواند به‌صورت خودکار پخش شود.
} else if (navigator.getAutoplayPolicy("mediaelement") === "allowed-muted") {
  // ویدیو را بی‌صدا کنید تا بتواند پخش خودکار شود.
} else {
  // پخش خودکار مجاز نیست.
  // یک دکمه‌ی پخش به عنصر ویدیو اضافه کنید.
}
```

همچنین می‌توان این متد را برای بررسی خط‌مشی پخش خودکار برای یک عنصر رسانه‌ای یا زمینه‌ی صوتی خاص فراخوانی کرد.
همانطور که در زیر نشان داده شده است، کد دقیقاً یکسان به نظر می‌رسد، فقط به جای رشته‌ی `type`، مورد خاص را ارسال می‌کنید.

```js
const video = document.getElementById("video_element_id");
if (navigator.getAutoplayPolicy(video) === "allowed") {
  // کاری نکنید. محتوا می‌تواند به‌صورت خودکار پخش شود.
} else if (navigator.getAutoplayPolicy(video) === "allowed-muted") {
  // ویدیو را بی‌صدا کنید تا بتواند پخش خودکار شود.
} else {
  // پخش خودکار مجاز نیست.
  // یک دکمه‌ی پخش به عنصر ویدیو اضافه کنید.
}
```

در هنگام بارگذاری صفحه، قبل از اینکه کاربر با صفحه یا سایت تعامل کند، خط‌مشی پخش خودکار برای نوع و تک‌تک موارد یکسان خواهد بود.
پس از تعامل کاربر با سایت، صفحه یا عناصر خاص، ممکن است خط‌مشی پخش خودکار برای کل `type` تغییر کند.
همچنین ممکن است خط‌مشی برای یک مورد خاص تغییر کند، حتی اگر خط‌مشی کلی برای `type` تغییر نکند.

هیچ راهی برای دریافت اعلان تغییر خط‌مشی پخش خودکار وجود ندارد.
به همین دلیل، اگرچه می‌توانید خط‌مشی را برای یک نوع یا مورد در هر زمان بررسی کنید، معمولاً فقط هنگام بارگذاری صفحه یا قبل از تلاش برای پخش محتوا این کار را انجام می‌دهید.

## مثال‌ها

### بررسی پشتیبانی از ویژگی

کد زیر نحوه‌ی بررسی پشتیبانی از `navigator.getAutoplayPolicy()` را نشان می‌دهد:

```html hidden
<div id="reportResult"></div>
```

```js hidden
const log = document.getElementById("reportResult");
```

```js
if (!navigator.getAutoplayPolicy) {
  log.textContent = "navigator.getAutoplayPolicy() پشتیبانی نمی‌شود.";
} else {
  log.textContent = "navigator.getAutoplayPolicy() پشتیبانی می‌شود.";
}
```

نتیجه‌ی اجرای این کد در این صفحه به این صورت است:

{{EmbedLiveSample('Checking if the feature is supported', '', '50')}}

### بررسی خط‌مشی پخش خودکار برای نوع عنصر رسانه‌ای

این مثال نشان می‌دهد که چگونه می‌توانید خط‌مشی پخش خودکار را برای نوع عناصر رسانه‌ای بررسی کنید.

کد یک عنصر ویدیو ایجاد می‌کند که ویژگی [`autoplay`](/en-US/docs/Web/API/HTMLMediaElement/autoplay) را دارد و به‌طور پیش‌فرض بی‌صدا نیست.
اگر خط‌مشی پخش خودکار "allowed-muted" باشد، ویدیو برای اجازه‌ی پخش، بی‌صدا می‌شود.

#### HTML

در HTML زیر یک عنصر `div` وجود دارد که به‌عنوان گزارش استفاده می‌شود و همچنین یک [`<video>`](/en-US/docs/Web/HTML/Reference/Elements/video) با ویژگی [`autoplay`](/en-US/docs/Web/API/HTMLMediaElement/autoplay) نمایش می‌دهد.
این ویدیو نباید به‌طور پیش‌فرض بی‌صدا باشد و اگر پخش خودکار مسدود نباشد، باید به‌صورت خودکار پخش شود.

```html
<div id="reportResult"></div>
<!-- مثال ساده ویدیو -->
<!-- 'Big Buck Bunny' تحت مجوز CC 3.0 توسط بنیاد بلندر. میزبانی شده توسط archive.org -->
<!-- پوستر از peach.blender.org -->
<video
  id="bunny_vid"
  autoplay
  controls
  src="https://archive.org/download/BigBuckBunny_124/Content/big_buck_bunny_720p_surround.mp4"
  poster="https://peach.blender.org/wp-content/uploads/title_anouncement.jpg?x11217"
  width="620">
  متأسفیم، مرورگر شما از ویدیوهای تعبیه‌شده پشتیبانی نمی‌کند، اما نگران نباشید، می‌توانید
  <a href="https://archive.org/details/BigBuckBunny_124">آن را دانلود کنید</a> و
  با پخش‌کننده‌ی ویدیوی موردعلاقه‌تان تماشا کنید!
</video>
```

#### جاوااسکریپت

کد گزارش می‌دهد که آیا متد `getAutoplayPolicy()` پشتیبانی می‌شود یا خیر، و اگر پشتیبانی شود، خط‌مشی عناصر رسانه‌ای را گزارش می‌دهد.

اگر خط‌مشی `allowed-muted` باشد، فقط ویدیوهای بی‌صدا می‌توانند پخش شوند.
در این حالت، متنی اضافه می‌کنیم که توضیح می‌دهد چه اتفاقی دارد می‌افتد و ویدیو را بی‌صدا می‌کنیم.

```js
const log = document.getElementById("reportResult");
const video = document.getElementById("bunny_vid");

if (!navigator.getAutoplayPolicy) {
  log.textContent =
    "navigator.getAutoplayPolicy() پشتیبانی نمی‌شود. ممکن است بسته به مرورگر پخش خودکار انجام شود یا نشود!";
} else {
  log.textContent = `خط‌مشی پخش خودکار برای عناصر رسانه‌ای: ${navigator.getAutoplayPolicy(
    "mediaelement",
  )}. `;

  if (navigator.getAutoplayPolicy("mediaelement") === "allowed-muted") {
    // ویدیو را بی‌صدا کنید تا بتواند پخش خودکار شود
    video.muted = true;
    log.textContent += "ویدیو برای اجازه‌ی پخش خودکار بی‌صدا شده است.";
  }
}
```

توجه داشته باشید که به‌طور مشابه می‌توانید مقادیر `allowed` و `disallowed` را نیز بررسی کنید.

#### نتیجه

ویدیو در زیر همراه با اطلاعاتی درباره‌ی اینکه آیا متد `getAutoplayPolicy()` پشتیبانی می‌شود و اگر بله، خط‌مشی چیست، نمایش داده می‌شود.

اگر `getAutoplayPolicy()` پشتیبانی شود و خط‌مشی `allowed` باشد، ویدیو به‌صورت خودکار با صدا پخش می‌شود.
اگر خط‌مشی `allowed-muted` باشد، ویدیو بدون صدا پخش می‌شود.

{{EmbedLiveSample('Test autoplay policy for media elements', '', '400')}}

توجه داشته باشید که اگر `getAutoplayPolicy()` پشتیبانی نشود، ویدیو یا با صدا پخش خودکار می‌شود یا اصلاً پخش نمی‌شود.
کد هیچ کنترلی روی این رفتار ندارد: شما به اجرای مرورگر وابسته هستید!

### بررسی خط‌مشی پخش خودکار برای یک عنصر رسانه‌ای خاص

این مثال نشان می‌دهد که چگونه می‌توانید بررسی کنید که آیا یک عنصر رسانه‌ای خاص پخش خودکار خواهد شد یا خیر.
این مثال تقریباً دقیقاً مشابه مثال قبلی است (بررسی `AudioContext` نیز مشابه خواهد بود).
توجه داشته باشید که ممکن است عناصر خاص حتی اگر بررسی نوع `mediaelement` نشان دهد که پخش خودکار `disallowed` است، پخش خودکار شوند؛ به عبارت دیگر، بررسی یک عنصر خاص قابل‌اعتمادتر است (اگرچه در بارگذاری صفحه تفاوتی ندارد).

کد یک عنصر ویدیو ایجاد می‌کند که ویژگی [`autoplay`](/en-US/docs/Web/API/HTMLMediaElement/autoplay) را دارد.
اگر خط‌مشی پخش خودکار "allowed-muted" باشد، ویدیو برای اجازه‌ی پخش، بی‌صدا می‌شود.

#### HTML

در HTML زیر یک عنصر `div` وجود دارد که به‌عنوان گزارش استفاده می‌شود و همچنین یک [`<video>`](/en-US/docs/Web/HTML/Reference/Elements/video) با ویژگی [`autoplay`](/en-US/docs/Web/API/HTMLMediaElement/autoplay) نمایش می‌دهد.
این ویدیو نباید به‌طور پیش‌فرض بی‌صدا باشد و اگر پخش خودکار مسدود نباشد، باید به‌صورت خودکار پخش شود.

```html
<div id="reportResult"></div>
<!-- مثال ساده ویدیو -->
<!-- 'Big Buck Bunny' تحت مجوز CC 3.0 توسط بنیاد بلندر. میزبانی شده توسط archive.org -->
<!-- پوستر از peach.blender.org -->
<video
  id="bunny_vid"
  autoplay
  controls
  src="https://archive.org/download/Big