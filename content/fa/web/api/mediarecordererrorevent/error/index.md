---
title: "MediaRecorderErrorEvent: error property"
---

---
title: "MediaRecorderErrorEvent: error property"
short-title: error
slug: Web/API/MediaRecorderErrorEvent/error
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MediaRecorderErrorEvent.error
---

{{APIRef("MediaStream Recording")}}{{Deprecated_Header}}{{Non-standard_Header}}

خاصیت فقطخواندنی **`error`** در رابط {{domxref("MediaRecorderErrorEvent")}} یک شیء {{domxref("DOMException")}} است که جزئیات مربوط به استثنای ایجادشده توسط یک نمونه از {{domxref("MediaRecorder")}} را ارائه می‌دهد.

هنگامی که یک `MediaRecorderErrorEvent` رخ می‌دهد، می‌توانید با بررسی خاصیت `error` درون همان `MediaRecorderErrorEvent` که توسط مدیر رویداد {{domxref("MediaRecorder/error_event", "error")}} متعلق به `MediaRecorder` (یعنی {{domxref("MediaRecorder/error_event", "onerror")}}) دریافت شده، تا حدی تشخیص دهید چه اشتباهی رخ داده است.

## مقدار

یک {{domxref("DOMException")}} که خطای نمایش‌داده‌شده توسط رویداد را توصیف می‌کند. مقدار خاصیت {{domxref("DOMException.name", "name")}} این خطا می‌تواند هر استثنایی باشد که در حین مدیریت ضبط رسانه معنادار باشد، از جمله موارد زیر که به‌طور مشخص در مشخصات شناسایی شده‌اند. توضیحات این‌جا عمومی هستند؛ توضیحات اختصاصی‌تر مربوط به سناریوهای مختلفی که این خطاها ممکن است در آن‌ها رخ دهند را می‌توانید در مستندات متدهای مربوطه بیابید.

- `InvalidStateError`
  - : عملیاتی در زمینه‌ای تلاش شده که در آن مجاز نیست، یا درخواستی روی شیءای انجام شده که حذف یا پاک شده است.
- `NotSupportedError`
  - : یک `MediaRecorder` نتوانسته ساخته شود، زیرا گزینه‌های مشخص‌شده معتبر نبوده‌اند. ویژگی `message` در صورت وجود باید اطلاعات بیشتری ارائه دهد.
- `SecurityError`
  - : {{domxref("MediaStream")}} به‌گونه‌ای پیکربندی شده که اجازه‌ی ضبط نمی‌دهد. این حالت ممکن است برای مثال درباره منبع‌هایی رخ دهد که با استفاده از {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} به دست آمده‌اند، زمانی که کاربر اجازه‌ی استفاده از یک دستگاه ورودی را رد کند.
- `InvalidModificationError`
  - : تعداد ترک‌های جریان در حال ضبط تغییر کرده است. در حین ضبط رسانه نمی‌توانید ترک اضافه یا حذف کنید.
- `UnknownError`
  - : خطایی غیرمرتبط با امنیت رخ داده که امکان دسته‌بندی دیگری ندارد. ضبط متوقف می‌شود، {{domxref("MediaRecorder.state", "state")}} متعلق به `MediaRecorder` به `inactive` تغییر می‌کند، یک رویداد نهایی {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} همراه با داده‌های دریافتی باقی‌مانده به `MediaRecorder` ارسال می‌شود و در نهایت یک رویداد {{domxref("MediaRecorder/stop_event", "stop")}} ارسال می‌گردد.

## مثال‌ها

### مثال پایه‌ی مدیریت خطا

این تابع برای یک {{domxref("MediaStream")}} مشخص، یک `MediaRecorder` می‌سازد و آن را برمی‌گرداند؛ به‌گونه‌ای پیکربندی شده که داده‌ها را در یک آرایه بافر کند و خطاها را زیر نظر بگیرد.

```js
function recordStream(stream) {
  let recorder = null;
  let bufferList = [];

  try {
    recorder = new MediaRecorder(stream);
  } catch (err) {
    /* exception while trying to create the recorder; handle that */
  }

  recorder.ondataavailable = (event) => {
    bufferList.push(event.data);
  };

  recorder.onerror = (event) => {
    console.error(`Error: ${event.error}`);
  };

  recorder.start(100); /* 100ms time slices per buffer */
  return recorder;
}
```

## مشخصات

این ویژگی دیگر بخشی از هیچ مشخصاتی نیست و دیگر در مسیر استاندارد شدن قرار ندارد.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API)
- [Using the MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)