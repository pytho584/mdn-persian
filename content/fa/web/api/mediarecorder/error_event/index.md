---
title: "MediaRecorder: error event"
short-title: error
slug: Web/API/MediaRecorder/error_event
page-type: web-api-event
browser-compat: api.MediaRecorder.error_event
---

{{APIRef("MediaStream Recording")}}

رویداد **`error`** از رابط {{domxref("MediaRecorder")}} زمانی رخ می‌دهد که خطایی اتفاق بیفتد؛ برای مثال، چون ضبط مجاز نبوده یا با استفاده از کدک پشتیبانی‌نشده تلاش شده است.

این رویداد لغوپذیر نیست و به عناصر بالادستی منتشر نمی‌شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("error", (event) => { })

onerror = (event) => { }
```

## نوع رویداد

یک {{domxref("MediaRecorderErrorEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("MediaRecorderErrorEvent")}}

## توضیحات

### محرک

تابعی که باید هر زمان در طول عمر ضبط‌کننده خطایی رخ دهد فراخوانی شود. علاوه بر سایر خطاهای عمومی که ممکن است رخ دهند، خطاهای زیر به‌طور خاص هنگام استفاده از MediaStream Recording API ممکن است رخ دهند؛ برای تعیین اینکه کدام یک رخ داده است، مقدار {{domxref("DOMException.name", "MediaRecorderErrorEvent.error.name")}} را بررسی کنید.

- `SecurityError`
  - : {{domxref("MediaStream")}} به‌گونه‌ای پیکربندی شده است که ضبط را غیرمجاز بداند. این ممکن است برای مثال با منابعی که با استفاده از {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} به دست آمده‌اند، زمانی که کاربر اجازه استفاده از یک دستگاه ورودی را رد می‌کند، رخ دهد.
- `InvalidModificationError`
  - : تعداد trackهای موجود در جریان در حال ضبط تغییر کرده است. در حین ضبط رسانه نمی‌توانید track اضافه یا حذف کنید.
- `UnknownError`
  - : خطایی غیرمرتبط با امنیت رخ داده است که نمی‌توان آن را در دسته دیگری قرار داد. ضبط متوقف می‌شود، {{domxref("MediaRecorder.state", "state")}} مربوط به `MediaRecorder` به حالت `inactive` تغییر می‌یابد، یک رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} به همراه داده‌های دریافتی باقی‌مانده به `MediaRecorder` ارسال می‌شود، و در نهایت یک رویداد {{domxref("MediaRecorder/stop_event", "stop")}} ارسال می‌گردد.

## مثال‌ها

برای گوش دادن به رویدادهای `error` از {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید:

```js
async function record() {
  const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
  const recorder = new MediaRecorder(stream);
  recorder.addEventListener("error", (event) => {
    console.error(`error recording stream: ${event.error.name}`);
  });
  recorder.start();
}

record();
```

همین کار، اما با استفاده از ویژگی کنترل‌کننده رویداد `onerror`:

```js
async function record() {
  const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
  const recorder = new MediaRecorder(stream);
  recorder.onerror = (event) => {
    console.error(`error recording stream: ${event.error.name}`);
  };
  recorder.start();
}

record();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)