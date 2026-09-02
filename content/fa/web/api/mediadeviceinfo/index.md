---
title: MediaDeviceInfo
slug: Web/API/MediaDeviceInfo
page-type: web-api-interface
browser-compat: api.MediaDeviceInfo
---

{{APIRef("Media Capture and Streams")}}{{securecontext_header}}

رابطهٔ **`MediaDeviceInfo`** در {{domxref("Media Capture and Streams API", "", "", "nocode")}} اطلاعاتی را توصیف می‌کند که یک دستگاه ورودی یا خروجی رسانه‌ای را مشخص می‌کند.

فهرست دستگاه‌هایی که با فراخوانی {{domxref("MediaDevices.enumerateDevices", "navigator.mediaDevices.enumerateDevices()")}} به دست می‌آید، آرایه‌ای از اشیاء `MediaDeviceInfo` است؛ برای هر دستگاه رسانه‌ای یک شیء.

## ویژگی‌های نمونه

- {{domxref("MediaDeviceInfo.deviceId")}} {{ReadOnlyInline}}
  - : رشته‌ای برمی‌گرداند که شناسه‌ای برای دستگاه نمایش‌داده‌شده است و در طول نشست‌ها (sessions) پایدار می‌ماند. این مقدار برای سایر برنامه‌ها قابل حدس‌زدن نیست و برای مبدأ (origin) برنامهٔ فراخوان یکتا است. وقتی کاربر کوکی‌ها را پاک می‌کند، این مقدار بازنشانی می‌شود (در حالت مرور خصوصی، از شناسهٔ متفاوتی استفاده می‌شود که در طول نشست‌ها پایدار نیست).
- {{domxref("MediaDeviceInfo.groupId")}} {{ReadOnlyInline}}
  - : رشته‌ای برمی‌گرداند که شناسهٔ گروه است. دو دستگاه اگر متعلق به یک دستگاه فیزیکی باشند، شناسهٔ گروه یکسانی دارند — برای مثال یک مانیتور که هم دوربین داخلی دارد و هم میکروفون داخلی.
- {{domxref("MediaDeviceInfo.kind")}} {{ReadOnlyInline}}
  - : مقدار شمارشی برمی‌گرداند که یا `"videoinput"` است، یا `"audioinput"` یا `"audiooutput"`.
- {{domxref("MediaDeviceInfo.label")}} {{ReadOnlyInline}}
  - : رشته‌ای برمی‌گرداند که این دستگاه را توصیف می‌کند (مثلاً «وب‌کم USB خارجی»).

> [!NOTE]
> به دلایل امنیتی، فیلد `label` همیشه خالی است مگر اینکه یک جریان رسانه‌ای فعال وجود داشته باشد _یا_ کاربر مجوز دائمی برای دسترسی به دستگاه رسانه‌ای داده باشد. در غیر این صورت، مجموعهٔ برچسب‌های دستگاه می‌تواند به‌عنوان بخشی از مکانیزم [اثرانگشت‌گیری](/en-US/docs/Glossary/Fingerprinting) برای شناسایی کاربر استفاده شود.

## روش‌های نمونه

- {{domxref("MediaDeviceInfo.toJSON()")}}
  - : یک نمایش JSON از شیء `MediaDeviceInfo` برمی‌گرداند.

## مثال

در اینجا مثالی داریم که از {{domxref("MediaDevices.enumerateDevices", "enumerateDevices()")}} برای به‌دست‌آوردن فهرست دستگاه‌ها استفاده می‌کند.

```js
if (!navigator.mediaDevices || !navigator.mediaDevices.enumerateDevices) {
  console.log("enumerateDevices() not supported.");
} else {
  // List cameras and microphones.
  navigator.mediaDevices
    .enumerateDevices()
    .then((devices) => {
      devices.forEach((device) => {
        console.log(`${device.kind}: ${device.label} id = ${device.deviceId}`);
      });
    })
    .catch((err) => {
      console.log(`${err.name}: ${err.message}`);
    });
}
```

خروجی این کد می‌تواند به شکل زیر باشد:

```bash
videoinput: id = csO9c0YpAf274OuCPUA53CNE0YHlIr2yXCi+SqfBZZ8=
audioinput: id = RKxXByjnabbADGQNNZqLVLdmXlS0YkETYCIbg+XxnvM=
audioinput: id = r2/xw1xUPIyZunfV1lGrKOma5wTOvCkWfZ368XCndm0=
```

یا اگر یک یا چند جریان رسانه‌ای فعال باشد، یا اگر مجوزهای دائمی اعطا شده باشد:

```bash
videoinput: FaceTime HD Camera (Built-in) id=csO9c0YpAf274OuCPUA53CNE0YHlIr2yXCi+SqfBZZ8=
audioinput: default (Built-in Microphone) id=RKxXByjnabbADGQNNZqLVLdmXlS0YkETYCIbg+XxnvM=
audioinput: Built-in Microphone id=r2/xw1xUPIyZunfV1lGrKOma5wTOvCkWfZ368XCndm0=
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [WebRTC API](/en-US/docs/Web/API/WebRTC_API)
- {{domxref("MediaDevices.enumerateDevices", "navigator.mediaDevices.enumerateDevices()")}}
- {{domxref("MediaDevices.getUserMedia", "navigator.mediaDevices.getUserMedia()")}}