---
title: "MediaRecorder: mimeType property"
short-title: mimeType
slug: Web/API/MediaRecorder/mimeType
page-type: web-api-instance-property
browser-compat: api.MediaRecorder.mimeType
---

{{APIRef("MediaStream Recording")}}

ویژگی فقط-خواندنی **`mimeType`** از رابط {{domxref("MediaRecorder")}}، نوع رسانه {{Glossary("MIME")}} را برمی‌گرداند که هنگام ایجاد شیء {{domxref("MediaRecorder")}} مشخص شده بود، یا اگر هیچ‌کدام مشخص نشده بود، نوعی که توسط مرورگر انتخاب شده است. این فرمت فایلی است که از نوشتن تمام داده‌های ضبط شده روی دیسک حاصل می‌شود.

به خاطر داشته باشید که همه کدک‌ها توسط یک ظرف خاص پشتیبانی نمی‌شوند؛ اگر رسانه را با استفاده از کدکی بنویسید که توسط یک ظرف رسانه پشتیبانی نمی‌شود، فایل حاصل ممکن است در هنگام پخش به‌طور قابل اعتماد کار نکند، اگر اصلاً کار کند. برای اطلاعات درباره پشتیبانی از ظرف‌ها و کدک‌ها در مرورگرها، به [راهنمای انواع و فرمت‌های رسانه](/en-US/docs/Web/Media/Guides/Formats) مراجعه کنید.

> [!NOTE]
> اصطلاح «نوع MIME» به‌طور رسمی تاریخی در نظر گرفته می‌شود؛ این رشته‌ها اکنون به‌طور رسمی با نام **انواع رسانه** شناخته می‌شوند.
> محتوای MDN Web Docs از این اصطلاحات به‌جای یکدیگر استفاده می‌کند.

## مقدار

نوع رسانه MIME که فرمت رسانه ضبط شده را توصیف می‌کند، به صورت یک رشته. این رشته _ممکن است_ شامل [پارامتر `codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter) باشد که جزئیات مربوط به کدک‌ها و پیکربندی کدک‌های استفاده شده توسط ضبط‌کننده رسانه را ارائه می‌دهد.

رشته‌های نوع رسانه توسط سازمان IANA (Internet Assigned Numbers Authority) استاندارد شده‌اند. برای فهرست رسمی آن‌ها از رشته‌های نوع رسانه تعریف شده، به مقاله [Media Types](https://www.iana.org/assignments/media-types/media-types.xhtml) در سایت IANA مراجعه کنید. همچنین به [انواع رسانه](/en-US/docs/Web/HTTP/Guides/MIME_types) مراجعه کنید تا درباره انواع رسانه و نحوه استفاده از آن‌ها در محتوای وب و توسط مرورگرهای وب بیشتر بدانید.

## مثال‌ها

```js
if (navigator.mediaDevices) {
  console.log("getUserMedia supported.");

  const constraints = { audio: true, video: true };
  const chunks = [];

  navigator.mediaDevices
    .getUserMedia(constraints)
    .then((stream) => {
      const options = {
        audioBitsPerSecond: 128000,
        videoBitsPerSecond: 2500000,
        mimeType: "video/mp4",
      };
      const mediaRecorder = new MediaRecorder(stream, options);
      m = mediaRecorder;

      m.mimeType; // would return 'video/mp4'
      // …
    })
    .catch((error) => {
      console.error(error.message);
    });
}
```

تغییر `mimeType` در `options` به `'video/mp4; codecs="avc1.424028, mp4a.40.2"'` باعث می‌شود `MediaRecorder` سعی کند از پروفایل AVC Constrained Baseline Profile Level 4 برای ویدیو و AAC-LC (Low Complexity) برای صدا استفاده کند، که برای دستگاه‌های همراه و سایر موقعیت‌های محدود از نظر منابع مناسب است.

با فرض اینکه این پیکربندی برای عامل کاربر قابل قبول باشد، مقداری که بعداً توسط `m.mimeType` برگردانده می‌شود `video/mp4; codecs="avc1.424028, mp4a.40.2"` خواهد بود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [کدک‌ها در انواع رسانه رایج](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): دموی تجسم‌سازی MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([متن منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone))
- [دموی ضبط MediaStream از simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton)
- {{domxref("MediaDevices.getUserMedia()")}}