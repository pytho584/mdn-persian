---
title: Notification
slug: Web/API/Notification
page-type: web-api-interface
browser-compat: api.Notification
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

رابط **`Notification`** از {{domxref("Notifications API", "", "", "nocode")}} برای پیکربندی و نمایش اعلان‌های دسکتاپ به کاربر استفاده می‌شود.

ظاهر و عملکرد خاص این اعلان‌ها در پلتفرم‌های مختلف متفاوت است، اما به طور کلی راهی برای ارائه اطلاعات به صورت ناهمزمان (asynchronous) به کاربر فراهم می‌کنند.

{{InheritanceDiagram}}

## سازنده (Constructor)

- {{domxref("Notification.Notification", "Notification()")}}
  - : یک نمونه جدید از شیء `Notification` ایجاد می‌کند.

## ویژگی‌های ایستا (Static properties)

_همچنین ویژگی‌هایی را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("Notification.permission_static", "Notification.permission")}} {{ReadOnlyInline}}
  - : رشته‌ای که نشان‌دهنده مجوز فعلی برای نمایش اعلان‌ها است. مقادیر ممکن عبارتند از:
    - `denied` — کاربر از نمایش اعلان‌ها خودداری کرده است.
    - `granted` — کاربر با نمایش اعلان‌ها موافقت کرده است.
    - `default` — انتخاب کاربر ناشناخته است و بنابراین مرورگر طوری عمل می‌کند که گویی مقدار denied است.

- {{domxref("Notification.maxActions_static", "Notification.maxActions")}} {{ReadOnlyInline}}
  - : حداکثر تعداد اقداماتی (actions) که توسط دستگاه و عامل کاربر (User Agent) پشتیبانی می‌شود.

## ویژگی‌های نمونه (Instance properties)

_همچنین ویژگی‌هایی را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("Notification.actions")}} {{ReadOnlyInline}}
  - : آرایه اقدامات (actions) اعلان، مطابق آنچه در پارامتر `options` سازنده مشخص شده است.
- {{domxref("Notification.badge")}} {{ReadOnlyInline}}
  - : رشته‌ای حاوی URL یک تصویر برای نمایش اعلان زمانی که فضای کافی برای نمایش خود اعلان وجود ندارد، مانند مثلاً نوار اعلان اندروید (Android Notification Bar). در دستگاه‌های اندروید، نشان (badge) باید تا وضوح ۴ برابر، حدود ۹۶ در ۹۶ پیکسل را پشتیبانی کند و تصویر به طور خودکار ماسک می‌شود.
- {{domxref("Notification.body")}} {{ReadOnlyInline}}
  - : رشته بدنه (body) اعلان، مطابق آنچه در پارامتر `options` سازنده مشخص شده است.
- {{domxref("Notification.data")}} {{ReadOnlyInline}}
  - : یک کلون ساختاریافته (structured clone) از داده‌های اعلان را برمی‌گرداند.
- {{domxref("Notification.dir")}} {{ReadOnlyInline}}
  - : جهت متن اعلان، مطابق آنچه در پارامتر `options` سازنده مشخص شده است.
- {{domxref("Notification.icon")}} {{ReadOnlyInline}}
  - : URL تصویری که به عنوان آیکون اعلان استفاده می‌شود، مطابق آنچه در پارامتر `options` سازنده مشخص شده است.
- {{domxref("Notification.image")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : URL تصویری که به عنوان بخشی از اعلان نمایش داده می‌شود، مطابق آنچه در پارامتر `options` سازنده مشخص شده است.
- {{domxref("Notification.lang")}} {{ReadOnlyInline}}
  - : کد زبان اعلان، مطابق آنچه در پارامتر `options` سازنده مشخص شده است.
- {{domxref("Notification.navigate")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : URL ناوبری اعلان. هنگامی که تنظیم شود، فعال‌سازی اعلان به جای فعال‌سازی رویداد {{domxref("Notification.click_event", "click")}} یا {{domxref("ServiceWorkerGlobalScope.notificationclick_event", "notificationclick")}}، به این URL هدایت می‌کند.
- {{domxref("Notification.renotify")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مشخص می‌کند که آیا پس از جایگزینی یک اعلان قدیمی با اعلان جدید، باید به کاربر اطلاع داده شود یا خیر.
- {{domxref("Notification.requireInteraction")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد یک اعلان باید تا زمانی که کاربر روی آن کلیک کند یا آن را رد کند، فعال باقی بماند، به جای اینکه به طور خودکار بسته شود.
- {{domxref("Notification.silent")}} {{ReadOnlyInline}}
  - : مشخص می‌کند که آیا اعلان باید بی‌صدا باشد — یعنی بدون توجه به تنظیمات دستگاه، هیچ صدایی یا لرزشی پخش نشود.
- {{domxref("Notification.tag")}} {{ReadOnlyInline}}
  - : شناسه (ID) اعلان (در صورت وجود)، مطابق آنچه در پارامتر `options` سازنده مشخص شده است.
- {{domxref("Notification.timestamp")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : زمانی را مشخص می‌کند که یک اعلان در آن ایجاد شده یا قابل اعمال است (گذشته، حال یا آینده).
- {{domxref("Notification.title")}} {{ReadOnlyInline}}
  - : عنوان اعلان، مطابق آنچه در اولین پارامتر سازنده مشخص شده است.
- {{domxref("Notification.vibrate")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک الگوی لرزش (vibration pattern) برای دستگاه‌هایی که سخت‌افزار لرزش دارند، مشخص می‌کند.

## روش‌های ایستا (Static methods)

_همچنین روش‌هایی را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("Notification.requestPermission_static", "Notification.requestPermission()")}}
  - : از کاربر برای نمایش اعلان‌ها درخواست مجوز می‌کند.

## روش‌های نمونه (Instance methods)

_همچنین روش‌هایی را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("Notification.close()")}}
  - : یک نمونه اعلان را به صورت برنامه‌ریزی شده (programmatically) می‌بندد.

## رویدادها (Events)

_همچنین رویدادهایی را از رابط والد خود، {{domxref("EventTarget")}}، به ارث می‌برد._

- {{domxref("Notification.click_event", "click")}}
  - : زمانی که کاربر روی اعلان کلیک می‌کند، فعال می‌شود.
- {{domxref("Notification.close_event", "close")}}
  - : زمانی که کاربر اعلان را می‌بندد، فعال می‌شود.
- {{domxref("Notification.error_event", "error")}}
  - : زمانی که اعلان با خطایی مواجه می‌شود، فعال می‌شود.
- {{domxref("Notification.show_event", "show")}}
  - : زمانی که اعلان نمایش داده می‌شود، فعال می‌شود.

## مثال‌ها

این HTML پایه را در نظر بگیرید:

```html
<button>Notify me!</button>
```

می‌توان یک اعلان را به صورت زیر ارسال کرد — در اینجا مجموعه‌ای نسبتاً طولانی و کامل از کد ارائه می‌دهیم که می‌توانید در صورت تمایل به بررسی ابتدا پشتیبانی از اعلان‌ها، سپس بررسی اینکه آیا مجوز برای مبدأ فعلی برای ارسال اعلان‌ها داده شده است، و در صورت نیاز درخواست مجوز، و سپس ارسال اعلان، از آن استفاده کنید.

```js
document.querySelector("button").addEventListener("click", notifyMe);

function notifyMe() {
  if (!("Notification" in window)) {
    // Check if the browser supports notifications
    alert("This browser does not support desktop notification");
  } else if (Notification.permission === "granted") {
    // Check whether notification permissions have already been granted;
    // if so, create a notification
    const notification = new Notification("Hi there!");
    // …
  } else if (Notification.permission !== "denied") {
    // We need to ask the user for permission
    Notification.requestPermission().then((permission) => {
      // If the user accepts, let's create a notification
      if (permission === "granted") {
        const notification = new Notification("Hi there!");
        // …
      }
    });
  }

  // At last, if the user has denied notifications, and you
  // want to be respectful there is no need to bother them anymore.
}
```

ما دیگر یک نمونه زنده در این صفحه نشان نمی‌دهیم، زیرا کروم و فایرفاکس دیگر اجازه درخواست مجوز اعلان از {{htmlelement("iframe")}}های متقابل-مبدأ (cross-origin) را نمی‌دهند، و مرورگرهای دیگر نیز به زودی این کار را انجام خواهند داد. برای دیدن یک مثال عملی، به [مثال لیست کارهای](https://github.com/mdn/dom-examples/tree/main/to-do-notifications) ما مراجعه کنید (همچنین [برنامه در حال اجرا](https://mdn.github.io/dom-examples/to-do-notifications/) را ببینید).

> [!NOTE]
> در مثال بالا، ما اعلان‌ها را در پاسخ به یک کنش کاربر (کلیک روی دکمه) ایجاد می‌کنیم. این نه تنها بهترین روش است — شما نباید کاربران را با اعلان‌هایی که با آن موافقت نکرده‌اند بمباران کنید — بلکه در آینده مرورگرها به صراحت از اعلان‌هایی که در پاسخ به یک کنش کاربر ایجاد نشده‌اند، جلوگیری خواهند کرد. برای مثال، فایرفاکس از نسخه ۷۲ این کار را انجام می‌دهد.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [استفاده از API اعلان‌ها](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)