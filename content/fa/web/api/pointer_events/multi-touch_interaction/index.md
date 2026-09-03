---
title: Multi-touch interaction
slug: Web/API/Pointer_events/Multi-touch_interaction
page-type: guide
---

{{DefaultAPISidebar("Pointer Events")}}

رویدادهای اشاره‌گر، رویدادهای ورودی DOM را گسترش می‌دهند تا از انواع دستگاه‌های ورودی اشاره‌گر مانند قلم/استایلوس و صفحه‌های لمسی و همچنین ماوس پشتیبانی کنند. _اشاره‌گر_ دستگاهی مستقل از سخت‌افزار است که می‌تواند مجموعه‌ای خاص از مختصات صفحه را هدف قرار دهد. داشتن یک مدل رویداد واحد برای اشاره‌گرها می‌تواند ایجاد وب‌سایت‌ها و برنامه‌ها را ساده‌تر کند و بدون توجه به سخت‌افزار کاربر، تجربه کاربری خوبی ارائه دهد.

رویدادهای اشاره‌گر شباهت‌های زیادی به رویدادهای ماوس دارند، اما از چند اشاره‌گر همزمان، مانند چند انگشت روی صفحه لمسی، پشتیبانی می‌کنند. این قابلیت اضافه می‌تواند برای ارائه مدل‌های تعامل غنی‌تر به کار رود، اما به بهای پیچیدگی بیشتر در مدیریت تعامل‌های چندلمسی تمام می‌شود. این سند با مثال کدنویسی نشان می‌دهد که چگونه می‌توان از رویدادهای اشاره‌گر با تعامل‌های مختلف چندلمسی استفاده کرد.

نسخه _زنده_ این برنامه در [GitHub](https://mdn.github.io/dom-examples/pointerevents/Multi-touch_interaction.html) در دسترس است. [کد منبع در GitHub](https://github.com/mdn/dom-examples/blob/main/pointerevents/Multi-touch_interaction.html) موجود است؛ Pull Requestها و [گزارش‌های خطا](https://github.com/mdn/dom-examples/issues) مورد استقبال هستند.

## مثال

این مثال استفاده از انواع رویدادهای اشاره‌گر ({{domxref("Element/pointerdown_event", "pointerdown")}}، {{domxref("Element/pointermove_event", "pointermove")}}، {{domxref("Element/pointerup_event", "pointerup")}}، {{domxref("Element/pointercancel_event", "pointercancel")}} و غیره) را برای تعامل‌های مختلف چندلمسی نشان می‌دهد.

### تعریف اهداف لمس

این برنامه برای تعریف سه ناحیه هدف لمس مختلف از {{HTMLElement("div")}} استفاده می‌کند.

```css
div {
  margin: 0em;
  padding: 2em;
}
#target1 {
  background: white;
  border: 1px solid black;
}
#target2 {
  background: white;
  border: 1px solid black;
}
#target3 {
  background: white;
  border: 1px solid black;
}
```

### وضعیت سراسری

برای پشتیبانی از تعامل چندلمسی، باید وضعیت رویداد اشاره‌گر در طول فازهای مختلف رویداد حفظ شود. این برنامه از سه آرایه برای کش کردن وضعیت رویداد استفاده می‌کند؛ برای هر عنصر هدف یک کش.

```js
// Log events flag
const logEvents = false;

// Event caches, one per touch target
const evCache1 = [];
const evCache2 = [];
const evCache3 = [];
```

### ثبت دستگیرنده‌های رویداد

دستگیرنده‌های رویداد برای رویدادهای اشاره‌گر زیر ثبت می‌شوند: {{domxref("Element/pointerdown_event", "pointerdown")}}، {{domxref("Element/pointermove_event", "pointermove")}} و {{domxref("Element/pointerup_event", "pointerup")}}. از دستگیرنده رویداد {{domxref("Element/pointerup_event", "pointerup")}} برای رویدادهای {{domxref("Element/pointercancel_event", "pointercancel")}}، {{domxref("Element/pointerout_event", "pointerout")}} و {{domxref("Element/pointerleave_event", "pointerleave")}} نیز استفاده می‌شود، زیرا این چهار رویداد در این برنامه معنای یکسانی دارند.

```js
function setHandlers(name) {
  // Install event handlers for the given element
  const el = document.getElementById(name);
  el.onpointerdown = pointerdownHandler;
  el.onpointermove = pointermoveHandler;

  // Use same handler for pointer{up,cancel,out,leave} events since
  // the semantics for these events - in this app - are the same.
  el.onpointerup = pointerupHandler;
  el.onpointercancel = pointerupHandler;
  el.onpointerout = pointerupHandler;
  el.onpointerleave = pointerupHandler;
}

setHandlers("target1");
setHandlers("target2");
setHandlers("target3");
```

### رویداد pointerdown

رویداد {{domxref("Element/pointerdown_event", "pointerdown")}} زمانی رخ می‌دهد که یک اشاره‌گر (ماوس، قلم/استایلوس یا نقطه لمس روی صفحه لمسی) با _سطح تماس_ تماس برقرار کند. وضعیت رویداد باید در کش ذخیره شود، در صورتی که این رویداد فشردن، بخشی از یک تعامل چندلمسی باشد.

در این برنامه، وقتی اشاره‌گری روی یک عنصر قرار می‌گیرد، رنگ پس‌زمینه عنصر با توجه به تعداد نقاط لمس فعال آن عنصر تغییر می‌کند. برای جزئیات بیشتر درباره تغییر رنگ‌ها به تابع [`update_background`](#update_background_color) مراجعه کنید.

```js
function pointerdownHandler(ev) {
  // The pointerdown event signals the start of a touch interaction.
  // Save this event for later processing (this could be part of a
  // multi-touch interaction) and update the background color
  pushEvent(ev);
  if (logEvents) {
    log(`pointerDown: name = ${ev.target.id}`, ev);
  }
  updateBackground(ev);
}
```

### رویداد pointermove

دستگیرنده رویداد pointermove زمانی فراخوانی می‌شود که اشاره‌گر حرکت کند. ممکن است این دستگیرنده چندین بار (مثلاً اگر کاربر اشاره‌گر را حرکت دهد) فراخوانی شود، پیش از آنکه نوع رویداد دیگری به وقوع بپیوندد.

در این برنامه، حرکت اشاره‌گر با قرار دادن حاشیه عنصر هدف روی `dashed` نمایش داده می‌شود تا نشانه تصویری واضحی ارائه شود که عنصر این رویداد را دریافت کرده است.

```js
function pointermoveHandler(ev) {
  // Note: if the user makes more than one "simultaneous" touch, most browsers
  // fire at least one pointermove event and some will fire several pointermove events.
  //
  // This function sets the target element's border to "dashed" to visually
  // indicate the target received a move event.
  if (logEvents) {
    log("pointerMove", ev);
  }
  updateBackground(ev);
  ev.target.style.border = "dashed";
}
```

### رویداد pointerup

رویداد {{domxref("Element/pointerup_event", "pointerup")}} زمانی رخ می‌دهد که یک اشاره‌گر از _سطح تماس_ برداشته شود. وقتی این اتفاق می‌افتد، رویداد از کش رویداد مرتبط حذف می‌شود.

در این برنامه، این دستگیرنده برای رویدادهای {{domxref("Element/pointercancel_event", "pointercancel")}}، {{domxref("Element/pointerleave_event", "pointerleave")}} و {{domxref("Element/pointerout_event", "pointerout")}} نیز استفاده می‌شود.

```js
function pointerupHandler(ev) {
  if (logEvents) {
    log(ev.type, ev);
  }
  // Remove this touch point from the cache and reset the target's
  // background and border
  removeEvent(ev);
  updateBackground(ev);
  ev.target.style.border = "1px solid black";
}
```

### رابط کاربری برنامه

این برنامه از عناصر {{HTMLElement("div")}} برای نواحی لمس استفاده می‌کند و دکمه‌هایی برای فعال کردن ثبت رویدادها (logging) و پاک کردن گزارش فراهم می‌آورد.

برای جلوگیری از اینکه رفتار پیش‌فرض لمس مرورگر، مدیریت اشاره‌گر این برنامه را تحت‌الشعاع قرار دهد، ویژگی {{cssxref("touch-action")}} روی عنصر {{HTMLElement("body")}} اعمال شده است.

```html
<div id="target1">Tap, Hold or Swipe me 1</div>
<div id="target2">Tap, Hold or Swipe me 2</div>
<div id="target3">Tap, Hold or Swipe me 3</div>

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

### سایر توابع

این توابع از برنامه پشتیبانی می‌کنند، اما مستقیماً در جریان رویدادها دخالت ندارند.

#### مدیریت کش

این توابع کش‌های سراسری رویداد `evCache1`، `evCache2` و `evCache3` را مدیریت می‌کنند.

```js
function getCache(ev) {
  // Return the cache for this event's target element
  switch (ev.target.id) {
    case "target1":
      return evCache1;
    case "target2":
      return evCache2;
    case "target3":
      return evCache3;
    default:
      log("Error with cache handling", ev);
  }
}

function pushEvent(ev) {
  // Save this event in the target's cache
  const evCache = getCache(ev);
  evCache.push(ev);
}

function removeEvent(ev) {
  // Remove this event from the target's cache
  const evCache = getCache(ev);
  const index = evCache.findIndex(
    (cachedEv) => cachedEv.pointerId === ev.pointerId,
  );
  evCache.splice(index, 1);
}
```

#### به‌روزرسانی رنگ پس‌زمینه

رنگ پس‌زمینه نواحی لمس به صورت زیر تغییر می‌کند: وقتی هیچ لمس فعالی وجود نداشته باشد، رنگ `white`؛ با یک لمس فعال، `yellow`؛ با دو لمس همزمان، `pink`؛ و با سه لمس همزمان یا بیشتر، `lightblue` خواهد بود.

```js
function updateBackground(ev) {
  // Change background color based on the number of simultaneous touches/pointers
  // currently down:
  //   white - target element has no touch points i.e. no pointers down
  //   yellow - one pointer down
  //   pink - two pointers down
  //   lightblue - three or more pointers down
  const evCache = getCache(ev);
  switch (evCache.length) {
    case 0:
      // Target element has no touch points
      ev.target.style.background = "white";
      break;
    case 1:
      // Single touch point
      ev.target.style.background = "yellow";
      break;
    case 2:
      // Two simultaneous touch points
      ev.target.style.background = "pink";
      break;
    default:
      // Three or more simultaneous touches
      ev.target.style.background = "lightblue";
  }
}
```

#### ثبت رویدادها

این توابع برای ارسال فعالیت رویدادها به پنجره برنامه استفاده می‌شوند (برای پشتیبانی از اشکال‌زدایی و یادگیری در مورد جریان رویدادها).

```js
// Log events flag
let logEvents = false;

document.getElementById("log").addEventListener("click", enableLog);
document.getElementById("clear-log").addEventListener("click", clearLog);

function enableLog(ev) {
  logEvents = !logEvents;
}

function log(name, ev) {
  const o = document.getElementsByTagName("output")[0];
  o.innerText += `${name}:
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