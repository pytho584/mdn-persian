---
title: "Notification: Notification() constructor"
---

---
title: "Notification: Notification() constructor"
short-title: Notification()
slug: Web/API/Notification/Notification
page-type: web-api-constructor
browser-compat: api.Notification.Notification
---

{{APIRef("Web Notifications")}}{{securecontext_header}} {{AvailableInWorkers}}

سازندهٔ **`Notification()`** یک نمونهٔ جدید از شیء {{domxref("Notification")}} می‌سازد که نمایانگر یک اعلان کاربر است.

> [!WARNING]
> این سازنده تقریباً در همهٔ مرورگرهای موبایل هنگام فراخوانی یک {{jsxref("TypeError")}} پرتاب می‌کند.
> در عوض، باید یک service worker ثبت کنید و از {{domxref("ServiceWorkerRegistration.showNotification()")}} استفاده کنید.

## سینتکس

```js-nolint
new Notification(title)
new Notification(title, options)
```

### پارامترها

- `title`
  - : عنوانی برای اعلان تعیین می‌کند که در بالای پنجرهٔ اعلان نمایش داده می‌شود.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها شامل هرگونه تنظیمات سفارشی که می‌خواهید روی اعلان اعمال کنید. گزینه‌های ممکن عبارت‌اند از:
    - `actions` {{optional_inline}}
      - : باید تعیین‌نشده یا یک آرایهٔ خالی باشد. `actions` فقط برای [اعلان‌های ماندگار](/en-US/docs/Web/API/Notifications_API#persistent_and_non-persistent_notifications) که از یک service worker با استفاده از {{domxref("ServiceWorkerRegistration.showNotification()")}} ارسال می‌شوند، پشتیبانی می‌شود.
    - `badge` {{optional_inline}}
      - : رشته‌ای شامل URL تصویری که وقتی فضای کافی برای نمایش خود اعلان وجود ندارد برای نمایش آن استفاده می‌شود؛ برای مثال، نوار اعلان اندروید. در دستگاه‌های اندرویدی، نشان (badge) باید دستگاه‌هایی با وضوح تا ۴ برابر (حدود ۹۶×۹۶ پیکسل) را پشتیبانی کند و تصویر به‌صورت خودکار ماسک می‌شود.
    - `body` {{optional_inline}}
      - : رشته‌ای شامل متن اصلی اعلان که در زیر عنوان نمایش داده می‌شود. مقدار پیش‌فرض رشتهٔ خالی است.
    - `data` {{optional_inline}}
      - : داده‌های دلخواهی که می‌خواهید با اعلان مرتبط شوند. این داده می‌تواند از هر نوع [دادهٔ ساختاریافته-کلون‌شدنی](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm#supported_types) باشد. مقدار پیش‌فرض `null` است.
    - `dir` {{optional_inline}}
      - : جهتی که اعلان باید در آن نمایش داده شود. مقدار پیش‌فرض `auto` است که رفتار تنظیم زبان مرورگر را به کار می‌گیرد، اما می‌توانید با تنظیم مقادیر `ltr` و `rtl` این رفتار را لغو کنید (اگرچه به نظر می‌رسد بیشتر مرورگرها این تنظیمات را نادیده می‌گیرند).
    - `icon` {{optional_inline}}
      - : رشته‌ای شامل URL نمادی که در اعلان نمایش داده می‌شود.
    - `image` {{optional_inline}}
      - : رشته‌ای شامل URL تصویری که در اعلان نمایش داده می‌شود.
    - `lang` {{optional_inline}}
      - : زبان اعلان که با رشته‌ای شامل یک {{glossary("BCP 47 language tag")}} مشخص می‌شود. مقدار پیش‌فرض رشتهٔ خالی است.
    - `navigate` {{optional_inline}} {{experimental_inline}}
      - : رشته‌ای شامل URL که وقتی کاربر اعلان را فعال می‌کند به آن هدایت شود. وقتی این مقدار تنظیم شود، عامل کاربر (user agent) به‌جای صدور رویداد {{domxref("Notification.click_event", "click")}} به این URL هدایت می‌شود. این مقدار نسبت به URL پایهٔ صفحه تفسیر می‌شود. برای اطلاعات بیشتر به {{domxref("Notification.navigate")}} مراجعه کنید.
    - `renotify` {{optional_inline}}
      - : یک مقدار بولی که مشخص می‌کند آیا پس از جایگزینی اعلان جدید با اعلان قبلی، کاربر دوباره آگاه شود یا نه. مقدار پیش‌فرض `false` است، یعنی کاربر آگاه نخواهد شد. اگر `true` باشد، باید `tag` نیز تنظیم شود.
    - `requireInteraction` {{optional_inline}}
      - : مشخص می‌کند که اعلان باید تا زمانی که کاربر روی آن کلیک کند یا آن را رد کند فعال بماند، نه این‌که خودکار بسته شود. مقدار پیش‌فرض `false` است.
    - `silent` {{optional_inline}}
      - : یک مقدار بولی که مشخص می‌کند آیا اعلان باید بی‌صدا باشد، یعنی بدون توجه به تنظیمات دستگاه، هیچ صدا یا لرزشی تولید نشود. اگر روی `true` تنظیم شود، اعلان بی‌صدا است؛ اگر روی `null` تنظیم شود (مقدار پیش‌فرض)، تنظیمات پیش‌فرض دستگاه رعایت می‌شود.
    - `tag` {{optional_inline}}
      - : رشته‌ای که یک برچسب شناسایی برای اعلان را نشان می‌دهد. مقدار پیش‌فرض رشتهٔ خالی است.
    - `timestamp` {{optional_inline}}
      - : یک برچسب زمانی که به‌صورت {{glossary("Unix time")}} در میلی‌ثانیه داده می‌شود و زمان مرتبط با اعلان را نشان می‌دهد. این زمان می‌تواند در گذشته باشد، مثلاً وقتی اعلان برای پیامی استفاده می‌شود که به دلیل آفلاین بودن دستگاه نتوانسته فوراً تحویل داده شود، یا در آینده برای جلسه‌ای که به‌زودی آغاز می‌شود.
    - `vibrate` {{optional_inline}}
      - : یک [الگوی لرزش](/en-US/docs/Web/API/Vibration_API#vibration_patterns) برای سخت‌افزار لرزش دستگاه تا همراه با اعلان تولید شود. اگر این گزینه مشخص شده باشد، `silent` نباید `true` باشد.

### مقدار بازگشتی

یک نمونه از شیء {{domxref("Notification")}}.

### استثناها

- {{jsxref("TypeError")}}
  - : در این موارد پرتاب می‌شود:
    - سازنده درون {{domxref("ServiceWorkerGlobalScope")}} فراخوانده شود.
    - گزینهٔ `actions` مشخص شده باشد و خالی نباشد.
    - گزینهٔ `silent` برابر با `true` باشد و گزینهٔ `vibrate` مشخص شده باشد.
    - گزینهٔ `renotify` برابر با `true` باشد اما گزینهٔ `tag` خالی باشد.
- `DataCloneError` {{domxref("DOMException")}}
  - : اگر به هر دلیلی سریال‌سازی گزینهٔ `data` با شکست مواجه شود، پرتاب می‌شود.

## توضیحات

سازنده یک نمونهٔ جدید از شیء {{domxref("Notification")}} می‌سازد که نمایانگر یک اعلان کاربر است.

برای نمایش اعلان‌ها باید با استفاده از {{domxref("Notification.requestPermission_static", "Notification.requestPermission()")}} اجازه بگیرید. ممکن است اجازه قابل اعطا نباشد، مثلاً اگر صفحه در حالت مرور خصوصی باشد.

این سازنده تقریباً در همهٔ مرورگرهای موبایل هنگام فراخوانی یک {{jsxref("TypeError")}} پرتاب می‌کند و تغییر این وضعیت بعید است، زیرا صفحه‌های وب در دستگاه‌های موبایل تقریباً هرگز «در پس‌زمینه اجرا نمی‌شوند» که کاربرد اصلی اعلان‌هاست. در عوض، باید یک service worker ثبت کنید و از {{domxref("ServiceWorkerRegistration.showNotification()")}} استفاده کنید. برای اطلاعات بیشتر به [مشکل Chrome با شمارهٔ 481856](https://crbug.com/481856) مراجعه کنید.

## مثال‌ها

برای مثال‌های بیشتر، صفحهٔ {{domxref("Notification")}} و راهنمای [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API) را ببینید.

### مثال ساده

این یک مثال ساده است که اگر اجازه قبلاً داده شده باشد، یک اعلان نشان می‌دهد. این روش روی دستگاه‌های موبایل کار نخواهد کرد.

```js
if (Notification.permission === "granted") {
  const notification = new Notification("Hi there!");
}
```

### استفاده از Notification() به‌عنوان گزینهٔ جایگزین

این مثال یک رویکرد مقاوم‌تر را نشان می‌دهد که امکان نمایش اعلان‌ها را روی دستگاه‌های رومیزی و موبایل فراهم می‌کند.

ابتدا بررسی می‌کنیم که آیا {{domxref("Notification")}} پشتیبانی می‌شود و آیا اجازه داده شده است؛ اگر هر یک از این شرایط برقرار نباشد، زودتر از تابع بازمی‌گردیم. سپس بررسی می‌کنیم که آیا یک service worker فعال وجود دارد یا نه. اگر وجود داشت، از آن برای فراخوانی {{domxref("ServiceWorkerRegistration.showNotification()")}} استفاده می‌کنیم؛ در غیر این صورت، به فراخوانی سازنده برمی‌گردیم.

```js
async function showNotification(title, options = {}) {
  if (!("Notification" in window)) return;
  if (Notification.permission !== "granted") return;

  // Only use SW if one is already active — don't hang waiting
  const swReg = navigator.serviceWorker?.controller
    ? await navigator.serviceWorker.getRegistration()
    : null;

  if (swReg) {
    await swReg.showNotification(title, options);
  } else {
    new Notification(title, options);
  }
}
```

توجه داشته باشید که اگر صفحه روی دستگاه موبایل service worker آماده‌ای نداشته باشد، این کد همچنان خطا پرتاب می‌کند. بسته به برنامهٔ خود، می‌توانید این کد را در یک بلوک `try...catch` قرار دهید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استفاده از Notifications API](/en-US/docs/Web/API/Notifications_API/Using_the_Notifications_API)