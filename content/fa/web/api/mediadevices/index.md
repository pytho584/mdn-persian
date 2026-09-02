---
title: "MediaDevices"
slug: Web/API/MediaDevices
page-type: web-api-interface
browser-compat: api.MediaDevices
---

{{APIRef("Media Capture and Streams API")}}{{SecureContext_Header}}

رابط **`MediaDevices`** موجود در {{domxref("Media Capture and Streams API", "", "", "nocode")}} دسترسی به دستگاه‌های ورودی رسانه‌ای متصل مانند دوربین‌ها و میکروفون‌ها و همچنین اشتراک‌گذاری صفحه را فراهم می‌کند. به طور خلاصه، این رابط به شما امکان دسترسی به هر منبع سخت‌افزاری داده‌های رسانه‌ای را می‌دهد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های رابط والد خود، {{domxref("EventTarget")}} را به ارث می‌برد._

## روش‌های نمونه

_روش‌های رابط والد خود، {{domxref("EventTarget")}} را به ارث می‌برد._

- {{domxref("MediaDevices.enumerateDevices", "enumerateDevices()")}}
  - : آرایه‌ای از اطلاعات مربوط به دستگاه‌های ورودی و خروجی رسانه‌ای موجود در سیستم را به دست می‌آورد.
- {{domxref("MediaDevices.getSupportedConstraints", "getSupportedConstraints()")}}
  - : یک شیء منطبق با {{domxref("MediaTrackSupportedConstraints")}} برمی‌گرداند که نشان می‌دهد کدام ویژگی‌های قابل محدودیت در رابط {{domxref("MediaStreamTrack")}} پشتیبانی می‌شوند. برای اطلاعات بیشتر درباره محدودیت‌ها و نحوه استفاده از آن‌ها به [Media Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) مراجعه کنید.
- {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}}
  - : از کاربر می‌خواهد یک صفحه نمایش یا بخشی از آن (مانند یک پنجره) را برای ضبط به عنوان {{domxref("MediaStream")}} برای اشتراک‌گذاری یا ضبط انتخاب کند. یک promise برمی‌گرداند که به یک `MediaStream` تبدیل می‌شود.
- {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}}
  - : با اجازه کاربر از طریق یک پنجره درخواست، دوربین و/یا میکروفون سیستم را روشن کرده و یک {{domxref("MediaStream")}} شامل یک track ویدیویی و/یا یک track صوتی با ورودی ارائه می‌دهد.
- {{domxref("MediaDevices.selectAudioOutput", "selectAudioOutput()") }} {{Experimental_Inline}}
  - : از کاربر می‌خواهد یک دستگاه خروجی صوتی خاص را انتخاب کند.

## رویدادها

- {{domxref("MediaDevices/devicechange_event", "devicechange")}}
  - : هنگامی که یک دستگاه ورودی یا خروجی رسانه‌ای به رایانه کاربر متصل یا از آن جدا می‌شود، فعال می‌گردد.

## مثال

```js
// Put variables in global scope to make them available to the browser console.
const video = document.querySelector("video");
const constraints = {
  audio: false,
  video: true,
};

navigator.mediaDevices
  .getUserMedia(constraints)
  .then((stream) => {
    const videoTracks = stream.getVideoTracks();
    console.log("Got stream with constraints:", constraints);
    console.log(`Using video device: ${videoTracks[0].label}`);
    stream.onremovetrack = () => {
      console.log("Stream ended");
    };
    video.srcObject = stream;
  })
  .catch((error) => {
    if (error.name === "OverconstrainedError") {
      console.error(
        `The resolution ${constraints.video.width.exact}x${constraints.video.height.exact} px is not supported by your device.`,
      );
    } else if (error.name === "NotAllowedError") {
      console.error(
        "You need to grant this page permission to access your camera and microphone.",
      );
    } else {
      console.error(`getUserMedia error: ${error.name}`, error);
    }
  });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API): APIای که این رابط بخشی از آن است.
- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API): APIای که روش {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} را تعریف می‌کند.
- [WebRTC API](/en-US/docs/Web/API/WebRTC_API)
- {{domxref("Navigator.mediaDevices")}}: یک ارجاع به یک شیء `MediaDevices` برمی‌گرداند که می‌توان از آن برای دسترسی به دستگاه‌ها استفاده کرد.
- [CameraCaptureJS](https://github.com/chrisjohndigital/CameraCaptureJS): ضبط و پخش ویدیوی HTML با استفاده از `MediaDevices` و MediaStream Recording API
- [OpenLang](https://github.com/chrisjohndigital/OpenLang): برنامه وب آزمایشگاه زبان ویدیویی HTML با استفاده از `MediaDevices` و MediaStream Recording API برای ضبط ویدیو