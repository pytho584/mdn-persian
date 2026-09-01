```yaml
---
title: "Document: visibilitychange event"
short-title: visibilitychange
slug: Web/API/Document/visibilitychange_event
page-type: web-api-event
browser-compat: api.Document.visibilitychange_event
---

{{APIRef}}

رویداد `visibilitychange` روی سند (Document) زمانی که وضعیت visibility آن تغییر می‌کند، شلیک می‌شود — برای مثال، زمانی که کاربر تب‌های مرورگر را عوض می‌کند، به صفحه جدیدی می‌رود، مرورگر را کوچک می‌کند یا می‌بندد، یا در دستگاه‌های همراه به برنامه دیگری سوئیچ می‌کند.

این رویداد قابل لغو (cancelable) نیست.

## نحو (Syntax)

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("visibilitychange", (event) => { })

onvisibilitychange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## نکات استفاده

این رویداد وضعیت visibility به‌روزرسانی شده سند را شامل نمی‌شود، اما می‌توانید آن اطلاعات را از ویژگی {{domxref("Document.visibilityState", "visibilityState")}} سند دریافت کنید.

این رویداد با `visibilityState` برابر با `hidden` زمانی شلیک می‌شود که کاربر به صفحه جدیدی می‌رود، تب‌ها را عوض می‌کند، تب را می‌بندد، مرورگر را کوچک یا می‌بندد، یا در دستگاه‌های همراه از مرورگر به برنامه دیگری سوئیچ می‌کند. انتقال به `hidden` آخرین رویدادی است که به طور قابل اعتماد توسط صفحه قابل مشاهده است، بنابراین توسعه‌دهندگان باید آن را به عنوان پایان احتمالی جلسه کاربر در نظر بگیرند (برای مثال، برای [ارسال داده‌های تحلیلی](/en-US/docs/Web/API/Navigator/sendBeacon)).

انتقال به `hidden` همچنین نقطه خوبی است که در آن صفحات می‌توانند به‌روزرسانی‌های UI را متوقف کنند و هر وظیفه‌ای را که کاربر نمی‌خواهد در پس‌زمینه اجرا شود، متوقف کنند.

## مثال‌ها

### توقف پخش صدا هنگام انتقال به حالت مخفی

این مثال پخش صدا را زمانی که صفحه مخفی می‌شود متوقف می‌کند و زمانی که صفحه دوباره قابل مشاهده می‌شود پخش را از سر می‌گیرد.
برای یک مثال کامل، به مستندات [Page Visibility API: توقف صدا در هنگام مخفی شدن صفحه](/en-US/docs/Web/API/Page_Visibility_API#pausing_audio_on_page_hide) مراجعه کنید.

```js
document.addEventListener("visibilitychange", () => {
  if (document.hidden) {
    playingOnHide = !audio.paused;
    audio.pause();
  } else if (playingOnHide) {
    // Resume playing if audio was "playing on hide"
    audio.play();
  }
});
```

### ارسال داده‌های تحلیلی پایان جلسه هنگام انتقال به حالت مخفی

این مثال انتقال به `hidden` را به عنوان پایان جلسه کاربر در نظر می‌گیرد و داده‌های تحلیلی مناسب را با استفاده از API {{domxref("Navigator.sendBeacon()")}} ارسال می‌کند:

```js
document.onvisibilitychange = () => {
  if (document.visibilityState === "hidden") {
    navigator.sendBeacon("/log", analyticsData);
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [Page Visibility API](/en-US/docs/Web/API/Page_Visibility_API)
- {{domxref("Document.visibilityState")}}
- {{domxref("Document.hidden")}}
- [وضعیت کاربر و برنامه را از دست ندهید، از Page Visibility استفاده کنید](https://www.igvita.com/2015/11/20/dont-lose-user-and-app-state-use-page-visibility/) به طور دقیق توضیح می‌دهد که چرا باید از `visibilitychange` استفاده کنید، نه `beforeunload`/`unload`.
- [Page Lifecycle API](https://developer.chrome.com/docs/web-platform/page-lifecycle-api) راهنمایی‌های بهترین روش‌ها را برای مدیریت رفتار چرخه حیات صفحه در برنامه‌های وب شما ارائه می‌دهد.
```