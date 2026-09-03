---
title: Notifications API
slug: Web/API/Notifications_API
page-type: web-api-overview
browser-compat:
  - api.Notification
  - api.ServiceWorkerRegistration.showNotification
  - api.ServiceWorkerRegistration.getNotifications
spec-urls: https://notifications.spec.whatwg.org/
---

{{DefaultAPISidebar("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

API اعلان‌ها (Notifications API) به صفحات وب اجازه می‌دهد نمایش اعلان‌های سیستمی را برای کاربر نهایی کنترل کنند.

## مفاهیم و کاربرد

اعلان وب، جعبهٔ پیامی است که برای اطلاع‌رسانی به کاربران هنگام وقوع رویدادها در برنامه‌های وب استفاده می‌شود. اعلان‌های وب توسط سیستم اعلان بومیِ سیستم عامل نمایش داده می‌شوند، بنابراین دقیقاً همانند اعلان‌های هر برنامهٔ دیگری روی همان پلتفرم نمایش داده می‌شوند. از آنجا که سیستم عاملِ زیرین اعلان‌های وب را رندر می‌کند، این اعلان‌ها خارج از viewport (نمای دید) زمینهٔ مرور سطح بالا قرار دارند و حتی زمانی که کاربر تب را عوض کرده یا به برنامهٔ دیگری رفته باشد نیز می‌توانند نمایش داده شوند.

### اعلان‌های ماندگار و غیرماندگار

API اعلان‌ها از دو نوع اعلان پشتیبانی می‌کند:

- **اعلان‌های غیرماندگار** در یک زمینهٔ مرور، مانند یک صفحهٔ وب یا تب، ایجاد می‌شوند.
  طول عمر آن‌ها به طول عمر صفحه وابسته است — اگر صفحه بسته شود، دیگر نمی‌توان با اعلان تعامل کرد.

  آن‌ها با استفاده از سازندهٔ {{domxref("Notification.Notification","Notification()")}} ایجاد می‌شوند و رویدادهایی مانند {{domxref("Notification/click_event", "click")}} را مستقیماً روی نمونهٔ `Notification` صادر می‌کنند.

- **اعلان‌های ماندگار** از یک service worker ایجاد می‌شوند و می‌توانند فراتر از طول عمر یک صفحهٔ مشخص، تعامل‌پذیر باقی بمانند.

  آن‌ها با فراخوانی {{domxref("ServiceWorkerRegistration.showNotification()")}} از داخل یک service worker ایجاد می‌شوند و رویدادهای {{domxref("ServiceWorkerGlobalScope/notificationclick_event", "notificationclick")}} و {{domxref("ServiceWorkerGlobalScope/notificationclose_event", "notificationclose")}} را روی {{domxref("ServiceWorkerGlobalScope")}} صادر می‌کنند.

> [!NOTE]
> اگر کد شما باید روی دستگاه‌های همراه اجرا شود، **باید** از اعلان‌های ماندگار استفاده کنید!
> سازندهٔ {{domxref("Notification.Notification","Notification()")}} در بیشتر مرورگرهای موبایل یک {{jsxref("TypeError")}} پرتاب می‌کند.

### اعلان‌ها به اجازهٔ کاربر نیاز دارند

برای استفاده از اعلان‌ها، کاربر باید به مبدأِ فعلی اجازه دهد که اعلان‌های سیستمی را نمایش دهد. این کار معمولاً هنگام راه‌اندازی برنامه یا سایت، با استفاده از متد {{domxref("Notification.requestPermission_static", "Notification.requestPermission()")}} انجام می‌شود. این متد فقط باید هنگام رسیدگی به یک ژست کاربر (مانند رسیدگی به کلیک ماوس) فراخوانی شود. برای مثال:

```js
btn.addEventListener("click", () => {
  let promise = Notification.requestPermission();
  // wait for permission
});
```

این کار یک کادر گفت‌وگوی درخواست را نمایش می‌دهد، تقریباً به این شکل:

![کادر گفتگویی که از کاربر می‌خواهد نمایش اعلان‌ها از آن مبدأ را مجاز کند؛ با گزینه‌های «هرگز اجازه نده» و «اجازه دادن به اعلان‌ها».](screen_shot_2019-12-11_at_9.59.14_am.png)

کاربر از این‌جا می‌تواند انتخاب کند که به اعلان‌ها از این مبدأ اجازه دهد یا آن‌ها را مسدود کند. پس از انتخاب، این تنظیم معمولاً برای جلسهٔ جاری حفظ می‌شود.

### نمایش و مدیریت اعلان‌ها

اعلان‌ها با استفاده از سازندهٔ {{domxref("Notification.Notification","Notification()")}} ایجاد می‌شوند. این سازنده باید یک آرگومان عنوان به آن ارسال شود، و به‌صورت اختیاری می‌توان پارامتری برای مشخص کردن گزینه‌هایی مانند جهت متن، متن بدنه، آیکنی که نمایش داده شود، صدای اعلانی که پخش شود و موارد دیگر به آن ارسال کرد.

برای مثال، کد زیر نشان می‌دهد که چگونه می‌توانید اعلانی ایجاد کنید که گزینهٔ [`navigate`](/en-US/docs/Web/API/Notification/Notification#navigate) را تنظیم می‌کند؛ این گزینه نشانی اینترنتی را تعیین می‌کند که در صورت پذیرفته‌شدن اعلان باز می‌شود (همچنین می‌توانید کنترل‌کننده‌های کلیک را برای پردازش اقدامات اعلان تعریف کنید).

```js
if (Notification.permission === "granted") {
  const notification = new Notification("New message from Alice", {
    body: "Hey, are you free for lunch?",
    navigate: "/messages/alice",
  });
}
```

برای نمونه‌های کاربرد بیشتر، [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API) را ببینید.

## رابط‌ها

- {{domxref("Notification")}}
  - : یک شیء اعلان را تعریف می‌کند.
    هنگام فعال‌شدن، یک اعلان غیرماندگار رویداد {{domxref("Notification.click_event", "click")}} را صادر می‌کند، مگر اینکه یک URL با {{domxref("Notification.navigate", "navigate")}} تنظیم شده باشد، که در این صورت عامل کاربر (user agent) به‌جای آن به آن URL می‌رود.
- {{domxref("NotificationEvent")}}
  - : نمایانگر رویداد اعلانی است که روی {{domxref("ServiceWorkerGlobalScope")}} یک {{domxref("ServiceWorker")}} ارسال می‌شود.

### توسعه‌های رابط‌های دیگر

- رویداد {{domxref("ServiceWorkerGlobalScope/notificationclick_event", "notificationclick")}}
  - : هنگامی رخ می‌دهد که کاربر روی یک اعلان ماندگارِ نمایش‌داده‌شده کلیک می‌کند، مگر اینکه یک URL با {{domxref("Notification.navigate", "navigate")}} تنظیم شده باشد.
- رویداد {{domxref("ServiceWorkerGlobalScope/notificationclose_event", "notificationclose")}}
  - : هنگامی رخ می‌دهد که کاربر یک اعلان نمایش‌داده‌شده را می‌بندد.
- {{domxref("ServiceWorkerRegistration.getNotifications()")}}
  - : فهرستی از اعلان‌ها را به ترتیبی که از مبدأ فعلی و از طریق ثبت (registration) جاریِ service worker ایجاد شده‌اند برمی‌گرداند.
- {{domxref("ServiceWorkerRegistration.showNotification()")}}
  - : اعلان را با عنوان درخواستی نمایش می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)