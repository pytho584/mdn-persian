---
title: "Pointer events"
---

---
title: Pointer events
slug: Web/API/Pointer_events
page-type: web-api-overview
browser-compat: api.PointerEvent
spec-urls: https://w3c.github.io/pointerevents/
---

{{DefaultAPISidebar("Pointer Events")}}

بسیاری از محتوای وب امروزی فرض می‌کنند که دستگاه اشارهٔ کاربر یک ماوس است. با این حال، از آنجا که بسیاری از دستگاه‌ها از انواع دیگری از دستگاه‌های ورودی اشاره مانند قلم/استایلوس و سطوح لمسی پشتیبانی می‌کنند، به توسعه‌هایی در مدل‌های رویداد دستگاه اشارهٔ موجود نیاز است. _[رویدادهای Pointer](#pointer_event)_ این نیاز را برطرف می‌کنند.

رویدادهای Pointer رویدادهای DOM هستند که برای یک دستگاه اشاره صادر می‌شوند. آن‌ها برای ایجاد یک مدل رویداد یکپارچه در DOM طراحی شده‌اند تا دستگاه‌های ورودی اشاره مانند ماوس، قلم/استایلوس یا لمس (مانند یک یا چند انگشت) را مدیریت کنند.

_[اشاره‌گر](#pointer)_ یک بازنمایی مستقل از سخت‌افزار است که می‌تواند مجموعه‌ای مشخص از مختصات صفحه را هدف بگیرد. داشتن یک مدل رویداد واحد برای اشاره‌گرها می‌تواند ساخت وب‌سایت‌ها و برنامه‌ها را ساده‌تر کند و بدون توجه به سخت‌افزار کاربر، تجربهٔ کاربری خوبی فراهم کند. با این حال، برای سناریوهایی که پردازش ویژهٔ دستگاه خاص مورد نظر است، رویدادهای Pointer ویژگی {{domxref("PointerEvent.pointerType","pointerType")}} را تعریف می‌کنند تا نوع دستگاهی که رویداد را تولید کرده است بررسی شود.

رویدادهای مورد نیاز برای مدیریت ورودی عمومی اشاره‌گر مشابه {{domxref("MouseEvent","mouse events", "", 1)}} هستند (`mousedown`/`pointerdown`, `mousemove`/`pointermove` و غیره). در نتیجه، انواع رویدادهای Pointer عمداً به انواع رویدادهای ماوس شباهت دارند.

علاوه بر این، یک رویداد Pointer شامل ویژگی‌های معمول موجود در رویدادهای ماوس (مختصات سمت کلاینت، عنصر هدف، وضعیت دکمه‌ها و غیره) به‌علاوهٔ ویژگی‌های جدید برای سایر اشکال ورودی است: فشار، هندسهٔ تماس، شیب و غیره. در واقع، رابط {{domxref("PointerEvent")}} همهٔ ویژگی‌های {{domxref("MouseEvent")}} را به ارث می‌برد و در نتیجه انتقال محتوا از رویدادهای ماوس به رویدادهای Pointer را تسهیل می‌کند.

## اصطلاحات

### وضعیت دکمه‌های فعال

وضعیتی که یک _[اشاره‌گر](#pointer)_ مقدار غیرصفر برای ویژگی `buttons` دارد. به‌عنوان مثال، در مورد قلم، زمانی که قلم با دیجیتایزر تماس فیزیکی دارد یا هنگام hover (نگه‌داشتن اشاره‌گر روی عنصر بدون کلیک) حداقل یک دکمه فشرده شده باشد.

### اشاره‌گر فعال

هر دستگاه ورودیِ _[اشاره‌گر](#pointer)_ که بتواند رویداد تولید کند. یک اشاره‌گر زمانی فعال در نظر گرفته می‌شود که همچنان بتواند رویدادهای بیشتری صادر کند. برای مثال، قلمی که در وضعیت فشرده (down) قرار دارد، فعال محسوب می‌شود، زیرا هنگام بلند شدن یا حرکت قلم می‌تواند رویدادهای دیگری تولید کند.

### دیجیتایزر

یک دستگاه حسگر با سطحی که می‌تواند تماس را تشخیص دهد. در اغلب موارد، این دستگاه حسگر، صفحه‌نمایش لمسی است که می‌تواند ورودی ابزاری مانند قلم، استایلوس یا انگشت را حس کند. برخی دستگاه‌های حسگر می‌توانند نزدیکی ابزار ورودی را نیز تشخیص دهند و این وضعیت به‌صورت hover مشابه ماوس بیان می‌شود.

### تست برخورد

فرایندی که مرورگر برای تعیین عنصر هدف یک رویداد Pointer استفاده می‌کند. معمولاً این تعیین با در نظر گرفتن موقعیت اشاره‌گر و همچنین چیدمان بصری عناصر سند در رسانهٔ نمایشگر انجام می‌شود.

### اشاره‌گر

بازنماییِ مستقل از سخت‌افزار از دستگاه‌های ورودی که می‌توانند مختصات مشخصی (یا مجموعه‌ای از مختصات) را روی صفحه هدف بگیرند. نمونه‌هایی از دستگاه‌های ورودی _اشاره‌گر_ عبارت‌اند از ماوس، قلم/استایلوس و تماس‌های لمسی.

### تصاحبِ اشاره‌گر (Pointer Capture)

تصاحبِ اشاره‌گر اجازه می‌دهد رویدادهای یک اشاره‌گر به عنصری خاص، به‌جای نتیجهٔ عادیِ [تست برخورد](#hit_test) بر اساس موقعیت اشاره‌گر، هدف‌گیری مجدد شوند. برای مثال به بخش [تصاحبِ اشاره‌گر](#capturing_the_pointer) مراجعه کنید.

> [!NOTE]
> _تصاحبِ اشاره‌گر_ با [_قفلِ اشاره‌گر_](/en-US/docs/Web/API/Pointer_Lock_API) متفاوت است؛ قفل اشاره‌گر به‌صورت فیزیکی از خارج‌شدن اشاره‌گر از یک ناحیه جلوگیری می‌کند.

### رویداد Pointer

یک {{domxref("PointerEvent","event")}} در DOM که به ازای یک _[اشاره‌گر](#pointer)_ صادر می‌شود.

## رابط‌ها

رابط اصلی، رابط {{domxref("PointerEvent")}} است که یک {{domxref("PointerEvent.PointerEvent","constructor")}} به همراه چند نوع رویداد و کنترل‌کننده‌های رویداد سراسری مرتبط دارد.

این استاندارد همچنین شامل برخی توسعه‌ها برای رابط‌های {{domxref("Element")}} و {{domxref("Navigator")}} است.

زیربخش‌های زیر شامل توضیح کوتاهی دربارهٔ هر رابط و ویژگی هستند.

### رابط PointerEvent

رابط {{domxref("PointerEvent")}} رابط {{domxref("MouseEvent")}} را گسترش می‌دهد و ویژگی‌های زیر را دارد.

- {{ domxref('PointerEvent.altitudeAngle', 'altitudeAngle')}} {{ReadOnlyInline}}
  - : زاویهٔ بین محور یک مبدل (یک اشاره‌گر یا استایلوس) و صفحهٔ X-Y صفحه‌نمایش دستگاه را نشان می‌دهد.
- {{ domxref('PointerEvent.azimuthAngle', 'azimuthAngle')}} {{ReadOnlyInline}}
  - : زاویهٔ بین صفحهٔ Y-Z و صفحه‌ای که هم محور مبدل (اشاره‌گر یا استایلوس) و هم محور Y را شامل می‌شود، نشان می‌دهد.
- {{domxref('PointerEvent.persistentDeviceId')}} {{ReadOnlyInline}}
  - : یک شناسهٔ یکتا برای دستگاه اشاره‌گری که `PointerEvent` را تولید می‌کند.
- {{ domxref('PointerEvent.pointerId','pointerId')}} {{ReadOnlyInline}}
  - : شناسهٔ یکتای اشاره‌گری که باعث رویداد شده است.
- {{ domxref('PointerEvent.width','width')}} {{ReadOnlyInline}}
  - : عرض (بزرگی در محور X) هندسهٔ تماس اشاره‌گر، بر حسب پیکسل CSS.
- {{ domxref('PointerEvent.height','height')}} {{ReadOnlyInline}}
  - : ارتفاع (بزرگی در محور Y) هندسهٔ تماس اشاره‌گر، بر حسب پیکسل CSS.
- {{ domxref('PointerEvent.pressure','pressure')}} {{ReadOnlyInline}}
  - : فشار نرمال‌شدهٔ ورودی اشاره‌گر در بازهٔ `0` تا `1` که در آن `0` و `1` به‌ترتیب حداقل و حداکثر فشاری هستند که سخت‌افزار قادر به تشخیص آن است.
- {{ domxref('PointerEvent.tangentialPressure','tangentialPressure')}} {{ReadOnlyInline}}
  - : فشار مماسی نرمال‌شدهٔ ورودی اشاره‌گر (که با نام‌های فشار بدنه یا تنش استوانه‌ای نیز شناخته می‌شود) در بازهٔ `1-` تا `1` که در آن `0` وضعیت خنثی کنترل است.
- {{ domxref('PointerEvent.tiltX','tiltX')}} {{ReadOnlyInline}}
  - : زاویهٔ صفحه‌ای (بر حسب درجه، در بازهٔ `90-` تا `90`) بین صفحهٔ Y–Z و صفحه‌ای که هم محور اشاره‌گر (مثلاً قلم استایلوس) و هم محور Y را در بر می‌گیرد.
- {{ domxref('PointerEvent.tiltY','tiltY')}} {{ReadOnlyInline}}
  - : زاویهٔ صفحه‌ای (بر حسب درجه، در بازهٔ `90-` تا `90`) بین صفحهٔ X–Z و صفحه‌ای که هم محور اشاره‌گر (مثلاً قلم استایلوس) و هم محور X را در بر می‌گیرد.
- {{ domxref('PointerEvent.twist','twist')}} {{ReadOnlyInline}}
  - : چرخش ساعت‌گرد اشاره‌گر (مثلاً قلم استایلوس) حول محور اصلی آن بر حسب درجه، با مقداری در بازهٔ `0` تا `359`.
- {{ domxref('PointerEvent.pointerType','pointerType')}} {{ReadOnlyInline}}
  - : نوع دستگاهی که رویداد را سبب شده است (ماوس، قلم، لمس و غیره) را نشان می‌دهد.
- {{ domxref('PointerEvent.isPrimary','isPrimary')}} {{ReadOnlyInline}}
  - : نشان می‌دهد که آیا این اشاره‌گر، اشاره‌گر اصلی این نوع اشاره‌گر است یا نه.

### انواع رویدادها و کنترل‌کننده‌های سراسری رویداد

رویدادهای Pointer ده نوع رویداد دارند که هفت تای آن‌ها از نظر معنایی مشابه رویدادهای متناظر ماوس هستند (`down`, `up`, `move`, `over`, `out`, `enter` و `leave`).

در ادامه توضیح کوتاهی از هر نوع رویداد آمده است.

| Event                                                                                     | Description                                                                                                                                                                                                                                                                                                                                                                |
| ----------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| {{domxref('Element/pointerover_event', 'pointerover')}}                                   | زمانی صادر می‌شود که یک اشاره‌گر به درون مرزهای [تست برخورد](#hit_test) یک عنصر حرکت کند.                                                                                                                                                                                                                                                                                 |
| {{domxref('Element/pointerenter_event', 'pointerenter')}}                                 | زمانی صادر می‌شود که یک اشاره‌گر به درون مرزهای [تست برخورد](#hit_test) یک عنصر یا یکی از فرزندان آن حرکت کند؛ از جمله در نتیجهٔ رویداد `pointerdown` از دستگاهی که از حالت hover پشتیبانی نمی‌کند (به `pointerdown` مراجعه کنید).                                                                        |
| {{domxref('Element/pointerdown_event', 'pointerdown')}}                                   | زمانی صادر می‌شود که یک اشاره‌گر وارد «وضعیت دکمه‌های فعال» می‌شود.                                                                                                                                                                                                                                                                                                    |
| {{domxref('Element/pointermove_event', 'pointermove')}}                                   | زمانی صادر می‌شود که مختصات یک اشاره‌گر تغییر کند. این رویداد همچنین زمانی استفاده می‌شود که تغییر وضعیت اشاره‌گر را نتوان با رویدادهای دیگر گزارش داد.                                                                                                                                                                                                                 |
| {{domxref('Element/pointerup_event', 'pointerup')}}                                       | زمانی صادر می‌شود که یک اشاره‌گر دیگر در «وضعیت دکمه‌های فعال» نباشد.                                                                                                                                                                                                                                                                                                    |
| {{domxref('Element/pointercancel_event', 'pointercancel')}}                               | مرورگر این رویداد را زمانی صادر می‌کند که به این نتیجه برسد که اشاره‌گر دیگر قادر به تولید رویداد نخواهد بود (برای مثال، اگر دستگاه مرتبط غیرفعال شود، یا مرورگر تصمیم بگیرد تعامل را به‌جای آن به‌صورت پیمایش/بزرگ‌نمایی تفسیر کند). برای اطلاعات دربارهٔ نحوه کنترل این رفتار، بخش [ویژگی CSS متعلق به `touch-action`](#touch-action_css_property) را در ادامه ببینید. |
| {{domxref('Element/pointerout_event', 'pointerout')}}                                     | به دلایل متعددی صادر می‌شود، از جمله: حرکت اشاره‌گر به خارج از مرزهای [تست برخورد](#hit_test) یک عنصر؛ صادرشدن رویداد `pointerup` برای دستگاهی که از hover پشتیبانی نمی‌کند (به `pointerup` مراجعه کنید)؛ پس از صادرشدن رویداد `pointercancel` (به `pointercancel` مراجعه کنید)؛ و زمانی که قلم استایلوس از محدودهٔ hover قابل تشخیص توسط دیجیتایزر خارج شود.               |
| {{domxref('Element/pointerleave_event', 'pointerleave')}}                                 | زمانی صادر می‌شود که یک اشاره‌گر به خارج از مرزهای [تست برخورد](#hit_test) یک عنصر حرکت کند. برای دستگاه‌های قلمی، این رویداد زمانی صادر می‌شود که استایلوس از محدودهٔ hover قابل تشخیص توسط دیجیتایزر خارج شود.                                                                                                                                                            |
| {{domxref('Element/pointerrawupdate_event', 'pointerrawupdate')}} {{experimental_inline}} | زمانی صادر می‌شود که یک اشاره‌گر هر ویژگی‌ای را تغییر دهد که باعث صادرشدن رویدادهای `pointerdown` یا `pointerup` نشود.                                                                                                                                                                                                                                                  |
| {{domxref('Element/gotpointercapture_event', 'gotpointercapture')}}                       | زمانی صادر می‌شود که یک عنصر تصاحبِ اشاره‌گر را دریافت کند.                                                                                                                                                                                                                                                                                                               |
| {{domxref('Element/lostpointercapture_event', 'lostpointercapture')}}                     | پس از آزادشدن تصاحبِ اشاره‌گر برای یک اشاره‌گر صادر می‌شود.                                                                                                                                                                                                                                                                                                               |

### توسعه‌های Element

سه توسعه برای رابط {{domxref("Element")}} وجود دارد:

- {{domxref("Element.hasPointerCapture()","hasPointerCapture()")}}
  - : نشان می‌دهد که آیا عنصری که این متد روی آن فراخوانی شده است، تصاحبِ اشاره‌گر را برای اشاره‌گری با شناسهٔ داده‌شده دارد یا خیر.
- {{domxref("Element.releasePointerCapture()","releasePointerCapture()")}}
  - : تصاحبِ اشاره‌گری را که قبلاً برای یک رویداد اشاره‌گر خاص تنظیم شده بود آزاد (متوقف) می‌کند.
- {{domxref("Element.setPointerCapture()","setPointerCapture()")}}
  - : یک عنصر خاص را به‌عنوان «هدف تصاحب» رویدادهای اشاره‌گر آینده تعیین می‌کند.

### توسعهٔ Navigator

ویژگی {{domxref("Navigator.maxTouchPoints")}} برای تعیین حداکثر تعداد نقاط لمسی هم‌زمان که در هر لحظهٔ مشخص پشتیبانی می‌شوند استفاده می‌شود.

## مثال‌ها

این بخش شامل مثال‌هایی از کاربرد پایهٔ رابط‌های Pointer Events است.

### ثبت کنترل‌کننده‌های رویداد

این مثال برای هر نوع رویدادِ عنصر داده‌شده یک کنترل‌کننده ثبت می‌کند.

```html
<div id="target">Touch me…</div>
```

```js
function overHandler(event) {}
function enterHandler(event) {}
function downHandler(event) {}
function moveHandler(event) {}
function upHandler(event) {}
function cancelHandler(event) {}
function outHandler(event) {}
function leaveHandler(event) {}
function rawUpdateHandler(event) {}
function gotCaptureHandler(event) {}
function lostCaptureHandler(event) {}

const el = document.getElementById("target");
// Register pointer event handlers
el.onpointerover = overHandler;
el.onpointerenter = enterHandler;
el.onpointerdown = downHandler;
el.onpointermove = moveHandler;
el.onpointerup = upHandler;
el.onpointercancel = cancelHandler;
el.onpointerout = outHandler;
el.onpointerleave = leaveHandler;
el.onpointerrawupdate = rawUpdateHandler;
el.ongotpointercapture = gotCaptureHandler;
el.onlostpointercapture = lostCaptureHandler;
```

### ویژگی‌های رویداد

این مثال نحوهٔ دسترسی به تمام ویژگی‌های یک رویداد Pointer را نشان می‌دهد.

```html
<div id="target">Touch me…</div>
```

```js
const id = -1;

function processId(event) {
  // Process this event based on the event's identifier
}
function processMouse(event) {
  // Process the mouse pointer event
}
function processPen(event) {
  // Process the pen pointer event
}
function processTouch(event) {
  // Process the touch pointer event
}
function processTilt(tiltX, tiltY) {
  // Tilt data handler
}
function processPressure(pressure) {
  // Pressure handler
}
function processNonPrimary(event) {
  // Non primary handler
}

function downHandler(ev) {
  // Calculate the touch point's contact area
  const area = ev.width * ev.height;

  // Compare cached id with this event's id and process accordingly
  if (id === ev.identifier) processId(ev);

  // Call the appropriate pointer type handler
  switch (ev.pointerType) {
    case "mouse":
      processMouse(ev);
      break;
    case "pen":
      processPen(ev);
      break;
    case "touch":
      processTouch(ev);
      break;
    default:
      console.log(`pointerType ${ev.pointerType} is not supported`);
  }

  // Call the tilt handler
  if (ev.tiltX !== 0 && ev.tiltY !== 0) processTilt(ev.tiltX, ev.tiltY);

  // Call the pressure handler
  processPressure(ev.pressure);

  // If this event is not primary, call the non primary handler
  if (!ev.isPrimary) processNonPrimary(ev);
}

const el = document.getElementById("target");
// Register pointerdown handler
el.onpointerdown = downHandler;
```

## تعیین اشاره‌گر اصلی

در برخی سناریوها ممکن است چند اشاره‌گر وجود داشته باشد (برای مثال دستگاهی که هم صفحه‌لمسی و هم ماوس دارد)، یا اشاره‌گری که از چند نقطهٔ تماس پشتیبانی می‌کند (برای مثال صفحه‌لمسی که لمس چند انگشت را پشتیبانی می‌کند). برنامه می‌تواند از ویژگی {{domxref("PointerEvent.isPrimary","isPrimary")}} استفاده کند تا یک اشاره‌گر اصلی را در میان مجموعهٔ _اشاره‌گرهای فعال_ برای هر نوع اشاره‌گر شناسایی کند. اگر برنامه‌ای فقط بخواهد از یک اشاره‌گر اصلی پشتیبانی کند، می‌تواند تمام رویدادهای Pointer را که primary نیستند نادیده بگیرد.

ماوس فقط یک اشاره‌گر دارد، بنابراین همیشه اشاره‌گر اصلی خواهد بود. برای ورودی لمسی، یک اشاره‌گر زمانی primary در نظر گرفته می‌شود که کاربر در حالی صفحه را لمس کرده باشد که هیچ لمس فعال دیگری وجود نداشته باشد. برای ورودی قلم و استایلوس، یک اشاره‌گر زمانی primary در نظر گرفته می‌شود که قلم کاربر در حالی در ابتدا با صفحه تماس برقرار کند که هیچ قلم فعال دیگری با صفحه در تماس نباشد.

## تعیین وضعیت دکمه‌ها

برخی دستگاه‌های اشاره‌گر (مانند ماوس و قلم) از چند دکمه پشتیبانی می‌کنند و فشردن دکمه‌ها می‌تواند _ترکیبی_ باشد (یعنی فشردن یک دکمهٔ اضافی در حالی که دکمهٔ دیگری روی دستگاه اشاره‌گر قبلاً فشرده شده است).

برای تعیین وضعیت فشردن دکمه‌ها، رویدادهای Pointer از ویژگی‌های {{domxref("MouseEvent.button","button")}} و {{domxref("MouseEvent.buttons","buttons")}} رابط {{domxref("MouseEvent")}} استفاده می‌کنند (که {{domxref("PointerEvent")}} از آن به ارث می‌برد).

جدول زیر مقادیر `button` و `buttons` را برای وضعیت‌های مختلف دکمه‌های دستگاه نشان می‌دهد.

| Device Button State                                                                  | button | buttons |
| ------------------------------------------------------------------------------------ | ------ | ------- |
| هیچ دکمه‌ای فشرده نشده و تماس لمس/قلم نسبت به رویداد قبلی تغییر نکرده است             | `-1`   | —       |
| حرکت ماوس بدون فشردن دکمه، حرکت قلم در حالت hover بدون فشردن دکمه                      | —      | `0`     |
| دکمهٔ چپ ماوس، تماس لمسی، تماس قلم                                                  | `0`    | `1`     |
| دکمهٔ وسط ماوس                                                                        | `1`    | `4`     |
| دکمهٔ راست ماوس، دکمهٔ بدنهٔ قلم                                                     | `2`    | `2`     |
| دکمهٔ X1 (عقب) ماوس                                                                  | `3`    | `8`     |
| دکمهٔ X2 (جلو) ماوس                                                                  | `4`    | `16`    |
| دکمهٔ پاک‌کن قلم                                                                     | `5`    | `32`    |

> [!NOTE]
> ویژگی `button` تغییری در وضعیت دکمه را نشان می‌دهد. با این حال، مانند مورد لمس، وقتی چند رویداد در یک تعامل رخ می‌دهند، همهٔ آن‌ها مقدار یکسانی دارند.

## تصاحبِ اشاره‌گر

تصاحبِ اشاره‌گر اجازه می‌دهد رویدادهای مربوط به یک {{domxref("PointerEvent","pointer event", "", 1)}} خاص به عنصری مشخص هدف‌گیری مجدد شوند، به‌جای [تست برخورد](#hit_test) معمول در موقعیت اشاره‌گر. این کار می‌تواند تضمین کند که یک عنصر حتی اگر تماس دستگاه اشاره‌گر از روی عنصر حرکت کند (مثلاً با اسکرول یا پیمایش)، همچنان رویدادهای Pointer را دریافت کند.

تصاحبِ اشاره‌گر باعث می‌شود عنصر هدف، تمام رویدادهای بعدی اشاره‌گر را به‌گونه‌ای دریافت کند که گویی روی همان عنصرِ تصاحب‌کننده رخ می‌دهند. در نتیجه، تا وقتی که این تصاحب برقرار است، رویدادهای `pointerover`، `pointerenter`، `pointerleave` و `pointerout` **صادر نخواهند شد**.
در مرورگرهای صفحه‌لمسی که امکان [دستکاری مستقیم](https://w3c.github.io/pointerevents/#dfn-direct-manipulation) را فراهم می‌کنند، وقتی رویداد `pointerdown` رخ دهد یک [تصاحبِ ضمنیِ اشاره‌گر](https://w3c.github.io/pointerevents/#dfn-implicit-pointer-capture) روی عنصر اعمال می‌شود. این تصاحب را می‌توان به‌صورت دستی با فراخوانی {{domxref('element.releasePointerCapture')}} روی عنصر هدف آزاد کرد، یا پس از رویداد `pointerup` یا `pointercancel` به‌صورت ضمنی آزاد می‌شود.

> [!NOTE]
> اگر نیاز دارید عنصری را در DOM جابه‌جا کنید، مطمئن شوید که `setPointerCapture()` را **پس از جابه‌جایی در DOM** فراخوانی کرده‌اید تا `setPointerCapture()` آن را گم نکند. برای مثال، اگر لازم است از `Element.append()` برای انتقال عنصر به جای دیگر استفاده کنید، مطمئن شوید که `setPointerCapture()` را فقط پس از فراخوانیِ `Element.append()` روی آن صدا می‌زنید.

مثال زیر، تنظیم تصاحبِ اشاره‌گر روی یک عنصر را نشان می‌دهد.

```html
<div id="target">Touch me…</div>
```

```js
function downHandler(ev) {
  const el = document.getElementById("target");
  // Element 'target' will receive/capture further events
  el.setPointerCapture(ev.pointerId);
}

const el = document.getElementById("target");
el.onpointerdown = downHandler;
```

مثال زیر، آزادسازی تصاحبِ اشاره‌گر را نشان می‌دهد (زمانی که رویداد {{domxref("Element/pointercancel_event", "pointercancel")}} رخ می‌دهد). مرورگر این کار را به‌صورت خودکار هنگام رخ‌دادن رویداد {{domxref("Element/pointerup_event", "pointerup")}} یا {{domxref("Element/pointercancel_event", "pointercancel")}} انجام می‌دهد.

```html
<div id="target">Touch me…</div>
```

```js
function downHandler(ev) {
  const el = document.getElementById("target");
  // Element "target" will receive/capture further events
  el.setPointerCapture(ev.pointerId);
}

function cancelHandler(ev) {
  const el = document.getElementById("target");
  // Release the pointer capture
  el.releasePointerCapture(ev.pointerId);
}

const el = document.getElementById("target");
// Register pointerdown and pointercancel handlers
el.onpointerdown = downHandler;
el.onpointercancel = cancelHandler;
```

## ویژگی CSS «touch-action»

ویژگی CSS {{cssxref("touch-action")}} برای مشخص‌کردن این استفاده می‌شود که آیا مرورگر باید رفتار لمسی پیش‌فرض (_بومی_) خود (مانند بزرگ‌نمایی یا پیمایش) را روی یک ناحیه اعمال کند یا نه. این ویژگی را می‌توان روی همهٔ عناصر اعمال کرد، به‌جز: عناصر درون‌خطیِ غیرجانشین (non-replaced inline)، ردیف‌های جدول، گروه‌های ردیف، ستون‌های جدول و گروه‌های ستون.

مقدار `auto` به این معناست که مرورگر مختار است رفتار لمسی پیش‌فرض خود را (در ناحیهٔ مشخص‌شده) اعمال کند و مقدار `none` رفتار لمسی پیش‌فرض مرورگر را برای آن ناحیه غیرفعال می‌کند. مقادیر `pan-x` و `pan-y` به‌ترتیب به این معنا هستند که لمس‌هایی که در ناحیهٔ مشخص‌شده شروع می‌شوند فقط برای پیمایش افقی و عمودی خواهند بود. مقدار `manipulation` به این معناست که مرورگر ممکن است لمس‌هایی را که روی عنصر شروع می‌شوند فقط برای پیمایش و بزرگ‌نمایی در نظر بگیرد.

در مثال زیر، رفتار پیش‌فرض لمسی برای برخی عناصر `button` غیرفعال شده است.

```css
button#tiny {
  touch-action: none;
}
```

در مثال زیر، وقتی عنصر `target` لمس شود، فقط در جهت افقی پیمایش خواهد شد.

```css
#target {
  touch-action: pan-x;
}
```

## سازگاری با رویدادهای ماوس

اگرچه رابط‌های Pointer Events به برنامه‌ها امکان می‌دهند تجربه‌های کاربری بهتری روی دستگاه‌های دارای اشاره‌گر ایجاد کنند، واقعیت این است که اکثریت قریب‌به‌اتفاق محتوای وب امروزی طوری طراحی شده است که فقط با ورودی ماوس کار کند. در نتیجه، حتی اگر مرورگری از Pointer Events پشتیبانی کند، باز هم باید رویدادهای ماوس را پردازش کند تا محتوایی که فقط ورودی ماوس را فرض می‌کند بدون تغییر مستقیم به کار خود ادامه دهد. در حالت ایده‌آل، یک برنامهٔ فعال‌شده با اشاره‌گر نیازی به مدیریت صریح ورودی ماوس ندارد. با این حال، از آنجا که مرورگر باید رویدادهای ماوس را پردازش کند، ممکن است مشکلات سازگاری وجود داشته باشد که باید به آن‌ها رسیدگی شود. این بخش حاوی اطلاعاتی دربارهٔ تعامل رویدادهای Pointer و رویدادهای ماوس و پیامدهای آن برای توسعه‌دهندگان برنامه است.

مرورگر _ممکن است ورودی عمومی اشاره‌گر را برای سازگاری با محتوای مبتنی بر ماوس، به رویدادهای ماوس نگاشت کند_. این نگاشت رویدادها _رویدادهای سازگاری ماوس_ نامیده می‌شود. نویسندگان می‌توانند با لغو رویداد pointerdown از تولید برخی رویدادهای سازگاری ماوس جلوگیری کنند، اما توجه داشته باشند که:

- رویدادهای ماوس فقط زمانی قابل جلوگیری هستند که اشاره‌گر در وضعیت پایین (down) باشد.
- اشاره‌گرهای در حالت hover (مثلاً ماوسی که هیچ دکمه‌ای فشرده نیست) رویدادهای ماوسشان قابل جلوگیری نیست.
- رویدادهای `mouseover`، `mouseout`، `mouseenter` و `mouseleave` هرگز قابل جلوگیری نیستند (حتی اگر اشاره‌گر در وضعیت down باشد).

## بهترین روش‌ها

در اینجا چند _بهترین روش_ برای در نظر گرفتن هنگام استفاده از Pointer Events آورده شده است:

- میزان کار انجام‌شده در کنترل‌کننده‌های رویداد را به حداقل برسانید.
- کنترل‌کننده‌های رویداد را به یک عنصر هدف مشخص اضافه کنید (به‌جای کل سند یا گره‌های بالاتر در درخت سند).
- عنصر هدف (گره) باید به اندازه‌ای بزرگ باشد که بزرگ‌ترین سطح تماس (معمولاً لمس انگشت) را در خود جای دهد. اگر ناحیهٔ هدف بیش از حد کوچک باشد، لمس آن ممکن است باعث صادرشدن رویدادهای دیگری برای عناصر مجاور شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

برخی مقادیر اضافی دیگر نیز برای ویژگی CSS {{cssxref("touch-action")}} به‌عنوان بخشی از مشخصات [Pointer Events](https://w3c.github.io/pointerevents/) تعریف شده‌اند، اما در حال حاضر پشتیبانی پیاده‌سازی این مقادیر محدود است.

## همچنین ببینید

- [رویدادهای لمس](/en-US/docs/Web/API/Touch_events)
- [گروه کاری Pointer Events](https://github.com/w3c/pointerevents)
- [فهرست پست الکترونیکی](https://lists.w3.org/Archives/Public/public-pointer-events/)
- [کانال IRC #pointerevents در W3C](irc://irc.w3.org:6667/)
- [آزمون‌ها و نسخه‌های نمایشی لمسی/اشاره‌گر](https://patrickhlauke.github.io/touch/) اثر Patrick H. Lauke