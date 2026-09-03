---
title: Using the Notifications API
slug: Web/API/Notifications_API/Using_the_Notifications_API
page-type: guide
---

{{DefaultAPISidebar("Web Notifications")}}

[Notifications API](/en-US/docs/Web/API/Notifications_API) به یک صفحهٔ وب یا برنامه اجازه می‌دهد اعلان‌هایی را ارسال کند که در سطح سیستم‌عامل و بیرون از صفحهٔ وب نمایش داده می‌شوند؛ به این ترتیب برنامه‌های وب می‌توانند حتی وقتی برنامه بیکار است یا در پس‌زمینه است، اطلاعاتی را برای کاربر ارسال کنند. این مقاله به اصول اولیهٔ استفاده از این API در برنامه‌های شما می‌پردازد.

به‌طور معمول، اعلان‌های سیستمی به سازوکار استاندارد اعلان سیستم‌عامل اشاره دارند؛ مثلاً در نظر بگیرید که یک سیستم دسکتاپ معمولی یا یک دستگاه موبایل چگونه اعلان‌ها را پخش می‌کند.

![Desktop notification: To do list via mdn.github.io HEY! Your task "Go shopping" is now overdue](desktop-notification.png)

البته سازوکار اعلان سیستمی بسته به پلتفرم و مرورگر متفاوت است؛ این مسئله اشکالی ندارد، زیرا Notifications API به‌گونه‌ای طراحی شده است که با بیشتر سازوکارهای اعلان سیستمی سازگاری کافی داشته باشد.

## مثال‌ها

یکی از بارزترین کاربردهای اعلان‌های وب، برنامه‌های ایمیل یا IRC مبتنی بر وب هستند که باید هنگام دریافت پیام جدید به کاربر اطلاع دهند، حتی اگر کاربر در حال انجام کار دیگری با برنامه‌ای دیگر باشد. امروزه نمونه‌های زیادی از این دست وجود دارد؛ مانند [Slack](https://slack.com/).

برای اینکه تصویر بهتری از کاربرد اعلان‌های وب داشته باشید، یک مثال واقعی — یک برنامهٔ فهرست کارها — آماده کرده‌ایم. این برنامه داده‌ها را به‌صورت محلی با استفاده از [IndexedDB](/en-US/docs/Web/API/IndexedDB_API) ذخیره می‌کند و با استفاده از اعلان‌های سیستمی، هنگام سررسیدن کارها به کاربر اطلاع می‌دهد. [کد برنامهٔ فهرست کارها را دانلود کنید](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) یا [نسخهٔ اجراشدهٔ برنامه را ببینید](https://mdn.github.io/dom-examples/to-do-notifications/).

## درخواست مجوز

قبل از اینکه یک برنامه بتواند اعلان ارسال کند، کاربر باید به آن برنامه اجازهٔ این کار را بدهد. این یک الزام رایج برای APIهایی است که می‌خواهند با چیزی خارج از صفحهٔ وب تعامل داشته باشند؛ کاربر باید حداقل یک بار به‌طور صریح به آن برنامه اجازهٔ نمایش اعلان‌ها را بدهد. به این ترتیب، کاربر کنترل می‌کند که کدام برنامه‌ها/وب‌سایت‌ها مجاز به نمایش اعلان هستند.

به دلیل سوءاستفاده‌های گذشته از اعلان‌های فشاری (push notifications)، مرورگرهای وب و توسعه‌دهندگان شروع به اجرای راهکارهایی برای کاهش این مشکل کرده‌اند. شما باید تنها در پاسخ به یک اقدام کاربر (مثلاً کلیک روی دکمه) درخواست رضایت برای نمایش اعلان بدهید. این فقط یک رویهٔ خوب نیست — نباید کاربران را با اعلان‌هایی که با آن موافقت نکرده‌اند بمباران کنید — بلکه از این پس مرورگرها به‌طور صریح درخواست‌های مجوز اعلان را که در پاسخ به اقدام کاربر انجام نشده باشند، رد خواهند کرد. مثلاً Firefox از نسخهٔ ۷۲ این کار را می‌کند و Safari نیز مدتی است چنین رفتاری دارد.

علاوه بر این، در Chrome و Firefox اگر وب‌سایت در یک زمینهٔ امن (secure context) نباشد، یعنی HTTPS نباشد، اساساً نمی‌توانید درخواست اعلان بدهید. همچنین دیگر نمی‌توانید اجازه دهید مجوز اعلان از {{htmlelement("iframe")}}های متقاطع‌ریشه (cross-origin) درخواست شود.

> [!NOTE]
> مثال‌های این مقاله برای ایجاد اعلان‌ها از سازندهٔ {{domxref("Notification/Notification", "Notification()")}} استفاده می‌کنند. این روش برای دسکتاپ مناسب است، اما در بیشتر مرورگرهای موبایل باعث بروز {{jsxref("TypeError")}} می‌شود. اگر هدف شما دستگاه‌های موبایل است، باید یک service worker ثبت کنید و به‌جای آن از {{domxref("ServiceWorkerRegistration.showNotification()")}} استفاده کنید.

### بررسی وضعیت فعلی مجوز

برای بررسی اینکه آیا از قبل مجوز دارید یا نه، می‌توانید مقدار ویژگی فقط‌خواندنی {{domxref("Notification.permission_static", "Notification.permission")}} را بررسی کنید. این ویژگی می‌تواند یکی از سه مقدار زیر را داشته باشد:

- `default`
  - : هنوز از کاربر اجازه خواسته نشده است، بنابراین اعلان‌ها نمایش داده نخواهند شد.
- `granted`
  - : کاربر پس از درخواست قبلی، اجازهٔ نمایش اعلان‌ها را داده است.
- `denied`
  - : کاربر به‌طور صریح از دادن اجازهٔ نمایش اعلان‌ها خودداری کرده است.

### دریافت مجوز

اگر هنوز اجازهٔ نمایش اعلان‌ها صادر نشده باشد، برنامه باید با استفاده از متد {{domxref("Notification.requestPermission_static", "Notification.requestPermission()")}} این اجازه را از کاربر درخواست کند. در ساده‌ترین شکل، فقط کد زیر را قرار می‌دهیم:

```js
Notification.requestPermission().then((result) => {
  console.log(result);
});
```

این کد از نسخهٔ مبتنی بر Promise این متد استفاده می‌کند. اگر می‌خواهید از نسخه‌های قدیمی‌تر پشتیبانی کنید، احتمالاً باید از نسخهٔ قدیمی مبتنی بر callback استفاده کنید که به شکل زیر است:

```js
Notification.requestPermission((result) => {
  console.log(result);
});
```

نسخهٔ مبتنی بر callback به‌صورت اختیاری یک تابع callback می‌پذیرد که وقتی کاربر به درخواست مجوز پاسخ داد، صدا زده می‌شود.

> [!NOTE]
> هیچ روش مطمئنی برای تشخیص اینکه آیا `Notification.requestPermission` از نسخهٔ مبتنی بر Promise پشتیبانی می‌کند وجود ندارد. اگر نیاز به پشتیبانی از مرورگرهای قدیمی‌تر دارید، فقط از نسخهٔ مبتنی بر callback استفاده کنید — هرچند این نسخه منسوخ (deprecated) شده است، اما همچنان در مرورگرهای جدید کار می‌کند. برای اطلاعات بیشتر به [جدول سازگاری مرورگرها](/en-US/docs/Web/API/Notification/requestPermission_static#browser_compatibility) مراجعه کنید.

### مثال

در نسخهٔ نمایشی فهرست کارهای خود، دکمه‌ای با عنوان «فعال‌سازی اعلان‌ها» گنجانده‌ایم که هنگام فشار دادن، مجوز اعلان را برای برنامه درخواست می‌کند.

```html
<button id="enable">Enable notifications</button>
```

کلیک روی این دکمه، تابع `askNotificationPermission()` را صدا می‌زند:

```js
function askNotificationPermission() {
  // Check if the browser supports notifications
  if (!("Notification" in window)) {
    console.log("This browser does not support notifications.");
    return;
  }
  Notification.requestPermission().then((permission) => {
    // set the button to shown or hidden, depending on what the user answers
    notificationBtn.style.display = permission === "granted" ? "none" : "block";
  });
}
```

در قطعه‌کد بالا می‌بینید که ابتدا بررسی می‌کنیم آیا اعلان‌ها پشتیبانی می‌شوند یا نه. اگر پشتیبانی شوند، نسخهٔ مبتنی بر Promise تابع `Notification.requestPermission()` را اجرا می‌کنیم؛ در غیر این صورت، پیامی را در کنسول ثبت می‌کنیم.

درون تابع کنترل‌کنندهٔ حل Promise که به `then` داده شده است، بسته به انتخابی که کاربر در گفت‌وگوی مجوز انجام داده، دکمه را نمایش می‌دهیم یا مخفی می‌کنیم. اگر مجوز قبلاً صادر شده باشد، نمی‌خواهیم دکمه را نمایش دهیم؛ اما اگر کاربر درخواست مجوز را رد کرده باشد، می‌خواهیم این فرصت را به او بدهیم که بعداً نظر خود را تغییر دهد.

## ایجاد یک اعلان

ایجاد یک اعلان ساده است؛ کافی است از سازندهٔ {{domxref("Notification")}} استفاده کنید. این سازنده یک عنوان برای نمایش در اعلان و برخی گزینه‌ها برای بهبود اعلان، مانند {{domxref("Notification.icon","icon")}} یا متن {{domxref("Notification.body","body")}} را می‌پذیرد.

برای مثال، در برنامهٔ فهرست کارها از قطعه‌کد زیر برای ایجاد اعلان در صورت نیاز استفاده می‌کنیم (این کد درون تابع `createNotification()` قرار دارد):

```js
const img = "/to-do-notifications/img/icon-128.png";
const text = `HEY! Your task "${title}" is now overdue.`;
const notification = new Notification("To do list", { body: text, icon: img });
```

## بستن اعلان‌ها

از {{domxref("Notification.close", "close()")}} برای حذف اعلانی استفاده کنید که دیگر برای کاربر مرتبط نیست (مثلاً در یک برنامهٔ پیام‌رسان، کاربر قبلاً آن اعلان را در صفحهٔ وب خوانده است؛ یا در یک برنامهٔ پخش موسیقی که هنگام تغییر آهنگ اعلان می‌دهد، آهنگ بعدی در حال پخش است). بیشتر مرورگرهای مدرن پس از چند لحظه (حدود چهار ثانیه) اعلان‌ها را به‌طور خودکار بسته و حذف می‌کنند؛ اما معمولاً نباید نگران این موضوع باشید، زیرا این رفتار به کاربر و عامل کاربر (user agent) بستگی دارد. بسته شدن اعلان ممکن است در سطح سیستم‌عامل نیز رخ دهد و کاربران باید کنترل آن را در دست داشته باشند. نسخه‌های قدیمی Chrome اعلان‌ها را به‌طور خودکار حذف نمی‌کردند؛ بنابراین فقط برای آن نسخه‌های قدیمی می‌توانید بعد از {{domxref("Window.setTimeout", "setTimeout()")}} اعلان را ببندید، به‌گونه‌ای که اعلان‌ها در مرورگرهای دیگر از سینی اعلان حذف نشوند.

> [!NOTE]
> نباید از این API فقط برای حذف اعلان از صفحه پس از یک تأخیر مشخص استفاده کنید (در مرورگرهای مدرن)، زیرا این روش اعلان را از هر سینی اعلانی نیز حذف می‌کند و در نتیجه کاربران پس از نمایش اولیه نمی‌توانند با آن تعامل کنند.

> [!NOTE]
> وقتی رویداد "close" دریافت می‌کنید، هیچ تضمینی وجود ندارد که خود کاربر اعلان را بسته باشد. این موضوع با مشخصات (specification) سازگار است، که می‌گوید: «هنگامی که یک اعلان بسته می‌شود — چه توسط پلتفرم اعلان‌های زیرساختی و چه توسط کاربر — مراحل بستن آن باید اجرا شود.»

## رویدادهای اعلان

این رویدادها روی نمونهٔ {{domxref("Notification")}} رخ می‌دهند:

- `click`
  - : زمانی رخ می‌دهد که کاربر روی اعلان کلیک می‌کند.
- `close`
  - : پس از بسته‌شدن اعلان رخ می‌دهد.
- `error`
  - : اگر مشکل در اعلان رخ دهد فعال می‌شود؛ معمولاً به این دلیل که اعلان به دلایلی نتوانسته نمایش داده شود.
- `show`
  - : هنگامی رخ می‌دهد که اعلان به کاربر نمایش داده می‌شود.

برای پیگیری این رویدادها می‌توانید از مدیریت‌کننده‌های {{domxref("Notification.click_event","onclick")}}، {{domxref("Notification.close_event","onclose")}}، {{domxref("Notification.error_event","onerror")}} و {{domxref("Notification.show_event","onshow")}} استفاده کنید. از آنجا که {{domxref("Notification")}} از {{domxref("EventTarget")}} ارث‌بری می‌کند، می‌توان متد {{domxref("EventTarget.addEventListener","addEventListener()")}} را نیز روی آن به کار برد.

> [!NOTE]
> رویدادهای فهرست‌شده در بالا مربوط به [اعلان‌های غیرماندگار](/en-US/docs/Web/API/Notifications_API#persistent_and_non-persistent_notifications) هستند که با سازندهٔ {{domxref("Notification.Notification", "Notification()")}} ایجاد می‌شوند. در مقابل، اعلان‌های ماندگار (persistent) که از طریق {{domxref("ServiceWorkerRegistration.showNotification()")}} ساخته می‌شوند، رویدادهای {{domxref("ServiceWorkerGlobalScope.notificationclick_event", "notificationclick")}} و {{domxref("ServiceWorkerGlobalScope.notificationclose_event", "notificationclose")}} را روی {{domxref("ServiceWorkerGlobalScope")}} فعال می‌کنند.

### پیمایش هنگام فعال‌سازی

به‌جای مدیریت رویدادهای کلیک، می‌توانید گزینهٔ {{domxref("Notification.navigate", "navigate")}} را طوری تنظیم کنید که وقتی کاربر اعلان را فعال می‌کند، به‌طور خودکار یک URL باز شود. این کار هر دو رویداد `click` و `notificationclick` را دور می‌زند. برای جزئیات بیشتر به {{domxref("Notification.navigate")}} مراجعه کنید.

## جایگزین کردن اعلان‌های موجود

معمولاً مطلوب نیست که کاربر در مدت‌زمان کوتاهی تعداد زیادی اعلان دریافت کند — برای مثال، اگر یک برنامهٔ پیام‌رسان برای هر پیام ورودی به کاربر اعلان بدهد و پیام‌های زیادی برای او ارسال شود چه اتفاقی می‌افتد؟ برای جلوگیری از ایجاد مزاحمت برای کاربر با اعلان‌های بیش از حد، می‌توان صف اعلان‌های در انتظار را تغییر داد و یک یا چند اعلان در انتظار را با یک اعلان جدید جایگزین کرد.

برای این کار می‌توان به هر اعلان جدید یک برچسب (tag) اضافه کرد. اگر اعلانی با همان برچسب از قبل وجود داشته باشد و هنوز نمایش داده نشده باشد، اعلان جدید جایگزین آن اعلان قبلی می‌شود. اگر اعلان با همان برچسب قبلاً نمایش داده شده باشد، اعلان قبلی بسته می‌شود و اعلان جدید نمایش داده می‌شود.

### مثال برچسب

فرض کنید HTML اولیهٔ زیر را داریم:

```html
<button id="notify">Notify me!</button>
<section id="demo-logs"></section>
```

```css hidden
#demo-logs {
  width: 90%;
  height: 100px;
  background-color: #dddddd;
  overflow-x: auto;
  padding: 10px;
  margin-top: 10px;
}
```

به این ترتیب می‌توان چند اعلان را مدیریت کرد:

```js
const demoLogs = document.querySelector("#demo-logs");

const button = document.querySelector("#notify");

button.addEventListener("click", () => {
  if (Notification?.permission === "granted") {
    demoLogs.innerText += `The site has permission to show notifications. Showing notifications.\n`;
    // If the user agreed to get notified
    // Let's try to send ten notifications
    let i = 0;
    // Using an interval cause some browsers (including Firefox) are blocking notifications if there are too much in a certain time.
    const interval = setInterval(() => {
      // Thanks to the tag, we should only see the "Hi no 9 from MDN." notification
      const n = new Notification(`Hi no ${i} from MDN.`, {
        tag: "soManyNotification",
      });
      if (i === 9) {
        clearInterval(interval);
      }
      i++;
    }, 200);
  } else if (Notification?.permission !== "denied") {
    demoLogs.innerText += "Requesting notification permission.\n";
    // If the user hasn't told if they want to be notified or not
    // Note: because of Chrome, we are not sure the permission property
    // is set, therefore it's unsafe to check for the "default" value.
    Notification.requestPermission().then((status) => {
      // If the user said okay
      if (status === "granted") {
        demoLogs.innerText +=
          "User granted the permission. Sending notifications.\n";
        let i = 0;
        // Using an interval cause some browsers (including Firefox) are blocking notifications if there are too much in a certain time.
        const interval = setInterval(() => {
          // Thanks to the tag, we should only see the "Message no 9 from MDN." notification
          const n = new Notification(`Message no ${i} from MDN.`, {
            tag: "soManyNotification",
          });
          if (i === 9) {
            clearInterval(interval);
          }
          i++;
        }, 200);
      } else {
        // Otherwise, we can fallback to a regular modal alert
        demoLogs.innerText += `User denied the permission request.\n`;
      }
    });
  } else {
    // If the user refuses to get notified, we can fallback to a regular modal alert
    demoLogs.innerText += `The site does not have permission to show notifications.\n`;
  }
});
```

### نتیجه

{{ EmbedLiveSample('Tag_example', '100%', 200) }}

برای آزمایش مثال بالا، [تنظیم ارسال اعلان](https://support.mozilla.org/en-US/kb/firefox-page-info-window#w_permissions) را برای وب‌سایت `https://live.mdnplay.dev` تغییر دهید.

## جستارهای وابسته

- {{ domxref("Notification") }}