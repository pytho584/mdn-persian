---
title: "MediaStreamTrack: applyConstraints() method"
short-title: applyConstraints()
slug: Web/API/MediaStreamTrack/applyConstraints
page-type: web-api-instance-method
browser-compat: api.MediaStreamTrack.applyConstraints
---

{{APIRef("Media Capture and Streams")}}

متد **`applyConstraints()`** از رابط {{domxref("MediaStreamTrack")}} مجموعه‌ای از محدودیت‌ها را روی track اعمال می‌کند؛ این محدودیت‌ها به وب‌سایت یا برنامه اجازه می‌دهند مقادیر ایده‌آل و بازه‌های قابل قبول را برای ویژگی‌های قابل‌محدودیتِ track، مانند نرخ فریم، ابعاد، حذف پژواک و غیره تعیین کنند.

از محدودیت‌ها می‌توان برای اطمینان از مطابقت رسانه با معیارهای خاصی که ترجیح می‌دهید استفاده کرد.
برای مثال، ممکن است ویدیوی با کیفیت بالا ترجیح دهید اما نرخ فریم را کمی پایین نگه دارید تا نرخ داده به اندازه‌ای کم بماند که شبکه را تحت فشار نگذارد.
محدودیت‌ها همچنین می‌توانند اندازه‌ها یا بازه‌های اندازه ایده‌آل و/یا قابل قبول را مشخص کنند.
برای اطلاعات بیشتر در مورد نحوه اعمال محدودیت‌های دلخواه، به [اعمال محدودیت‌ها](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#applying_constraints) در [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) مراجعه کنید.

## نحو (Syntax)

```js-nolint
applyConstraints()
applyConstraints(constraints)
```

### پارامترها

- `constraints` {{optional_inline}}
  - : یک شیء {{domxref("MediaTrackConstraints")}} که محدودیت‌های مورد نظر برای اعمال بر ویژگی‌های قابل‌محدودیتِ track را فهرست می‌کند؛ هر محدودیت موجود با مقادیر جدید مشخص‌شده جایگزین می‌شود و هر ویژگی قابل‌محدودیتی که درج نشده باشد به محدودیت‌های پیش‌فرض خود بازنشانی می‌شود.
    اگر این پارامتر حذف شود، تمام محدودیت‌های سفارشیِ در حال تنظیم پاک می‌شوند.
    این شیء مجموعه محدودیت‌های پایه را نشان می‌دهد که برای حل شدن {{jsxref("Promise")}} باید اعمال شوند.
    شیء ممکن است شامل یک ویژگی `advanced` باشد که آرایه‌ای از اشیاء `MediaTrackConstraints` اضافی را در خود دارد و به‌عنوان الزامات دقیق در نظر گرفته می‌شوند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که هنگام اعمال موفقیت‌آمیز محدودیت‌ها حل می‌شود.
اگر محدودیت‌ها قابل اعمال نباشند، promise با یک {{domxref("OverconstrainedError")}} رد می‌شود که یک {{domxref("DOMException")}} با نام `OverconstrainedError` و پارامترهای اضافی است و نشان می‌دهد که محدودیت‌ها قابل برآورده شدن نبودند.
این اتفاق می‌تواند رخ دهد اگر محدودیت‌های مشخص‌شده بیش از حد سخت‌گیرانه باشند و هنگام تلاش برای پیکربندی track مطابقت‌ای یافت نشود.

## مثال‌ها

مثال زیر نحوه مشخص‌کردن مجموعه‌ای از محدودیت‌های پایه و پیشرفته را نشان می‌دهد.
این مثال مشخص می‌کند که صفحه یا وب‌اپلیکیشن به عرضی بین ۶۴۰ و ۱۲۸۰ و ارتفاعی بین ۴۸۰ و ۷۲۰ نیاز دارد و عدد دوم در هر جفت ترجیح داده می‌شود.
ویژگی `advanced` همچنین مشخص می‌کند که اندازه تصویر ۱۹۲۰ در ۱۲۸۰ ترجیح داده می‌شود یا اگر در دسترس نبود، یک {{glossary("aspect ratio")}} (نسبت ابعاد) برابر با ۱٫۳۳۳.
توجه کنید که این محدودیت‌ها همچنین چیزی را نشان می‌دهند که مشخصات آن را _راهبرد عقب‌نشینی_ (backoff strategy) می‌نامند.

```js
const constraints = {
  width: { min: 640, ideal: 1280 },
  height: { min: 480, ideal: 720 },
  advanced: [{ width: 1920, height: 1280 }, { aspectRatio: 1.333 }],
};

navigator.mediaDevices.getUserMedia({ video: true }).then((mediaStream) => {
  const track = mediaStream.getVideoTracks()[0];
  track
    .applyConstraints(constraints)
    .then(() => {
      // کارهایی مانند استفاده از API تصویربرداری را با track انجام دهید.
    })
    .catch((e) => {
      // محدودیت‌ها توسط دستگاه‌های موجود قابل برآورده شدن نبودند.
    });
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [MediaStream Image Capture API](/en-US/docs/Web/API/MediaStream_Image_Capture_API)