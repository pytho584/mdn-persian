```
---
title: "MediaCapabilities: encodingInfo() method"
short-title: encodingInfo()
slug: Web/API/MediaCapabilities/encodingInfo
page-type: web-api-instance-method
browser-compat: api.MediaCapabilities.encodingInfo
---

{{APIRef("Media Capabilities API")}}{{AvailableInWorkers}}

متد **`encodingInfo()`** در رابط {{domxref("MediaCapabilities")}} یک {{jsxref('Promise')}} برمی‌گرداند که با قابلیت‌های پیکربندی رسانهٔ آزمایش‌شده برای رمزگذاری رسانه تکمیل می‌شود. این Promise شامل سه ویژگی بولین `supported`، `smooth` و `powerefficient` است که میزان سازگاری دستگاه با آن نوع رسانه را توصیف می‌کنند.

## نحو (Syntax)

```js-nolint
encodingInfo(configuration)
```

### پارامترها

- `configuration`
  - : یک شیء با ویژگی `type` و _یا_ یک ویژگی `video` یا ویژگی `audio` که شامل پیکربندی از نوع مناسب است: <!-- MediaEncodingConfiguration in the spec -->
    - `type`
      - : نوع رسانه‌ای است که آزمایش می‌شود. این ویژگی یکی از مقادیر زیر را می‌پذیرد:
        - `record`
          - : نمایانگر پیکربندی برای ضبط رسانه است، برای مثال با استفاده از {{domxref("MediaRecorder")}}.
        - `webrtc`
          - : نمایانگر پیکربندی‌ای است که برای انتقال از طریق ابزارهای الکترونیکی در نظر گرفته شده است (مثلاً با {{domxref("RTCPeerConnection")}}).
        - `transmission` {{non-standard_inline}}
          - : مترادفی برای `webrtc`.

    - `video`
      - : شیء پیکربندی برای منبع رسانهٔ ویدیویی. این ویژگی‌های زیر را دارد: <!-- VideoConfiguration in the spec -->
        - `contentType`
          - : رشته‌ای شامل یک نوع MIME ویدیویی معتبر و (به‌صورت اختیاری) یک [پارامتر `codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter).
        - `width`
          - : عرض ویدیو.
        - `height`
          - : ارتفاع ویدیو.
        - `bitrate`
          - : تعداد بیت‌هایی که برای رمزگذاری یک ثانیه از فایل ویدیو استفاده می‌شود.
        - `framerate`
          - : تعداد فریم‌هایی که یک ثانیه از پخش ویدیو را تشکیل می‌دهند.

    - `audio`
      - : شیء پیکربندی برای منبع رسانهٔ صوتی. این ویژگی‌های زیر را دارد: <!-- AudioConfiguration in the spec -->
        - `contentType`
          - : رشته‌ای شامل یک نوع MIME صوتی معتبر و (به‌صورت اختیاری) یک [پارامتر `codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter).
        - `channels`
          - : تعداد کانال‌های استفاده‌شده توسط تراک صوتی.
        - `bitrate`
          - : تعداد بیت‌هایی که برای رمزگذاری یک ثانیه از فایل صوتی استفاده می‌شود.
        - `samplerate`
          - : تعداد نمونه‌های صوتی تشکیل‌دهندهٔ یک ثانیه از فایل صوتی.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که با شیءای شامل سه ویژگی بولین تکمیل می‌شود:

- `supported`
  - : اگر محتوای رسانه اصلاً قابل رمزگذاری باشد، `true` خواهد بود. در غیر این صورت، `false` است.
- `smooth`
  - : اگر پخش رسانه روان (با کیفیت بالا) باشد، `true` خواهد بود. در غیر این صورت، `false` است.
- `powerEfficient`
  - : اگر پخش رسانه از نظر مصرف انرژی کارآمد باشد، `true` خواهد بود. در غیر این صورت، `false` است.

مرورگرها تا زمانی که آمار مربوط به این دستگاه ثبت نشده باشد، یک پیکربندی رسانهٔ پشتیبانی‌شده را به‌عنوان `smooth` و `powerEfficient` گزارش می‌کنند. همهٔ کدک‌های صوتی پشتیبانی‌شده نیز به‌عنوان کارآمد از نظر مصرف انرژی گزارش می‌شوند.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `configuration` ارسال‌شده به متد `encodingInfo()` نامعتبر باشد پرتاب می‌شود. این خطا ممکن است به هر یک از دلایل زیر رخ دهد:
    - نوع، ویدیو یا صدا نباشد،
    - `contentType` یک نوع MIME کدک معتبر نباشد،
    - خطای دیگری در پیکربندی رسانهٔ ارسال‌شده به متد وجود داشته باشد، از جمله حذف هر یک از عناصر `configuration`.

## مثال‌ها

### تنظیم یک پیکربندی رسانه

```js
// Create media configuration to be tested
const mediaConfig = {
  type: "record",
  video: {
    contentType: "video/webm;codecs=vp8.0", // valid content type
    width: 1920, // width of the video
    height: 1080, // height of the video
    bitrate: 120000, // number of bits used to encode 1s of video
    framerate: 48, // number of frames making up that 1s.
  },
};

// check support and performance
navigator.mediaCapabilities.encodingInfo(mediaConfig).then((result) => {
  console.log(
    `This configuration is ${result.supported ? "" : "not "}supported,`,
  );
  console.log(`${result.smooth ? "" : "not "}smooth, and`);
  console.log(`${result.powerEfficient ? "" : "not "}power efficient.`);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaCapabilities.decodingInfo()")}}
```