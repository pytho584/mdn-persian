---
title: Prioritized Task Scheduling API
slug: Web/API/Prioritized_Task_Scheduling_API
page-type: web-api-overview
browser-compat:
  - api.Scheduler
  - api.Scheduling
---

{{DefaultAPISidebar("Prioritized Task Scheduling API")}}{{AvailableInWorkers}}

**رابط برنامه‌نویسی Prioritized Task Scheduling API** روشی استاندارد برای اولویت‌بندی همه وظایف متعلق به یک برنامه فراهم می‌کند؛ خواه این وظایف در کد توسعه‌دهنده وب‌سایت تعریف شده باشند یا در کتابخانه‌ها و فریمورک‌های شخص ثالث.

اولویت‌های [وظیفه](#task_priorities) در سطح بسیار کلی تعریف شده‌اند و مبنای آن‌ها این است که آیا وظایف تعامل کاربر را مسدود می‌کنند یا به شکل دیگری تجربه کاربری را تحت تأثیر قرار می‌دهند، یا می‌توانند در پس‌زمینه اجرا شوند. توسعه‌دهندگان و فریمورک‌ها می‌توانند در درون همین دسته‌بندی‌های کلیِ تعریف‌شده توسط API، طرح‌های اولویت‌بندی دقیق‌تری پیاده‌سازی کنند.

این API مبتنی بر Promise است و از این قابلیت‌ها پشتیبانی می‌کند: تنظیم و تغییر اولویت وظایف، تأخیر در افزوده‌شدن وظایف به زمان‌بند، لغو وظایف، و نظارت بر رویدادهای تغییر اولویت و لغو.

## مفاهیم و کاربرد

این API هم در ریسمان پنجره (window) و هم در ریسمان worker در دسترس است و از طریق خاصیت `scheduler` روی شیء سراسری (global object) قابل استفاده است.

متدهای اصلی API عبارت‌اند از {{domxref('scheduler.postTask()')}} و {{domxref('scheduler.yield()')}}. متد `scheduler.postTask()` یک تابع callback (وظیفه) دریافت می‌کند و یک promise برمی‌گرداند که با مقدار بازگشتی تابع resolve می‌شود یا با یک خطا reject می‌شود. متد `scheduler.yield()` نیز با واگذاری ریسمان اصلی به مرورگر برای انجام کارهای دیگر، هر تابع [`async`](/en-US/docs/Web/JavaScript/Reference/Statements/async_function) را به یک وظیفه تبدیل می‌کند و اجرا پس از resolve شدن promise بازگشتی ادامه می‌یابد.

این دو متد عملکرد مشابهی دارند اما سطح کنترل متفاوتی ارائه می‌دهند. `scheduler.postTask()` پیکربندی‌پذیرتر است؛ برای مثال، امکان تعیین صریح اولویت وظیفه و لغو وظیفه را از طریق [`AbortSignal`](/en-US/docs/Web/API/AbortSignal) فراهم می‌کند. از سوی دیگر، `scheduler.yield()` ساده‌تر است و می‌توان در هر تابع `async` آن را `await` کرد، بدون آنکه لازم باشد وظیفه بعدی در تابع دیگری تعریف شود.

### `scheduler.yield()`

برای این‌که وظایف طولانی‌مدت جاوااسکریپت را به بخش‌های کوچک‌تری تقسیم کنید تا ریسمان اصلی را مسدود نکنند، یک فراخوانی `scheduler.yield()` در کد قرار دهید تا ریسمان اصلی به‌طور موقت به مرورگر بازگردانده شود. مرورگر نیز وظیفه‌ای می‌سازد تا اجرا از همان جایی که متوقف شده ادامه یابد.

```js
async function slowTask() {
  firstHalfOfWork();
  await scheduler.yield();
  secondHalfOfWork();
}
```

`scheduler.yield()` یک promise برمی‌گرداند که می‌توان برای ادامه اجرا منتظر آن ماند. این امکان می‌دهد کارهای مربوط به همان تابع در همان‌جا ادامه پیدا کنند، بدون آن‌که هنگام اجرای تابع، ریسمان اصلی مسدود شود.

`scheduler.yield()` هیچ آرگومانی نمی‌گیرد. وظیفه‌ای که ادامه اجرای آن را فعال می‌کند، به‌طور پیش‌فرض اولویت [`user-visible`](#user-visible) دارد؛ با این حال، اگر `scheduler.yield()` درون یک callback متعلق به `scheduler.postTask()` فراخوانده شود، [اولویت وظیفه‌ی فراگیر را به ارث می‌برد](/en-US/docs/Web/API/Scheduler/yield#inheriting_task_priorities).

### `scheduler.postTask()`

وقتی `scheduler.postTask()` بدون آرگومان فراخوانده شود، وظیفه‌ای با اولویت پیش‌فرض [`user-visible`](#user-visible) می‌سازد که نه می‌توان آن را لغو کرد و نه اولویت آن را تغییر داد.

```js
const promise = scheduler.postTask(myTask);
```

چون این متد یک promise برمی‌گرداند، می‌توانید با استفاده از [`then()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then) به‌صورت ناهمگام منتظر resolve شدن آن بمانید و خطاهای پرتاب‌شده توسط تابع callback وظیفه (یا خطای مربوط به لغو وظیفه) را با [`catch`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/catch) بگیرید. تابع callback می‌تواند هر نوع تابعی باشد (در ادامه یک تابع پیکانی نشان داده شده است).

```js
scheduler
  .postTask(() => "Task executing")
  // Promise resolved: log task result when promise resolves
  .then((taskResult) => console.log(`${taskResult}`))
  // Promise rejected: log AbortError or errors thrown by task
  .catch((error) => console.error(`Error: ${error}`));
```

برای همین کار می‌توان از `await`/`async` نیز استفاده کرد؛ چنان‌که در پایین نشان داده شده است (توجه کنید که این نمونه درون یک {{Glossary("IIFE", "Immediately Invoked Function Expression (IIFE)")}} اجرا می‌شود):

```js
(async () => {
  try {
    const result = await scheduler.postTask(() => "Task executing");
    console.log(result);
  } catch (error) {
    // Log AbortError or error thrown in task function
    console.error(`Error: ${error}`);
  }
})();
```

اگر بخواهید رفتار پیش‌فرض را تغییر دهید، می‌توانید یک شیء options نیز به متد `postTask()` بدهید. این گزینه‌ها عبارت‌اند از:

- `priority`: این گزینه به شما امکان می‌دهد یک اولویت خاص و تغییرناپذیر تعیین کنید. پس از تعیین، اولویت دیگر قابل تغییر نیست.
- `signal`: این گزینه به شما امکان می‌دهد یک سیگنال مشخص کنید؛ این سیگنال می‌تواند یک {{domxref("TaskSignal")}} یا {{domxref("AbortSignal")}} باشد. سیگنال به یک کنترل‌کننده مرتبط است که می‌توان از آن برای لغو وظیفه استفاده کرد. همچنین اگر [وظیفه تغییرپذیر باشد](#mutable_and_immutable_task_priority)، می‌توان از {{domxref("TaskSignal")}} برای تنظیم و تغییر اولویت وظیفه استفاده کرد.
- `delay`: این گزینه به شما امکان می‌دهد تأخیر پیش از افزوده‌شدن وظیفه به زمان‌بندی را بر حسب میلی‌ثانیه مشخص کنید.

مثال بالا با یک گزینه `priority` به این شکل خواهد بود:

```js
scheduler
  .postTask(() => "Task executing", { priority: "user-blocking" })
  .then((taskResult) => console.log(`${taskResult}`)) // Log the task result
  .catch((error) => console.error(`Error: ${error}`)); // Log any errors
```

## اولویت‌های وظیفه

وظایف زمان‌بندی‌شده ابتدا بر اساس اولویت اجرا می‌شوند و سپس بر اساس ترتیبی که به صف زمان‌بند اضافه شده‌اند.

فقط سه سطح اولویت وجود دارد که در ادامه از بالاترین به پایین‌ترین فهرست شده‌اند:

- `user-blocking`
  - : وظایفی که مانع تعامل کاربر با صفحه می‌شوند؛ از جمله رندر کردن صفحه تا حدی که قابل استفاده باشد، یا پاسخ به ورودی کاربر.

- `user-visible`
  - : وظایفی که برای کاربر قابل مشاهده‌اند اما لزوماً مانع اقدام‌های کاربر نمی‌شوند؛ مانند رندر کردن بخش‌های غیرضروری صفحه، مثل تصاویر یا انیمیشن‌های غیرضروری.

    این اولویت پیش‌فرض برای `scheduler.postTask()` و `scheduler.yield()` است.

- `background`
  - : وظایفی که حساس به زمان نیستند؛ مانند پردازش لاگ‌ها یا مقداردهی اولیه کتابخانه‌های شخص ثالثی که برای رندر کردن صفحه ضروری نیستند.

### اولویت وظیفه تغییرپذیر و تغییرناپذیر

بسیاری از موارد استفاده وجود دارند که در آن‌ها هرگز نیازی به تغییر اولویت وظیفه نیست، در حالی که در موارد دیگر این تغییر لازم است. برای مثال، وقتی یک کاروسل به محدوده دید اسکرول می‌شود، اولویت دریافت تصویر ممکن است از یک وظیفه `background` به `user-visible` تغییر کند.

بسته به آرگومان‌هایی که به {{domxref('Scheduler.postTask()')}} داده می‌شود، اولویت وظیفه می‌تواند ایستا (تغییرناپذیر) یا پویا (قابل تغییر) باشد.

اگر در آرگومان `options.priority` مقداری مشخص شود، اولویت وظیفه تغییرناپذیر است. مقدار داده‌شده برای اولویت وظیفه استفاده می‌شود و نمی‌توان آن را تغییر داد.

اولویت فقط زمانی قابل تغییر است که یک {{domxref("TaskSignal")}} به آرگومان `options.signal` داده شود **و** `options.priority` تنظیم نشده باشد. در این حالت، وظیفه اولویت اولیه خود را از اولویت سیگنال می‌گیرد و بعداً می‌توان با فراخواندن {{domxref("TaskController.setPriority()")}} روی کنترل‌کننده مرتبط با آن سیگنال، اولویت را تغییر داد.

اگر اولویت نه با `options.priority` تنظیم شده باشد و نه با دادن یک {{domxref("TaskSignal")}} به `options.signal`، آن‌گاه مقدار پیش‌فرض `user-visible` خواهد بود (و بنا به تعریف، تغییرناپذیر است).

توجه کنید که وظیفه‌ای که باید لغو شود، باید `options.signal` را روی {{domxref("TaskSignal")}} یا {{domxref("AbortSignal")}} تنظیم کند. با این حال، برای وظیفه‌ای با اولویت تغییرناپذیر، استفاده از {{domxref("AbortSignal")}} به‌وضوح بیشتری نشان می‌دهد که اولویت وظیفه را نمی‌توان با استفاده از سیگنال تغییر داد.

برای روشن شدن منظور، مثالی را بررسی می‌کنیم. وقتی چند وظیفه دارید که اولویت تقریباً یکسانی دارند، منطقی است که آن‌ها را برای سهولت نگهداری، اشکال‌زدایی و دلایل بسیار دیگر به توابع جداگانه تقسیم کنید.

برای مثال:

```js
function main() {
  a();
  b();
  c();
  d();
  e();
}
```

اما چنین ساختاری به رفع مسدود شدن ریسمان اصلی کمک نمی‌کند. چون هر پنج وظیفه درون یک تابع اصلی اجرا می‌شوند، مرورگر همه آن‌ها را به‌صورت یک وظیفه واحد اجرا می‌کند.

برای مقابله با این مشکل، معمولاً تابعی را به‌صورت متناوب اجرا می‌کنیم تا کد به ریسمان اصلی «واگذار» شود. این یعنی کد ما به چند وظیفه تقسیم می‌شود و در فاصله اجرای این وظایف، مرورگر فرصت پیدا می‌کند وظایف با اولویت بالا مانند به‌روزرسانی رابط کاربری را انجام دهد. الگوی رایج برای چنین تابعی استفاده از {{domxref("Window.setTimeout", "setTimeout()")}} است تا اجرای ادامه کار به یک وظیفه جداگانه موکول شود:

```js
function yield() {
  return new Promise((resolve) => {
    setTimeout(resolve, 0);
  });
}
```

این تابع را می‌توان در الگوی task runner به شکل زیر استفاده کرد تا پس از اجرای هر وظیفه، کنترل به ریسمان اصلی بازگردانده شود:

```js
async function main() {
  // Create an array of functions to run
  const tasks = [a, b, c, d, e];

  // Loop over the tasks
  while (tasks.length > 0) {
    // Shift the first task off the tasks array
    const task = tasks.shift();

    // Run the task
    task();

    // Yield to the main thread
    await yield();
  }
}
```

برای بهبود بیشتر، می‌توانیم در صورت در دسترس بودن از {{domxref("Scheduler.yield")}} استفاده کنیم تا این کد بتواند پیش از سایر وظایف کم‌اهمیت‌تر در صف به اجرا ادامه دهد:

```js
function yield() {
  // Use scheduler.yield if it exists:
  if ("scheduler" in window && "yield" in scheduler) {
    return scheduler.yield();
  }

  // Fall back to setTimeout:
  return new Promise((resolve) => {
    setTimeout(resolve, 0);
  });
}
```

## رابط‌ها

- {{domxref("Scheduler")}}
  - : شامل متدهای {{domxref('Scheduler.postTask', 'postTask()')}} و {{domxref('Scheduler.yield', 'yield()')}} برای افزودن وظایف اولویت‌دار به زمان‌بندی است. نمونه‌ای از این رابط روی شیءهای سراسری {{domxref("Window")}} یا {{domxref("WorkerGlobalScope")}} در دسترس است (`globalThis.scheduler`).
- {{domxref("TaskController")}}
  - : از لغو یک وظیفه و تغییر اولویت آن پشتیبانی می‌کند.
- {{domxref("TaskSignal")}}
  - : یک شیء سیگنال که با استفاده از یک شیء {{domxref("TaskController")}} به شما امکان می‌دهد در صورت نیاز وظیفه‌ای را لغو کنید و اولویت آن را تغییر دهید.
- {{domxref("TaskPriorityChangeEvent")}}
  - : رابط مربوط به رویداد {{domxref("TaskSignal/prioritychange_event","prioritychange")}} که هنگام تغییر اولویت یک وظیفه ارسال می‌شود.

> [!NOTE]
> اگر [اولویت وظیفه](#task_priorities) هرگز نیازی به تغییر ندارد، می‌توانید به‌جای {{domxref("TaskController")}} و {{domxref("TaskSignal")}} از {{domxref("AbortController")}} و {{domxref("AbortSignal")}} مرتبط با آن استفاده کنید.

### توسعه سایر رابط‌ها

- {{domxref("Window.scheduler")}} و {{domxref("WorkerGlobalScope.scheduler")}}
  - : این ویژگی‌ها نقاط ورود برای استفاده از متد `Scheduler.postTask()` به‌ترتیب در محدوده (scope) یک پنجره یا یک worker هستند.

## مثال‌ها

توجه کنید که مثال‌های زیر از `myLog()` برای نوشتن در یک ناحیه متنی استفاده می‌کنند. کد مربوط به ناحیه لاگ و این متد معمولاً پنهان شده تا حواس را از کدهای مرتبط‌تر پرت نکند.

```html hidden
<textarea id="log"></textarea>
```

```css hidden
#log {
  min-height: 20px;
  width: 95%;
}
```

```js hidden
// hidden logger code - simplifies example
let log = document.getElementById("log");
function myLog(text) {
  log.textContent += `${text}\n`;
}
```

### بررسی پشتیبانی از ویژگی

برای بررسی پشتیبانی از زمان‌بندی وظایف اولویت‌دار، وجود خاصیت `scheduler` را در محدوده سراسری (global scope) آزمایش کنید.

کد زیر اگر API در این مرورگر پشتیبانی شود، عبارت «Feature: Supported» را چاپ می‌کند.

```html hidden
<textarea id="log"></textarea>
```

```css hidden
#log {
  min-height: 20px;
  width: 95%;
}
```

```js hidden
// hidden logger code - simplifies example
let log = document.getElementById("log");
function myLog(text) {
  log.textContent += `${text}\n`;
}
```

```js
// Check that feature is supported
if ("scheduler" in globalThis) {
  myLog("Feature: Supported");
} else {
  myLog("Feature: NOT Supported");
}
```

{{EmbedLiveSample('Feature checking','400px','70px')}}

### استفاده پایه

وظایف با استفاده از {{domxref('Scheduler.postTask()')}} ارسال می‌شوند؛ تابع callback (وظیفه) در آرگومان اول مشخص می‌شود و آرگومان دوم اختیاری است و می‌توان از آن برای تعیین اولویت وظیفه، سیگنال و/یا تأخیر استفاده کرد. این متد یک {{jsxref("Promise")}} برمی‌گرداند که با مقدار بازگشتی تابع callback resolve می‌شود یا با خطای لغو (abort error) یا خطایی که در تابع پرتاب شده reject می‌شود.

```html hidden
<textarea id="log"></textarea>
```

```css hidden
#log {
  min-height: 100px;
  width: 95%;
}
```

```js hidden
let log = document.getElementById("log");
function myLog(text) {
  log.textContent += `${text}\n`;
}
```

چون این متد یک promise برمی‌گرداند، {{domxref('Scheduler.postTask()')}} را می‌توان با [سایر promiseها زنجیره کرد](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#chained_promises). در پایین نشان می‌دهیم که چگونه با استفاده از [`then`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then) منتظر resolve شدن promise بمانیم. این کار از اولویت پیش‌فرض (`user-visible`) استفاده می‌کند.

```js
// A function that defines a task
function myTask() {
  return "Task 1: user-visible";
}

if ("scheduler" in this) {
  // Post task with default priority: 'user-visible' (no other options)
  // When the task resolves, Promise.then() logs the result.
  scheduler.postTask(myTask).then((taskResult) => myLog(`${taskResult}`));
}
```

این متد را می‌توان با [`await`](/en-US/docs/Web/JavaScript/Reference/Operators/await) درون یک [تابع async](/en-US/docs/Web/JavaScript/Reference/Statements/async_function) نیز استفاده کرد. کد زیر نشان می‌دهد که چگونه می‌توانید از این روش برای منتظر ماندن روی یک وظیفه `user-blocking` استفاده کنید.

```js
function myTask2() {
  return "Task 2: user-blocking";
}

async function runTask2() {
  const result = await scheduler.postTask(myTask2, {
    priority: "user-blocking",
  });
  myLog(result); // Logs 'Task 2: user-blocking'.
}
runTask2();
```

در برخی موارد ممکن است اصلاً نیازی به منتظر ماندن برای پایان کار نداشته باشید. برای سادگی، بسیاری از مثال‌های این صفحه، نتیجه را همان هنگام اجرای وظیفه در لاگ می‌نویسند.

```js
// A function that defines a task
function myTask3() {
  myLog("Task 3: user-visible");
}

if ("scheduler" in this) {
  // Post task and log result when it runs
  scheduler.postTask(myTask3);
}
```

لاگ زیر خروجی سه وظیفه بالا را نشان می‌دهد. توجه کنید که ترتیب اجرای آن‌ها ابتدا بر اساس اولویت و سپس بر اساس ترتیب اعلان است.

{{EmbedLiveSample('Basic usage','400px','170px')}}

### اولویت‌های دائمی

[اولویت‌های وظیفه](#task_priorities) را می‌توان با استفاده از پارامتر `priority` در آرگومان اختیاری دوم تنظیم کرد. اولویت‌هایی که به این روش تنظیم می‌شوند [تغییرناپذیر](#mutable_and_immutable_task_priority) هستند و نمی‌توان آن‌ها را تغییر داد.

در ادامه دو گروه سه‌تایی از وظایف ارسال می‌کنیم که هر عضو آن‌ها به ترتیب معکوس اولویت قرار دارد. آخرین وظیفه اولویت پیش‌فرض دارد. هنگام اجرا، هر وظیفه صرفاً ترتیب مورد انتظار خود را در لاگ می‌نویسد (برای نمایش ترتیب اجرا منتظر نتیجه نمی‌مانیم، چون به آن نیازی نیست).

```js hidden
let log = document.getElementById("log");
function myLog(text) {
  log.textContent += `${text}\n`;
}
```

```js
if ("scheduler" in this) {
  // three tasks, in reverse order of priority
  scheduler.postTask(() => myLog("bkg 1"), { priority: "background" });
  scheduler.postTask(() => myLog("usr-vis 1"), { priority: "user-visible" });
  scheduler.postTask(() => myLog("usr-blk 1"), { priority: "user-blocking" });

  // three more tasks, in reverse order of priority
  scheduler.postTask(() => myLog("bkg 2"), { priority: "background" });
  scheduler.postTask(() => myLog("usr-vis 2"), { priority: "user-visible" });
  scheduler.postTask(() => myLog("usr-blk 2"), { priority: "user-blocking" });

  // Task with default priority: user-visible
  scheduler.postTask(() => myLog("usr-vis 3 (default)"));
}
```

```html hidden
<textarea id="log"></textarea>
```

```css hidden
#log {
  min-height: 120px;
  width: 95%;
}
```

خروجی زیر نشان می‌دهد که وظایف ابتدا بر اساس اولویت و سپس بر اساس ترتیب اعلان اجرا می‌شوند.

{{EmbedLiveSample("Permanent priorities",'400px','170px')}}

### تغییر اولویت وظایف

[اولویت‌های وظیفه](#task_priorities) همچنین می‌توانند مقدار اولیه خود را از یک {{domxref("TaskSignal")}} بگیرند که در آرگومان اختیاری دوم به `postTask()` داده می‌شود. اگر اولویت به این روش تنظیم شود، می‌توان اولویت وظیفه را [سپس با استفاده از کنترل‌کننده مرتبط با سیگنال تغییر داد](#mutable_and_immutable_task_priority).

> [!NOTE]
> تنظیم و تغییر اولویت وظیفه با استفاده از سیگنال فقط زمانی کار می‌کند که آرگومان `options.priority` به `postTask()` تنظیم نشده باشد و `options.signal` یک {{domxref("TaskSignal")}} باشد (نه یک {{domxref("AbortSignal")}}).

کد زیر ابتدا نشان می‌دهد که چگونه یک {{domxref("TaskController")}} بسازیم و اولویت اولیه سیگنال آن را در سازنده {{domxref("TaskController.TaskController", "TaskController()")}} روی `user-blocking` تنظیم کنیم.

سپس کد از `addEventListener()` برای افزودن یک شنونده رویداد به سیگنال کنترل‌کننده استفاده می‌کند (در عوض می‌توانستیم از خاصیت `TaskSignal.onprioritychange` برای افزودن یک کنترل‌کننده رویداد استفاده کنیم). کنترل‌کننده رویداد از {{domxref('TaskPriorityChangeEvent.previousPriority', 'previousPriority')}} روی رویداد برای به دست آوردن اولویت قبلی و از {{domxref("TaskSignal.priority")}} روی هدف رویداد برای به دست آوردن اولویت جدید/فعلی استفاده می‌کند.

سپس وظیفه با دادن سیگنال ارسال می‌شود و بلافاصله اولویت را با فراخواندن {{domxref("TaskController.setPriority()")}} روی کنترل‌کننده به `background` تغییر می‌دهیم.

```html hidden
<textarea id="log"></textarea>
```

```css hidden
#log {
  min-height: 70px;
  width: 95%;
}
```

```js hidden
let log = document.getElementById("log");
function myLog(text) {
  log.textContent += `${text}\n`;
}
```

```js
if ("scheduler" in this) {
  // Create a TaskController, setting its signal priority to 'user-blocking'
  const controller = new TaskController({ priority: "user-blocking" });

  // Listen for 'prioritychange' events on the controller's signal.
  controller.signal.addEventListener("prioritychange", (event) => {
    const previousPriority = event.previousPriority;
    const newPriority = event.target.priority;
    myLog(`Priority changed from ${previousPriority} to ${newPriority}.`);
  });

  // Post task using the controller's signal.
  // The signal priority sets the initial priority of the task
  scheduler.postTask(() => myLog("Task 1"), { signal: controller.signal });

  // Change the priority to 'background' using the controller
  controller.setPriority("background");
}
```

خروجی زیر نشان می‌دهد که اولویت با موفقیت از `user-blocking` به `background` تغییر کرده است. توجه کنید که در این مورد، اولویت پیش از اجرای وظیفه تغییر می‌کند؛ اما به همان اندازه می‌توانست هنگام اجرای وظیفه نیز تغییر کند.

{{EmbedLiveSample("Changing task priorities",'400px','130px')}}

### لغو وظایف

وظایف را می‌توان دقیقاً به یک روش، با {{domxref("TaskController")}} یا {{domxref("AbortController")}} لغو کرد. تنها تفاوت این است که اگر بخواهید اولویت وظیفه را نیز تنظیم کنید، باید از {{domxref("TaskController")}} استفاده کنید.

```html hidden
<textarea id="log"></textarea>
```

```css hidden
#log {
  min-height: 50px;
  width: 95%;
}
```

```js hidden
let log = document.getElementById("log");
function myLog(text) {
  log.textContent += `${text}\n`;
}
```

کد زیر یک کنترل‌کننده می‌سازد و سیگنال آن را به وظیفه می‌دهد. سپس وظیفه بلافاصله لغو می‌شود. این کار باعث می‌شود promise با یک `AbortError` reject شود که در بلوک `catch` گرفته و در لاگ نوشته می‌شود. توجه کنید که می‌توانستیم به رویداد {{domxref("AbortSignal/abort_event", "abort")}} که روی {{domxref("TaskSignal")}} یا {{domxref("AbortSignal")}} رخ می‌دهد نیز گوش دهیم و لغو شدن را آن‌جا ثبت کنیم.

```js
if ("scheduler" in this) {
  // Declare a TaskController with default priority
  const abortTaskController = new TaskController();
  // Post task passing the controller's signal
  scheduler
    .postTask(() => myLog("Task executing"), {
      signal: abortTaskController.signal,
    })
    .then((taskResult) => myLog(`${taskResult}`)) // This won't run!
    .catch((error) => myLog(`Error: ${error}`)); // Log the error

  // Abort the task
  abortTaskController.abort();
}
```

لاگ زیر وظیفه لغوشده را نشان می‌دهد.

{{EmbedLiveSample("Aborting tasks",'400px','100px')}}

### تأخیر انداختن وظایف

وظایف را می‌توان با تعیین یک عدد صحیح میلی‌ثانیه در پارامتر `options.delay` در `postTask()` به تأخیر انداخت. این کار عملاً وظیفه را با یک تأخیر زمانی به صف اولویت‌دار اضافه می‌کند؛ درست مانند چیزی که ممکن است با {{domxref("Window.setTimeout", "setTimeout()")}} ساخته شود. `delay` کمترین مقدار زمانی است که پیش از افزوده‌شدن وظیفه به زمان‌بند می‌گذرد و ممکن است بیشتر از آن نیز طول بکشد.

```html hidden
<textarea id="log"></textarea>
```

```css hidden
#log {
  min-height: 50px;
  width: 95%;
}
```

```js hidden
let log = document.getElementById("log");
function myLog(text) {
  log.textContent += `${text}\n`;
}
```

کد زیر دو وظیفه را نشان می‌دهد که (به‌صورت تابع پیکانی) با تأخیر اضافه شده‌اند.

```js
if ("scheduler" in this) {
  // Post task as arrow function with delay of 2 seconds
  scheduler
    .postTask(() => "Task delayed by 2000ms", { delay: 2000 })
    .then((taskResult) => myLog(`${taskResult}`));
  scheduler
    .postTask(() => "Next task should complete in about 2000ms", { delay: 1 })
    .then((taskResult) => myLog(`${taskResult}`));
}
```

صفحه را تازه‌سازی کنید. توجه کنید که رشته دوم پس از حدود ۲ ثانیه در لاگ ظاهر می‌شود.

{{EmbedLiveSample("Delaying tasks",'400px','100px')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Building a Faster Web Experience with the postTask Scheduler](https://medium.com/airbnb-engineering/building-a-faster-web-experience-with-the-posttask-scheduler-276b83454e91) در وبلاگ Airbnb (۲۰۲۱)
- [Optimizing long tasks](https://web.dev/articles/optimize-long-tasks) در web.dev (۲۰۲۲)