---
title: "MediaTrackSettings: screenPixelRatio property"
short-title: screenPixelRatio
slug: Web/API/MediaTrackSettings/screenPixelRatio
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.MediaStreamTrack.getSettings.return_object_property_screenPixelRatio
---

{{APIRef("Media Capture and Streams")}}{{SeeCompatTable}}

ویژگی **`screenPixelRatio`** در {{domxref("MediaTrackSettings")}} عددی است که نسبت اندازهٔ فیزیکی یک پیکسل روی سطح نمایشِ در حال ضبط (که با وضوح فیزیکی خودش نمایش داده می‌شود) را به اندازهٔ منطقی یک پیکسل CSS روی صفحهٔ در حال ضبط (که با وضوح منطقی خودش نمایش داده می‌شود) نشان می‌دهد. این ویژگی را نمی‌توان به‌عنوان محدودیت (constraint) یا قابلیت (capability) استفاده کرد.

این ویژگی به برنامه‌هایی که از [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API) استفاده می‌کنند امکان می‌دهد با ارسال ویدیوی ضبط‌شدهٔ صفحه با وضوح منطقی یا وضوح مستقل از دستگاه، در مصرف منابع صرفه‌جویی کنند.

## مقدار

عددی که نسبت پیکسل صفحه را نشان می‌دهد.

این مقدار از تقسیم اندازهٔ یک {{glossary("CSS pixel")}} با بزرگ‌نمایی صفحه برابر با `1.0` و اعمال ضریب مقیاس `1.0` روی صفحهٔ در حال ضبط بر اندازهٔ عمودی یک پیکسل از [سطح نمایش](/en-US/docs/Web/API/MediaTrackConstraints/displaySurface) ضبط‌شده، محاسبه می‌شود.

## توضیحات

معمول است که سیستم‌عامل روی صفحه بزرگ‌نمایی (zoom) اعمال کند؛ مثلاً وقتی نمایشگر، نمایشگری با وضوح بالا باشد و بخواهید گرافیک‌ها با همان اندازهٔ فیزیکی که در یک نمایشگر با وضوح استاندارد دیده می‌شوند، نمایش داده شوند. به وضوح قبل از اعمال بزرگ‌نمایی، **وضوح منطقی (logical resolution)** و به وضوح پس از اعمال بزرگ‌نمایی، **وضوح فیزیکی (physical resolution)** گفته می‌شود.

اگر صفحهٔ در حال ضبطِ فرستنده بزرگ‌نمایی شده باشد، وضوح فیزیکی از وضوح منطقی بیشتر است؛ بنابراین یک برنامهٔ ویدئوکنفرانس می‌تواند با انجام کارهای زیر در پهنای باند و مصرف CPU صرفه‌جویی کند:

1. حذف بزرگ‌نمایی اعمال‌شده توسط سیستم‌عامل روی سطح نمایشِ در حال ضبط.
2. ارسال ویدیوی ضبط صفحه با وضوح منطقی.
3. اعمال دوبارهٔ بزرگ‌نمایی پس از دریافت ویدیو در کلاینت راه دور، تا اندازهٔ آن دوباره به وضوح فیزیکی بازگردد.

ویژگی `screenPixelRatio` نسبت اندازهٔ فیزیکی یک پیکسل به اندازهٔ منطقی یک پیکسل CSS را توصیف می‌کند و بنابراین به برنامه امکان می‌دهد بفهمد چه ضریب بزرگ‌نمایی‌ای اعمال شده است و سپس ویدیو را به اندازهٔ منطقی محدود کند.

برای مثال:

- اگر سطح نمایشِ در حال ضبط روی یک نمایشگر با وضوح استاندارد نمایش داده شود، جایی که ابعاد فیزیکی پیکسل‌ها تقریباً با ابعاد پیکسل‌های CSS برابر است، `screenPixelRatio` مقدار `1` را برمی‌گرداند.
- اما اگر سطح نمایشِ در حال ضبط روی یک نمایشگر با تراکم پیکسلی بالا (high-dpi) نمایش داده شود، جایی که ابعاد فیزیکی پیکسل‌ها تقریباً دو برابر ابعاد پیکسل‌های CSS است، `screenPixelRatio` مقدار `2` را برمی‌گرداند.

## مثال‌ها

### استفادهٔ مقدماتی از `screenPixelRatio`

در این مثال، برنامه یک ثابت به نام `RESOLUTION_LIMIT` تعریف می‌کند که ضریب مقیاسی را نشان می‌دهد که اگر از آن فراتر رود، برنامهٔ فرستنده باید ویدیو را با وضوح منطقی ارسال کند نه با وضوح فیزیکی.

وقتی `screenPixelRatio` از این حد فراتر رود، برنامه از مقدار `screenPixelRatio` برای محاسبهٔ وضوح منطقی از روی وضوح فیزیکی استفاده می‌کند و سپس {{domxref("MediaStreamTrack")}} ضبط‌شده را به وضوح منطقی محدود می‌کند.

```js
const RESOLUTION_LIMIT = 1.5;

async function startCapture() {
  const stream = await navigator.mediaDevices.getDisplayMedia({
    video: true,
  });
  const track = stream.getVideoTracks()[0];
  const settings = track.getSettings();
  const capabilities = track.getCapabilities();

  if (settings.screenPixelRatio > RESOLUTION_LIMIT) {
    const physicalWidth = capabilities.width.max;
    const physicalHeight = capabilities.height.max;
    const logicalWidth = physicalWidth / settings.screenPixelRatio;
    const logicalHeight = physicalHeight / settings.screenPixelRatio;
    await track.applyConstraints({
      width: logicalWidth,
      height: logicalHeight,
    });
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackSettings")}}