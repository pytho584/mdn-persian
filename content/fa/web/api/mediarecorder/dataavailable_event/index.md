---
title: "MediaRecorder: dataavailable event"
short-title: dataavailable
slug: Web/API/MediaRecorder/dataavailable_event
page-type: web-api-event
browser-compat: api.MediaRecorder.dataavailable_event
---

{{APIRef("MediaStream Recording")}}

رویداد **`dataavailable`** از رابط {{domxref("MediaRecorder")}} زمانی رخ می‌دهد که MediaRecorder داده‌های رسانه‌ای را برای استفادهٔ برنامهٔ شما تحویل می‌دهد. این داده‌ها در قالب یک شیء {{domxref("Blob")}} که حاوی داده‌ها است ارائه می‌شوند. این اتفاق در چهار حالت رخ می‌دهد:

- وقتی جریان رسانه‌ای به پایان می‌رسد، هر دادهٔ رسانه‌ای که هنوز به مدیریت‌کنندهٔ `ondataavailable` شما تحویل داده نشده است، در قالب یک {{domxref("Blob")}} واحد ارسال می‌شود.
- وقتی {{domxref("MediaRecorder.stop()")}} فراخوانده می‌شود، تمام داده‌های رسانه‌ای که از شروع ضبط یا از آخرین بار وقوع رویداد `dataavailable` جمع‌آوری شده‌اند، در یک {{domxref("Blob")}} تحویل داده می‌شوند؛ پس از آن، ضبط پایان می‌یابد.
- وقتی {{domxref("MediaRecorder.requestData()")}} فراخوانده می‌شود، تمام داده‌های رسانه‌ای که از شروع ضبط یا از آخرین بار وقوع رویداد `dataavailable` جمع‌آوری شده‌اند تحویل داده می‌شوند؛ سپس یک `Blob` جدید ساخته می‌شود و ضبط رسانه در آن ادامه می‌یابد.
- اگر یک ویژگی `timeslice` به متد {{domxref("MediaRecorder.start()")}} که ضبط رسانه را آغاز کرده است ارسال شده باشد، هر `timeslice` میلی‌ثانیه یک بار رویداد `dataavailable` رخ می‌دهد. این بدان معناست که معمولاً هر blob مدت‌زمان مشخصی خواهد داشت (به‌جز آخرین blob که ممکن است کوتاه‌تر باشد، زیرا محتوای باقی‌مانده از آخرین رویداد را شامل می‌شود). بنابراین اگر فراخوانی متد به این شکل باشد — `recorder.start(1000);` — رویداد `dataavailable` پس از هر ثانیه ضبط رسانه رخ می‌دهد و مدیریت‌کنندهٔ رویداد ما هر ثانیه با یک blob از دادهٔ رسانه‌ای به طول یک ثانیه فراخوانی می‌شود. می‌توانید `timeslice` را همراه با {{domxref("MediaRecorder.stop()")}} و {{domxref("MediaRecorder.requestData()")}} استفاده کنید تا چند blob هم‌طول و همچنین blobهای کوتاه‌تر دیگری تولید کنید.

> [!NOTE]
> مانند سایر مقادیر زمانی در web APIها، `timeslice` دقیق نیست و فواصل واقعی ممکن است به دلیل وظایف در انتظار دیگر، ویژگی‌های مرورگر (مکث دوربین و میکروفون در Safari)، رفتارهای خاص مرورگر (قفل شدن صفحه در حین ضبط در Chrome روی Android که رویداد `dataavailable` را متوقف می‌کند) یا سایر اشکالات مرورگر به تأخیر بیفتند. چنین سناریوهایی می‌توانند به تکه‌های به‌طور قابل توجهی بزرگ‌تر نیز منجر شوند.
>
> بنابراین، برای محاسبهٔ زمان سپری‌شده به `timeslice` و تعداد تکه‌های دریافت‌شده تکیه نکنید، زیرا خطاها ممکن است انباشته شوند. در عوض، یک تایمر جداگانه با استفاده از {{domxref("Event.timeStamp")}} یا موارد مشابه نگه دارید که کل زمان سپری‌شده از شروع را ثبت کند.

{{domxref("Blob")}} حاوی دادهٔ رسانه‌ای در ویژگی `data` رویداد `dataavailable` در دسترس است.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("dataavailable", (event) => { })

ondataavailable = (event) => { }
```

## نوع رویداد

یک {{domxref("BlobEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("BlobEvent")}}

## مثال

```js
const chunks = [];

mediaRecorder.onstop = (e) => {
  console.log("data available after MediaRecorder.stop() called.");

  const audio = document.createElement("audio");
  audio.controls = true;
  const blob = new Blob(chunks, { type: mediaRecorder.mimeType });
  const audioURL = window.URL.createObjectURL(blob);
  audio.src = audioURL;
  console.log("recorder stopped");
};

mediaRecorder.ondataavailable = (e) => {
  chunks.push(e.data);
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط جریان رسانه‌ای](/en-US/docs/Web/API/MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): دموی تجسم MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).)
- [دموی ضبط جریان رسانه‌ای simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton).
- {{domxref("Navigator.getUserMedia()")}}
- [برخورد با تکه‌های بزرگ MediaRecorder](https://blog.addpipe.com/dealing-with-huge-mediarecorder-slices/) در addpipe.com (2024)