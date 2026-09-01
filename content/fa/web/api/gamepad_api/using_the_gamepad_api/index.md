---
title: Using the Gamepad API
slug: Web/API/Gamepad_API/Using_the_Gamepad_API
page-type: guide
browser-compat: api.Gamepad
---

{{DefaultAPISidebar("Gamepad API")}}

HTML اجزای لازم برای توسعهٔ بازیهای تعاملی و غنی را فراهم میکند. فناوریهایی مانند `<canvas>`، WebGL، `<audio>` و `<video>` همراه با پیادهسازیهای جاوااسکریپت، کارهایی را پشتیبانی میکنند که ویژگیهایی مشابه، اگر نه همان، با کد بومی ارائه میدهند. Gamepad API به توسعهدهندگان و طراحان اجازه میدهد تا به گیمپدها و سایر کنترلرهای بازی دسترسی داشته باشند و از آن‌ها استفاده کنند.

[Gamepad API](/en-US/docs/Web/API/Gamepad_API) رویدادهای جدیدی را روی شیء {{ domxref("Window") }} برای خواندن وضعیت گیمپد و کنترلر (که از این پس _گیمپد_ نامیده میشود) معرفی میکند. علاوه بر این رویدادها، این API همچنین یک شیء {{ domxref("Gamepad") }} اضافه میکند که می‌توانید برای پرس‌وجو دربارهٔ وضعیت یک گیمپد متصل از آن استفاده کنید، و یک متد {{ domxref("navigator.getGamepads()") }} که برای دریافت فهرستی از گیمپدهای شناخته‌شده برای صفحه در دسترس است.

## اتصال به یک گیمپد

وقتی یک گیمپد جدید به رایانه متصل می‌شود، صفحهٔ در حال فوکوس ابتدا یک رویداد {{ domxref("Window/gamepadconnected_event", "gamepadconnected") }} دریافت می‌کند. اگر هنگام بارگذاری صفحه، یک گیمپد از قبل متصل باشد، رویداد {{ domxref("Window/gamepadconnected_event", "gamepadconnected") }} زمانی به صفحهٔ در حال فوکوس ارسال می‌شود که کاربر دکمه‌ای را فشار دهد یا یک محور را حرکت دهد.

> [!NOTE]
> در فایرفاکس، گیمپدها فقط زمانی در معرض دید صفحه قرار می‌گیرند که کاربر با نمایان بودن صفحه با یکی از آن‌ها تعامل کند. این کار به جلوگیری از استفاده از گیمپدها برای [اثرانگشت دیجیتال](/en-US/docs/Glossary/Fingerprinting) کاربر کمک می‌کند. پس از تعامل با یک گیمپد، سایر گیمپدهایی که متصل هستند به‌طور خودکار قابل مشاهده خواهند شد.

می‌توانید از {{domxref("Window/gamepadconnected_event", "gamepadconnected")}} به این صورت استفاده کنید:

```js
window.addEventListener("gamepadconnected", (e) => {
  console.log(
    "Gamepad connected at index %d: %s. %d buttons, %d axes.",
    e.gamepad.index,
    e.gamepad.id,
    e.gamepad.buttons.length,
    e.gamepad.axes.length,
  );
});
```

هر گیمپد یک شناسهٔ یکتا دارد که از طریق ویژگی {{domxref("GamepadEvent.gamepad", "gamepad")}} رویداد در دسترس است.

## قطع اتصال یک گیمپد

هنگامی که یک گیمپد قطع می‌شود و اگر صفحه قبلاً داده‌هایی برای آن گیمپد دریافت کرده باشد (مثلاً {{ domxref("Window/gamepadconnected_event", "gamepadconnected") }})، رویداد دومی به پنجرهٔ در حال فوکوس ارسال می‌شود که {{domxref("Window.gamepaddisconnected_event", "gamepaddisconnected")}} نام دارد:

```js
window.addEventListener("gamepaddisconnected", (e) => {
  console.log(
    "Gamepad disconnected from index %d: %s",
    e.gamepad.index,
    e.gamepad.id,
  );
});
```

ویژگی {{domxref("Gamepad.index", "index")}} گیمپد برای هر دستگاه متصل به سیستم یکتا خواهد بود، حتی اگر چند کنترلر از یک نوع استفاده شوند. ویژگی `index` همچنین به‌عنوان شاخصی برای {{jsxref("Array")}} بازگردانده‌شده توسط {{ domxref("Navigator.getGamepads()") }} عمل می‌کند.

```js
const gamepads = {};

function gamepadHandler(event, connected) {
  const gamepad = event.gamepad;
  // Note: Use gamepad.index as the stable key, then read the latest
  // state from navigator.getGamepads() inside your update loop.

  if (connected) {
    gamepads[gamepad.index] = gamepad;
  } else {
    delete gamepads[gamepad.index];
  }
}

window.addEventListener("gamepadconnected", (e) => {
  gamepadHandler(e, true);
});
window.addEventListener("gamepaddisconnected", (e) => {
  gamepadHandler(e, false);
});
```

این مثال قبلی نشان می‌دهد که چگونه می‌توان دستگاه‌های متصل را با استفاده از `index` ردیابی کرد. برای وضعیت فعلی دکمه‌ها و محورها، هر فریم {{domxref("Navigator.getGamepads()")}} را فراخوانی کنید و آخرین شیء را برای آن `index` بخوانید.

## جست‌وجو در شیء Gamepad

همان‌طور که می‌بینید، رویدادهای **گیمپد** که در بالا بحث شد شامل یک ویژگی `gamepad` در شیء رویداد هستند که یک شیء {{ domxref("Gamepad") }} برمی‌گرداند. می‌توانیم از این برای تعیین اینکه کدام گیمپد (یعنی شناسهٔ آن) باعث رویداد شده استفاده کنیم، زیرا ممکن است چند گیمپد همزمان متصل باشند. برای خواندن وضعیت فعلی دکمه‌ها و محورها، از `index` گیمپد استفاده کنید و آخرین شیء را از {{ domxref("Navigator.getGamepads()") }} در حلقهٔ انیمیشن خود دریافت کنید.

انجام چنین بررسی‌هایی معمولاً شامل استفاده از شیء {{ domxref("Gamepad") }} همراه با یک حلقهٔ انیمیشن (مثلاً {{ domxref("Window.requestAnimationFrame","requestAnimationFrame") }}) است، جایی که توسعه‌دهندگان می‌خواهند بر اساس وضعیت گیمپد یا گیمپدها، برای فریم فعلی تصمیم بگیرند.

متد {{domxref("Navigator.getGamepads()")}} آرایه‌ای از همهٔ دستگاه‌های قابل مشاهده برای صفحهٔ وب را به‌صورت اشیاء {{ domxref("Gamepad") }} برمی‌گرداند (اولین مقدار همیشه `null` است، بنابراین اگر هیچ گیمپدی متصل نباشد `null` برگردانده می‌شود). سپس می‌توان از این برای دریافت همان اطلاعات استفاده کرد. به‌عنوان مثال، اولین مثال کد در بالا می‌تواند به شکل زیر بازنویسی شود:

```js
window.addEventListener("gamepadconnected", (e) => {
  const gp = navigator.getGamepads()[e.gamepad.index];
  console.log(
    "Gamepad connected at index %d: %s. %d buttons, %d axes.",
    gp.index,
    gp.id,
    gp.buttons.length,
    gp.axes.length,
  );
});
```

ویژگی‌های شیء {{ domxref("Gamepad") }} به شرح زیر است:

- `id`: رشته‌ای حاوی اطلاعاتی دربارهٔ کنترلر. این رشته به‌طور دقیق مشخص نشده است، اما در فایرفاکس شامل سه بخش اطلاعاتی است که با خط تیره (`-`) از هم جدا شده‌اند: دو رشتهٔ هگزادسیمال چهار رقمی که شناسهٔ USB فروشنده و محصول کنترلر را نشان می‌دهند و نام کنترلر که توسط درایور ارائه شده است. این اطلاعات برای این در نظر گرفته شده‌اند که بتوانید نگاشتی برای کنترل‌های دستگاه پیدا کنید و همچنین بازخورد مفیدی را به کاربر نمایش دهید.
- `index`: یک عدد صحیح که برای هر گیمپد متصل به سیستم در حال حاضر یکتا است. می‌توان از آن برای تشخیص چند کنترلر استفاده کرد. توجه داشته باشید که قطع اتصال یک دستگاه و سپس اتصال یک دستگاه جدید ممکن است شاخص قبلی را دوباره استفاده کند.
- `mapping`: رشته‌ای که نشان می‌دهد آیا مرورگر کنترل‌های دستگاه را به یک چیدمان شناخته‌شده نگاشت مجدد کرده است یا خیر. در حال حاضر فقط یک چیدمان شناخته‌شده پشتیبانی می‌شود — [گیمپد استاندارد](https://w3c.github.io/gamepad/gamepad.html#remapping). اگر مرورگر بتواند کنترل‌های دستگاه را به آن چیدمان نگاشت کند، ویژگی `mapping` روی رشتهٔ `standard` تنظیم می‌شود.
- `connected`: یک مقدار بولی که نشان می‌دهد آیا گیمپد همچنان به سیستم متصل است یا خیر. اگر چنین باشد مقدار `True` است؛ در غیر این صورت `False` است.
- `buttons`: آرایه‌ای از اشیاء {{ domxref("GamepadButton") }} که دکمه‌های موجود روی دستگاه را نشان می‌دهند. هر {{ domxref("GamepadButton") }} دارای ویژگی‌های `pressed` و `value` است:
  - ویژگی `pressed` یک مقدار بولی است که نشان می‌دهد دکمه در حال حاضر فشرده شده است (`true`) یا فشرده نشده است (`false`).
  - ویژگی `value` یک مقدار اعشاری است که برای نمایش دکمه‌های آنالوگ، مانند ماشه‌ها در بسیاری از گیمپدهای مدرن، استفاده می‌شود. مقادیر در محدودهٔ 0.0 تا 1.0 نرمال‌سازی می‌شوند، به طوری که 0.0 نشان‌دهندهٔ دکمهٔ فشرده‌نشده و 1.0 نشان‌دهندهٔ دکمهٔ کاملاً فشرده است.

- `axes`: آرایه‌ای که کنترل‌های دارای محور را روی دستگاه نشان می‌دهد (مثلاً انگشت‌های آنالوگ). هر ورودی در آرایه یک مقدار اعشاری در محدودهٔ 1.0- تا 1.0 است که موقعیت محور را از کمترین مقدار (1.0-) تا بیشترین مقدار (1.0) نشان می‌دهد.
- `timestamp`: این ویژگی یک {{ domxref("DOMHighResTimeStamp") }} برمی‌گرداند که آخرین زمانی را نشان می‌دهد که داده‌های این گیمپد به‌روزرسانی شده است و به توسعه‌دهندگان اجازه می‌دهد تعیین کنند آیا داده‌های `axes` و `button` از سخت‌افزار به‌روزرسانی شده‌اند یا خیر. مقدار باید نسبت به ویژگی `navigationStart` رابط {{ domxref("PerformanceTiming") }} باشد. مقادیر به‌صورت یکنواخت افزایش می‌یابند، به این معنی که می‌توان آن‌ها را مقایسه کرد تا ترتیب به‌روزرسانی‌ها مشخص شود، زیرا مقادیر جدیدتر همیشه بزرگ‌تر یا مساوی مقادیر قدیمی‌تر هستند. توجه داشته باشید که این ویژگی در حال حاضر در فایرفاکس پشتیبانی نمی‌شود.

> [!NOTE]
> شیء Gamepad به دلایل امنیتی روی رویداد {{ domxref("Window/gamepadconnected_event", "gamepadconnected") }} در دسترس است، نه روی خود شیء {{ domxref("Window") }}. همچنین می‌توانید از طریق {{domxref("Navigator.getGamepads()")}} به گیمپدها دسترسی داشته باشید. در عمل، بهتر است هر فریم {{domxref("Navigator.getGamepads()")}} را بررسی کرده و شیء فعلی را برای یک `index` شناخته‌شده بخوانید، به‌جای اتکا به ارجاع طولانی‌مدت از یک رویداد قبلی.

### استفاده از اطلاعات دکمه‌ها

بیایید به مثالی نگاه کنیم که اطلاعات اتصال یک گیمپد را نمایش می‌دهد (اتصالات بعدی گیمپد را نادیده می‌گیرد) و به شما اجازه می‌دهد با استفاده از چهار دکمهٔ گیمپد در سمت راست، یک توپ را روی صفحه حرکت دهید. می‌توانید [نسخهٔ زندهٔ demo را مشاهده کنید](https://chrisdavidmills.github.io/gamepad-buttons/) و [کد منبع را در GitHub پیدا کنید](https://github.com/chrisdavidmills/gamepad-buttons/tree/master).

برای شروع، چند متغیر اعلام می‌کنیم: پاراگراف `gamepadInfo` که اطلاعات اتصال در آن نوشته می‌شود، `ball` که می‌خواهیم حرکت دهیم، متغیر `start` که به‌عنوان شناسه برای `requestAnimationFrame` عمل می‌کند، متغیرهای `a` و `b` که به‌عنوان اصلاح‌کنندهٔ موقعیت برای حرکت توپ عمل می‌کنند، و متغیرهای کوتاه‌شده که برای نسخه‌های بین مرورگری {{ domxref("Window.requestAnimationFrame", "requestAnimationFrame()") }} و {{ domxref("Window.cancelAnimationFrame", "cancelAnimationFrame()") }} استفاده خواهند شد.

```js
const gamepadInfo = document.getElementById("gamepad-info");
const ball = document.getElementById("ball");
let start;
let a = 0;
let b = 0;
```

سپس از رویداد {{domxref("Window/gamepadconnected_event", "gamepadconnected")}} برای بررسی اتصال گیمپد استفاده می‌کنیم. وقتی یکی متصل شد، گیمپد را با استفاده از {{ domxref("Navigator.getGamepads()", "navigator.getGamepads()[0]") }} دریافت می‌کنیم، اطلاعات مربوط به گیمپد را در `div` اطلاعات گیمپد چاپ می‌کنیم و تابع `gameLoop()` را اجرا می‌کنیم که کل فرایند حرکت توپ را آغاز می‌کند.

```js
window.addEventListener("gamepadconnected", (e) => {
  const gp = navigator.getGamepads()[e.gamepad.index];
  gamepadInfo.textContent = `Gamepad connected at index ${gp.index}: ${gp.id}. It has ${gp.buttons.length} buttons and ${gp.axes.length} axes.`;

  gameLoop();
});
```

اکنون از رویداد {{domxref("Window/gamepaddisconnected_event", "gamepaddisconnected")}} برای بررسی قطع اتصال گیمپد استفاده می‌کنیم. اگر قطع شده باشد، حلقهٔ {{DOMxRef("Window.requestAnimationFrame", "requestAnimationFrame()")}} را متوقف می‌کنیم (به زیر مراجعه کنید) و اطلاعات گیمپد را به حالت اولیه برمی‌گردانیم.

```js
window.addEventListener("gamepaddisconnected", (e) => {
  gamepadInfo.textContent = "Waiting for gamepad.";

  cancelAnimationFrame(start);
});
```

حالا به حلقهٔ اصلی بازی می‌رسیم. در هر اجرای حلقه بررسی می‌کنیم که آیا یکی از چهار دکمه فشار داده شده است؛ اگر چنین باشد، مقادیر متغیرهای حرکتی `a` و `b` را به‌طور مناسب به‌روزرسانی می‌کنیم، سپس ویژگی‌های {{ cssxref("left") }} و {{ cssxref("top") }} را به‌روزرسانی کرده و مقادیر آن‌ها را به ترتیب به مقادیر فعلی `a` و `b` تغییر می‌دهیم. این اثر توپ را در اطراف صفحه حرکت می‌دهد.

پس از انجام همهٔ این کارها، از `requestAnimationFrame()` برای درخواست فریم انیمیشن بعدی استفاده می‌کنیم و دوباره `gameLoop()` را اجرا می‌کنیم.

```js
function gameLoop() {
  const gamepads = navigator.getGamepads();
  if (!gamepads) {
    return;
  }

  const gp = gamepads[0];
  if (gp.buttons[0].pressed) {
    b--;
  }
  if (gp.buttons[2].pressed) {
    b++;
  }
  if (gp.buttons[1].pressed) {
    a++;
  }
  if (gp.buttons[3].pressed) {
    a--;
  }

  ball.style.left = `${a * 2}px`;
  ball.style.top = `${b * 2}px`;

  start = requestAnimationFrame(gameLoop);
}
```

## مثال کامل: نمایش وضعیت گیمپد

این مثال نشان می‌دهد که چگونه می‌توان از شیء {{domxref("Gamepad")}} و همچنین رویدادهای {{domxref("Window/gamepadconnected_event", "gamepadconnected")}} و {{domxref("Window/gamepaddisconnected_event", "gamepaddisconnected")}} برای نمایش وضعیت همهٔ گیمپدهای متصل به سیستم استفاده کرد. این مثال بر اساس یک [دموی Gamepad](https://luser.github.io/gamepadtest/) است که [کد منبع آن در GitHub در دست