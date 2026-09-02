---
title: Capabilities, constraints, and settings
slug: Web/API/Media_Capture_and_Streams_API/Constraints
page-type: guide
browser-compat: api.MediaDevices.getSupportedConstraints
---

{{DefaultAPISidebar("Media Capture and Streams")}}

این مقاله به بررسی مفاهیم دوقلوی **محدودیت‌ها** (constraints) و **قابلیت‌ها** (capabilities) به همراه تنظیمات رسانه می‌پردازد و شامل یک نمونه به نام [Constraint Exerciser](#example_constraint_exerciser) (تمرین‌گر محدودیت‌ها) است. تمرین‌گر محدودیت‌ها به شما امکان می‌دهد نتایج اعمال مجموعه‌های مختلف محدودیت بر روی track‌های صوتی و تصویری که از دستگاه‌های ورودی A/V رایانه (مانند وب‌کم و میکروفون) می‌آیند، آزمایش کنید.

از نظر تاریخی، نوشتن اسکریپت‌هایی برای وب که با Web API‌ها کار نزدیکی دارند، چالش شناخته‌شده‌ای داشته است: اغلب کد شما باید بداند که آیا یک API وجود دارد یا خیر و اگر وجود دارد، محدودیت‌های آن در {{Glossary("user agent")}} (عامل کاربر) که روی آن اجرا می‌شود چیست. فهمیدن این موضوع اغلب دشوار بوده و معمولاً شامل نگاه کردن به ترکیبی از اینکه روی کدام {{Glossary("user agent")}} (یا مرورگر) اجرا می‌شوید، چه نسخه‌ای است، بررسی وجود اشیاء خاص، تلاش برای دیدن اینکه آیا چیزهای مختلف کار می‌کنند یا نه و تعیین خطاهای رخ داده، و غیره بوده است. نتیجه کدهای بسیار شکننده یا اتکا به کتابخانه‌هایی است که این مسائل را برای شما حل می‌کنند و سپس {{Glossary("polyfill", "polyfill‌ها")}} را برای پر کردن شکاف‌های پیاده‌سازی از طرف شما پیاده‌سازی می‌کنند.

قابلیت‌ها و محدودیت‌ها به مرورگر و وب‌سایت یا برنامه اجازه می‌دهند تا اطلاعاتی را در مورد اینکه چه **ویژگی‌های قابل محدودیت** (constrainable properties) توسط پیاده‌سازی مرورگر پشتیبانی می‌شود و چه مقادیری برای هر یک پشتیبانی می‌کند، مبادله کنند.

## مرور کلی

فرآیند به این صورت کار می‌کند (با استفاده از {{domxref("MediaStreamTrack")}} به عنوان مثال):

1. در صورت نیاز، {{domxref("MediaDevices.getSupportedConstraints()")}} را فراخوانی کنید تا لیست **محدودیت‌های پشتیبانی‌شده** را دریافت کنید، که به شما می‌گوید مرورگر چه ویژگی‌های قابل محدودیتی را می‌شناسد. این همیشه ضروری نیست، زیرا هر ویژگی که ناشناخته باشد هنگام مشخص کردن نادیده گرفته می‌شود - اما اگر ویژگی‌ای دارید که بدون آن نمی‌توانید کار کنید، می‌توانید با بررسی اینکه در لیست وجود دارد شروع کنید.
2. پس از اینکه اسکریپت فهمید آیا ویژگی یا ویژگی‌هایی که می‌خواهد استفاده کند پشتیبانی می‌شوند یا نه، می‌تواند **قابلیت‌های** API و پیاده‌سازی آن را با بررسی شیء برگشتی از متد `getCapabilities()` track بررسی کند. این شیء هر محدودیت پشتیبانی‌شده و مقادیر یا محدوده مقادیری که پشتیبانی می‌شوند را لیست می‌کند.
3. در نهایت، متد `applyConstraints()` track برای پیکربندی API به دلخواه با مشخص کردن مقادیر یا محدوده مقادیری که می‌خواهید برای هر یک از ویژگی‌های قابل محدودیتی که ترجیح دارید استفاده شود، فراخوانی می‌شود.
4. متد `getConstraints()` track مجموعه محدودیت‌هایی را که در آخرین فراخوانی به `applyConstraints()` ارسال شده است، برمی‌گرداند. این ممکن است وضعیت فعلی واقعی track را نشان ندهد، به دلیل ویژگی‌هایی که مقادیر درخواستی آنها باید تنظیم می‌شد و به این دلیل که مقادیر پیش‌فرض پلتفرم نشان داده نمی‌شوند. برای نمایش کامل پیکربندی فعلی track، از `getSettings()` استفاده کنید.

در Media Capture and Streams API، هر دو {{domxref("MediaStream")}} و {{domxref("MediaStreamTrack")}} دارای ویژگی‌های قابل محدودیت هستند.

## تعیین اینکه آیا یک محدودیت پشتیبانی می‌شود

اگر نیاز دارید بدانید که آیا یک محدودیت خاص توسط user agent پشتیبانی می‌شود یا نه، می‌توانید با فراخوانی {{domxref("MediaDevices.getSupportedConstraints", "navigator.mediaDevices.getSupportedConstraints()")}} لیستی از ویژگی‌های قابل محدودیتی که مرورگر می‌شناسد دریافت کنید، به این شکل:

```js
const supported = navigator.mediaDevices.getSupportedConstraints();

document.getElementById("frameRateSlider").disabled = !supported["frameRate"];
```

در این مثال، محدودیت‌های پشتیبانی‌شده واکشی می‌شوند و یک کنترل که به کاربر اجازه می‌دهد نرخ فریم را پیکربندی کند، در صورتی که محدودیت `frameRate` پشتیبانی نشود، غیرفعال می‌شود.

## نحوه تعریف محدودیت‌ها

یک محدودیت منفرد شیئی است که نام آن با نام ویژگی قابل محدودیتی که مقدار یا محدوده مقادیر مورد نظر برای آن مشخص می‌شود مطابقت دارد. این شیء شامل صفر یا چند محدودیت منفرد و همچنین یک زیر-شیء اختیاری به نام `advanced` است که شامل مجموعه دیگری از صفر یا چند محدودیت است که user agent باید در صورت امکان آنها را برآورده کند. user agent سعی می‌کند محدودیت‌ها را به ترتیب مشخص شده در مجموعه محدودیت برآورده کند.

مهمترین نکته‌ای که باید درک کنید این است که بیشتر محدودیت‌ها الزام نیستند؛ بلکه درخواست هستند. استثناهایی وجود دارد که به زودی به آنها می‌پردازیم.

### درخواست یک مقدار مشخص برای یک تنظیم

بیشتر محدودیت‌ها می‌توانند یک مقدار خاص باشند که نشان‌دهنده مقدار مورد نظر برای آن تنظیم است. برای مثال:

```js
const constraints = {
  width: 1920,
  height: 1080,
  aspectRatio: 1.777777778,
};

myTrack.applyConstraints(constraints);
```

در این حالت، محدودیت‌ها نشان می‌دهند که برای تقریباً همه ویژگی‌ها هر مقداری قابل قبول است، اما اندازه ویدیوی با کیفیت بالا (HD) استاندارد با {{glossary("aspect ratio")}} (نسبت تصویر) استاندارد 16:9 مورد نظر است. هیچ تضمینی وجود ندارد که track حاصل با هیچ‌یک از اینها مطابقت داشته باشد، اما user agent باید تمام تلاش خود را برای تطبیق هرچه بیشتر انجام دهد.

اولویت‌بندی ویژگی‌ها ساده است: اگر مقادیر درخواستی دو ویژگی متقابلاً منحصر به فرد باشند، ویژگی‌ای که ابتدا در مجموعه محدودیت ذکر شده است استفاده می‌شود. به عنوان مثال، اگر مرورگری که کد بالا را اجرا می‌کند نتواند یک track 1920x1080 ارائه دهد اما بتواند 1920x900 ارائه دهد، آنگاه آن ارائه خواهد شد.

محدودیت‌های ساده مانند اینها که یک مقدار واحد را مشخص می‌کنند، همیشه به عنوان غیرالزامی در نظر گرفته می‌شوند. user agent سعی می‌کند آنچه را که درخواست می‌کنید ارائه دهد اما تضمین نمی‌کند که آنچه دریافت می‌کنید مطابقت داشته باشد. با این حال، اگر از مقادیر ساده برای ویژگی‌ها هنگام فراخوانی {{domxref("MediaStreamTrack.applyConstraints()")}} استفاده کنید، درخواست همیشه موفق خواهد بود، زیرا این مقادیر به عنوان یک درخواست در نظر گرفته می‌شوند، نه یک الزام.

### مشخص کردن یک محدوده از مقادیر

گاهی اوقات، هر مقداری در یک محدوده برای مقدار یک ویژگی قابل قبول است. می‌توانید محدوده‌ها را با مقادیر حداقل و/یا حداکثر مشخص کنید، و حتی می‌توانید یک مقدار ایده‌آل در محدوده تعیین کنید، اگر بخواهید. اگر یک مقدار ایده‌آل ارائه دهید، مرورگر سعی می‌کند تا حد امکان به آن مقدار نزدیک شود، با توجه به سایر محدودیت‌های مشخص شده.

```js
const supports = navigator.mediaDevices.getSupportedConstraints();

if (
  !supports["width"] ||
  !supports["height"] ||
  !supports["frameRate"] ||
  !supports["facingMode"]
) {
  // ویژگی‌های مورد نیاز وجود ندارند، بنابراین خطا را مدیریت کنید.
} else {
  const constraints = {
    width: { min: 640, ideal: 1920, max: 1920 },
    height: { min: 400, ideal: 1080 },
    aspectRatio: 1.777777778,
    frameRate: { max: 30 },
    facingMode: { exact: "user" },
  };

  myTrack
    .applyConstraints(constraints)
    .then(() => {
      /* اگر محدودیت‌ها با موفقیت اعمال شوند، کارهای لازم را انجام دهید */
    })
    .catch((reason) => {
      /* اعمال محدودیت‌ها ناموفق بود؛ دلیل آن reason است */
    });
}
```

در اینجا، پس از اطمینان از اینکه ویژگی‌های قابل محدودیتی که باید مطابقت پیدا کنند پشتیبانی می‌شوند (`width`، `height`، `frameRate` و `facingMode`)، محدودیت‌هایی را تنظیم می‌کنیم که عرضی نه کمتر از 640 و نه بیشتر از 1920 (اما ترجیحاً 1920)، ارتفاعی نه کمتر از 400 (اما ایده‌آل 1080)، نسبت تصویر 16:9 (1.777777778) و نرخ فریمی حداکثر 30 فریم در ثانیه را درخواست می‌کنند. علاوه بر این، تنها دستگاه ورودی قابل قبول دوربینی است که رو به کاربر است (یک "selfie cam"). اگر محدودیت‌های `width`، `height`، `frameRate` یا `facingMode` قابل برآورده شدن نباشند، promise برگشتی از `applyConstraints()` رد خواهد شد.

> [!NOTE]
> محدودیت‌هایی که با استفاده از هر یک یا همه `max`، `min` یا `exact` مشخص می‌شوند، همیشه به عنوان اجباری در نظر گرفته می‌شوند. اگر هر محدودیتی که از یک یا چند مورد از اینها استفاده می‌کند هنگام فراخوانی `applyConstraints()` قابل برآورده شدن نباشد، promise رد خواهد شد.

### محدودیت‌های پیشرفته

به اصطلاح محدودیت‌های پیشرفته با افزودن یک ویژگی `advanced` به مجموعه محدودیت ایجاد می‌شوند؛ مقدار این ویژگی آرایه‌ای از مجموعه‌های محدودیت اضافی است که اختیاری در نظر گرفته می‌شوند. موارد استفاده کمی برای این ویژگی وجود دارد یا اصلاً وجود ندارد و برخی علاقه به حذف آن از مشخصات نشان داده‌اند، بنابراین در اینجا بحث نخواهد شد. اگر مایل به یادگیری بیشتر هستید، به [بخش 11 از مشخصات Media Capture and Streams](https://w3c.github.io/mediacapture-main/#constrainable-interface)، مثال 2 گذشته مراجعه کنید.

## بررسی قابلیت‌ها

می‌توانید {{domxref("MediaStreamTrack.getCapabilities()")}} را فراخوانی کنید تا لیستی از تمام قابلیت‌های پشتیبانی‌شده و مقادیر یا محدوده مقادیری که هر کدام در پلتفرم و user agent فعلی می‌پذیرند دریافت کنید. این تابع یک شیء برمی‌گرداند که هر ویژگی قابل محدودیت پشتیبانی‌شده توسط مرورگر و یک مقدار یا محدوده مقادیری که برای هر یک از آن ویژگی‌ها پشتیبانی می‌شود را لیست می‌کند.

به عنوان مثال، قطعه کد زیر منجر به درخواست اجازه از کاربر برای دسترسی به دوربین و میکروفون محلی می‌شود. پس از اعطای مجوز، اشیاء `MediaTrackCapabilities` در کنسول ثبت می‌شوند که جزئیات قابلیت‌های هر {{domxref("MediaStreamTrack")}} را نشان می‌دهد:

```js
navigator.mediaDevices
  .getUserMedia({ video: true, audio: true })
  .then((stream) => {
    const tracks = stream.getTracks();
    tracks.map((t) => console.log(t.getCapabilities()));
  });
```

یک مثال از شیء قابلیت‌ها به این شکل است:

```json
{
  "autoGainControl": [true, false],
  "channelCount": {
    "max": 1,
    "min": 1
  },
  "deviceId": "jjxEMqxIhGdryqbTjDrXPWrkjy55Vte70kWpMe3Lge8=",
  "echoCancellation": [true, false],
  "groupId": "o2tZiEj4MwOdG/LW3HwkjpLm1D8URat4C5kt742xrVQ=",
  "noiseSuppression": [true, false]
}
```

محتوای دقیق شیء به مرورگر و سخت‌افزار رسانه بستگی دارد.

## اعمال محدودیت‌ها

اولین و رایج‌ترین راه برای استفاده از محدودیت‌ها، مشخص کردن آنها هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} است:

```js
navigator.mediaDevices
  .getUserMedia({
    video: {
      width: { min: 640, ideal: 1920 },
      height: { min: 400, ideal: 1080 },
      aspectRatio: { ideal: 1.7777777778 },
    },
    audio: {
      sampleSize: 16,
      channelCount: 2,
    },
  })
  .then((stream) => {
    videoElement.srcObject = stream;
  })
  .catch(handleError);
```

در این مثال، محدودیت‌ها در زمان `getUserMedia()` اعمال می‌شوند و مجموعه‌ای ایده‌آل از گزینه‌ها با گزینه‌های جایگزین برای ویدیو درخواست می‌شود.

> [!NOTE]
> می‌توانید یک یا چند شناسه دستگاه ورودی رسانه را مشخص کنید تا محدودیت‌هایی در مورد اینکه کدام منابع ورودی مجاز هستند ایجاد کنید. برای جمع‌آوری لیست دستگاه‌های موجود، می‌توانید {{domxref("MediaDevices.enumerateDevices", "navigator.mediaDevices.enumerateDevices()")}} را فراخوانی کنید، سپس برای هر دستگاهی که معیارهای مورد نظر را برآورده می‌کند، `deviceId` آن را به شیء `MediaConstraints` که در نهایت به `getUserMedia()` ارسال می‌شود اضافه کنید.

همچنین می‌توانید محدودیت‌های یک {{domxref("MediaStreamTrack")}} موجود را در حال اجرا تغییر دهید، با فراخوانی متد {{domxref("MediaStreamTrack.applyConstraints", "applyConstraints()")}} track و ارسال یک شیء به آن که نشان‌دهنده محدودیت‌هایی است که می‌خواهید به track اعمال کنید:

```js
videoTrack.applyConstraints({
  width: 1920,
  height: 1080,
});
```

در این قطعه، track ویدیویی که توسط `videoTrack` ارجاع داده شده است به‌روزرسانی می‌شود تا وضوح آن تا حد امکان نزدیک به 1920x1080 پیکسل (1080p با کیفیت بالا) باشد.

## بازیابی محدودیت‌ها و تنظیمات فعلی

مهم است که تفاوت بین **محدودیت‌ها** (constraints) و **تنظیمات** (settings) را به خاطر بسپارید. محدودیت‌ها راهی برای مشخص کردن مقادیری هستند که نیاز دارید، می‌خواهید و مایل به پذیرش آنها برای ویژگی‌های قابل محدودیت مختلف هستید (همانطور که در مستندات {{domxref("MediaTrackConstraints")}} توضیح داده شده است)، در حالی که تنظیمات مقادیر واقعی هر ویژگی قابل محدودیت در زمان حال هستند.

### دریافت محدودیت‌های در حال اجرا

اگر در هر زمانی نیاز به واکشی مجموعه محدودیت‌هایی دارید که در حال حاضر به رسانه اعمال شده‌اند، می‌توانید آن اطلاعات را با فراخوانی {{domxref("MediaStreamTrack.getConstraints()")}} دریافت کنید، همانطور که در مثال زیر نشان داده شده است.

```js
function switchCameras(track, camera) {
  const constraints = track.getConstraints();
  constraints.facingMode = camera;
  track.applyConstraints(constraints);
}
```

این تابع یک {{domxref("MediaStreamTrack")}} و یک رشته که نشان‌دهنده حالت دوربین مورد استفاده است می‌پذیرد، محدودیت‌های فعلی را واکشی می‌کند، مقدار {{domxref("MediaTrackConstraints.facingMode")}} را به مقدار مشخص شده تنظیم می‌کند و سپس مجموعه محدودیت به‌روزرسانی شده را اعمال می‌کند.

### دریافت تنظیمات فعلی یک track

مگر اینکه فقط از محدودیت‌های دقیق استفاده کنید (که بسیار محدودکننده است، پس مطمئن باشید منظورتان همین است)، هیچ تضمینی وجود ندارد که دقیقاً چه چیزی پس از اعمال محدودیت‌ها دریافت خواهید کرد. مقادیر ویژگی‌های قابل محدودیت همانطور که در رسانه حاصل هستند، تنظیمات نامیده می‌شوند. اگر نیاز به دانستن قالب واقعی و سایر ویژگی‌های رسانه دارید، می‌توانید آن تنظیمات را با فراخوانی {{domxref("MediaStreamTrack.getSettings()")}} بدست آورید. این تابع یک شیء بر اساس دیکشنری {{domxref("MediaTrackSettings")}} برمی‌گرداند. برای مثال:

```js
function whichCamera(track) {
  return track.getSettings().facingMode;
}
```

این تابع از `getSettings()` برای به دست آوردن مقادیر فعلی مورد استفاده track برای ویژگی‌های قابل محدودیت استفاده می‌کند و مقدار {{domxref("MediaTrackSettings.facingMode", "facingMode")}} را برمی‌گرداند.

## مثال: تمرین‌گر محدودیت‌ها (Constraint exerciser)

در این مثال، یک تمرین‌گر ایجاد می‌کنیم که به شما امکان می‌دهد با محدودیت‌های رسانه با ویرایش کد منبع توصیف‌کننده مجموعه محدودیت‌ها برای track‌های صوتی و تصویری آزمایش کنید. سپس می‌توانید آن تغییرات را اعمال کنید و نتیجه را ببینید، از جمله اینکه جریان چه شکلی است و تنظیمات واقعی رسانه پس از اعمال محدودیت‌های جدید چه مقادیری دارند.

HTML و CSS برای این مثال بسیار ساده هستند و در اینجا نشان داده نمی‌شوند. می‌توانید با کلیک روی "Play" برای مشاهده آن در محیط اجرا، کد کامل را ببینید.

```html hidden
<p>
  Experiment with media constraints! Edit the constraint sets for the video and
  audio tracks in the edit boxes on the left, then click the "Apply Constraints"
  button to try them out. The actual settings the browser selected and is using
  are shown in the boxes on the right. Below all of that, you'll see the video
  itself.
</p>
<p>Click the "Start" button to begin.</p>

<h3>Constrainable properties available:</h3>
<ul id="supportedConstraints"></ul>
<div id="startButton" class="button">Start</div>
<div class="wrapper">
  <div class="track-row">
    <div class="left-side">
      <h3>Requested video constraints:</h3>
      <textarea id="videoConstraintEditor" cols="32" rows="8"></textarea>
    </div>
    <div class="right-side">
      <h3>Actual video settings:</h3>
      <textarea id="videoSettingsText" cols="32" rows="8" disabled></textarea>
    </div>
  </div>
  <div class="track-row">
    <div class="left-side">
      <h3>Requested audio constraints:</h3>
      <textarea id="audioConstraintEditor" cols="32" rows="8"></textarea>
    </div>
    <div class="right-side">
      <h3>Actual audio settings:</h3>
      <textarea id="audioSettingsText" cols="32" rows="8" disabled></textarea>
    </div>
  </div>

  <div class="button" id="applyButton">Apply Constraints</div>
</div>
<video id="video" autoplay></video>

<div class="button" id="stopButton">Stop Video</div>

<div id="log"></div>
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
  width: 150px;
  border: 1px solid black;
  font-size: 16px;
  text-align: center;
  padding-top: 2px;
  padding-bottom: 4px;
  color: white;
  background-color: darkgreen;
}

.wrapper {
  margin-bottom: 10px;
  width: 600px;
}

.track-row {
  height: 200px;
}

.left-side {
  float: left;
  width: calc(calc(100% / 2) - 10px);
}

.right-side {
  float: right;
  width: calc(calc(100% / 2) - 10px);
}

textarea {
  padding: 8px;
}

h3 {
  margin-bottom: 3px;
}

#supportedConstraints {
  column-count: 2;
}

#log {
  padding-top: 10px;
}
```

### پیش‌فرض‌ها و متغیرها

ابتدا مجموعه محدودیت‌های پیش‌فرض را به صورت رشته داریم. این رشته‌ها در {{HTMLElement("textarea")}}های قابل ویرایش نمایش داده می‌شوند، اما این پیکربندی اولیه جریان است.

```js
const videoDefaultConstraintString =
  '{\n  "width": 320,\n  "height": 240,\n  "frameRate": 30\n}';
const audioDefaultConstraintString =
  '{\n  "sampleSize": 16,\n  "channelCount": 2,\n  "echoCancellation": false\n}';
```

این پیش‌فرض‌ها یک پیکربندی نسبتاً رایج دوربین را درخواست می‌کنند، اما بر اهمیت خاص هیچ ویژگی‌ای تأکید نمی‌کنند. مرورگر باید تمام تلاش خود را برای تطبیق این تنظیمات انجام دهد، اما به هر چیزی که آن را یک تطابق نزدیک بداند رضایت می‌دهد.

سپس متغیرهایی را که اشیاء {{domxref("MediaTrackConstraints")}} را برای track‌های ویدیو و صدا نگه می‌دارند، و همچنین متغیرهایی که ارجاعات به خود track‌های ویدیو و صدا را نگه می‌دارند، به `null` مقداردهی می‌کنیم.

```js
let videoConstraints = null;
let audioConstraints = null;

let audioTrack = null;
let videoTrack = null;
```

و ارجاعات به تمام عناصری که باید به آنها دسترسی داشته باشیم را دریافت می‌کنیم.

```js
const videoElement = document.getElementById("video");
const logElement = document.getElementById("log");
const supportedConstraintList = document.getElementById("supportedConstraints");
const videoConstraintEditor = document.getElementById("videoConstraintEditor");
const audioConstraintEditor = document.getElementById("audioConstraintEditor");
const videoSettingsText = document.getElementById("videoSettingsText");
const audioSettingsText = document.getElementById("audioSettingsText");
```

این عناصر عبارتند از:

- `videoElement`
  - : عنصر {{HTMLElement("video")}} که جریان را نمایش می‌دهد.
- `logElement`
  - : یک {{HTMLElement("div")}} که هر پیام خطا یا خروجی از نوع لاگ در آن نوشته می‌شود.
- `supportedConstraintList`
  - : یک {{HTMLElement("ul")}} (لیست نامرتب) که به صورت برنامه‌نویسی نام هر یک از ویژگی‌های قابل محدودیت پشتیبانی‌شده توسط مرورگر کاربر را به آن اضافه می‌کنیم.
- `videoConstraintEditor`
  - : یک عنصر {{HTMLElement("textarea")}} که به کاربر اجازه می‌دهد کد مجموعه محدودیت track ویدیو را ویرایش کند.
- `audioConstraintEditor`
  - : یک عنصر {{HTMLElement("textarea")}} که به کاربر اجازه می‌دهد کد مجموعه محدودیت track صدا را ویرایش کند.
- `videoSettingsText`
  - : یک {{HTMLElement("textarea")}} (که همیشه غیرفعال است) که تنظیمات فعلی ویژگی‌های قابل محدودیت track ویدیو را نمایش می‌دهد.
- `audioSettingsText`
  - : یک {{HTMLElement("textarea")}} (که همیشه غیرفعال است) که تنظیمات فعلی ویژگی‌های قابل محدودیت track صدا را نمایش می‌دهد.

در نهایت، محتوای فعلی دو عنصر ویرایشگر مجموعه محدودیت را به مقادیر پیش‌فرض تنظیم می‌کنیم.

```js
videoConstraintEditor.value = videoDefaultConstraintString;
audioConstraintEditor.value = audioDefaultConstraintString;
```

### به‌روزرسانی نمایش تنظیمات

در سمت راست هر یک از ویرایشگرهای مجموعه محدودیت، یک جعبه متن دوم وجود دارد که از آن برای نمایش پیکربندی فعلی ویژگی‌های قابل پیکربندی track استفاده می‌کنیم. این نمایش توسط تابع `getCurrentSettings()` به‌روزرسانی می‌شود که تنظیمات فعلی را برای track‌های صدا و ویدیو دریافت می‌کند و کد مربوطه را در جعبه‌های نمایش تنظیمات track‌ها با تنظیم [`value`](/en-US/docs/Web/API/HTMLTextAreaElement/value) آنها وارد می‌کند.

```js
function getCurrentSettings() {
  if (videoTrack) {
    videoSettingsText.value = JSON.stringify(videoTrack.getSettings(), null, 2);
  }

  if (audioTrack) {
    audioSettingsText.value = JSON.stringify(audioTrack.getSettings(), null, 2);
  }
}
```

این تابع پس از شروع اولیه جریان و همچنین هر زمان که محدودیت‌های به‌روزرسانی شده را اعمال می‌کنیم، فراخوانی می‌شود، همانطور که در ادامه خواهید دید.

### ساخت اشیاء مجموعه محدودیت track

تابع `buildConstraints()` اشیاء {{domxref("MediaTrackConstraints")}} را برای track‌های صدا و ویدیو با استفاده از کد موجود در جعبه‌های ویرایش مجموعه محدودیت دو track می‌سازد.

```js
function buildConstraints() {
  try {
    videoConstraints = JSON.parse(videoConstraintEditor.value);
    audioConstraints = JSON.parse(audioConstraintEditor.value);
  } catch (error) {
    handleError(error);
  }
}
```

این تابع از {{jsxref("JSON.parse()")}} برای تجزیه کد هر ویرایشگر به یک شیء استفاده می‌کند. اگر هر فراخوانی به JSON.parse() یک استثنا پرتاب کند، `handleError()` برای خروجی پیام خطا به لاگ فراخوانی می‌شود.

### پیکربندی و شروع جریان

متد `startVideo()` راه‌اندازی و شروع جریان ویدیو را مدیریت می‌کند.

```js
function startVideo() {
  buildConstraints();

  navigator.mediaDevices
    .getUserMedia({
      video: videoConstraints,
      audio: audioConstraints,
    })
    .then((stream) => {
      const audioTracks = stream.getAudioTracks();
      const videoTracks = stream.getVideoTracks();

      videoElement.srcObject = stream;

      if (audioTracks.length > 0) {
        audioTrack = audioTracks[0];
      }

      if (videoTracks.length > 0) {
        videoTrack = videoTracks[0];
      }
    })
    .then(
      () =>
        new Promise((resolve) => {
          videoElement.onloadedmetadata = resolve;
        }),
    )
    .then(() => {
      getCurrentSettings();
    })
    .catch(handleError);
}
```

چندین مرحله در اینجا وجود دارد:

1. `buildConstraints()` را فراخوانی می‌کند تا اشیاء {{domxref("MediaTrackConstraints")}} را برای دو track از کد موجود در جعبه‌های ویرایش ایجاد کند.
2. {{domxref("MediaDevices.getUserMedia", "navigator.mediaDevices.getUserMedia()")}} را فراخوانی می‌کند و اشیاء محدودیت را برای track‌های ویدیو و صدا ارسال می‌کند. این یک {{domxref("MediaStream")}} با صدا و ویدیو از یک منبع مطابق با ورودی‌ها (معمولاً یک وب‌کم، اگرچه اگر محدودیت‌های مناسب را ارائه دهید می‌توانید رسانه را از منابع دیگر دریافت کنید) برمی‌گرداند.
3. هنگامی که جریان به دست آمد، به عنصر {{HTMLElement("video")}} متصل می‌شود تا روی صفحه قابل مشاهده باشد، و track صدا و track ویدیو را به ترتیب در متغیرهای `audioTrack` و `videoTrack` ذخیره می‌کنیم.
4. سپس یک promise تنظیم می‌کنیم که با وقوع رویداد {{domxref("HTMLMediaElement/loadedmetadata_event", "loadedmetadata")}} در عنصر ویدیو حل می‌شود.
5. هنگامی که این اتفاق می‌افتد، می‌دانیم که ویدیو شروع به پخش کرده است، بنابراین تابع `getCurrentSettings()` خود را (که در بالا توضیح داده شد) فراخوانی می‌کنیم تا تنظیمات واقعی را که مرورگر پس از در نظر گرفتن محدودیت‌های ما و قابلیت‌های سخت‌افزار تصمیم گرفته است، نمایش دهد.
6. اگر خطایی رخ دهد، آن را با استفاده از متد `handleError()` که در ادامه این مقاله بررسی خواهیم کرد، ثبت می‌کنیم.

همچنین باید یک شنونده رویداد برای تماشای کلیک دکمه "Start Video" تنظیم کنیم:

```js
document.getElementById("startButton").addEventListener("click", () => {
  startVideo();
});
```

### اعمال به‌روزرسانی‌های مجموعه محدودیت

در مرحله بعد، یک شنونده رویداد برای دکمه "Apply Constraints" تنظیم می‌کنیم. اگر روی آن کلیک شود و از قبل رسانه‌ای در حال استفاده نباشد، `startVideo()` را فراخوانی می‌کنیم و اجازه می‌دهیم آن تابع شروع جریان را با تنظیمات مشخص شده مدیریت کند. در غیر این صورت، مراحل زیر را برای اعمال محدودیت‌های به‌روزرسانی شده به جریان از قبل فعال دنبال می‌کنیم:

1. `buildConstraints()` برای ساخت اشیاء {{domxref("MediaTrackConstraints")}} به‌روزرسانی شده برای track صدا (`audioConstraints`) و track ویدیو (`videoConstraints`) فراخوانی می‌شود.
2. {{domxref("MediaStreamTrack.applyConstraints()")}} روی track ویدیو (اگر وجود داشته باشد) برای اعمال `videoConstraints` جدید فراخوانی می‌شود. اگر این موفقیت‌آمیز باشد، محتویات جعبه تنظیمات فعلی track ویدیو بر اساس نتیجه فراخوانی متد {{domxref("MediaStreamTrack.getSettings", "getSettings()")}} آن به‌روزرسانی می‌شود.
3. پس از انجام این کار، `applyConstraints()` روی track صدا (اگر وجود داشته باشد) برای اعمال محدودیت‌های صوتی جدید فراخوانی می‌شود. اگر این موفقیت‌آمیز باشد، محتویات جعبه تنظیمات فعلی track صدا بر اساس نتیجه فراخوانی متد {{domxref("MediaStreamTrack.getSettings", "getSettings()")}} آن به‌روزرسانی می‌شود.
4. اگر در اعمال هر یک از مجموعه محدودیت‌ها خطایی رخ دهد، از `handleError()` برای خروجی یک پیام در لاگ استفاده می‌شود.

```js
document.getElementById("applyButton").addEventListener("click", () => {
  if (!videoTrack && !audioTrack) {
    startVideo();
  } else {
    buildConstraints();

    const prettyJson = (obj) => JSON.stringify(obj, null, 2);

    if (videoTrack) {
      videoTrack
        .applyConstraints(videoConstraints)
        .then(() => {
          videoSettingsText.value = prettyJson(videoTrack.getSettings());
        })
        .catch(handleError);
    }

    if (audioTrack) {
      audioTrack
        .applyConstraints(audioConstraints)
        .then(() => {
          audioSettingsText.value = prettyJson(audioTrack.getSettings());
        })
        .catch(handleError);
    }
  }
});
```

### مدیریت دکمه توقف

سپس کنترل‌کننده دکمه توقف را تنظیم می‌کنیم.

```js
document.getElementById("stopButton").addEventListener("click", () => {
  if (videoTrack) {
    videoTrack.stop();
  }

  if (audioTrack) {
    audioTrack.stop();
  }

  videoTrack = audioTrack = null;
  videoElement.srcObject = null;
});
```

این کار track‌های فعال را متوقف می‌کند، متغیرهای `videoTrack` و `audioTrack` را به `null` تنظیم می‌کند تا بدانیم وجود ندارند، و جریان را با تنظیم {{domxref("HTMLMediaElement.srcObject")}} به `null` از عنصر {{HTMLElement("video")}} حذف می‌کند.

### پشتیبانی ساده از تب در ویرایشگر

این کد پشتیبانی ساده‌ای از تب‌ها را به عناصر {{HTMLElement("textarea")}} اضافه می‌کند با این کار که کلید Tab دو کاراکتر فاصله را زمانی که هر یک از جعبه‌های ویرایش محدودیت متمرکز هستند، درج می‌کند.

```js
function keyDownHandler(event) {
  if (event.key === "Tab") {
    const elem = event.target;
    const str = elem.value;

    const position = elem.selectionStart;
    const beforeTab = str.substring(0, position);
    const afterTab = str.substring(position, str.length);
    const newStr = `${beforeTab}  ${afterTab}`;
    elem.value = newStr;
    elem.selectionStart = elem.selectionEnd = position + 2;
    event.preventDefault();
  }
}

videoConstraintEditor.addEventListener("keydown", keyDownHandler);
audioConstraintEditor.addEventListener("keydown", keyDownHandler);
```

### نمایش ویژگی‌های قابل محدودیت پشتیبانی‌شده توسط مرورگر

آخرین قطعه مهم از پازل: کدی که برای مرجع کاربر، لیستی از ویژگی‌های قابل محدودیتی که مرورگرشان پشتیبانی می‌کند را نمایش می‌دهد. هر ویژگی یک پیوند به مستندات آن در MDN برای راحتی کاربر است. برای جزئیات نحوه کار این کد، به [نمونه‌های `MediaDevices.getSupportedConstraints()`](/en-US/docs/Web/API/MediaDevices/getSupportedConstraints#examples) مراجعه کنید.

> [!NOTE]
> البته ممکن است ویژگی‌های غیراستانداردی در این لیست وجود داشته باشد، که در این صورت احتمالاً متوجه خواهید شد که پیوند مستندات کمک چندانی نمی‌کند.

```js
const supportedConstraints = navigator.mediaDevices.getSupportedConstraints();
for (const constraint in supportedConstraints) {
  if (Object.hasOwn(supportedConstraints, constraint)) {
    const elem = document.createElement("li");

    elem.innerHTML = `<code><a href='https://developer.mozilla.org/docs/Web/API/MediaTrackSupportedConstraints/${constraint}' target='_blank'>${constraint}</a></code>`;
    supportedConstraintList.appendChild(elem);
  }
}
```

### مدیریت خطا

همچنین کد ساده‌ای برای مدیریت خطا داریم؛ `handleError()` برای مدیریت promise‌های ناموفق فراخوانی می‌شود و تابع `log()` پیام خطا را به یک جعبه ثبت ویژه {{HTMLElement("div")}} در زیر ویدیو اضافه می‌کند.

```js
function log(msg) {
  logElement.innerHTML += `${msg}<br>`;
}

function handleError(reason) {
  log(
    `خطا <code>${reason.name}</code> در محدودیت <code>${reason.constraint}</code>: ${reason.message}`,
  );
}
```

### نتیجه

در اینجا می‌توانید مثال کامل را در عمل مشاهده کنید.

{{EmbedLiveSample("Example_Constraint_exerciser", 650, 1200, , , , "camera;microphone")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaTrackSettings")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}