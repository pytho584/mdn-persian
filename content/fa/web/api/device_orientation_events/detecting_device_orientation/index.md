---
title: "تشخیص جهتگیری دستگاه"
---

---
title: Detecting device orientation
slug: Web/API/Device_orientation_events/Detecting_device_orientation
page-type: guide
browser-compat:
  - api.DeviceMotionEvent
  - api.DeviceOrientationEvent
---

{{DefaultAPISidebar("Device Orientation Events")}}{{securecontext_header}}

بهطور فزایندهای، دستگاههای متصل به وب قادر به تعیین **جهتگیری** (orientation) خود هستند؛ یعنی میتوانند دادههایی را گزارش دهند که تغییرات جهتگیری آنها را نسبت به نیروی جاذبه نشان میدهد. بهویژه، دستگاههای دستی مانند تلفنهای همراه میتوانند از این اطلاعات برای چرخاندن خودکار نمایشگر و ثابت نگه داشتن آن در حالت عمودی استفاده کنند؛ به این ترتیب وقتی دستگاه چرخانده میشود بهگونهای که عرض آن بیشتر از ارتفاعش باشد، نمای عریضی از محتوای وب ارائه میشود.

دو رویداد جاوااسکریپت وجود دارند که اطلاعات جهتگیری را مدیریت میکنند. اولین مورد، {{domxref("DeviceOrientationEvent")}} است که وقتی شتابسنج تغییر در جهتگیری دستگاه را تشخیص دهد، ارسال میشود. با دریافت و پردازش دادههای گزارششده توسط این رویدادهای جهتگیری، میتوان بهطور تعاملی به چرخش و تغییرات ارتفاع ناشی از حرکت دستگاه توسط کاربر پاسخ داد.

دومین رویداد، {{domxref("DeviceMotionEvent")}} است که وقتی تغییری در شتاب اضافه شود ارسال میشود. این رویداد با {{domxref("DeviceOrientationEvent")}} تفاوت دارد، زیرا بهجای جهتگیری، به تغییرات شتاب گوش میدهد. سنسورهایی که معمولاً قادر به تشخیص {{domxref("DeviceMotionEvent")}} هستند شامل سنسورهای موجود در لپتاپها برای محافظت از دستگاههای ذخیرهسازی در حال حرکت میباشند. {{domxref("DeviceOrientationEvent")}} بیشتر در دستگاههای تلفن همراه یافت میشود.

## درخواست مجوز

برخی از {{Glossary("user agent", "عاملهای کاربر")}} قبل از دسترسی به دادههای جهتگیری و حرکت دستگاه، به مجوز صریح از کاربر نیاز دارند. در محیطهایی که این نیاز وجود دارد، میتوان از متدهای استاتیک {{domxref("DeviceOrientationEvent.requestPermission_static", "DeviceOrientationEvent.requestPermission()")}} و {{domxref("DeviceMotionEvent.requestPermission_static", "DeviceMotionEvent.requestPermission()")}} برای درخواست این مجوز استفاده کرد. هر دو متد یک {{jsxref("Promise")}} برمیگردانند که با مقدار `"granted"` یا `"denied"` حل میشود و هر دو باید از داخل یک ژست کاربر (مانند یک هندلر رویداد `click`) فراخوانی شوند.

از آنجا که همه عاملهای کاربر این متدها را پیادهسازی نمیکنند، باید قبل از فراخوانی، وجود آنها را بررسی کنید (feature-detect). مثال زیر نحوه درخواست هر دو مجوز را از یک هندلر کلیک دکمه نشان میدهد:

```js
function handleClick() {
  if (typeof DeviceMotionEvent.requestPermission === "function") {
    // API به مجوز نیاز دارد — آن را درخواست کن
    Promise.all([
      DeviceMotionEvent.requestPermission(),
      DeviceOrientationEvent.requestPermission(),
    ]).then(([motionPermission, orientationPermission]) => {
      if (
        motionPermission === "granted" &&
        orientationPermission === "granted"
      ) {
        window.addEventListener("devicemotion", handleMotion);
        window.addEventListener("deviceorientation", handleOrientation);
      }
    });
  } else {
    // نیازی به مجوز نیست؛ مستقیماً شنوندههای رویداد را اضافه کن
    window.addEventListener("devicemotion", handleMotion);
    window.addEventListener("deviceorientation", handleOrientation);
  }
}
```

## پردازش رویدادهای جهتگیری

تنها کاری که برای شروع دریافت تغییرات جهتگیری باید انجام دهید، گوش دادن به رویداد {{domxref("Window.deviceorientation_event", "deviceorientation")}} است:

```js
window.addEventListener("deviceorientation", handleOrientation);
```

پس از ثبت شنونده رویداد خود (در این مثال، یک تابع جاوااسکریپت به نام `handleOrientation()`)، تابع شنونده شما بهطور دورهای با دادههای بهروز جهتگیری فراخوانی میشود.

رویداد جهتگیری شامل چهار مقدار است:

- {{domxref("DeviceOrientationEvent.absolute")}}
- {{domxref("DeviceOrientationEvent.alpha")}}
- {{domxref("DeviceOrientationEvent.beta")}}
- {{domxref("DeviceOrientationEvent.gamma")}}

تابع هندلر رویداد میتواند چیزی شبیه به این باشد:

```js
function handleOrientation(event) {
  const absolute = event.absolute;
  const alpha = event.alpha;
  const beta = event.beta;
  const gamma = event.gamma;

  // کارهای لازم با دادههای جدید جهتگیری
}
```

> [!NOTE]
> [parallax](https://github.com/wagerfield/parallax) یک polyfill برای نرمالسازی دادههای شتابسنج و ژیروسکوپ در دستگاههای تلفن همراه است. این ابزار برای غلبه بر برخی تفاوتهای پشتیبانی دستگاهها از جهتگیری دستگاه مفید است.

### توضیح مقادیر جهتگیری

مقدار گزارششده برای هر محور، میزان چرخش حول آن محور را نسبت به یک دستگاه مختصات استاندارد نشان میدهد. این مقادیر با جزئیات بیشتر در مقاله [توضیح دادههای جهتگیری و حرکت](/en-US/docs/Web/API/Device_orientation_events/Orientation_and_motion_data_explained) شرح داده شدهاند که در ادامه خلاصهای از آنها آمده است.

- مقدار {{domxref("DeviceOrientationEvent.alpha")}} حرکت دستگاه حول محور z را نشان میدهد و بر حسب درجه با مقادیری از 0 (شامل) تا 360 (نا شامل) بیان میشود.
- مقدار {{domxref("DeviceOrientationEvent.beta")}} حرکت دستگاه حول محور x را نشان میدهد و بر حسب درجه با مقادیری از 180- (شامل) تا 180 (نا شامل) بیان میشود. این مقدار حرکت دستگاه از جلو به عقب را نشان میدهد.
- مقدار {{domxref("DeviceOrientationEvent.gamma")}} حرکت دستگاه حول محور y را نشان میدهد و بر حسب درجه با مقادیری از 90- (شامل) تا 90 (نا شامل) بیان میشود. این مقدار حرکت دستگاه از چپ به راست را نشان میدهد.

### مثال جهتگیری

این مثال در هر مرورگری که از رویداد {{domxref("Window.deviceorientation_event", "deviceorientation")}} پشتیبانی میکند و روی دستگاهی که قادر به تشخیص جهتگیری خود است اجرا شود، کار خواهد کرد.

بیایید یک توپ در یک باغچه تصور کنیم:

```html
<div class="garden">
  <div class="ball"></div>
</div>
دستگاه را موازی با زمین نگه دارید. آن را حول محورهای x و y بچرخانید تا بهترتیب حرکت توپ را به بالا/پایین و چپ/راست ببینید.
<pre class="output"></pre>
```

این باغچه ۲۰۰ پیکسل عرض دارد (بله، خیلی کوچک است) و توپ در مرکز آن قرار دارد:

```css
.garden {
  position: relative;
  width: 200px;
  height: 200px;
  border: 5px solid #cccccc;
  border-radius: 10px;
}

.ball {
  position: absolute;
  top: 90px;
  left: 90px;
  width: 20px;
  height: 20px;
  background: green;
  border-radius: 100%;
}
```

حالا اگر دستگاه را حرکت دهیم، توپ متناسب با آن حرکت خواهد کرد:

```js
const ball = document.querySelector(".ball");
const garden = document.querySelector(".garden");
const output = document.querySelector(".output");

const maxX = garden.clientWidth - ball.clientWidth;
const maxY = garden.clientHeight - ball.clientHeight;

function handleOrientation(event) {
  let x = event.beta; // بر حسب درجه در بازه [180-,180)
  let y = event.gamma; // بر حسب درجه در بازه [90-,90)

  output.textContent = `beta: ${x}\n`;
  output.textContent += `gamma: ${y}\n`;

  // چون نمیخواهیم دستگاه وارونه باشد
  // مقدار x را به بازه [90-,90] محدود میکنیم
  if (x > 90) {
    x = 90;
  }
  if (x < -90) {
    x = -90;
  }

  // برای سادهتر شدن محاسبات، بازه
  // x و y را به [0,180] منتقل میکنیم
  x += 90;
  y += 90;

  // 10 نصف اندازه توپ است
  // نقطه موقعیتیابی را به مرکز توپ منتقل میکند
  ball.style.left = `${(maxY * y) / 180 - 10}px`; // چرخش دستگاه حول محور y توپ را افقی حرکت میدهد
  ball.style.top = `${(maxX * x) / 180 - 10}px`; // چرخش دستگاه حول محور x توپ را عمودی حرکت میدهد
}

window.addEventListener("deviceorientation", handleOrientation);
```

{{LiveSampleLink("Orientation_example", "برای باز کردن این مثال در یک پنجره جدید اینجا کلیک کنید"}}؛ زیرا {{domxref("Window.deviceorientation_event", "deviceorientation")}} در یک {{HTMLElement("iframe")}} متقاطع (cross-origin) در همه مرورگرها کار نمیکند.

{{EmbedLiveSample('Orientation_example', '230', '260')}}

## پردازش رویدادهای حرکت

رویدادهای حرکت به همان روش رویدادهای جهتگیری مدیریت میشوند، با این تفاوت که نام رویداد خودشان را دارند: {{domxref("Window.devicemotion_event", "devicemotion")}}

```js
window.addEventListener("devicemotion", handleMotion);
```

آنچه واقعاً تغییر میکند، اطلاعات ارائهشده در شیء {{domxref("DeviceMotionEvent")}} است که بهعنوان پارامتر به شنونده رویداد (در مثال ما `handleMotion()`) منتقل میشود.

رویداد حرکت شامل چهار ویژگی است:

- {{domxref("DeviceMotionEvent.acceleration")}}
- {{domxref("DeviceMotionEvent.accelerationIncludingGravity")}}
- {{domxref("DeviceMotionEvent.rotationRate")}}
- {{domxref("DeviceMotionEvent.interval")}}

### توضیح مقادیر حرکت

اشیاء {{domxref("DeviceMotionEvent")}} اطلاعاتی درباره سرعت تغییرات موقعیت و جهتگیری دستگاه در اختیار توسعهدهندگان وب قرار میدهند. این تغییرات در سه محور ارائه میشوند (برای جزئیات به [توضیح دادههای جهتگیری و حرکت](/en-US/docs/Web/API/Device_orientation_events/Orientation_and_motion_data_explained) مراجعه کنید).

برای {{domxref("DeviceMotionEvent.acceleration","acceleration")}} و {{domxref("DeviceMotionEvent.accelerationIncludingGravity","accelerationIncludingGravity")}}، این محورها به صورت زیر هستند:

- `x`
  - : محوری از غرب به شرق را نشان میدهد
- `y`
  - : محوری از جنوب به شمال را نشان میدهد
- `z`
  - : محوری عمود بر زمین را نشان میدهد

برای {{domxref("DeviceMotionEvent.rotationRate","rotationRate")}}، وضعیت کمی متفاوت است؛ اطلاعات در هر مورد به صورت زیر است:

- `alpha`
  - : نرخ چرخش حول محوری عمود بر صفحه نمایش (یا صفحهکلید در دسکتاپ) را نشان میدهد.
- `beta`
  - : نرخ چرخش حول محوری که از چپ به راست صفحه نمایش (یا صفحهکلید در دسکتاپ) میرود را نشان میدهد.
- `gamma`
  - : نرخ چرخش حول محوری که از پایین به بالای صفحه نمایش (یا صفحهکلید در دسکتاپ) میرود را نشان میدهد.

در نهایت، {{domxref("DeviceMotionEvent.interval","interval")}} بازه زمانی بر حسب میلیثانیه را نشان میدهد که دادهها از دستگاه دریافت میشوند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DeviceOrientationEvent")}}
- {{domxref("DeviceMotionEvent")}}
- [توضیح دادههای جهتگیری و حرکت](/en-US/docs/Web/API/Device_orientation_events/Orientation_and_motion_data_explained)
- [استفاده از deviceorientation در تبدیلهای سهبعدی](/en-US/docs/Web/API/Device_orientation_events/Using_device_orientation_with_3D_transforms)
- [Cyber Orb: بازی ماز دوبعدی با جهتگیری دستگاه](/en-US/docs/Games/Tutorials/HTML5_Gamedev_Phaser_Device_Orientation)