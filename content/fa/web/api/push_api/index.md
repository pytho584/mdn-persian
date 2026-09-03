---
title: "Push API"
slug: Web/API/Push_API
page-type: web-api-overview
browser-compat:
  - api.PushEvent
  - api.PushMessageData
---

{{DefaultAPISidebar("Push API")}}{{AvailableInWorkers}}

**Push API** به برنامه‌های وب این امکان را می‌دهد که پیام‌هایی را که سرور به سمت آن‌ها ارسال می‌کند دریافت کنند، چه برنامه در پیش‌زمینه باشد، چه در حال حاضر بارگذاری شده باشد یا حتی اصلاً در مرورگر باز نباشد. این قابلیت به توسعه‌دهندگان اجازه می‌دهد تا اعلان‌ها و به‌روزرسانی‌های ناهمگام را به کاربرانی که رضایت داده‌اند تحویل دهند و در نتیجه تعامل بهتری با محتوای جدید و به‌موقع ایجاد شود.

## مفاهیم و کاربرد Push

> [!WARNING]
> هنگام پیاده‌سازی اشتراک‌های PushManager، بسیار مهم است که از برنامه خود در برابر مشکلات CSRF/XSRF محافظت کنید. برای اطلاعات بیشتر مقالات زیر را ببینید:
>
> - [برگه تقلب جلوگیری از جعل درخواست بین‌سایتی (CSRF)](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html)
> - [جلوگیری از حملات CSRF و XSRF](https://blog.codinghorror.com/preventing-csrf-and-xsrf-attacks/)

برای اینکه یک برنامه بتواند پیام‌های فشاری (push) دریافت کند، باید یک [service worker](/en-US/docs/Web/API/Service_Worker_API) فعال داشته باشد. وقتی service worker فعال شد، می‌تواند با استفاده از {{domxref("PushManager.subscribe()")}} در اعلان‌های فشاری مشترک شود.

{{domxref("PushSubscription")}} حاصل شامل تمام اطلاعات موردنیاز برنامه برای ارسال پیام فشاری است: یک آدرس endpoint و کلید رمزنگاری لازم برای ارسال داده.

service worker در صورت نیاز برای مدیریت پیام‌های فشاری ورودی راه‌اندازی می‌شود و این پیام‌ها به رویدادگردان {{domxref("ServiceWorkerGlobalScope.push_event", "onpush")}} تحویل داده می‌شوند. این امکان را به برنامه‌ها می‌دهد که به دریافت پیام‌های فشاری واکنش نشان دهند، مثلاً با نمایش یک اعلان (با استفاده از {{domxref("ServiceWorkerRegistration.showNotification()")}}).

هر اشتراک منحصر‌به‌فرد برای یک service worker است. endpoint اشتراک یک [URL قابلیت](https://w3ctag.github.io/capability-urls/) منحصربه‌فرد است: دانستن endpoint تنها چیزی است که برای ارسال پیام به برنامه شما لازم است. بنابراین آدرس endpoint باید محرمانه بماند؛ در غیر این صورت، برنامه‌های دیگر ممکن است بتوانند پیام‌های فشاری به برنامه شما ارسال کنند.

فعال‌کردن یک service worker برای تحویل پیام فشاری می‌تواند مصرف منابع، به‌ویژه باتری را افزایش دهد. مرورگرهای مختلف روش‌های متفاوتی برای مدیریت این موضوع دارند و در حال حاضر هیچ سازوکار استانداردی وجود ندارد. فایرفاکس تعداد محدودی (سهمیه) پیام فشاری را برای ارسال به یک برنامه مجاز می‌داند، اگرچه پیام‌های فشاری که اعلان تولید می‌کنند از این محدودیت مستثنی هستند. این سهمیه هر بار که سایت بازدید می‌شود بازنشانی می‌شود. در کروم هیچ محدودیتی وجود ندارد.

## رابط‌ها (Interfaces)

- {{domxref("PushEvent")}}
  - : یک اقدام فشاری را نشان می‌دهد که به [حوزه سراسری](/en-US/docs/Web/API/ServiceWorkerGlobalScope) یک {{domxref("ServiceWorker")}} ارسال می‌شود. این رویداد حاوی اطلاعاتی است که از یک برنامه به یک {{domxref("PushSubscription")}} ارسال شده است.
- {{domxref("PushManager")}}
  - : راهی برای دریافت اعلان‌ها از سرورهای شخص ثالث و همچنین درخواست URL برای اعلان‌های فشاری فراهم می‌کند.
- {{domxref("PushMessageData")}}
  - : دسترسی به داده‌های فشاری ارسال‌شده توسط سرور را فراهم می‌کند و شامل روش‌هایی برای دستکاری داده‌های دریافتی است.
- {{domxref("PushSubscription")}}
  - : آدرس endpoint اشتراک را فراهم می‌کند و امکان لغو اشتراک از سرویس فشاری را می‌دهد.
- {{domxref("PushSubscriptionOptions")}}
  - : گزینه‌های مرتبط با اشتراک فشاری را نشان می‌دهد.

## افزوده‌های service worker

افزوده‌های زیر به [Service Worker API](/en-US/docs/Web/API/Service_Worker_API) در مشخصات Push API تعریف شده‌اند تا نقطه ورودی برای استفاده از پیام‌های فشاری فراهم کنند. این افزوده‌ها همچنین رویدادهای push و تغییر اشتراک را پایش و پاسخ می‌دهند.

- {{domxref("ServiceWorkerRegistration.pushManager")}} {{ReadOnlyInline}}
  - : ارجاعی به رابط {{domxref("PushManager")}} برای مدیریت اشتراک‌های فشاری، از جمله اشتراک‌گرفتن، دریافت اشتراک فعال و دسترسی به وضعیت مجوز فشاری برمی‌گرداند. این نقطه ورود به استفاده از پیام‌رسانی فشاری است.
- {{domxref("ServiceWorkerGlobalScope.push_event", "onpush")}}
  - : رویدادگردانی که هر بار یک رویداد {{domxref("ServiceWorkerGlobalScope/push_event", "push")}} رخ می‌دهد فراخوانی می‌شود؛ یعنی هر زمان که یک پیام فشاری از سمت سرور دریافت شود.
- {{domxref("ServiceWorkerGlobalScope.pushsubscriptionchange_event", "onpushsubscriptionchange")}}
  - : رویدادگردانی که هر بار یک رویداد {{domxref("ServiceWorkerGlobalScope/pushsubscriptionchange_event", "pushsubscriptionchange")}} رخ می‌دهد فراخوانی می‌شود؛ مثلاً وقتی یک اشتراک فشاری باطل شده یا در آستانه باطل‌شدن است (مثلاً وقتی سرویس فشاری زمان انقضا تعیین می‌کند).

## مثال‌ها

[کتاب دستور پخت ServiceWorker مایلا](https://github.com/mdn/serviceworker-cookbook) شامل مثال‌های کاربردی بسیاری درباره Push است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [ارسال اعلان‌های وب WebPush شناسایی‌شده با VAPID از طریق سرویس Push مایلا](https://blog.mozilla.org/services/2016/08/23/sending-vapid-identified-webpush-notifications-via-mozillas-push-service/)
- [نمای کلی اعلان‌های فشاری](https://web.dev/articles/push-notifications-overview)
- [Service Worker API](/en-US/docs/Web/API/Service_Worker_API)