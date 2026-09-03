---
title: "Pointer Lock API"
---

---
title: Pointer Lock API
slug: Web/API/Pointer_Lock_API
page-type: web-api-overview
browser-compat:
  - api.Document.exitPointerLock
  - api.Element.requestPointerLock
spec-urls: https://w3c.github.io/pointerlock/
---

{{DefaultAPISidebar("Pointer Lock API")}}

**Pointer Lock API** (که پیشتر *Mouse Lock API* نامیده میشد) روش‌های ورودی مبتنی بر حرکت ماوس در طول زمان (یعنی دلتاها) را فراهم می‌کند، نه صرفاً موقعیت مطلق مکان‌نمای ماوس در viewport (نمایشگر دید). این API به شما امکان دسترسی به حرکت خام ماوس را می‌دهد، هدف رویدادهای ماوس را به یک عنصر واحد قفل می‌کند، محدودیت‌های میزان حرکت ماوس در یک جهت را از بین می‌برد و مکان‌نما را از دید خارج می‌کند. برای مثال، برای بازی‌های سه‌بعدی اول‌شخص ایده‌آل است.

علاوه بر این، این API برای هر برنامه‌ای که به ورودی قابل توجه ماوس برای کنترل حرکات، چرخاندن اشیا و تغییر ورودی‌ها نیاز دارد، مفید است؛ برای مثال، به کاربران اجازه می‌دهد بدون کلیک کردن روی هیچ دکمه‌ای، با حرکت دادن ماوس، زاویه دید را کنترل کنند. بدین ترتیب دکمه‌ها برای سایر اقدامات آزاد می‌شوند. سایر مثال‌ها شامل برنامه‌های نمایش نقشه یا تصاویر ماهواره‌ای است.

Pointer lock به شما امکان می‌دهد حتی زمانی که مکان‌نما از مرز مرورگر یا صفحه نمایش عبور می‌کند، به رویدادهای ماوس دسترسی داشته باشید. برای مثال، کاربران شما می‌توانند بدون توقف، با حرکت دادن ماوس، یک مدل سه‌بعدی را بچرخانند یا دستکاری کنند. بدون Pointer lock، چرخش یا دستکاری، به محض رسیدن مکان‌نما به لبه مرورگر یا صفحه نمایش متوقف می‌شود. بازیکنان اکنون می‌توانند روی دکمه‌ها کلیک کنند و مکان‌نمای ماوس را به جلو و عقب بکشند، بدون نگرانی از ترک منطقه بازی و کلیک تصادفی روی برنامه دیگری که ممکن است تمرکز ماوس را از بازی بگیرد.

## مفاهیم پایه

Pointer lock با [pointer capture (دریافت اشاره‌گر)](/en-US/docs/Web/API/Pointer_events#pointer_capture) مرتبط است. Pointer capture تحویل مداوم رویدادها را به یک عنصر هدف در حالی که ماوس در حال کشیده شدن است فراهم می‌کند، اما با رها شدن دکمه ماوس متوقف می‌شود. Pointer lock از جهات زیر با pointer capture متفاوت است:

- پایدار است: Pointer lock ماوس را آزاد نمی‌کند مگر اینکه یک فراخوانی صریح API انجام شود یا کاربر از یک ژست رهاسازی خاص استفاده کند.
- توسط مرزهای مرورگر یا صفحه نمایش محدود نمی‌شود.
- بدون توجه به وضعیت دکمه ماوس، به ارسال رویدادها ادامه می‌دهد.
- مکان‌نما را پنهان می‌کند.

## مرور کلی متدها و ویژگی‌ها

### متد requestPointerLock()

API Pointer lock، مشابه Fullscreen API، عناصر DOM را با افزودن متد جدیدی به نام {{domxref("Element.requestPointerLock","requestPointerLock()")}} گسترش می‌دهد. مثال زیر pointer lock را روی یک عنصر {{htmlelement("canvas")}} درخواست می‌کند:

```js
canvas.addEventListener("click", async () => {
  await canvas.requestPointerLock();
});
```

> [!NOTE]
> اگر کاربر از طریق [ژست قفل‌گشایی پیش‌فرض](https://w3c.github.io/pointerlock/#dfn-default-unlock-gesture) از حالت pointer lock خارج شده باشد، یا pointer lock قبلاً برای این سند وارد نشده باشد، سند باید قبل از موفقیت [`requestPointerLock`](https://w3c.github.io/pointerlock/#dom-element-requestpointerlock)، رویدادی را که در نتیجه یک [ژست درگیری](https://w3c.github.io/pointerlock/#dfn-engagement-gesture) تولید شده است دریافت کند. (برگرفته از <https://w3c.github.io/pointerlock/#extensions-to-the-element-interface>)

سیستم‌عامل‌ها شتاب ماوس را به‌طور پیش‌فرض فعال می‌کنند؛ این ویژگی زمانی مفید است که گاهی به حرکتی آهسته و دقیق نیاز دارید (به استفاده از یک نرم‌افزار گرافیکی فکر کنید) و در عین حال می‌خواهید با حرکت سریع‌تر ماوس مسافت‌های زیادی را طی کنید (به پیمایش و انتخاب چندین فایل فکر کنید). با این حال، برای برخی بازی‌های با دید اول‌شخص، داده‌های خام ورودی ماوس برای کنترل چرخش دوربین ترجیح داده می‌شوند — جایی که همان میزان حرکت، سریع یا آهسته، به چرخش یکسانی منجر می‌شود. به گفته گیمرهای حرفه‌ای، این امر تجربه بازی بهتر و دقت بالاتری را به همراه دارد.

برای غیرفعال کردن شتاب ماوس در سطح سیستم‌عامل و دسترسی به ورودی خام ماوس، می‌توانید گزینه `unadjustedMovement` را روی `true` تنظیم کنید:

```js
canvas.addEventListener("click", async () => {
  await canvas.requestPointerLock({
    unadjustedMovement: true,
  });
});
```

### مدیریت نسخه‌های Promise و غیر Promise مربوط به requestPointerLock()

قطعه کد بالا همچنان در مرورگرهایی که از نسخه مبتنی بر Promise مربوط به `requestPointerLock()` یا گزینه `unadjustedMovement` پشتیبانی نمی‌کنند کار خواهد کرد؛ عملگر [`await`](/en-US/docs/Web/JavaScript/Reference/Operators/await) در جلوی تابعی که Promise برنمی‌گرداند مجاز است و شیء options در مرورگرهای غیرپشتیبان نادیده گرفته می‌شود.

با این حال، این موضوع می‌تواند گیج‌کننده باشد و عوارض جانبی بالقوه دیگری نیز داشته باشد (برای مثال، تلاش برای استفاده از `requestPointerLock().then()` در مرورگرهای غیرپشتیبان خطا ایجاد می‌کند)، بنابراین ممکن است بخواهید این موضوع را به‌طور صریح و با استفاده از کدی مشابه کد زیر مدیریت کنید:

```js
function requestPointerLockWithUnadjustedMovement() {
  const promise = myTargetElement.requestPointerLock({
    unadjustedMovement: true,
  });

  if (!promise) {
    console.log("disabling mouse acceleration is not supported");
    return;
  }

  return promise
    .then(() => console.log("pointer is locked"))
    .catch((error) => {
      if (error.name === "NotSupportedError") {
        // Some platforms may not support unadjusted movement.
        // You can request again a regular pointer lock.
        return myTargetElement.requestPointerLock();
      }
    });
}
```

### ویژگی pointerLockElement و متد exitPointerLock()

API Pointer lock همچنین رابط {{domxref("Document")}} را گسترش می‌دهد و یک ویژگی و یک متد جدید به آن اضافه می‌کند:

- {{domxref("Document.pointerLockElement","pointerLockElement")}} برای دسترسی به عنصر قفل‌شده فعلی (در صورت وجود) استفاده می‌شود.
- {{domxref("Document.exitPointerLock","exitPointerLock()")}} برای خروج از حالت pointer lock استفاده می‌شود.

ویژگی {{domxref("Document.pointerLockElement","pointerLockElement")}} برای تعیین اینکه آیا عنصری در حال حاضر در حالت pointer lock قرار دارد (مثلاً برای انجام یک بررسی بولی) و همچنین برای دریافت ارجاعی به عنصر قفل‌شده، در صورت وجود، مفید است.

در اینجا نمونه‌ای از استفاده از `pointerLockElement` آورده شده است:

```js
if (document.pointerLockElement === canvas) {
  console.log("The pointer lock status is now locked");
} else {
  console.log("The pointer lock status is now unlocked");
}
```

متد {{domxref("Document.exitPointerLock()")}} برای خروج از حالت pointer lock استفاده می‌شود و مانند {{domxref("Element.requestPointerLock","requestPointerLock")}}، به‌صورت ناهمزمان با استفاده از رویدادهای {{domxref("Document/pointerlockchange_event", "pointerlockchange")}} و {{domxref("Document/pointerlockerror_event", "pointerlockerror")}} کار می‌کند که در ادامه درباره آن‌ها بیشتر خواهید دید.

```js
document.exitPointerLock();
```

### رویداد pointerlockchange

هنگامی که وضعیت Pointer lock تغییر می‌کند — برای مثال، هنگام فراخوانی {{domxref("Element.requestPointerLock","requestPointerLock()")}} یا {{domxref("Document.exitPointerLock","exitPointerLock()")}}، فشردن کلید ESC توسط کاربر و غیره — رویداد {{domxref("Document/pointerlockchange_event", "pointerlockchange")}} به سند (`document`) ارسال می‌شود. این یک رویداد ساده و بدون داده اضافی است.

```js
document.addEventListener("pointerlockchange", lockChangeAlert);

function lockChangeAlert() {
  if (document.pointerLockElement === canvas) {
    console.log("The pointer lock status is now locked");
    // Do something useful in response
  } else {
    console.log("The pointer lock status is now unlocked");
    // Do something useful in response
  }
}
```

### رویداد pointerlockerror

هنگامی که خطایی ناشی از فراخوانی {{domxref("Element.requestPointerLock","requestPointerLock()")}} یا {{domxref("Document.exitPointerLock","exitPointerLock()")}} رخ دهد، رویداد {{domxref("Document/pointerlockerror_event", "pointerlockerror")}} به سند (`document`) ارسال می‌شود. این یک رویداد ساده و بدون داده اضافی است.

```js
document.addEventListener("pointerlockerror", lockError);

function lockError(e) {
  alert("Pointer lock failed");
}
```

### توسعه‌های رویدادهای ماوس

API Pointer lock رابط معمولی {{domxref("MouseEvent")}} را با ویژگی‌های حرکت گسترش می‌دهد. دو ویژگی جدید برای رویدادهای ماوس — {{domxref("MouseEvent.movementX","movementX")}} و {{domxref("MouseEvent.movementY","movementY")}} — تغییر موقعیت ماوس را فراهم می‌کنند. مقادیر این پارامترها معادل تفاوت بین مقادیر ویژگی‌های {{domxref("MouseEvent")}} یعنی {{domxref("MouseEvent.screenX","screenX")}} و {{domxref("MouseEvent.screenY","screenY")}} است که در دو رویداد متوالی {{domxref("Element/mousemove_event", "mousemove")}}، با نام‌های `eNow` و `ePrevious` ذخیره شده‌اند. به عبارت دیگر، پارامتر Pointer lock به صورت `movementX = eNow.screenX - ePrevious.screenX` خواهد بود.

#### حالت قفل‌شده

هنگامی که Pointer lock فعال است، ویژگی‌های استاندارد {{domxref("MouseEvent")}} یعنی {{domxref("MouseEvent.clientX","clientX")}}، {{domxref("MouseEvent.clientY","clientY")}}، {{domxref("MouseEvent.screenX","screenX")}} و {{domxref("MouseEvent.screenY","screenY")}} ثابت نگه داشته می‌شوند، گویی ماوس در حال حرکت نیست. ویژگی‌های {{domxref("MouseEvent.movementX","movementX")}} و {{domxref("MouseEvent.movementY","movementY")}} همچنان تغییر موقعیت ماوس را فراهم می‌کنند. اگر ماوس به‌طور مداوم در یک جهت حرکت کند، هیچ محدودیتی برای مقادیر {{domxref("MouseEvent.movementX","movementX")}} و {{domxref("MouseEvent.movementY","movementY")}} وجود ندارد. مفهوم مکان‌نمای ماوس وجود ندارد و مکان‌نما نمی‌تواند از پنجره خارج شود یا توسط لبه صفحه نمایش محدود شود.

#### حالت قفل‌گشایی‌شده

پارامترهای {{domxref("MouseEvent.movementX","movementX")}} و {{domxref("MouseEvent.movementY","movementY")}} بدون توجه به وضعیت قفل ماوس معتبر هستند و برای سهولت، حتی در حالت قفل‌گشایی‌شده نیز در دسترس هستند.

هنگامی که ماوس قفل نیست، مکان‌نمای سیستم می‌تواند از پنجره مرورگر خارج شده و دوباره وارد شود. اگر این اتفاق بیفتد، {{domxref("MouseEvent.movementX","movementX")}} و {{domxref("MouseEvent.movementY","movementY")}} ممکن است روی صفر تنظیم شوند.

### بررسی گام‌به‌گام یک مثال ساده

ما یک [نسخه نمایشی pointer lock](https://mdn.github.io/dom-examples/pointer-lock/) ([مشاهده کد منبع](https://github.com/mdn/dom-examples/tree/main/pointer-lock)) نوشته‌ایم تا به شما نشان دهیم که چگونه می‌توانید از آن برای راه‌اندازی یک سیستم کنترلی ساده استفاده کنید. این نسخه نمایشی از JavaScript برای رسم یک توپ روی یک عنصر {{ htmlelement("canvas") }} استفاده می‌کند. هنگامی که روی canvas کلیک می‌کنید، pointer lock برای حذف مکان‌نمای ماوس استفاده می‌شود و به شما امکان می‌دهد توپ را مستقیماً با استفاده از ماوس حرکت دهید. بیایید ببینیم این چگونه کار می‌کند.

ما موقعیت‌های اولیه x و y را روی canvas تنظیم می‌کنیم:

```js
let x = 50;
let y = 50;
```

در مرحله بعد، یک شنونده رویداد تنظیم می‌کنیم تا متد `requestPointerLock()` را روی canvas هنگام کلیک شدن اجرا کند، که pointer lock را آغاز می‌کند. بررسی `document.pointerLockElement` برای این است که ببینیم آیا قبلاً یک pointer lock فعال وجود دارد یا خیر — اگر قبلاً pointer lock داریم، نمی‌خواهیم هر بار که داخل آن کلیک می‌کنیم، `requestPointerLock()` را دوباره روی canvas فراخوانی کنیم.

```js
canvas.addEventListener("click", async () => {
  if (!document.pointerLockElement) {
    await canvas.requestPointerLock({
      unadjustedMovement: true,
    });
  }
});
```

> [!NOTE]
> قطعه کد بالا در مرورگرهایی که از نسخه promise مربوط به `requestPointerLock()` پشتیبانی نمی‌کنند کار می‌کند. برای توضیح، به بخش [مدیریت نسخه‌های Promise و غیر Promise مربوط به requestPointerLock()](#handling_promise_and_non-promise_versions_of_requestpointerlock) مراجعه کنید.

اکنون به سراغ شنونده رویداد اختصاصی pointer lock می‌رویم: رویداد `pointerlockchange`. وقتی این رویداد رخ می‌دهد، تابعی به نام `lockChangeAlert()` را برای مدیریت تغییر اجرا می‌کنیم.

```js
document.addEventListener("pointerlockchange", lockChangeAlert);
```

این تابع ویژگی `pointerLockElement` را بررسی می‌کند تا ببیند آیا عنصر مورد نظر canvas ما است یا خیر. اگر چنین بود، یک شنونده رویداد برای مدیریت حرکات ماوس با تابع `updatePosition()` متصل می‌کند. اگر نه، دوباره شنونده رویداد را حذف می‌کند.

```js
function lockChangeAlert() {
  if (document.pointerLockElement === canvas) {
    console.log("The pointer lock status is now locked");
    document.addEventListener("mousemove", updatePosition);
  } else {
    console.log("The pointer lock status is now unlocked");
    document.removeEventListener("mousemove", updatePosition);
  }
}
```

تابع `updatePosition()` موقعیت توپ را روی canvas (مختصات `x` و `y`) به‌روزرسانی می‌کند و همچنین شامل دستورات `if ()` است تا بررسی کند که آیا توپ از لبه‌های canvas خارج شده است یا خیر. در صورت خروج، باعث می‌شود توپ به لبه مخالف منتقل شود (wrap around). همچنین شامل یک بررسی است که آیا قبلاً فراخوانی [`requestAnimationFrame()`](/en-US/docs/Web/API/Window/requestAnimationFrame) انجام شده است یا خیر؛ اگر چنین باشد، در صورت نیاز دوباره آن را فراخوانی کرده و تابع `canvasDraw()` را که صحنه canvas را به‌روزرسانی می‌کند، فراخوانی می‌کند. یک ردیاب (tracker) نیز برای نمایش مقادیر X و Y روی صفحه، به عنوان مرجع، راه‌اندازی شده است.

```js
const tracker = document.getElementById("tracker");

let animation;
function updatePosition(e) {
  x += e.movementX;
  y += e.movementY;
  if (x > canvas.width + RADIUS) {
    x = -RADIUS;
  }
  if (y > canvas.height + RADIUS) {
    y = -RADIUS;
  }
  if (x < -RADIUS) {
    x = canvas.width + RADIUS;
  }
  if (y < -RADIUS) {
    y = canvas.height + RADIUS;
  }
  tracker.textContent = `X position: ${x}, Y position: ${y}`;

  animation ??= requestAnimationFrame(() => {
    animation = null;
    canvasDraw();
  });
}
```

تابع `canvasDraw()` توپ را در موقعیت‌های فعلی `x` و `y` رسم می‌کند:

```js
function canvasDraw() {
  ctx.fillStyle = "black";
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ctx.fillStyle = "red";
  ctx.beginPath();
  ctx.arc(x, y, RADIUS, 0, degToRad(360), true);
  ctx.fill();
}
```

### محدودیت‌های IFrame

Pointer lock می‌تواند تنها یک {{htmlelement("iframe")}} را در هر بار قفل کند. اگر یک `<iframe>` را قفل کنید، نمی‌توانید `<iframe>` دیگری را قفل کرده و هدف را به آن منتقل کنید؛ در این صورت pointer lock با خطا مواجه می‌شود. برای جلوگیری از این محدودیت، ابتدا `<iframe>` قفل‌شده را قفل‌گشایی کنید و سپس دیگری را قفل کنید.

در حالی که `<iframe>`ها به‌طور پیش‌فرض کار می‌کنند، `<iframe>`های «sandboxed» (جعبه‌شنی) Pointer lock را مسدود می‌کنند. برای جلوگیری از این محدودیت، از `<iframe sandbox="allow-pointer-lock">` استفاده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("MouseEvent")}}
- {{domxref("Element.requestPointerLock()")}}