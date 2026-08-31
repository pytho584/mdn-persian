---
title: "Beacon API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Beacon_API"
translated_by: "n8n + AI"
---

---
title: Beacon API
slug: Web/API/Beacon_API
page-type: web-api-overview
browser-compat: api.Navigator.sendBeacon
---

{{DefaultAPISidebar("Beacon")}}

API **`Beacon`** برای ارسال یک درخواست ناهمگام و غیرمسدودکننده به یک وب‌سرور استفاده می‌شود. این درخواست انتظار پاسخی ندارد. برخلاف درخواست‌هایی که با استفاده از {{domxref("XMLHttpRequest")}} یا [Fetch API](/en-US/docs/Web/API/Fetch_API) ساخته می‌شوند، مرورگر تضمین می‌کند که درخواست‌های beacon را قبل از تخلیه صفحه آغاز کند و آن‌ها را تا پایان اجرا کند.

کاربرد اصلی API Beacon ارسال داده‌های تحلیلی مانند رویدادهای سمت کلاینت یا داده‌های نشست به سرور است. از لحاظ تاریخی، وب‌سایت‌ها از {{domxref("XMLHttpRequest")}} برای این کار استفاده کرده‌اند، اما مرورگرها در برخی شرایط ارسال این درخواست‌های ناهمگام را تضمین نمی‌کنند (مثلاً اگر صفحه در آستانه تخلیه باشد). برای مقابله با این مشکل، وب‌سایت‌ها به تکنیک‌های مختلفی متوسل شده‌اند، مانند همگام کردن درخواست، که تأثیر بدی بر پاسخگویی دارند. از آنجا که درخواست‌های beacon هم ناهمگام هستند و هم ارسال آن‌ها تضمین شده است، ترکیبی از ویژگی‌های عملکرد خوب و قابلیت اطمینان را دارند.

برای جزئیات بیشتر درباره انگیزه و استفاده از این API، مستندات متد {{domxref("navigator.sendBeacon()")}} را ببینید.

> [!NOTE]
> این API در [Web Workers](/en-US/docs/Web/API/Web_Workers_API) _در دسترس نیست_ (از طریق {{domxref("WorkerNavigator")}} در معرض دید قرار نمی‌گیرد).

## رابط‌ها

این API یک متد واحد را تعریف می‌کند: {{domxref("navigator.sendBeacon()")}}.

این متد دو آرگومان می‌گیرد: URL و داده‌ای که در درخواست ارسال می‌شود. آرگومان داده اختیاری است و نوع آن ممکن است یک رشته، یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یک {{jsxref("DataView")}}، یک {{domxref("ReadableStream")}}، یک {{domxref("Blob")}}، یک شیء {{domxref("FormData")}} یا یک شیء {{domxref("URLSearchParams")}} باشد. اگر مرورگر با موفقیت درخواست را برای ارسال در صف قرار دهد، متد `true` برمی‌گرداند؛ در غیر این صورت `false` برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [استاندارد Beacon](https://w3c.github.io/beacon/)
- [داده‌های CanIUse برای Beacon](https://caniuse.com/#search=beacon)
- [رهگیری beacon‌ها از طریق service workers](https://ehsanakhgari.org/blog/2015-04-08/intercepting-beacons-through-service-workers/)؛ Ehsan Akhgari؛ 2015-Apr-08
- <https://webkit.org/blog/8821/link-click-analytics-and-privacy/>
- [ارسال Beacon در عمل](https://calendar.perfplanet.com/2020/beaconing-in-practice/)