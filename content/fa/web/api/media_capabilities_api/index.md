---
title: "Media Capabilities API"
slug: Web/API/Media_Capabilities_API
page-type: web-api-overview
browser-compat: api.MediaCapabilities
---

{{DefaultAPISidebar("Media Capabilities API")}}{{AvailableInWorkers}}

**Media Capabilities API** به توسعه‌دهندگان امکان می‌دهد تا قابلیت‌های رمزگشایی و رمزگذاری دستگاه را تعیین کنند و اطلاعاتی از جمله پشتیبانی از رسانه، روان بودن پخش و بهینه بودن مصرف انرژی را در اختیار آن‌ها قرار دهد.

## مفاهیم

انواع بی‌شماری از کدک‌های ویدئویی و صوتی وجود دارند. مرورگرهای مختلف از انواع مختلف رسانه پشتیبانی می‌کنند و انواع جدید رسانه نیز همواره در حال توسعه هستند. با استفاده از Media Capabilities API، توسعه‌دهندگان می‌توانند اطمینان حاصل کنند که هر کاربر بهترین نرخ بیت (bitrate) و صرفه‌جویی در فضای ذخیره‌سازی را متناسب با قابلیت‌های مرورگر، دستگاه و سیستم عامل خود دریافت می‌کند.

اینکه یک دستگاه از رمزگشایی سخت‌افزاری یا نرم‌افزاری استفاده کند، تأثیر مستقیمی بر روانی و بهینه بودن مصرف انرژی در رمزگشایی ویدئو و کارایی پخش دارد. Media Capabilities API به توسعه‌دهندگان امکان می‌دهد تعیین کنند کدام کدک‌ها پشتیبانی می‌شوند و یک فایل رسانه از نظر روانی و بازده انرژی چقدر عملکرد خوبی خواهد داشت.

Media Capabilities API قابلیت‌های قدرتمندتری نسبت به APIهای دیگر مانند {{DOMxref("MediaRecorder.isTypeSupported_static", "MediaRecorder.isTypeSupported()")}} یا {{DOMxRef("HTMLMediaElement.canPlayType()")}} ارائه می‌دهد، زیرا آن‌ها تنها به پشتیبانی کلی مرورگر می‌پردازند و نه عملکرد.

برای آزمایش پشتیبانی، روانی و بازده انرژی در رمزگذاری و رمزگشایی محتوای ویدئویی یا صوتی، از متدهای {{DOMxRef("MediaCapabilities.encodingInfo()","encodingInfo()")}} و {{DOMxRef("MediaCapabilities.decodingInfo()","decodingInfo()")}} موجود در رابط {{DOMxRef("MediaCapabilities")}} استفاده می‌کنید.

## رابط‌ها (Interfaces)

- {{DOMxRef("MediaCapabilities")}}
  - : اطلاعاتی در مورد قابلیت‌های رمزگشایی دستگاه، سیستم و مرورگر بر اساس کدک، پروفایل، وضوح و نرخ بیت ارائه می‌دهد. از این اطلاعات می‌توان برای ارائه جریان‌های رسانه‌ای بهینه به کاربر و تعیین اینکه آیا پخش باید روان و از نظر مصرف انرژی بهینه باشد، استفاده کرد.

### افزونه‌هایی به سایر رابط‌ها

- {{domxref("Navigator.mediaCapabilities")}} {{readonlyinline}}
  - : یک شیء {{domxref("MediaCapabilities")}} که می‌تواند اطلاعاتی در مورد قابلیت‌های رمزگشایی و رمزگذاری برای یک قالب رسانه و قابلیت‌های خروجی مشخص ارائه دهد.
- {{DOMxRef("WorkerNavigator.mediaCapabilities")}} {{readonlyinline}}
  - : یک شیء {{domxref("MediaCapabilities")}} که می‌تواند اطلاعاتی در مورد قابلیت‌های رمزگشایی و رمزگذاری برای یک قالب رسانه و قابلیت‌های خروجی مشخص ارائه دهد.

## مثال‌ها

### تشخیص پشتیبانی از فایل صوتی و عملکرد مورد انتظار

این مثال یک پیکربندی صوتی تعریف می‌کند و سپس بررسی می‌کند که آیا عامل کاربر (user agent) از رمزگشایی آن پیکربندی رسانه پشتیبانی می‌کند و آیا از نظر روانی و بازده انرژی عملکرد خوبی خواهد داشت یا خیر.

```js
if ("mediaCapabilities" in navigator) {
  const audioFileConfiguration = {
    type: "file",
    audio: {
      contentType: "audio/mp3",
      channels: 2,
      bitrate: 132700,
      samplerate: 5200,
    },
  };

  navigator.mediaCapabilities
    .decodingInfo(audioFileConfiguration)
    .then((result) => {
      console.log(
        `This configuration is ${result.supported ? "" : "not "}supported,`,
      );
      console.log(`${result.smooth ? "" : "not "}smooth, and`);
      console.log(`${result.powerEfficient ? "" : "not "}power efficient.`);
    })
    .catch(() => {
      console.log(`decodingInfo error: ${contentType}`);
    });
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- متد [canPlayType()](/en-US/docs/Web/API/HTMLMediaElement/canPlayType) در [HTMLMediaElement](/en-US/docs/Web/API/HTMLMediaElement)
- متد [isTypeSupported()](/en-US/docs/Web/API/MediaSource/isTypeSupported_static) در [MediaSource](/en-US/docs/Web/API/MediaSource)
- [استفاده از Media Capabilities API](/en-US/docs/Web/API/Media_Capabilities_API/Using_the_Media_Capabilities_API)