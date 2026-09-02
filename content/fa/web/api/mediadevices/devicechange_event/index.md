---
title: "MediaDevices: devicechange event"
short-title: devicechange
slug: Web/API/MediaDevices/devicechange_event
page-type: web-api-event
browser-compat: api.MediaDevices.devicechange_event
---

{{APIRef("Media Capture and Streams")}}{{SecureContext_Header}}

رویداد **`devicechange`** هر زمان که یک دستگاه رسانه‌ای مانند دوربین، میکروفون یا بلندگو به سیستم متصل یا از آن جدا شود، به یک نمونهٔ {{domxref("MediaDevices")}} ارسال می‌شود.

این رویداد قابل لغو (cancelable) نیست و حباب نمی‌زند (bubble نمی‌کند).

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("devicechange", (event) => { })

ondevicechange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

در این مثال، تابعی به نام `updateDeviceList()` می‌سازیم که ابتدا یک بار، وقتی {{domxref("MediaDevices.getUserMedia()")}} با موفقیت یک جریان (stream) دریافت می‌کند، فراخوانی می‌شود و سپس هر بار که فهرست دستگاه‌ها تغییر کند، مجدداً فراخوانی می‌شود. این تابع در پنجرهٔ مرورگر دو فهرست نمایش می‌دهد: یکی فهرست دستگاه‌های صوتی و دیگری فهرست دستگاه‌های ویدیویی، که در هر دو، برچسب (نام) دستگاه و ورودی یا خروجی بودن آن نشان داده می‌شود. از آنجا که این مثال یک کنترل‌کننده برای رویداد `devicechange` فراهم کرده است، هر بار که یک دستگاه رسانه‌ای به دستگاهی که نمونه در آن اجرا می‌شود متصل یا از آن جدا شود، فهرست به‌روزرسانی می‌شود.

```html hidden
<p>Click the start button below to begin the demonstration.</p>
<div id="startButton" class="button">Start</div>
<video id="video" width="160" height="120" autoplay></video><br />

<div class="left">
  <h2>Audio devices:</h2>
  <ul class="deviceList" id="audioList"></ul>
</div>
<div class="right">
  <h2>Video devices:</h2>
  <ul class="deviceList" id="videoList"></ul>
</div>

<output></output>
```

```css hidden
body {
  font:
    14px "Open Sans",
    "Arial",
    sans-serif;
}

video {
  margin-top: 20px;
  border: 1px solid black;
}

.button {
  cursor: pointer;
  width: 160px;
  border: 1px solid black;
  font-size: 16px;
  text-align: center;
  padding-top: 2px;
  padding-bottom: 4px;
  color: white;
  background-color: darkgreen;
}

h2 {
  margin-bottom: 4px;
}

.left {
  float: left;
  width: 48%;
  margin-right: 2%;
}

.right {
  float: right;
  width: 48%;
  margin-left: 2%;
}

.deviceList {
  border: 1px solid black;
  list-style-type: none;
  margin-top: 2px;
  padding: 6px;
}
```

```js hidden
// UI elements
const videoElement = document.querySelector("#video");
const logElement = document.querySelector("output");
const startButton = document.querySelector("#startButton");

function log(msg) {
  logElement.innerText += `${msg}\n`;
}

startButton.addEventListener("click", () => {
  const constraints = {
    video: {
      width: 160,
      height: 120,
      frameRate: 30,
    },
    audio: {
      sampleRate: 44100,
      sampleSize: 16,
      volume: 0.25,
    },
  };

  navigator.mediaDevices
    .getUserMedia(constraints)
    .then((stream) => {
      videoElement.srcObject = stream;
      updateDeviceList();
    })
    .catch((err) => {
      log(`${err.name}: ${err.message}`);
    });
});
```

متغیرهای سراسری‌ای تعریف می‌کنیم که ارجاع‌هایی به عناصر {{HTMLElement("ul")}} نگه می‌دارند؛ عناصری که برای فهرست کردن دستگاه‌های صوتی و ویدیویی استفاده می‌شوند:

```js
const audioList = document.getElementById("audioList");
const videoList = document.getElementById("videoList");
```

### دریافت و رسم فهرست دستگاه‌ها

حالا بیایید خودِ `updateDeviceList()` را بررسی کنیم. این روش هر بار که بخواهیم فهرست کنونی دستگاه‌های رسانه‌ای را دریافت کرده و سپس فهرست‌های نمایش‌داده‌شدهٔ دستگاه‌های صوتی و ویدیویی را با استفاده از آن اطلاعات به‌روزرسانی کنیم، فراخوانی می‌شود.

`updateDeviceList()` صرفاً از یک فراخوانی به تابع {{domxref("MediaDevices.enumerateDevices", "enumerateDevices()")}} روی شیء {{domxref("MediaDevices")}} که در ویژگی {{domxref("navigator.mediaDevices")}} ارجاع داده شده است، و همچنین کدی که هنگام برآورده شدن (fulfilled) {{jsxref("Promise")}} برگشتی از `enumerateDevices()` اجرا می‌شود، تشکیل شده است. کنترل‌کنندهٔ برآورده شدن وقتی فراخوانی می‌شود که فهرست دستگاه‌ها آماده باشد. فهرست به‌صورت آرایه‌ای از اشیاء {{domxref("MediaDeviceInfo")}} به کنترل‌کنندهٔ برآورده شدن پاس داده می‌شود که هر کدام یک دستگاه ورودی یا خروجی رسانه‌ای را توصیف می‌کنند.

برای پیمایش همهٔ دستگاه‌ها از یک حلقهٔ {{jsxref("Array.forEach", "forEach()")}} استفاده می‌شود. برای هر دستگاه، یک شیء {{HTMLElement("li")}} جدید می‌سازیم که برای نمایش آن به کاربر استفاده می‌شود.

خط `let [kind, type, direction] = device.kind.match(/(\w+)(input|output)/i);` شایستهٔ توجه ویژه است. این خط از [تخصیص ساختارشکن (destructuring assignment)](/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring) استفاده می‌کند تا مقادیر سه آیتم نخست آرایهٔ برگشتی از {{jsxref("String.match()")}} را به متغیرهای `kind`، `type` و `direction` تخصیص دهد. دلیل این کار آن است که مقدار {{domxref("MediaDeviceInfo.kind")}} یک رشتهٔ واحد است که هم نوع رسانه و هم جهت جریان رسانه را شامل می‌شود؛ مانند `"audioinput"` یا `"videooutput"`. بنابراین این خط، نوع ("audio" یا "video") و جهت ("input" یا "output") را جدا می‌کند تا بتوان از آن‌ها برای ساخت رشتهٔ نمایش‌داده‌شده در فهرست استفاده کرد.

پس از ساخته‌شدن رشته — که نام دستگاه را به‌صورت پررنگ و جهت را داخل پرانتز دربردارد — با فراخوانی {{domxref("Node.appendChild", "appendChild()")}} روی `audioList` یا `videoList`، بسته به نوع دستگاه، به فهرست مناسب افزوده می‌شود.

### مدیریت تغییرات فهرست دستگاه‌ها

`updateDeviceList()` را در دو مکان فراخوانی می‌کنیم. مکان نخست، در کنترل‌کنندهٔ برآورده شدن وعدهٔ (promise) {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} است تا در ابتدا، وقتی جریان باز می‌شود، فهرست پر شود. مکان دوم، در کنترل‌کنندهٔ رویدادِ `devicechange` است:

```js
navigator.mediaDevices.ondevicechange = (event) => {
  updateDeviceList();
};
```

با قرار گرفتن این کد، هر بار که کاربر یک دوربین، میکروفون یا دستگاه رسانه‌ای دیگر را وصل کند یا یکی از آن‌ها را روشن یا خاموش کند، `updateDeviceList()` را فراخوانی می‌کنیم تا فهرست دستگاه‌های متصل دوباره ترسیم شود.

### نتیجه

{{ EmbedLiveSample('Example', 600, 460, "", "", "", "camera;microphone") }}

## توصیه‌نامه‌ها

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}