---
title: Using the MediaStream Recording API
slug: Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API
page-type: guide
browser-compat: api.MediaRecorder
---

{{DefaultAPISidebar("MediaStream Recording")}}

رابط برنامه‌نویسی ضبط جریان رسانه (MediaStream Recording API) ضبط جریان‌های صوتی و/یا تصویری را آسان می‌کند. هنگامی که با {{domxref("MediaDevices.getUserMedia()","navigator.mediaDevices.getUserMedia()")}} استفاده شود، روشی آسان برای ضبط از دستگاه‌های ورودی کاربر و استفاده فوری از نتیجه در برنامه‌های وب فراهم می‌کند.

هم صدا و هم تصویر را می‌توان به صورت جداگانه یا با هم ضبط کرد. هدف این مقاله ارائه یک راهنمای اولیه برای استفاده از واسط MediaRecorder است که این API را فراهم می‌کند.

## یک نمونه برنامه: دیکتافون تحت وب

![An image of the Web dictaphone sample app - a sine wave sound visualization, then record and stop buttons, then an audio jukebox of recorded tracks that can be played back.](web-dictaphone.png)

برای نمایش استفاده پایه از MediaStream Recording API، یک دیکتافون مبتنی بر وب ساخته‌ایم. این امکان را به شما می‌دهد که تکه‌هایی از صدا را ضبط کرده و سپس پخش کنید. حتی با استفاده از Web Audio API یک نمایش بصری از ورودی صدای دستگاه شما ارائه می‌دهد. در این مقاله بر روی قابلیت ضبط و پخش تمرکز خواهیم کرد.

می‌توانید این [نمونه زنده](https://mdn.github.io/dom-examples/media/web-dictaphone/) را ببینید یا [کد منبع](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone) را در GitHub دریافت کنید.

## نکات جالب CSS

HTML در این برنامه بسیار ساده است، بنابراین در اینجا به آن نمی‌پردازیم؛ با این حال، چند نکته جالب‌تر در CSS وجود دارد که ارزش ذکر دارند، بنابراین در زیر به آنها می‌پردازیم. اگر به CSS علاقه ندارید و می‌خواهید مستقیماً به بخش JavaScript بروید، به بخش [راه‌اندازی پایه برنامه](#basic_app_setup) بروید.

### محدود نگه داشتن رابط کاربری به نمای دید (viewport) بدون توجه به ارتفاع دستگاه، با استفاده از calc()

به عنوان مثال، در Web Dictaphone سه ناحیه اصلی رابط کاربری داریم که به صورت عمودی روی هم قرار گرفته‌اند. می‌خواستیم به دو ناحیه اول (هدر و کنترل‌ها) ارتفاع ثابت بدهیم:

```css
header {
  height: 70px;
}

.main-controls {
  padding-bottom: 0.7rem;
  height: 170px;
}
```

با این حال، می‌خواستیم ناحیه سوم (که شامل نمونه‌های ضبط شده قابل پخش است) هر فضای باقی‌مانده را پر کند، بدون توجه به ارتفاع دستگاه. Flexbox می‌توانست راه حل باشد، اما برای چنین چیدمان ساده‌ای کمی زیاده‌روی است. در عوض، مشکل با تنظیم ارتفاع ظرف سوم برابر با 100% ارتفاع والد، منهای ارتفاع و padding دو ظرف دیگر حل شد:

```css
.sound-clips {
  box-shadow: inset 0 3px 4px rgb(0 0 0 / 70%);
  background-color: rgb(0 0 0 / 10%);
  height: calc(100% - 240px - 0.7rem);
  overflow: scroll;
}
```

### ترفند چک‌باکس برای نمایش/پنهان کردن

این ترفند قبلاً به خوبی مستند شده است، اما فکر کردیم اشاره‌ای به آن داشته باشیم. ترفند چک‌باکس از این واقعیت سوءاستفاده می‌کند که می‌توانید روی {{htmlelement("label")}} یک چک‌باکس کلیک کنید تا وضعیت علامت‌خورده/علامت‌نخورده آن تغییر کند. در Web Dictaphone این کار صفحه اطلاعات را تغذیه می‌کند که با کلیک روی نماد علامت سوال در گوشه بالا سمت راست نمایش/پنهان می‌شود. ابتدا `<label>` را به دلخواه استایل می‌دهیم، مطمئن می‌شویم که z-index کافی دارد تا همیشه بالای عناصر دیگر قرار گیرد و بنابراین قابل تمرکز/کلیک باشد:

```css
label {
  font-family: "Noto Color Emoji", emoji;
  font-size: 3rem;
  position: absolute;
  top: 2px;
  right: 3px;
  z-index: 5;
  cursor: pointer;
}
```

سپس چک‌باکس واقعی را پنهان می‌کنیم، زیرا نمی‌خواهیم رابط کاربری ما را شلوغ کند:

```css
input[type="checkbox"] {
  position: absolute;
  top: -100px;
}
```

در مرحله بعد، صفحه اطلاعات (که در یک عنصر {{htmlelement("aside")}} قرار دارد) را به دلخواه استایل می‌دهیم، موقعیت ثابت (fixed) به آن می‌دهیم تا در جریان چیدمان ظاهر نشود و روی رابط کاربری اصلی تأثیر نگذارد، آن را به موقعیت پیش‌فرض مورد نظر تبدیل می‌کنیم (translate) و یک transition برای نمایش/پنهان کردن روان به آن می‌دهیم:

```css
aside {
  position: fixed;
  top: 0;
  left: 0;
  text-shadow: 1px 1px 1px black;
  width: 100%;
  height: 100%;
  transform: translateX(100%);
  transition: 0.6s all;
  background-color: #999999;
  background-image: linear-gradient(
    to top right,
    transparent,
    rgb(0 0 0 / 50%)
  );
}
```

در آخر، یک قانون می‌نویسیم که وقتی چک‌باکس علامت‌خورده است (وقتی روی label کلیک/تمرکز می‌کنیم)، عنصر `<aside>` مجاور مقدار translate افقی خود را تغییر دهد و به آرامی در دید ظاهر شود:

```css
input[type="checkbox"]:checked ~ aside {
  transform: translateX(0);
}
```

## راه‌اندازی پایه برنامه

برای گرفتن جریان رسانه‌ای که می‌خواهیم ضبط کنیم، از `getUserMedia()` استفاده می‌کنیم. سپس از MediaStream Recording API برای ضبط جریان استفاده می‌کنیم و هر تکه ضبط شده را به منبع (source) یک عنصر {{htmlelement("audio")}} تولید شده خروجی می‌دهیم تا قابل پخش باشد.

متغیرهایی برای دکمه‌های ضبط و توقف و {{htmlelement("article")}} که شامل پخش‌کننده‌های صوتی تولید شده خواهد بود، اعلام می‌کنیم:

```js
const record = document.querySelector(".record");
const stop = document.querySelector(".stop");
const soundClips = document.querySelector(".sound-clips");
```

در نهایت برای این بخش، ساختار پایه `getUserMedia` را تنظیم می‌کنیم:

```js
if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
  console.log("getUserMedia supported.");
  navigator.mediaDevices
    .getUserMedia(
      // constraints - only audio needed for this app
      {
        audio: true,
      },
    )

    // Success callback
    .then((stream) => {})

    // Error callback
    .catch((err) => {
      console.error(`The following getUserMedia error occurred: ${err}`);
    });
} else {
  console.log("getUserMedia not supported on your browser!");
}
```

کل این بخش در یک تست پیچیده شده است که بررسی می‌کند آیا `getUserMedia` پشتیبانی می‌شود قبل از اجرای هر چیز دیگری. سپس `getUserMedia()` را فراخوانی می‌کنیم و در داخل آن تعریف می‌کنیم:

- **محدودیت‌ها (constraints)**: فقط صدا برای دیکتافون ما ضبط شود.
- **فراخوانی موفقیت (success callback)**: این کد پس از اتمام موفقیت‌آمیز فراخوانی `getUserMedia` اجرا می‌شود.
- **فراخوانی خطا/شکست (error/failure callback)**: این کد در صورت شکست فراخوانی `getUserMedia` به هر دلیلی اجرا می‌شود.

> [!NOTE]
> تمام کدهای زیر در داخل فراخوانی موفقیت `getUserMedia` قرار دارند.

## ضبط جریان رسانه

پس از اینکه `getUserMedia` با موفقیت یک جریان رسانه ایجاد کرد، یک نمونه جدید از Media Recorder با سازنده `MediaRecorder()` ایجاد می‌کنید و جریان را مستقیماً به آن می‌دهید. این نقطه ورود شما به استفاده از MediaStream Recording API است — جریان اکنون آماده است تا در یک {{domxref("Blob")}}، در فرمت رمزگذاری پیش‌فرض مرورگر شما ضبط شود.

```js
const mediaRecorder = new MediaRecorder(stream);
```

مجموعه‌ای از متدها در واسط {{domxref("MediaRecorder")}} موجود است که به شما امکان کنترل ضبط جریان رسانه را می‌دهد؛ در Web Dictaphone فقط از دو مورد استفاده می‌کنیم و به برخی رویدادها گوش می‌دهیم. ابتدا از {{domxref("MediaRecorder.start()")}} برای شروع ضبط جریان پس از فشار دادن دکمه ضبط استفاده می‌شود:

```js
record.onclick = () => {
  mediaRecorder.start();
  console.log(mediaRecorder.state);
  console.log("recorder started");
  record.style.background = "red";
  record.style.color = "black";
};
```

هنگامی که `MediaRecorder` در حال ضبط است، ویژگی {{domxref("MediaRecorder.state")}} مقدار "recording" را برمی‌گرداند.

همانطور که ضبط پیشرفت می‌کند، باید داده‌های صوتی را جمع‌آوری کنیم. با استفاده از {{domxref("mediaRecorder.dataavailable_event", "ondataavailable")}} یک رویدادگردان برای این کار ثبت می‌کنیم:

```js
let chunks = [];

mediaRecorder.ondataavailable = (e) => {
  chunks.push(e.data);
};
```

> [!NOTE]
> مرورگر رویدادهای `dataavailable` را در صورت نیاز شلیک می‌کند، اما اگر می‌خواهید مداخله کنید، می‌توانید هنگام فراخوانی متد `start()` یک برش زمانی (timeslice) نیز اضافه کنید — برای مثال `start(10000)` — تا این بازه را کنترل کنید، یا {{domxref("MediaRecorder.requestData()")}} را فراخوانی کنید تا در زمان مورد نیاز یک رویداد را راه‌اندازی کند.

در آخر، از متد {{domxref("MediaRecorder.stop()")}} برای توقف ضبط هنگام فشار دادن دکمه توقف استفاده می‌کنیم و {{domxref("Blob")}} را نهایی می‌کنیم تا برای استفاده در جای دیگر برنامه آماده شود.

```js
stop.onclick = () => {
  mediaRecorder.stop();
  console.log(mediaRecorder.state);
  console.log("recorder stopped");
  record.style.background = "";
  record.style.color = "";
};
```

توجه داشته باشید که ضبط ممکن است به طور طبیعی نیز متوقف شود اگر جریان رسانه پایان یابد (مثلاً اگر در حال گرفتن یک آهنگ بودید و آهنگ تمام شد، یا کاربر اشتراک‌گذاری میکروفون خود را متوقف کرد).

## گرفتن و استفاده از blob

وقتی ضبط متوقف می‌شود، ویژگی `state` مقدار "inactive" را برمی‌گرداند و یک رویداد stop شلیک می‌شود. ما با استفاده از {{domxref("mediaRecorder.stop_event", "onstop")}} یک رویدادگردان برای این مورد ثبت می‌کنیم و blob خود را از تمام تکه‌هایی که دریافت کرده‌ایم نهایی می‌کنیم:

```js
mediaRecorder.onstop = (e) => {
  console.log("recorder stopped");

  const clipName = prompt("Enter a name for your sound clip");

  const clipContainer = document.createElement("article");
  const clipLabel = document.createElement("p");
  const audio = document.createElement("audio");
  const deleteButton = document.createElement("button");

  clipContainer.classList.add("clip");
  audio.setAttribute("controls", "");
  deleteButton.textContent = "Delete";
  clipLabel.textContent = clipName;

  clipContainer.appendChild(audio);
  clipContainer.appendChild(clipLabel);
  clipContainer.appendChild(deleteButton);
  soundClips.appendChild(clipContainer);

  const blob = new Blob(chunks, { type: "audio/ogg; codecs=opus" });
  chunks = [];
  const audioURL = window.URL.createObjectURL(blob);
  audio.src = audioURL;

  deleteButton.onclick = (e) => {
    let evtTgt = e.target;
    evtTgt.parentNode.parentNode.removeChild(evtTgt.parentNode);
  };
};
```

بیایید کد بالا را مرور کنیم و ببینیم چه اتفاقی می‌افتد.

ابتدا، یک اعلان (prompt) نمایش می‌دهیم که از کاربر می‌خواهد نام کلیپ خود را وارد کند.

سپس، یک ساختار HTML مانند زیر ایجاد می‌کنیم و آن را در ظرف کلیپ خود که یک عنصر {{htmlelement("article")}} است، قرار می‌دهیم.

```html
<article class="clip">
  <audio controls></audio>
  <p>your clip name</p>
  <button>Delete</button>
</article>
```

پس از آن، یک {{domxref("Blob")}} ترکیبی از تکه‌های صوتی ضبط شده ایجاد می‌کنیم و با استفاده از `window.URL.createObjectURL(blob)` یک URL شیء (object URL) به آن ایجاد می‌کنیم. سپس مقدار ویژگی [`src`](/en-US/docs/Web/HTML/Reference/Elements/audio#src) عنصر {{HTMLElement("audio")}} را به این object URL تنظیم می‌کنیم، به طوری که وقتی دکمه پخش روی پخش‌کننده صوتی فشرده شود، آن `Blob` را پخش کند.

در نهایت، یک رویدادگردان `onclick` روی دکمه حذف تنظیم می‌کنیم که تابعی است که کل ساختار HTML کلیپ را حذف می‌کند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- صفحه اصلی [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaDevices.getUserMedia()")}}