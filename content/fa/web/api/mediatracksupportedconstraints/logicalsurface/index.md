```
---
title: "MediaTrackSupportedConstraints: logicalSurface property"
---

---
title: "MediaTrackSupportedConstraints: logicalSurface property"
short-title: logicalSurface
slug: Web/API/MediaTrackSupportedConstraints/logicalSurface
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.logicalSurface_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`logicalSurface`** از {{domxref("MediaTrackSupportedConstraints")}} نشان می‌دهد که آیا محدودیت {{domxref("MediaTrackConstraints.logicalSurface", "logicalSurface")}} توسط عامل کاربر (user agent) و دستگاهی که محتوا روی آن استفاده می‌شود پشتیبانی می‌شود یا نه.

فهرست محدودیت‌های پشتیبانی‌شده با فراخوانی {{domxref("MediaDevices.getSupportedConstraints","navigator.mediaDevices.getSupportedConstraints()")}} به دست می‌آید.

## Value

یک مقدار بولی است که اگر محدودیت {{domxref("MediaTrackConstraints.logicalSurface", "logicalSurface")}} توسط دستگاه و عامل کاربر پشتیبانی شود، `true` خواهد بود.

## Example

این متد، شیء محدودیت‌ها را می‌سازد که گزینه‌های فراخوانی {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} را مشخص می‌کند. اگر معلوم باشد که مرورگر از آن پشتیبانی می‌کند، محدودیت `logicalSurface` را اضافه می‌کند (با این درخواست که فقط سطوح نمایش منطقی — آن‌هایی که ممکن است کاملاً روی صفحه نمایش قابل مشاهده نباشند — در میان گزینه‌های موجود برای کاربر گنجانده شوند). سپس ضبط با فراخوانی `getDisplayMedia()` آغاز می‌شود و جریان برگشتی به عنصر ویدیویی که متغیر `videoElem` به آن اشاره دارد متصل می‌شود.

```js
async function capture() {
  const supportedConstraints = navigator.mediaDevices.getSupportedConstraints();
  const displayMediaOptions = {
    video: {},
    audio: false,
  };

  if (supportedConstraints.logicalSurface) {
    displayMediaOptions.video.logicalSurface = "monitor";
  }

  try {
    videoElem.srcObject =
      await navigator.mediaDevices.getDisplayMedia(displayMediaOptions);
  } catch (err) {
    /* handle the error */
  }
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [Using the screen capture API](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}
```