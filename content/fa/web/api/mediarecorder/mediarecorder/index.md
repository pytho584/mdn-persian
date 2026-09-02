---
title: "MediaRecorder: MediaRecorder() constructor"
short-title: MediaRecorder()
slug: Web/API/MediaRecorder/MediaRecorder
page-type: web-api-constructor
browser-compat: api.MediaRecorder.MediaRecorder
---

{{APIRef("MediaStream Recording")}}

سازنده **`MediaRecorder()`** یک شیء جدید از نوع {{domxref("MediaRecorder")}} می‌سازد که یک {{domxref("MediaStream")}} مشخص را ضبط می‌کند.

این شیء به صورت اختیاری می‌تواند برای ضبط با استفاده از یک ظرف رسانه‌ای (نوع فایل) خاص پیکربندی شود، و همچنین می‌تواند کدک و تنظیمات کدک دقیق را با مشخص کردن [پارامتر `codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter) تعیین کند.

## ساختار

```js-nolint
new MediaRecorder(stream)
new MediaRecorder(stream, options)
```

### پارامترها

- `stream`
  - : {{domxref("MediaStream")}}ای که قرار است ضبط شود. این منبع رسانه می‌تواند از یک جریان ایجاد شده با استفاده از {{domxref("MediaDevices.getUserMedia", "navigator.mediaDevices.getUserMedia()")}} یا از یک عنصر {{HTMLElement("audio")}}، {{HTMLElement("video")}} یا {{HTMLElement("canvas")}} به دست آید.
- `options` {{optional_inline}}
  - : یک شیء دیکشنری که می‌تواند شامل ویژگی‌های زیر باشد:
    - `mimeType` {{optional_inline}}
      - : یک نوع MIME که فرمت رسانه حاصل را مشخص می‌کند؛ می‌توانید فرمت ظرف را تعیین کنید (مرورگر کدک‌های ترجیحی خود را برای صدا و/یا ویدیو انتخاب می‌کند)، یا می‌توانید [از پارامتر `codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter) و/یا پارامتر `profiles` برای ارائه اطلاعات دقیق درباره اینکه از کدام کدک‌ها استفاده شود و چگونه آن‌ها را پیکربندی کنید، استفاده کنید. برنامه‌ها می‌توانند از قبل با فراخوانی {{domxref("MediaRecorder.isTypeSupported_static", "MediaRecorder.isTypeSupported()")}} بررسی کنند که آیا یک `mimeType` توسط {{Glossary("user agent")}} پشتیبانی می‌شود یا خیر. پیش‌فرض یک رشته خالی است.
    - `audioBitsPerSecond` {{optional_inline}}
      - : نرخ بیت انتخابی برای مؤلفه صوتی رسانه.
    - `videoBitsPerSecond` {{optional_inline}}
      - : نرخ بیت انتخابی برای مؤلفه ویدیویی رسانه.
    - `bitsPerSecond` {{optional_inline}}
      - : نرخ بیت انتخابی برای مؤلفه‌های صوتی و ویدیویی رسانه. این می‌تواند به جای دو ویژگی فوق مشخص شود. اگر این همراه با یکی از دو ویژگی فوق مشخص شود، این ویژگی برای آن‌که مشخص نشده استفاده خواهد شد.
    - `audioBitrateMode` {{optional_inline}}
      - : حالت نرخ بیتی که باید برای رمزگذاری صدا استفاده شود. می‌تواند `constant` باشد که نشان می‌دهد ضبط‌کننده باید با نرخ بیت ثابت رمزگذاری کند، یا `variable` که نشان می‌دهد ضبط‌کننده باید با نرخ بیت متغیر رمزگذاری کند، بنابراین فضای بیشتری برای سیگنال‌های پیچیده و فضای کمتری برای سیگنال‌های کم‌پیچیده اختصاص می‌دهد. پیش‌فرض `variable` است.
    - `videoKeyFrameIntervalDuration` {{optional_inline}}
      - : فاصله زمانی اسمی بین فریم‌های کلیدی در جریان ویدیوی رمزگذاری‌شده. {{glossary("user agent")}} تولید فریم کلیدی را بر اساس این گزینه و گزینه `videoKeyFrameIntervalCount` کنترل می‌کند.
    - `videoKeyFrameIntervalCount` {{optional_inline}}
      - : فاصله بر حسب تعداد فریم‌ها بین فریم‌های کلیدی در جریان ویدیوی رمزگذاری‌شده. {{glossary("user agent")}} تولید فریم کلیدی را با در نظر گرفتن این گزینه و همچنین گزینه `videoKeyFrameIntervalDuration` کنترل می‌کند.

    > [!NOTE]
    > اگر مقادیر بیت در ثانیه برای ویدیو و/یا صدا مشخص نشود، پیش‌فرض برای ویدیو بسته به مرورگر ۲.۵ مگابیت در ثانیه یا ۱۰ مگابیت در ثانیه است. پیش‌فرض صدا تطبیقی است و به نرخ نمونه‌برداری و تعداد کانال‌ها بستگی دارد.

    > [!NOTE]
    > وضوح ویدیو، نرخ فریم و تنظیمات مشابه به عنوان محدودیت‌ها هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} مشخص می‌شوند، نه در اینجا در API ضبط MediaStream.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر نوع MIME مشخص شده توسط عامل کاربر پشتیبانی نشود، پرتاب می‌شود.

## مثال‌ها

این مثال نحوه ایجاد یک ضبط‌کننده رسانه برای یک جریان مشخص را نشان می‌دهد که نرخ بیت صوتی آن روی ۱۲۸ کیلوبیت در ثانیه و نرخ بیت ویدیویی آن روی ۲.۵ مگابیت در ثانیه تنظیم شده است. داده‌های رسانه ضبط‌شده در یک ظرف MP4 ذخیره می‌شوند (بنابراین اگر تکه‌های داده رسانه را جمع‌آوری کرده و در دیسک ذخیره کنید، در یک فایل MP4 خواهند بود).

```js
if (navigator.mediaDevices.getUserMedia) {
  const constraints = { audio: true, video: true };
  const chunks = [];

  const onSuccess = (stream) => {
    const options = {
      audioBitsPerSecond: 128000,
      videoBitsPerSecond: 2500000,
      mimeType: "video/mp4",
    };
    const mediaRecorder = new MediaRecorder(stream, options);
    m = mediaRecorder;

    // …
  };
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Using the MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): MediaRecorder +
  getUserMedia + Web Audio API visualization demo, by [Chris Mills](https://github.com/chrisdavidmills) ([source on GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [simpl.info MediaStream Recording demo](https://simpl.info/mediarecorder/), by [Sam Dutton](https://github.com/samdutton).
- {{domxref("MediaDevices.getUserMedia")}}
- [MediaRecorder Video Bitrates](https://blog.addpipe.com/mediarecorder-video-bitrates/)