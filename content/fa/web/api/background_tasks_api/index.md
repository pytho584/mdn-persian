---
title: "Background Tasks API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Background_Tasks_API"
translated_by: "n8n + AI"
---

---
title: Background Tasks API
slug: Web/API/Background_Tasks_API
page-type: web-api-overview
browser-compat: api.Window.requestIdleCallback
---

{{DefaultAPISidebar("Background Tasks")}}

**API زمان‌بندی مشارکتی وظایف پس‌زمینه** (همچنین با نام API وظایف پس‌زمینه یا API `requestIdleCallback()`) قابلیت قرار دادن وظایف در صف را فراهم می‌کند تا زمانی که عامل کاربر تشخیص دهد زمان آزاد برای انجام آن‌ها وجود دارد، به‌طور خودکار اجرا شوند.

> [!NOTE]
> این API در [کارگران وب](/en-US/docs/Web/API/Web_Workers_API) در دسترس نیست.

## مفاهیم و کاربرد

رشته اصلی یک مرورگر وب حول حلقه رویداد آن متمرکز است. این کد هر به‌روزرسانی در انتظار را به {{domxref("Document")}} در حال نمایش می‌کشد، هر کد جاوااسکریپتی که صفحه نیاز دارد را اجرا می‌کند، رویدادها را از دستگاه‌های ورودی می‌پذیرد و آن رویدادها را به عناصری که باید دریافت کنند، ارسال می‌کند. علاوه بر این، حلقه رویداد تعاملات با سیستم عامل، به‌روزرسانی‌های رابط کاربری خود مرورگر و موارد دیگر را نیز مدیریت می‌کند. این یک قطعه کد بسیار پرمشغله است و کد جاوااسکریپت اصلی شما ممکن است درست درون همین رشته همراه با تمام این موارد اجرا شود. مطمئناً بیشتر اگر نه تمام کدهایی که قادر به ایجاد تغییرات در DOM هستند، در رشته اصلی اجرا می‌شوند، زیرا معمولاً تغییرات رابط کاربری فقط در رشته اصلی در دسترس هستند.

از آنجایی که مدیریت رویداد و به‌روزرسانی صفحه دو مورد از واضح‌ترین راه‌هایی هستند که کاربران مشکلات عملکرد را متوجه می‌شوند، مهم است که کد شما یک شهروند خوب وب باشد و به جلوگیری از توقف در اجرای حلقه رویداد کمک کند. در گذشته، هیچ راه قابل اعتمادی برای انجام این کار وجود نداشت جز نوشتن کدی تا حد امکان کارآمد و واگذاری هرچه بیشتر کار به [کارگران](/en-US/docs/Web/API/Web_Workers_API). {{domxref("Window.requestIdleCallback()")}} با اجازه دادن به مرورگر برای اینکه به کد شما بگوید چقدر زمان می‌تواند با خیال راحت بدون ایجاد کندی سیستم استفاده کند، این امکان را فراهم می‌کند که فعالانه در کمک به اجرای روان حلقه رویداد مرورگر مشارکت کنید. اگر در محدوده داده شده باقی بمانید، می‌توانید تجربه کاربر را بسیار بهتر کنید.

### بهره‌وری بیشتر از بازخوانی‌های بیکار

از آنجایی که بازخوانی‌های بیکار برای ارائه راهی به کد شما برای همکاری با حلقه رویداد در نظر گرفته شده‌اند تا اطمینان حاصل شود که سیستم به طور کامل بدون فشار بیش از حد استفاده می‌شود و در نتیجه کندی یا سایر مشکلات عملکرد ایجاد نمی‌شود، باید در مورد نحوه استفاده از آن‌ها دقت کنید.

- **از بازخوانی‌های بیکار برای وظایفی استفاده کنید که اولویت بالایی ندارند.** چون نمی‌دانید چند بازخوانی ایجاد شده است و نمی‌دانید سیستم کاربر چقدر شلوغ است، نمی‌دانید بازخوانی شما چند وقت یک بار اجرا می‌شود (مگر اینکه یک `timeout` مشخص کنید). هیچ تضمینی وجود ندارد که هر بار عبور از حلقه رویداد (یا حتی هر چرخه به‌روزرسانی صفحه) شامل اجرای هیچ بازخوانی بیکاری باشد؛ اگر حلقه رویداد از تمام زمان موجود استفاده کند، شانس ندارید (دوباره، مگر اینکه از `timeout` استفاده کرده باشید).
- **بازخوانی‌های بیکار باید بهترین تلاش خود را انجام دهند تا از زمان اختصاص داده شده تجاوز نکنند.** در حالی که مرورگر، کد شما و وب به طور کلی اگر از محدوده زمانی مشخص شده فراتر بروید (حتی اگر خیلی زیاد فراتر بروید) به طور عادی به کار خود ادامه می‌دهند، محدودیت زمانی برای اطمینان از این است که شما زمان کافی برای سیستم باقی بگذارید تا عبور فعلی از حلقه رویداد را به پایان برساند و به عبور بعدی برود بدون اینکه باعث لرزش کد دیگر یا تأخیر در انیمیشن‌ها شود. در حال حاضر، {{domxref("IdleDeadline.timeRemaining", "timeRemaining()")}} یک حد بالای ۵۰ میلی‌ثانیه دارد، اما در واقعیت اغلب زمان کمتری از آن خواهید داشت، زیرا حلقه رویداد ممکن است در سایت‌های پیچیده از آن زمان استفاده کند، افزونه‌های مرورگر به زمان پردازنده نیاز دارند و غیره.
- **از ایجاد تغییرات در DOM درون بازخوانی بیکار خود خودداری کنید.** زمانی که بازخوانی شما اجرا می‌شود، فریم فعلی قبلاً ترسیم شده است و تمام به‌روزرسانی‌های طرح‌بندی و محاسبات تکمیل شده‌اند. اگر تغییراتی ایجاد کنید که بر طرح‌بندی تأثیر بگذارد، ممکن است مجبور شوید مرورگر را مجبور به توقف و انجام محاسبات مجددی کنید که در غیر این صورت غیرضروری بودند. اگر بازخوانی شما نیاز به تغییر DOM دارد، باید از {{domxref("Window.requestAnimationFrame()")}} برای زمان‌بندی آن استفاده کند.
- **از وظایفی که زمان اجرای آن‌ها قابل پیش‌بینی نیست خودداری کنید.** بازخوانی بیکار شما باید از انجام هر کاری که ممکن است زمان غیرقابل پیش‌بینی ببرد خودداری کند. به عنوان مثال، از هر چیزی که ممکن است بر طرح‌بندی تأثیر بگذارد باید اجتناب شود. همچنین باید از حل یا رد {{jsxref("Promise")}}ها خودداری کنید، زیرا این کار باعث فراخوانی مدیریت‌کننده آن وعده به محض بازگشت بازخوانی شما می‌شود.
- **در صورت نیاز از timeout استفاده کنید، اما فقط زمانی که نیاز دارید.** استفاده از timeout می‌تواند اطمینان حاصل کند که کد شما به موقع اجرا می‌شود، اما همچنین می‌تواند باعث کندی یا لرزش انیمیشن شود با الزام مرورگر به فراخوانی شما زمانی که زمان کافی برای اجرا بدون اختلال در عملکرد ندارید.

## رابط‌ها

API وظایف پس‌زمینه فقط یک رابط جدید اضافه می‌کند:

- {{domxref("IdleDeadline")}}
  - : یک شی از این نوع به بازخوانی بیکار ارسال می‌شود تا تخمینی از مدت زمان مورد انتظار دوره بیکاری و همچنین اینکه آیا بازخوانی به دلیل منقضی شدن دوره timeout آن اجرا می‌شود یا خیر، ارائه دهد.

رابط {{domxref("Window")}} نیز توسط این API با ارائه روش‌های جدید {{domxref("window.requestIdleCallback", "requestIdleCallback()")}} و {{domxref("window.cancelIdleCallback", "cancelIdleCallback()")}} تقویت شده است.

## مثال

در این مثال، نحوه استفاده از {{domxref("window.requestIdleCallback", "requestIdleCallback()")}} برای اجرای وظایف زمان‌بر و با اولویت پایین در زمانی که مرورگر در غیر این صورت بیکار است را بررسی می‌کنیم. علاوه بر این، این مثال نحوه زمان‌بندی به‌روزرسانی‌های محتوای سند با استفاده از {{domxref("window.requestAnimationFrame", "requestAnimationFrame()")}} را نشان می‌دهد.

در زیر فقط HTML و جاوااسکریپت این مثال را مشاهده می‌کنید. CSS نشان داده نشده است زیرا برای درک این عملکرد چندان حیاتی نیست.

### HTML

برای آشنایی با آنچه می‌خواهیم انجام دهیم، بیایید نگاهی به HTML بیندازیم. این یک جعبه (با `id="container"`) ایجاد می‌کند که برای نمایش پیشرفت یک عملیات استفاده می‌شود (زیرا هرگز نمی‌دانید رمزگشایی "گسیل‌های تکیون رشته کوانتومی" چقدر طول می‌کشد) و همچنین یک جعبه اصلی دوم (با `id="logBox"`) که برای نمایش خروجی متنی استفاده می‌شود.

```html
<p>
  Demonstration of using cooperatively scheduled background tasks using the
  <code>requestIdleCallback()</code> method.
</p>

<div id="container">
  <div class="label">Decoding quantum filament tachyon emissions…</div>

  <progress id="progress" value="0"></progress>

  <button class="button" id="startButton">Start</button>

  <div class="label counter">
    Task <span id="currentTaskNumber">0</span> of
    <span id="totalTaskCount">0</span>
  </div>
</div>

<div id="logBox">
  <div class="logHeader">Log</div>
  <div id="log"></div>
</div>
```

جعبه پیشرفت از یک عنصر {{HTMLElement("progress")}} برای نمایش پیشرفت استفاده می‌کند، همراه با یک برچسب با بخش‌هایی که برای نمایش اطلاعات عددی درباره پیشرفت تغییر می‌کنند. علاوه بر این، یک دکمه "شروع" (با شناسه خلاقانه "startButton") وجود دارد که کاربر از آن برای شروع پردازش داده استفاده می‌کند.

```css hidden
body {
  font-family: "Open Sans", "Lucida Grande", "Arial", sans-serif;
  font-size: 16px;
}

#logBox {
  margin-top: 16px;
  width: 400px;
  height: 500px;
  border-radius: 6px;
  border: 1px solid black;
  box-shadow: 4px 4px 2px black;
}

.logHeader {
  margin: 0;
  padding: 0 6px 4px;
  height: 22px;
  background-color: lightblue;
  border-bottom: 1px solid black;
  border-radius: 6px 6px 0 0;
}

#log {
  font:
    12px "Courier",
    monospace;
  padding: 6px;
  overflow: auto;
  overflow-y: scroll;
  width: 388px;
  height: 460px;
}

#container {
  width: 400px;
  padding: 6px;
  border-radius: 6px;
  border: 1px solid black;
  box-shadow: 4px 4px 2px black;
  display: block;
  overflow: auto;
}

.label {
  display: inline-block;
}

.counter {
  text-align: right;
  padding-top: 4px;
  float: right;
}

.button {
  padding-top: 2px;
  padding-bottom: 4px;
  width: 100px;
  display: inline-block;
  float: left;
  border: 1px solid black;
  cursor: pointer;
  text-align: center;
  margin-top: 0;
  color: white;
  background-color: darkgreen;
}

#progress {
  width: 100%;
  padding-top: 6px;
}
```

### جاوااسکریپت

اکنون که ساختار سند تعریف شده است، کد جاوااسکریپتی را می‌سازیم که کار را انجام می‌دهد. هدف: قابلیت افزودن درخواست‌ها برای فراخوانی توابع به یک صف، با یک بازخوانی بیکار که آن توابع را هر زمان که سیستم به اندازه کافی بیکار است تا پیشرفت کند، اجرا کند.

#### اعلان متغیرها

```js
const taskList = [];
let totalTaskCount = 0;
let currentTaskNumber = 0;
let taskHandle = null;
```

این متغیرها برای مدیریت لیست وظایفی که در انتظار اجرا هستند، و همچنین اطلاعات وضعیت درباره صف وظایف و اجرای آن استفاده می‌شوند:

- `taskList` یک {{jsxref("Array")}} از اشیاء است که هر کدام یک وظیفه در انتظار اجرا را نشان می‌دهد.
- `totalTaskCount` یک شمارنده از تعداد وظایفی است که به صف اضافه شده است؛ فقط افزایش می‌یابد، هرگز کاهش نمی‌یابد. ما از این برای انجام محاسبات برای نمایش پیشرفت به عنوان درصدی از کل کار انجام شده استفاده می‌کنیم.
- `currentTaskNumber` برای پیگیری تعداد وظایف پردازش شده تا کنون استفاده می‌شود.
- `taskHandle` یک مرجع به وظیفه‌ای است که در حال پردازش است.

```js
const totalTaskCountElem = document.getElementById("totalTaskCount");
const currentTaskNumberElem = document.getElementById("currentTaskNumber");
const progressBarElem = document.getElementById("progress");
const startButtonElem = document.getElementById("startButton");
const logElem = document.getElementById("log");
```

سپس متغیرهایی داریم که به عناصر DOM مورد نیاز برای تعامل اشاره می‌کنند. این عناصر عبارتند از:

- `totalTaskCountElem` {{HTMLElement("span")}} است که برای درج تعداد کل وظایف ایجاد شده در نمایش وضعیت در جعبه پیشرفت استفاده می‌کنیم.
- `currentTaskNumberElem` عنصری است که برای نمایش تعداد وظایف پردازش شده تا کنون استفاده می‌شود.
- `progressBarElem` عنصر {{HTMLElement("progress")}} است که درصد وظایف پردازش شده را نشان می‌دهد.
- `startButtonElem` دکمه شروع است.
- `logElem` {{HTMLElement("div")}} است که پیام‌های متنی ثبت شده را در آن درج می‌کنیم.

```js
let logFragment = null;
let statusRefreshScheduled = false;
```

در نهایت، چند متغیر برای موارد دیگر تنظیم می‌کنیم:

- `logFragment` برای ذخیره یک {{domxref("DocumentFragment")}} استفاده می‌شود که توسط توابع ثبت ما برای ایجاد محتوایی برای افزودن به لاگ هنگام رندر شدن فریم انیمیشن بعدی تولید می‌شود.
- `statusRefreshScheduled` برای پیگیری اینکه آیا قبلاً یک به‌روزرسانی از جعبه نمایش وضعیت برای فریم آینده زمان‌بندی کرده‌ایم یا خیر استفاده می‌شود، تا فقط یک بار در هر فریم انجام دهیم.

```js hidden
window.requestIdleCallback ||= (handler) => {
  const startTime = Date.now();

  return setTimeout(() => {
    handler({
      didTimeout: false,
      timeRemaining() {
        return Math.max(0, 50.0 - (Date.now() - startTime));
      },
    });
  }, 1);
};

window.cancelIdleCallback ||= (id) => {
  clearTimeout(id);
};
```

#### مدیریت صف وظایف

در ادامه، نحوه مدیریت وظایفی که باید انجام شوند را بررسی می‌کنیم. ما این کار را با ایجاد یک صف FIFO از وظایف انجام می‌دهیم که در زمان مجاز در طول دوره بازخوانی بیکار اجرا می‌کنیم.

##### در صف قرار دادن وظایف

ابتدا به یک تابع نیاز داریم که وظایف را برای اجرای آینده در صف قرار دهد. آن تابع، `enqueueTask()`، به این شکل است:

```js
function enqueueTask(taskHandler, taskData) {
  taskList.push({
    handler: taskHandler,
    data: taskData,
  });

  totalTaskCount++;

  taskHandle ||= requestIdleCallback(runTaskQueue, { timeout: 1000 });

  scheduleStatusRefresh();
}
```

`enqueueTask()` دو پارامتر ورودی می‌پذیرد:

- `taskHandler` تابعی است که برای مدیریت وظیفه فراخوانی می‌شود.
- `taskData` یک شی است که به عنوان پارامتر ورودی به مدیریت‌کننده وظیفه ارسال می‌شود تا به وظیفه اجازه دریافت داده‌های سفارشی را بدهد.

برای در صف قرار دادن وظیفه، یک شی را به آرایه `taskList` [push](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push) می‌کنیم. این شی شامل مقادیر `taskHandler` و `taskData` با نام‌های `handler` و `data` است. سپس `totalTaskCount` را افزایش می‌دهیم که تعداد کل وظایفی را که تا به حال در صف قرار گرفته‌اند منعکس می‌کند (زمانی که وظایف از صف حذف می‌شوند، آن را کاهش نمی‌دهیم).

سپس بررسی می‌کنیم که آیا قبلاً یک بازخوانی بیکار ایجاد کرده‌ایم. اگر `taskHandle` برابر ۰ باشد، می‌دانیم که هنوز بازخوانی بیکاری وجود ندارد، بنابراین {{domxref("Window.requestIdleCallback", "requestIdleCallback()")}} را برای ایجاد یکی فراخوانی می‌کنیم. این بازخوانی طوری پیکربندی شده است که تابعی به نام `runTaskQueue()` را فراخوانی کند که به زودی آن را بررسی می‌کنیم، و با یک `timeout` ۱ ثانیه، به طوری که حداقل یک بار در ثانیه اجرا شود حتی اگر زمان بیکار واقعی در دسترس نباشد.

##### اجرای وظایف

مدیریت‌کننده بازخوانی بیکار ما، `runTaskQueue()`، زمانی فراخوانی می‌شود که مرورگر تشخیص دهد زمان بیکار کافی برای انجام کار در دسترس است یا timeout یک ثانیه‌ای ما منقضی شود. وظیفه این تابع اجرای وظایف در صف است.

```js
function runTaskQueue(deadline) {
  while (
    (deadline.timeRemaining() > 0 || deadline.didTimeout) &&
    taskList.length
  ) {
    const task = taskList.shift();
    currentTaskNumber++;

    task.handler(task.data);
    scheduleStatusRefresh();
  }

  if (taskList.length) {
    taskHandle = requestIdleCallback(runTaskQueue, { timeout: 1000 });
  } else {
    taskHandle = 0;
  }
}
```

هسته `runTaskQueue()` یک حلقه است که تا زمانی که زمان باقی مانده باشد (با بررسی {{domxref("IdleDeadline.timeRemaining", "deadline.timeRemaining")}} برای اطمینان از اینکه بیشتر از ۰ است) یا اگر محدودیت timeout رسیده باشد ({{domxref("IdleDeadline.didTimeout", "deadline.didTimeout")}} true باشد)، و تا زمانی که وظایفی در لیست وظایف وجود داشته باشد، ادامه می‌یابد.

برای هر وظیفه در صف که زمان اجرای آن را داریم، موارد زیر را انجام می‌دهیم:

1. شی وظیفه را از صف [حذف می‌کنیم](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift).
2. `currentTaskNumber` را افزایش می‌دهیم تا تعداد وظایف اجرا شده را پیگیری کنیم.
3. مدیریت‌کننده وظیفه را فراخوانی می‌کنیم، `task.handler`، و شی داده وظیفه (`task.data`) را به آن ارسال می‌کنیم.
4. تابعی به نام `scheduleStatusRefresh()` را فراخوانی می‌کنیم تا زمان‌بندی یک به‌روزرسانی صفحه برای منعکس کردن تغییرات پیشرفت ما را مدیریت کند.

زمانی که زمان تمام می‌شود، اگر هنوز وظایفی در لیست باقی مانده باشد، دوباره {{domxref("Window.requestIdleCallback", "requestIdleCallback()")}} را فراخوانی می‌کنیم تا بتوانیم در زمان بیکار بعدی به پردازش وظایف ادامه دهیم. اگر صف خالی باشد، `taskHandle` را به ۰ تنظیم می‌کنیم تا نشان دهیم که بازخوانی زمان‌بندی شده‌ای نداریم. به این ترتیب، دفعه بعد که `enqueueTask()` فراخوانی می‌شود، می‌دانیم که باید یک بازخوانی درخواست کنیم.

#### به‌روزرسانی نمایش وضعیت

یکی از کارهایی که می‌خواهیم انجام دهیم، به‌روزرسانی سند با خروجی لاگ و اطلاعات پیشرفت است. با این حال، نمی‌توانید با خیال راحت DOM را از درون یک بازخوانی بیکار تغییر دهید. در عوض، از {{domxref("Window.requestAnimationFrame", "requestAnimationFrame()")}} استفاده می‌کنیم تا از مرورگر بخواهیم زمانی که ایمن است برای به‌روزرسانی نمایش، ما را فراخوانی کند.

##### زمان‌بندی به‌روزرسانی‌های نمایش

تغییرات DOM با فراخوانی تابع `scheduleStatusRefresh()` زمان‌بندی می‌شوند.

```js
function scheduleStatusRefresh() {
  if (!statusRefreshScheduled) {
    requestAnimationFrame(updateDisplay);
    statusRefreshScheduled = true;
  }
}
```

این یک تابع ساده است. بررسی می‌کند که آیا قبلاً یک تازه‌سازی نمایش را با بررسی مقدار `statusRefreshScheduled` زمان‌بندی کرده‌ایم. اگر `false` باشد، {{domxref("Window.requestAnimationFrame", "requestAnimationFrame()")}} را برای زمان‌بندی یک تازه‌سازی فراخوانی می‌کنیم و تابع `updateDisplay()` را برای مدیریت آن کار فراهم می‌کنیم.

##### به‌روزرسانی نمایش

تابع `updateDisplay()` مسئول رسم محتویات جعبه پیشرفت و لاگ است. این تابع توسط مرورگر زمانی فراخوانی می‌شود که DOM در وضعیت ایمن برای اعمال تغییرات در طول فرآیند رندر فریم بعدی باشد.

```js
function updateDisplay() {
  const scrolledToEnd =
    logElem.scrollHeight - logElem.clientHeight <= logElem.scrollTop + 1;

  if (totalTaskCount) {
    if (progressBarElem.max !== totalTaskCount) {
      totalTaskCountElem.textContent = totalTaskCount;
      progressBarElem.max = totalTaskCount;
    }

    if (progressBarElem.value !== currentTaskNumber) {
      currentTaskNumberElem.textContent = currentTaskNumber;
      progressBarElem.value = currentTaskNumber;
    }
  }

  if (logFragment) {
    logElem.appendChild(logFragment);
    logFragment = null;
  }

  if (scrolledToEnd) {
    logElem.scrollTop = logElem.scrollHeight - logElem.clientHeight;
  }

  statusRefreshScheduled = false;
}
```

ابتدا، `scrolledToEnd` اگر متن در لاگ به پایین اسکرول شده باشد، `true` تنظیم می‌شود؛ در غیر این صورت `false` است. از این استفاده می‌کنیم تا تعیین کنیم آیا باید موقعیت اسکرول را به‌روزرسانی کنیم تا اطمینان حاصل شود که لاگ پس از افزودن محتوا در انتها باقی می‌ماند.

سپس، اگر وظایفی در صف قرار گرفته باشند، اطلاعات پیشرفت و وضعیت را به‌روزرسانی می‌کنیم.

1. اگر مقدار حداکثر فعلی نوار پیشرفت با تعداد کل فعلی وظایف در صف (`totalTaskCount`) متفاوت باشد، محتویات تعداد کل وظایف نمایش داده شده (`totalTaskCountElem`) و مقدار حداکثر نوار پیشرفت را به‌روزرسانی می‌کنیم تا به درستی مقیاس‌بندی شود.
2. همین کار را با تعداد وظایف پردازش شده تا کنون انجام می‌دهیم. اگر `progressBarElem.value` با شماره وظیفه در حال پردازش (`currentTaskNumber`) متفاوت باشد، مقدار نمایش داده شده وظیفه در حال پردازش و مقدار فعلی نوار پیشرفت را به‌روزرسانی می‌کنیم.

سپس، اگر متنی برای افزودن به لاگ در انتظار باشد (یعنی اگر `logFragment` `null` نباشد)، آن را با استفاده از {{domxref("Node.appendChild", "Element.appendChild()")}} به عنصر لاگ اضافه می‌کنیم و `logFragment` را به `null` تنظیم می‌کنیم تا دوباره اضافه نشود.

اگر لاگ در زمان شروع به انتها اسکرول شده بود، مطمئن می‌شویم که همچنان در انتها است. سپس `statusRefreshScheduled` را به `false` تنظیم می‌کنیم تا نشان دهیم که تازه‌سازی را انجام داده‌ایم و درخواست یک تازه‌سازی جدید ایمن است.

#### افزودن متن به لاگ

تابع `log()` متن مشخص شده را به لاگ اضافه می‌کند. از آنجایی که در زمان فراخوانی `log()` نمی‌دانیم آیا ایمن است که بلافاصله DOM را لمس کنیم، متن لاگ را تا زمانی که ایمن شود ذخیره می‌کنیم. در بالا، در کد `updateDisplay()`، می‌توانید کدی را پیدا کنید که در واقع متن ثبت شده را هنگام به‌روزرسانی فریم انیمیشن به عنصر لاگ اضافه می‌کند.

```js
function log(text) {
  logFragment ??= document.createDocumentFragment();
  const el = document.createElement("div");
  el.textContent = text;
  logFragment.appendChild(el);
}
```

ابتدا، یک شی {{domxref("DocumentFragment")}} به نام `logFragment` ایجاد می‌کنیم اگر یکی وجود نداشته باشد. این عنصر یک DOM شبه است که می‌توانیم بدون تغییر فوری DOM اصلی، عناصر را در آن درج کنیم.

سپس یک عنصر جدید {{HTMLElement("div")}} ایجاد می‌کنیم و محتوای آن را با متن ورودی `text` مطابقت می‌دهیم. سپس عنصر جدید را به انتهای DOM شبه در `logFragment` اضافه می‌کنیم. `logFragment` ورودی‌های لاگ را تا زمان فراخوانی بعدی `updateDisplay()`، زمانی که DOM برای تغییرات آماده باشد، جمع‌آوری می‌کند.

### اجرای وظایف

اکنون که کد مدیریت وظایف و نگهداری نمایش را داریم، می‌توانیم شروع به تنظیم کدی برای اجرای وظایفی کنیم که کار را انجام می‌دهند.

#### مدیریت‌کننده وظیفه

تابعی که به عنوان مدیریت‌کننده وظیفه خود استفاده می‌کنیم - یعنی تابعی که به عنوان مقدار ویژگی `handler` شی وظیفه استفاده می‌شود - `logTaskHandler()` است. این یک تابع ساده است که برای هر وظیفه تعدادی چیز را به لاگ خروجی می‌دهد. در برنامه خودتان، این کد را با هر وظیفه‌ای که می‌خواهید در زمان بیکار انجام دهید، جایگزین می‌کنید. فقط به یاد داشته باشید که هر کاری که می‌خواهید انجام دهید و DOM را تغییر می‌دهد باید از طریق {{domxref("Window.requestAnimationFrame", "requestAnimationFrame()")}} مدیریت شود.

```js
function logTaskHandler(data) {
  log(`Running task #${currentTaskNumber}`);

  for (let i = 0; i < data.count; i += 1) {
    log(`${(i + 1).toString()}. ${data.text}`);
  }
}
```

#### برنامه اصلی

همه چیز زمانی شروع می‌شود که کاربر روی دکمه شروع کلیک کند، که باعث فراخوانی تابع `decodeTechnoStuff()` می‌شود.

```js hidden
function getRandomIntInclusive(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
```

```js
function decodeTechnoStuff() {
  totalTaskCount = 0;
  currentTaskNumber = 0;
  updateDisplay();

  const n = getRandomIntInclusive(100, 200);

  for (let i = 0; i < n; i++) {
    const taskData = {
      count: getRandomIntInclusive(75, 150),
      text: `This text is from task number ${i + 1} of ${n}`,
    };

    enqueueTask(logTaskHandler, taskData);
  }
}

document
  .getElementById("startButton")
  .addEventListener("click", decodeTechnoStuff);
```

`decodeTechnoStuff()` با صفر کردن مقادیر `totalTaskCount` (تعداد وظایف اضافه شده به صف تا کنون) و `currentTaskNumber` (وظیفه در حال اجرا) شروع می‌کند و سپس `updateDisplay()` را برای بازنشانی نمایش به حالت "هنوز هیچ اتفاقی نیفتاده" فراخوانی می‌کند.

این مثال یک تعداد تصادفی از وظایف (بین ۱۰۰ تا ۲۰۰) ایجاد می‌کند. برای انجام این کار، از [تابع `getRandomIntInclusive()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random#getting_a_random_integer_between_two_values_inclusive) استفاده می‌کنیم که به عنوان یک مثال در مستندات {{jsxref("Math.random()")}} ارائه شده است تا تعداد وظایف را بدست آوریم.

سپس یک حلقه برای ایجاد وظایف واقعی شروع می‌کنیم. برای هر وظیفه، یک شی به نام `taskData` ایجاد می‌کنیم که شامل دو ویژگی است:

- `count` تعداد رشته‌هایی است که از وظیفه به لاگ خروجی داده می‌شود.
- `text` متنی است که به تعداد مشخص شده توسط `count` به لاگ خروجی داده می‌شود.

هر وظیفه سپس با فراخوانی `enqueueTask()` و ارسال `logTaskHandler()` به عنوان تابع مدیریت‌کننده و شی `taskData` به عنوان شیء برای ارسال به تابع در زمان فراخوانی، در صف قرار می‌گیرد.

### نتیجه

در زیر نتیجه واقعی عملکرد کد بالا است. آن را امتحان کنید، با آن در ابزارهای توسعه‌دهنده مرورگر خود بازی کنید و با استفاده از آن در کد خود آزمایش کنید.

{{ EmbedLiveSample('Example', 600, 700) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Window.requestIdleCallback()")}}
- {{domxref("Window.cancelIdleCallback()")}}
- {{domxref("IdleDeadline")}}