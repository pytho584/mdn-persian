---
title: "MediaRecorder: start() method"
short-title: start()
slug: Web/API/MediaRecorder/start
page-type: web-api-instance-method
browser-compat: api.MediaRecorder.start
---

{{APIRef("MediaStream Recording")}}

متد **`start()`** از رابط {{domxref("MediaRecorder")}} شروع ضبط رسانه را در یک یا چند شیء {{domxref("Blob")}} آغاز می‌کند.

می‌توانید تمام مدت رسانه را در یک `Blob` واحد ضبط کنید (یا تا زمانی که {{domxref("MediaRecorder.requestData", "requestData()")}} را فراخوانی کنید)، یا می‌توانید تعداد میلی‌ثانیه‌هایی را که هر بار ضبط می‌شود مشخص کنید. سپس هر بار که آن مقدار از رسانه ضبط شد، یک رویداد ارسال می‌شود تا بتوانید روی رسانه ضبط‌شده اقدام کنید، در حالی که یک `Blob` جدید برای ضبط بخش بعدی رسانه ایجاد می‌شود.

با فرض اینکه {{domxref("MediaRecorder.state", "state")}} «MediaRecorder» برابر با `inactive` باشد، `start()` مقدار `state` را به `recording` تنظیم کرده و سپس ضبط رسانه از جریان ورودی را آغاز می‌کند. یک `Blob` ایجاد می‌شود و داده‌ها در آن جمع‌آوری می‌شوند تا زمانی که بازه زمانی تعیین‌شده به پایان برسد یا رسانه منبع تمام شود. هر بار که یک `Blob` تا آن نقطه پر شود (مدت زمان slice یا پایان رسانه، در صورت عدم ارائه مدت زمان slice)، یک رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} به `MediaRecorder` ارسال می‌شود که حاوی داده‌های ضبط‌شده است. اگر منبع همچنان در حال پخش باشد، یک `Blob` جدید ایجاد می‌شود و ضبط در آن ادامه می‌یابد و به همین ترتیب.

وقتی جریان منبع به پایان می‌رسد، `state` به `inactive` تنظیم می‌شود و جمع‌آوری داده متوقف می‌شود. یک رویداد نهایی {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} به `MediaRecorder` ارسال می‌شود و به دنبال آن یک رویداد {{domxref("MediaRecorder/stop_event", "stop")}} ارسال می‌شود.

> [!NOTE]
> اگر مرورگر نتواند ضبط را شروع کند یا ادامه دهد، یک رویداد {{domxref("MediaRecorder.error_event", "error")}} ایجاد می‌کند و به دنبال آن یک رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} حاوی `Blob` جمع‌آوری‌شده و سپس رویداد {{domxref("MediaRecorder/stop_event", "stop")}} ارسال می‌شود.

## نحو (Syntax)

```js-nolint
start()
start(timeslice)
```

### پارامترها

- `timeslice` {{optional_inline}}
  - : تعداد میلی‌ثانیه‌هایی که برای ضبط در هر {{domxref("Blob")}} در نظر گرفته شده است. اگر این پارامتر ارائه نشود، کل مدت رسانه در یک `Blob` واحد ضبط می‌شود، مگر اینکه متد {{domxref("MediaRecorder.requestData", "requestData()")}} برای دریافت `Blob` و ایجاد یک `Blob` جدید که ضبط رسانه در آن ادامه می‌یابد، فراخوانی شود.

    > [!NOTE]
    > مانند سایر مقادیر زمانی در APIهای وب، `timeslice` دقیق نیست و فواصل واقعی ممکن است به دلیل وجود وظایف در انتظار دیگر قبل از ایجاد blob بعدی، کمی طولانی‌تر باشند.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

خطاهایی که می‌توانند بلافاصله شناسایی شوند به عنوان استثناهای DOM پرتاب می‌شوند. سایر خطاها از طریق رویدادهای {{domxref("MediaRecorder.error_event", "error")}} که به شیء `MediaRecorder` ارسال می‌شوند، گزارش می‌شوند. می‌توانید هندلر رویداد {{domxref("MediaRecorder.error_event", "onerror")}} را برای پاسخ به این خطاها پیاده‌سازی کنید.

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر `MediaRecorder` در حالت `inactive` نباشد پرتاب می‌شود؛ اگر در حال حاضر رسانه در حال ضبط باشد، نمی‌توانید ضبط را شروع کنید. به ویژگی {{domxref("MediaRecorder.state", "state")}} مراجعه کنید.
- `NotSupportedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - جریان رسانه‌ای که قصد ضبط آن را دارید غیرفعال (inactive) است.
    - یک یا چند track از جریان در قالبی هستند که با پیکربندی فعلی قابل ضبط نیستند.
    - هر دو پارامتر `videoKeyFrameIntervalDuration` و `videoKeyFrameIntervalCount` در زمان ایجاد `MediaRecorder` مشخص شده باشند.
- `SecurityError` {{domxref("DOMException")}}
  - : اگر {{domxref("MediaStream")}} به گونه‌ای پیکربندی شده باشد که ضبط را غیرمجاز کند، پرتاب می‌شود. این ممکن است برای مثال، در منابعی که با استفاده از {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} به دست آمده‌اند، زمانی که کاربر اجازه استفاده از یک دستگاه ورودی را رد می‌کند، رخ دهد. این استثنا همچنین ممکن است به عنوان یک رویداد {{domxref("MediaRecorder.error_event", "error")}} در صورت تغییر گزینه‌های امنیتی منبع رسانه پس از شروع ضبط، تحویل داده شود.

## مثال‌ها

```js
record.onclick = () => {
  mediaRecorder.start();
  console.log("recorder started");
};
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط MediaStream](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): نمایش MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([کد منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone))
- [نمایش ساده‌شده ضبط MediaStream در simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton)
- {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}}