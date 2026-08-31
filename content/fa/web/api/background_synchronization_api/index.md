---
title: "Background Synchronization API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Background_Synchronization_API"
translated_by: "n8n + AI"
---

---
title: Background Synchronization API
slug: Web/API/Background_Synchronization_API
page-type: web-api-overview
browser-compat:
  - api.SyncManager
  - api.ServiceWorkerGlobalScope.sync_event
spec-urls: https://wicg.github.io/background-sync/spec/
---

{{DefaultAPISidebar("Background Sync")}}{{Securecontext_Header}}{{AvailableInWorkers}}

رابط برنامه‌نویسی **همگام‌سازی پس‌زمینه** (Background Synchronization API) به یک برنامه وب امکان می‌دهد تا وظایف را به تعویق بیندازد تا بتوانند در یک [کارگر سرویس](/en-US/docs/Web/API/Service_Worker_API) پس از اینکه کاربر به یک اتصال شبکه پایدار دست یافت، اجرا شوند.

## مفاهیم و کاربرد

رابط برنامه‌نویسی همگام‌سازی پس‌زمینه به برنامه‌های وب اجازه می‌دهد تا کارهای همگام‌سازی سرور را به کارگر سرویس خود واگذار کنند تا در زمان بعدی، اگر دستگاه آفلاین است، انجام شوند. موارد استفاده ممکن است شامل ارسال درخواست‌ها در پس‌زمینه باشد اگر در حین استفاده از برنامه نتوانستند ارسال شوند.

به عنوان مثال، یک برنامه کلاینت ایمیل می‌تواند به کاربران خود اجازه دهد در هر زمان، حتی زمانی که دستگاه به شبکه متصل نیست، پیام‌ها را بنویسند و ارسال کنند. فرانت‌اند برنامه فقط یک درخواست همگام‌سازی ثبت می‌کند و کارگر سرویس زمانی که شبکه دوباره حاضر شد مطلع شده و همگام‌سازی را انجام می‌دهد.

رابط {{domxref('SyncManager')}} از طریق {{domxref('ServiceWorkerRegistration.sync')}} در دسترس است. یک شناسه برچسب منحصر به فرد برای 'نام‌گذاری' رویداد همگام‌سازی تنظیم می‌شود، که سپس می‌توان در اسکریپت {{domxref('ServiceWorker')}} به آن گوش داد. پس از دریافت رویداد، می‌توانید هر عملکرد موجود مانند ارسال درخواست‌ها به سرور را اجرا کنید.

از آنجایی که این API به کارگرهای سرویس متکی است، عملکرد ارائه شده توسط این API فقط در یک زمینه امن در دسترس است.

## رابط‌ها

- {{domxref('SyncManager')}} {{Experimental_Inline}}
  - : وظایفی را ثبت می‌کند که در زمان بعدی با اتصال شبکه در یک کارگر سرویس اجرا شوند. این وظایف به عنوان _درخواست‌های همگام‌سازی پس‌زمینه_ شناخته می‌شوند.
- {{domxref('SyncEvent')}} {{Experimental_Inline}}
  - : نمایانگر یک رویداد همگام‌سازی است که به [حوزه سراسری](/en-US/docs/Web/API/ServiceWorkerGlobalScope) یک {{domxref('ServiceWorker')}} ارسال می‌شود. این راهی برای اجرای وظایف در کارگر سرویس پس از اینکه دستگاه به اتصال شبکه دست یافت، فراهم می‌کند.

### افزونه‌های دیگر رابط‌ها

افزونه‌های زیر به [رابط برنامه‌نویسی کارگر سرویس](/en-US/docs/Web/API/Service_Worker_API) یک نقطه ورود برای راه‌اندازی همگام‌سازی پس‌زمینه فراهم می‌کنند.

- {{domxref("ServiceWorkerRegistration.sync")}} {{ReadOnlyInline}}
  - : یک مرجع به رابط {{domxref("SyncManager")}} برای ثبت وظایفی که پس از برقراری اتصال شبکه اجرا می‌شوند، برمی‌گرداند.
- {{domxref("ServiceWorkerGlobalScope/sync_event", "sync")}} event
  - : یک کنترل‌کننده رویداد که هر زمان یک رویداد {{domxref("ServiceWorkerGlobalScope/sync_event", "sync")}} رخ می‌دهد، فعال می‌شود. این به محض در دسترس شدن شبکه اتفاق می‌افتد.

## مثال‌ها

مثال‌های زیر نحوه استفاده از رابط را نشان می‌دهند.

### درخواست یک همگام‌سازی پس‌زمینه

تابع ناهمگام زیر یک همگام‌سازی پس‌زمینه را از یک زمینه مرورگر ثبت می‌کند:

```js
async function syncMessagesLater() {
  const registration = await navigator.serviceWorker.ready;
  try {
    await registration.sync.register("sync-messages");
  } catch {
    console.log("Background Sync could not be registered!");
  }
}
```

### تأیید یک همگام‌سازی پس‌زمینه با برچسب

این کد بررسی می‌کند که آیا یک وظیفه همگام‌سازی پس‌زمینه با یک برچسب مشخص ثبت شده است یا خیر.

```js
navigator.serviceWorker.ready.then((registration) => {
  registration.sync.getTags().then((tags) => {
    if (tags.includes("sync-messages")) {
      console.log("Messages sync already requested");
    }
  });
});
```

### گوش دادن به یک همگام‌سازی پس‌زمینه در داخل یک کارگر سرویس

مثال زیر نحوه پاسخ به یک رویداد همگام‌سازی پس‌زمینه در کارگر سرویس را نشان می‌دهد.

```js
self.addEventListener("sync", (event) => {
  if (event.tag === "sync-messages") {
    event.waitUntil(sendOutboxMessages());
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [معرفی همگام‌سازی پس‌زمینه](https://developer.chrome.com/blog/background-sync/)