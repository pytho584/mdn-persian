---
title: "MediaTrackSettings: restrictOwnAudio property"
short-title: restrictOwnAudio
slug: Web/API/MediaTrackSettings/restrictOwnAudio
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.MediaStreamTrack.applyConstraints.restrictOwnAudio_constraint
---

{{APIRef("Media Capture and Streams")}}{{SeeCompatTable}}

دیکشنری {{domxref("MediaTrackSettings")}}، ویژگی **`restrictOwnAudio`** کنترل می‌کند که آیا صدای سیستم که از تبِ در حال ضبط (capturing tab) می‌آید، از ضبط صفحه فیلتر شود یا نه. این امکان در برخی موارد ضبط‌های تمیزتری از صفحه فراهم می‌کند.

برای مثال، اگر خودِ صفحه‌ی وبِ در حال ضبط، صوتی مانند صدای یک ویدیو یا فایل صوتیِ تعبیه‌شده را پخش کند، آن صدا در ضبط گنجانده می‌شود. از آنجا که این موضوع می‌تواند به پژواک (echo) نامطلوب منجر شود یا با منابع صوتی موردنظر از تب‌ها یا برنامه‌های دیگر تداخل کند، حذف آن از ضبط مطلوب است.

## مقدار

یک مقدار بولی (boolean) که در آن `true` محدودیت صدای سیستمِ تبِ در حال ضبط را فعال می‌کند و `false` آن را غیرفعال می‌کند.

اگر مقدار `true` باشد، عامل کاربر (user agent) تلاش می‌کند هر صدایی را که از صدای ضبط‌شده‌ی تولیدشده توسط تبی که برای شروع ضبط صفحه، {{domxref("MediaDevices.getDisplayMedia()")}} را فراخوانی کرده است، حذف کند. اگر حذف صدا از طریق پردازش ناموفق باشد، عامل کاربر ممکن است تمام صداهای منتسب به تبِ در حال ضبط را از ضبط خارج کند.

> [!NOTE]
> اگر سطح نمایشِ ضبط‌شده شامل صدای سیستم نباشد، این تنظیم هیچ تأثیری نخواهد داشت.

## مثال‌ها

تابع زیر یک شیء محدودیت‌ها (constraints) می‌سازد که گزینه‌های فراخوانی {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} را مشخص می‌کند.
این تابع محدودیت `restrictOwnAudio` را (با درخواست حذف صدای سیستمِ منتسب به تبِ در حال ضبط از ضبط صفحه) فقط در صورتی اضافه می‌کند که مشخص باشد مرورگر از آن پشتیبانی می‌کند.
سپس ضبط با فراخوانی `getDisplayMedia()` شروع می‌شود و جریان برگشتی به عنصر {{htmlelement("video")}} اشاره‌شده توسط متغیر `videoElem` متصل می‌شود.

```js
async function capture() {
  const supportedConstraints = navigator.mediaDevices.getSupportedConstraints();
  const displayMediaOptions = {
    audio: {},
  };

  if (supportedConstraints.restrictOwnAudio) {
    displayMediaOptions.audio.restrictOwnAudio = true;
  }

  try {
    videoElem.srcObject =
      await navigator.mediaDevices.getDisplayMedia(displayMediaOptions);
  } catch (err) {
    /* handle the error */
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [Using the screen capture API](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}