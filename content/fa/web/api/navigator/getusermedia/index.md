---
title: "Navigator: getUserMedia() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Navigator/getUserMedia"
---

---
title: "Navigator: getUserMedia() method"
short-title: getUserMedia()
slug: Web/API/Navigator/getUserMedia
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.Navigator.getUserMedia
---

{{APIRef("Media Capture and Streams")}}{{deprecated_header}}{{SecureContext_Header}}

متد منسوخ‌شدهٔ **`Navigator.getUserMedia()`** از کاربر برای دریافت اجازهٔ استفاده از حداکثر یک دستگاه ورودی ویدیو (مانند دوربین یا صفحهٔ به‌اشتراک‌گذاری‌شده) و حداکثر یک دستگاه ورودی صدا (مانند میکروفون) به‌عنوان منبع یک {{domxref("MediaStream")}} درخواست می‌کند.

اگر اجازه داده شود، یک `MediaStream` که مسیرهای ویدیویی و/یا صوتی آن از آن دستگاه‌ها می‌آیند، به تابع موفقیت (success callback) مشخص‌شده تحویل داده می‌شود.
اگر اجازه رد شود، هیچ دستگاه ورودی سازگاری وجود نداشته باشد، یا هر شرایط خطای دیگری رخ دهد، تابع خطا با یک شیء که شرح می‌دهد چه چیزی اشتباه شده است، اجرا می‌شود.
اگر کاربر اصلاً انتخابی انجام ندهد، هیچ‌کدام از توابع فراخوانی اجرا نمی‌شوند.

> [!NOTE]
> این یک متد قدیمی است.
> لطفاً به‌جای آن از نسخهٔ جدیدتر {{domxref("MediaDevices.getUserMedia", "navigator.mediaDevices.getUserMedia()")}} استفاده کنید.
> اگرچه از نظر فنی منسوخ نشده است، این نسخهٔ قدیمی مبتنی بر تابع فراخوانی به‌عنوان منسوخ علامت‌گذاری شده است، زیرا مشخصات به‌شدت استفاده از نسخهٔ جدیدتر مبتنی بر وعده (Promise) را توصیه می‌کند.

## Syntax

```js-nolint
getUserMedia(constraints, successCallback, errorCallback)
```

### Parameters

- `constraints`
  - : یک شیء که انواع رسانه‌ای را که باید درخواست شوند، همراه با هرگونه الزامات برای هر نوع، مشخص می‌کند. برای جزئیات، بخش [constraints](/en-US/docs/Web/API/MediaDevices/getUserMedia#parameters) را در متد مدرن {{domxref("MediaDevices.getUserMedia()")}} و همچنین مقالهٔ [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) را ببینید.
- `successCallback`
  - : تابعی که وقتی درخواست دسترسی به رسانه تأیید می‌شود فراخوانی می‌شود. این تابع با یک پارامتر فراخوانی می‌شود: شیء {{domxref("MediaStream")}} که جریان رسانه را شامل می‌شود. تابع فراخوانی شما سپس می‌تواند جریان را به شیء موردنظر (مانند یک عنصر {{HTMLElement("audio")}} یا {{HTMLElement("video")}}) اختصاص دهد، همان‌گونه که در مثال زیر نشان داده شده است:

    ```js
    function successCallback(stream) {
      const video = document.querySelector("video");
      video.srcObject = stream;
      video.onloadedmetadata = (e) => {
        // Do something with the video here.
      };
    }
    ```

- `errorCallback`
  - : وقتی فراخوانی با شکست مواجه شود، تابع مشخص‌شده در `errorCallback` با یک شیء به‌عنوان تنها آرگومان خود فراخوانی می‌شود؛ این شیء بر اساس {{domxref("DOMException")}} مدل‌سازی شده است.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

### عرض و ارتفاع

در اینجا نمونه‌ای از استفاده از `getUserMedia()`، شامل کدی برای مقابله با پیشوندهای مختلف مرورگرها آورده شده است. توجه داشته باشید که این روش منسوخ انجام این کار است: برای نمونه‌های مدرن، بخش [Examples](/en-US/docs/Web/API/MediaDevices/getUserMedia#frame_rate) را در زیر {{domxref("MediaDevices.getUserMedia()")}} ببینید.

```js
navigator.getUserMedia =
  navigator.getUserMedia ||
  navigator.webkitGetUserMedia ||
  navigator.mozGetUserMedia;

if (navigator.getUserMedia) {
  navigator.getUserMedia(
    { audio: true, video: { width: 1280, height: 720 } },
    (stream) => {
      const video = document.querySelector("video");
      video.srcObject = stream;
      video.onloadedmetadata = (e) => {
        video.play();
      };
    },
    (err) => {
      console.error(`The following error occurred: ${err.name}`);
    },
  );
} else {
  console.log("getUserMedia not supported");
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("MediaDevices.getUserMedia()")}} که جایگزین این متد منسوخ‌شده می‌شود.
- [WebRTC](/en-US/docs/Web/API/WebRTC_API) - صفحهٔ مقدماتی این API
- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API) - API مربوط به اشیاء جریان رسانه
- [Taking webcam photos](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Taking_still_photos) - یک آموزش برای استفاده از `getUserMedia()` جهت گرفتن عکس به‌جای ویدیو.