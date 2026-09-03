---
title: "Pinch zoom gestures"
---

---
title: Pinch zoom gestures
slug: Web/API/Pointer_events/Pinch_zoom_gestures
page-type: guide
---

{{DefaultAPISidebar("Pointer Events")}}

افزودن _ژست‌ها_ به یک برنامه می‌تواند تجربهٔ کاربری را به‌طور چشمگیری بهبود بخشد. ژست‌ها انواع گوناگونی دارند، از ژست سادهٔ تک‌لمسیِ _کشیدن (swipe)_ گرفته تا ژست پیچیده‌ترِ چندلمسیِ _چرخاندن (twist)_، که در آن نقاط لمس (که _نشانگرها_ نیز نامیده می‌شوند) در جهت‌های مختلف حرکت می‌کنند.

این مثال نشان می‌دهد که چگونه می‌توان ژست _پینچ/زوم (pinch/zoom)_ را شناسایی کرد؛ ژستی که از [رویدادهای نشانگر](/en-US/docs/Web/API/Pointer_events) استفاده می‌کند تا تشخیص دهد کاربر دو نشانگر را به یکدیگر نزدیک کرده یا آن‌ها را از هم دور کرده است.

نسخهٔ _زندهٔ_ این برنامه در [GitHub](https://mdn.github.io/dom-examples/pointerevents/Pinch_zoom_gestures.html) در دسترس است. [کد منبع](https://github.com/mdn/dom-examples/blob/main/pointerevents/Pinch_zoom_gestures.html) نیز در GitHub قرار دارد؛ درخواست‌های Pull Request و [گزارش‌های باگ](https://github.com/mdn/dom-examples/issues) پذیرفته می‌شوند.

## مثال

در این مثال، از [رویدادهای نشانگر](/en-US/docs/Web/API/Pointer_events) استفاده می‌شود تا هم‌زمان دو دستگاه اشاره‌گر از هر نوع، از جمله انگشت، موس و قلم، شناسایی شوند. ژستِ _بستن پینچ_ (pinch in؛ کوچک‌نمایی) که دو نشانگر را به سمت یکدیگر حرکت می‌دهد، رنگ پس‌زمینهٔ عنصر هدف را به `lightblue` تغییر می‌دهد. ژستِ _باز کردن پینچ_ (pinch out؛ بزرگ‌نمایی) که دو نشانگر را از یکدیگر دور می‌کند، رنگ پس‌زمینهٔ عنصر هدف را به `pink` تغییر می‌دهد.

### تعریف هدف لمس

برنامه برای تعریف ناحیه‌های هدفِ نشانگرها از یک عنصر {{HTMLElement("div")}} استفاده می‌کند.

```css
div {
  margin: 0em;
  padding: 2em;
}
#target {
  background: white;
  border: 1px solid black;
}
```

### حالت سراسری

پشتیبانی از یک ژست دونشانگری مستلزم نگهداری حالت رویدادِ نشانگرها در فازهای مختلف رویداد است. این برنامه برای کش‌کردن حالت رویداد از دو متغیر سراسری استفاده می‌کند.

```js
// Global vars to cache event state
const evCache = [];
let prevDiff = -1;
```

### ثبت رویدادگردان‌ها

برای رویدادهای نشانگر زیر، رویدادگردان ثبت می‌شود: {{domxref("Element/pointerdown_event", "pointerdown")}}، {{domxref("Element/pointermove_event", "pointermove")}} و {{domxref("Element/pointerup_event", "pointerup")}}. از رویدادگردانِ رویداد {{domxref("Element/pointerup_event", "pointerup")}} برای رویدادهای {{domxref("Element/pointercancel_event", "pointercancel")}}، {{domxref("Element/pointerout_event", "pointerout")}} و {{domxref("Element/pointerleave_event", "pointerleave")}} نیز استفاده می‌شود، زیرا در این برنامه این چهار رویداد معنای یکسانی دارند.

```js
// Install event handlers for the pointer target
const el = document.getElementById("target");
el.onpointerdown = pointerdownHandler;
el.onpointermove = pointermoveHandler;

// Use same handler for pointer{up,cancel,out,leave} events since
// the semantics for these events - in this app - are the same.
el.onpointerup = pointerupHandler;
el.onpointercancel = pointerupHandler;
el.onpointerout = pointerupHandler;
el.onpointerleave = pointerupHandler;
```

### فشردن نشانگر

رویداد {{domxref("Element/pointerdown_event", "pointerdown")}} زمانی رخ می‌دهد که یک نشانگر (موس، قلم/استایلوس یا نقطهٔ لمس روی صفحهٔ لمسی) با _سطح تماس_ تماس برقرار کند. در این برنامه، حالت رویداد باید در حافظهٔ کش نگهداری شود، زیرا ممکن است این رویدادِ فشردن (down) بخشی از یک ژست پینچ/زوم دونشانگری باشد.

```js
function pointerdownHandler(ev) {
  // The pointerdown event signals the start of a touch interaction.
  // This event is cached to support 2-finger gestures
  evCache.push(ev);
  log("pointerDown", ev);
}
```

### حرکت نشانگر

رویدادگردان {{domxref("Element/pointermove_event", "pointermove")}} تشخیص می‌دهد که آیا کاربر در حال اجرای یک ژست پینچ/زوم دونشانگری است. اگر دو نشانگر فعال باشند و فاصلهٔ بین آن دو افزایش یابد (یعنی باز شدن پینچ یا بزرگ‌نمایی)، رنگ پس‌زمینهٔ عنصر به `pink` تغییر می‌کند؛ و اگر فاصلهٔ بین دو نشانگر کاهش یابد (یعنی بسته شدن پینچ یا کوچک‌نمایی)، رنگ پس‌زمینه به `lightblue` تغییر می‌کند. در یک برنامهٔ پیچیده‌تر، می‌توان از تشخیصِ بسته یا باز شدن پینچ برای اعمال رفتارهای مختص آن برنامه استفاده کرد.

هنگام پردازش این رویداد، حاشیهٔ عنصر هدف به حالت `dashed` تنظیم می‌شود تا نشانهٔ بصری واضحی از دریافت رویداد حرکت توسط آن عنصر فراهم شود.

```js
function pointermoveHandler(ev) {
  // This function implements a 2-pointer pinch/zoom gesture.
  //
  // If the distance between the two pointers has increased (zoom in),
  // the target element's background is changed to "pink" and if the
  // distance is decreasing (zoom out), the color is changed to "lightblue".
  //
  // This function sets the target element's border to "dashed" to visually
  // indicate the pointer's target received a move event.
  log("pointerMove", ev);
  ev.target.style.border = "dashed";

  // Find this event in the cache and update its record with this event
  const index = evCache.findIndex(
    (cachedEv) => cachedEv.pointerId === ev.pointerId,
  );
  evCache[index] = ev;

  // If two pointers are down, check for pinch gestures
  if (evCache.length === 2) {
    // Calculate the distance between the two pointers
    const curDiff = Math.hypot(
      evCache[0].clientX - evCache[1].clientX,
      evCache[0].clientY - evCache[1].clientY,
    );

    if (prevDiff > 0) {
      if (curDiff > prevDiff) {
        // The distance between the two pointers has increased
        log("Pinch moving OUT -> Zoom in", ev);
        ev.target.style.background = "pink";
      }
      if (curDiff < prevDiff) {
        // The distance between the two pointers has decreased
        log("Pinch moving IN -> Zoom out", ev);
        ev.target.style.background = "lightblue";
      }
    }

    // Cache the distance for the next move event
    prevDiff = curDiff;
  }
}
```

### رها کردن نشانگر

رویداد {{domxref("Element/pointerup_event", "pointerup")}} زمانی رخ می‌دهد که یک نشانگر از _سطح تماس_ برداشته شود. در این هنگام، رویداد از حافظهٔ کش رویدادها حذف می‌شود و رنگ پس‌زمینه و حاشیهٔ عنصر هدف به مقادیر اولیهٔ خود بازگردانده می‌شوند.

در این برنامه، از همین رویدادگردان برای رویدادهای {{domxref("Element/pointercancel_event", "pointercancel")}}، {{domxref("Element/pointerleave_event", "pointerleave")}} و {{domxref("Element/pointerout_event", "pointerout")}} نیز استفاده می‌شود.

```js
function pointerupHandler(ev) {
  log(ev.type, ev);
  // Remove this pointer from the cache and reset the target's
  // background and border
  removeEvent(ev);
  ev.target.style.background = "white";
  ev.target.style.border = "1px solid black";

  // If the number of pointers down is less than two then reset diff tracker
  if (evCache.length < 2) {
    prevDiff = -1;
  }
}
```

### رابط کاربری برنامه

برنامه برای ناحیهٔ لمس از یک عنصر {{HTMLElement("div")}} استفاده می‌کند و دکمه‌هایی برای فعال‌کردن ثبت رویدادها و پاک‌کردن گزارش در اختیار کاربر قرار می‌دهد.

برای جلوگیری از بازنویسی مدیریت نشانگرِ این برنامه توسط رفتار لمس پیش‌فرض مرورگر، ویژگی {{cssxref("touch-action")}} روی عنصر {{HTMLElement("body")}} اعمال شده است.

```html
<div id="target">
  Touch and Hold with 2 pointers, then pinch in or out.<br />
  The background color will change to pink if the pinch is opening (Zoom In) or
  changes to lightblue if the pinch is closing (Zoom out).
</div>
<!-- UI for logging/debugging -->
<button id="log">Start/Stop event logging</button>
<button id="clear-log">Clear the log</button>
<p></p>
<output></output>
```

```css
body {
  touch-action: none; /* Prevent default touch behavior */
}
```

### توابع متفرقه

این توابع از برنامه پشتیبانی می‌کنند اما مستقیماً در جریان رویدادها دخالت ندارند.

#### مدیریت حافظهٔ کش

این تابع به مدیریت کش سراسری رویدادها، یعنی `evCache`، کمک می‌کند.

```js
function removeEvent(ev) {
  // Remove this event from the target's cache
  const index = evCache.findIndex(
    (cachedEv) => cachedEv.pointerId === ev.pointerId,
  );
  evCache.splice(index, 1);
}
```

#### ثبت رویدادها

این توابع برای ارسال فعالیت رویدادها به پنجرهٔ برنامه استفاده می‌شوند (برای پشتیبانی از اشکال‌زدایی و یادگیری جریان رویدادها).

```js
// Log events flag
let logEvents = false;

document.getElementById("log").addEventListener("click", enableLog);
document.getElementById("clear-log").addEventListener("click", clearLog);

// Logging/debugging functions
function enableLog(ev) {
  logEvents = !logEvents;
}

function log(prefix, ev) {
  if (!logEvents) return;
  const o = document.getElementsByTagName("output")[0];
  o.innerText += `${prefix}:
  pointerID   = ${ev.pointerId}
  pointerType = ${ev.pointerType}
  isPrimary   = ${ev.isPrimary}
`;
}

function clearLog(event) {
  const o = document.getElementsByTagName("output")[0];
  o.textContent = "";
}
```

## همچنین ببینید

- [Pointer Events now in Firefox Nightly](https://hacks.mozilla.org/2015/08/pointer-events-now-in-firefox-nightly/)؛ Mozilla Hacks؛ نوشتهٔ Matt Brubeck و Jason Weathersby؛ ۴ اوت ۲۰۱۵
- [jQuery Pointer Events Polyfill](https://github.com/jquery-archive/PEP)
- [ژست‌ها (Gestures)](https://m2.material.io/design/interaction/gestures.html)؛ Material Design