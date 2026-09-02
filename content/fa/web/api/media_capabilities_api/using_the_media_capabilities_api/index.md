---
title: "Using the Media Capabilities API"
slug: Web/API/Media_Capabilities_API/Using_the_Media_Capabilities_API
page-type: guide
browser-compat: api.MediaCapabilities
---

{{DefaultAPISidebar("Media Capabilities API")}}

[API قابلیت‌های رسانه](/en-US/docs/Web/API/Media_Capabilities_API) به شما امکان می‌دهد از مرورگر بپرسید که آیا می‌تواند رسانه را با مجموعه‌ای مشخص از پارامترهای کدگذاری رمزگشایی یا رمزگذاری کند. این پارامترها می‌توانند شامل کدک‌ها، وضوح تصویر، نرخ بیت، نرخ فریم و جزئیات مشابه باشند.

با API قابلیت‌های رسانه، نه تنها می‌توانید تعیین کنید که آیا مرورگر از یک قالب خاص پشتیبانی می‌کند، بلکه می‌توانید بفهمید که آیا این کار را به‌طور کارآمد و روان انجام می‌دهد. به طور خلاصه، این API جایگزین و بهبود یافته‌ای برای متد {{domxref("MediaSource.isTypeSupported_static", "isTypeSupported()")}} در {{domxref("MediaSource")}} یا متد {{domxref("HTMLMediaElement.canPlayType","canPlayType()")}} در {{domxref("HTMLMediaElement")}} است.

## رابط MediaCapabilities

رابط {{domxref("MediaCapabilities")}} از طریق ویژگی {{domxref("Navigator.mediaCapabilities", "mediaCapabilities")}} در دسترس است که هم در شیء `navigator` و هم در شیء {{domxref("WorkerNavigator")}} تعریف شده است؛ به عبارت دیگر، API قابلیت‌های رسانه هم در نخ اصلی و هم در workerها در دسترس است.

اگر این شیء وجود داشته باشد، API قابلیت‌های رسانه در دسترس است. بنابراین می‌توانید وجود API را به این صورت بررسی کنید:

```js
if ("mediaCapabilities" in navigator) {
  // mediaCapabilities در دسترس است
} else {
  // mediaCapabilities در دسترس نیست
}
```

برای مثال، برای به‌دست آوردن اطلاعات درباره قابلیت‌های رمزگشایی ویدئو، یک پیکربندی رمزگشایی ویدئو ایجاد می‌کنید و آن را به عنوان پارامتر به متد {{domxref("MediaCapabilities.decodingInfo()")}} می‌دهید. این متد یک promise برمی‌گرداند که با اطلاعاتی درباره قابلیت‌های رسانه، از جمله اینکه آیا ویدئو قابل رمزگشایی است و آیا رمزگشایی روان و کم‌مصرف خواهد بود، تکمیل می‌شود. همچنین می‌توانید رمزگشایی صدا و رمزگذاری ویدئو و صدا را آزمایش کنید.

### ایجاد یک پیکربندی رمزگشایی ویدئو

متد {{domxref("MediaCapabilities.decodingInfo()")}} یک پیکربندی رمزگشایی رسانه را به عنوان پارامتر می‌گیرد.

در مثال ما، قابلیت‌های رمزگشایی یک پیکربندی ویدئو را آزمایش می‌کنیم. این پیکربندی به نوع رسانه‌ای که آزمایش می‌شود (مثلاً یک `file` ساده یا {{domxref("MediaSource")}}) و یک شیء پیکربندی ویدئو نیاز دارد که شامل مقادیر `contentType`، `width`، `height`، `bitrate` و `framerate` باشد:

- `contentType` باید یک رشته باشد که یک [نوع MIME ویدئوی معتبر](/en-US/docs/Web/Media/Guides/Formats/Video_codecs) را مشخص کند.
- `width` و `height` ابعاد افقی و عمودی ویدئو هستند؛ همچنین برای تعیین {{glossary("aspect ratio")}} (نسبت تصویر) استفاده می‌شوند.
- `bitrate` تعداد بیت‌هایی است که برای رمزگذاری یک ثانیه از ویدئو استفاده می‌شود.
- `framerate` تعداد فریم‌هایی است که در هر ثانیه هنگام پخش ویدئو نمایش داده می‌شود.

```js
const videoConfiguration = {
  type: "file",
  video: {
    contentType: "video/webm;codecs=vp8",
    width: 800,
    height: 600,
    bitrate: 10000,
    framerate: 15,
  },
};
```

اگر قابلیت رمزگشایی یک فایل صوتی را بررسی می‌کردیم، یک پیکربندی صوتی شامل تعداد کانال‌ها و نرخ نمونه‌برداری ایجاد می‌کردیم و ویژگی‌هایی که فقط به ویدئو مربوط می‌شوند (یعنی ابعاد و نرخ فریم) را حذف می‌کردیم:

```js
const audioConfiguration = {
  type: "file",
  audio: {
    contentType: "audio/ogg",
    channels: 2,
    bitrate: 132700,
    samplerate: 5200,
  },
};
```

اگر قابلیت‌های رمزگذاری را آزمایش می‌کردیم، یک پیکربندی کمی متفاوت ایجاد می‌کردیم. در این حالت، نوع رسانه‌ای که آزمایش می‌شود یا `record` (برای ضبط رسانه، یعنی شیء {{domxref("MediaRecorder")}}) است یا `transmission` (برای رسانه‌ای که از طریق وسایل الکترونیکی مانند [`RTCPeerConnection`](/en-US/docs/Web/API/RTCPeerConnection) منتقل می‌شود) — به علاوه یک پیکربندی صوتی یا ویدئویی همانطور که در بالا توضیح داده شد.

### پرس‌وجو از مرورگر درباره قابلیت‌های رمزگشایی

حالا که یک پیکربندی رمزگشایی ویدئو ایجاد کرده‌ایم، می‌توانیم آن را به عنوان پارامتر متد {{domxref("MediaCapabilities.decodingInfo", "decodingInfo()")}} ارسال کنیم تا مشخص شود آیا ویدئویی با این پیکربندی قابل رمزگشایی است و آیا پخش آن روان و کم‌مصرف خواهد بود.

```js
let promise = navigator.mediaCapabilities.decodingInfo(videoConfiguration);
```

متدهای `decodingInfo()` و {{domxref("MediaCapabilities.encodingInfo", "encodingInfo()")}} هر دو promise برمی‌گردانند. پس از تکمیل شدن state promise، می‌توانید به ویژگی‌های `supported`، `smooth` و `powerEfficient` از شیء برگشتی دسترسی پیدا کنید.

### مدیریت پاسخ

به جای نسبت دادن promise به یک متغیر، می‌توانیم مقادیر برگشتی promise را در کنسول چاپ کنیم:

```js
navigator.mediaCapabilities.decodingInfo(videoConfiguration).then((result) => {
  console.log(
    `This configuration is ${result.supported ? "" : "not "}supported,`,
  );
  console.log(`${result.smooth ? "" : "not "}smooth, and`);
  console.log(`${result.powerEfficient ? "" : "not "}power efficient.`);
});
```

## مدیریت خطاها

در مثال رمزگشایی ویدئوی ما، اگر پیکربندی رسانه‌ای که به متد {{domxref("MediaCapabilities.decodingInfo", "decodingInfo()")}} ارسال شده نامعتبر باشد، یک {{jsxref("TypeError")}} پرتاب می‌شود. دلایل مختلفی برای بروز خطا وجود دارد، از جمله:

- `type` مشخص‌شده یکی از دو مقدار مجاز (`file` یا `media-source`) نباشد.
- `contentType` داده‌شده یک نوع MIME کدک معتبر نباشد.

خطا می‌تواند به دلیل `type` نبودن یکی از دو مقدار ممکن، `contentType` نبودن یک نوع MIME کدک معتبر، یا تعریف‌های نامعتبر یا حذف‌شده در شیء پیکربندی ویدئو رخ دهد.

```js
navigator.mediaCapabilities
  .decodingInfo(videoConfiguration)
  .then(() => console.log("It worked"))
  .catch((error) => console.error(`It failed: ${error}`));
```

## مثال زنده قابلیت‌های رسانه

### CSS

```css
li {
  margin: 1em;
}
```

### HTML

```html
<form>
  <p>
    Select your video configuration and find out if this browser supports the
    codec, and whether decoding will be smooth and power efficient:
  </p>
  <ul>
    <li>
      <label for="codec">Select a codec</label>
      <select id="codec">
        <option>video/webm; codecs=vp8</option>
        <option>video/webm; codecs=vp9</option>
        <option>video/mp4; codecs=avc1</option>
        <option>video/mp4; codecs=avc1.420034</option>
        <option>invalid</option>
      </select>
    </li>
    <li>
      <label for="size">Select a size</label>
      <select id="size">
        <option>7680x4320</option>
        <option>3840x2160</option>
        <option>2560x1440</option>
        <option>1920x1080</option>
        <option>1280x720</option>
        <option selected>800x600</option>
        <option>640x480</option>
        <option>320x240</option>
        <option value=" x ">none</option>
      </select>
    </li>
    <li>
      <label for="framerate">Select a framerate</label>
      <select id="framerate">
        <option>60</option>
        <option>50</option>
        <option>30</option>
        <option>24</option>
        <option selected>15</option>
      </select>
    </li>
    <li>
      <label for="bitrate">Select a bitrate</label>
      <select id="bitrate">
        <option>4000</option>
        <option>2500</option>
        <option>800</option>
      </select>
    </li>
  </ul>
  <p>
    <input type="button" value="Test this Video Configuration" id="try-it" />
  </p>
</form>

<ul id="results"></ul>
```

### JavaScript

```js
let mc = {
  videoConfiguration: {},

  tryIt() {
    mc.createConfiguration();
    mc.testIt();
  },

  createConfiguration() {
    const size = document.getElementById("size").value.split("x");
    mc.videoConfiguration = {
      type: "file",
      video: {
        contentType: document.getElementById("codec").value,
        width: size[0],
        height: size[1],
        bitrate: document.getElementById("bitrate").value,
        framerate: document.getElementById("framerate").value,
      },
    };
  },

  testIt() {
    let content = "";
    navigator.mediaCapabilities
      .decodingInfo(mc.videoConfiguration)
      .then((result) => {
        const li = document.createElement("li"),
          mcv = mc.videoConfiguration.video;
        content = `A ${mcv.width}x${mcv.height}, ${mcv.contentType} at ${
          mcv.framerate
        }fps and ${mcv.bitrate} bps video ${
          result.supported ? " IS " : "IS NOT "
        } supported,`;
        content += `${result.smooth ? " IS " : " is NOT "} smooth, and`;
        content += `${
          result.powerEfficient ? " IS " : " IS NOT "
        }power efficient.`;
        const ul = document.getElementById("results");
        li.textContent = content;
        ul.appendChild(li);
      })
      .catch((error) => {
        const li = document.createElement("li"),
          ul = document.getElementById("results");
        li.textContent = `Codec ${mc.videoConfiguration.video.contentType} threw an error: ${error}`;
        ul.appendChild(li);
      });
  },
};

document.getElementById("try-it").addEventListener("click", mc.tryIt);
```

### نتیجه زنده

{{EmbedLiveSample('Media_Capabilities_live_example', '100%', '400')}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("navigator.mediaCapabilities")}}