---
title: "MediaRecorder"
slug: Web/API/MediaRecorder
page-type: web-api-interface
browser-compat: api.MediaRecorder
---

{{APIRef("MediaStream Recording")}}

رابط **`MediaRecorder`** از [API ضبط جریان رسانه‌ای](/en-US/docs/Web/API/MediaStream_Recording_API) قابلیت ضبط آسان رسانه را فراهم می‌کند. این رابط با استفاده از سازنده {{domxref("MediaRecorder.MediaRecorder", "MediaRecorder()")}} ایجاد می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("MediaRecorder.MediaRecorder", "MediaRecorder()")}}
  - : یک شیء `MediaRecorder` جدید ایجاد می‌کند که یک {{domxref("MediaStream")}} برای ضبط به آن داده می‌شود. گزینه‌هایی برای تنظیم نوع MIME ظرف (مانند `"video/webm"` یا `"video/mp4"`) و نرخ بیت آهنگ‌های صوتی و تصویری یا یک نرخ بیت کلی واحد در دسترس است.

## ویژگی‌های نمونه

- {{domxref("MediaRecorder.mimeType")}} {{ReadOnlyInline}}
  - : نوع MIME انتخاب‌شده به عنوان ظرف ضبط برای شیء `MediaRecorder` در زمان ایجاد آن را برمی‌گرداند.
- {{domxref("MediaRecorder.state")}} {{ReadOnlyInline}}
  - : وضعیت فعلی شیء `MediaRecorder` را برمی‌گرداند (`inactive`، `recording` یا `paused`).
- {{domxref("MediaRecorder.stream")}} {{ReadOnlyInline}}
  - : جریانی را که در زمان ایجاد `MediaRecorder` به سازنده داده شده است برمی‌گرداند.
- {{domxref("MediaRecorder.videoBitsPerSecond")}} {{ReadOnlyInline}}
  - : نرخ بیت رمزگذاری ویدیوی در حال استفاده را برمی‌گرداند. این مقدار ممکن است با نرخ بیت مشخص‌شده در سازنده (اگر ارائه شده باشد) متفاوت باشد.
- {{domxref("MediaRecorder.audioBitsPerSecond")}} {{ReadOnlyInline}}
  - : نرخ بیت رمزگذاری صوتی در حال استفاده را برمی‌گرداند. این مقدار ممکن است با نرخ بیت مشخص‌شده در سازنده (اگر ارائه شده باشد) متفاوت باشد.
- {{domxref("MediaRecorder.audioBitrateMode")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : حالت نرخ بیت استفاده‌شده برای رمزگذاری آهنگ‌های صوتی را برمی‌گرداند.

## روش‌های ایستا

- {{domxref("MediaRecorder.isTypeSupported_static", "MediaRecorder.isTypeSupported()")}}
  - : یک روش ایستا که مقدار `true` یا `false` را برمی‌گرداند و نشان می‌دهد آیا نوع رسانه MIME داده‌شده توسط عامل کاربر فعلی پشتیبانی می‌شود یا خیر.

## روش‌های نمونه

- {{domxref("MediaRecorder.pause()")}}
  - : ضبط رسانه را متوقف می‌کند.
- {{domxref("MediaRecorder.requestData()")}}
  - : یک {{domxref("Blob")}} حاوی داده‌های ذخیره‌شده تا این لحظه (یا از آخرین باری که `requestData()` فراخوانی شده است) درخواست می‌کند. پس از فراخوانی این روش، ضبط ادامه می‌یابد اما در یک `Blob` جدید.
- {{domxref("MediaRecorder.resume()")}}
  - : ضبط رسانه را پس از توقف مجدد از سر می‌گیرد.
- {{domxref("MediaRecorder.start()")}}
  - : شروع به ضبط رسانه می‌کند؛ این روش می‌تواند به صورت اختیاری یک آرگومان `timeslice` با مقدار میلی‌ثانیه دریافت کند. اگر مشخص شود، رسانه به جای رفتار پیش‌فرض (ضبط در یک تکه بزرگ) در تکه‌های جداگانه با آن مدت زمان ضبط خواهد شد.
- {{domxref("MediaRecorder.stop()")}}
  - : ضبط را متوقف می‌کند، در این زمان یک رویداد {{domxref("MediaRecorder.dataavailable_event", "dataavailable")}} حاوی `Blob` نهایی داده‌های ذخیره‌شده فعال می‌شود. دیگر ضبطی انجام نمی‌شود.

## رویدادها

برای گوش دادن به این رویدادها از `addEventListener()` یا با اختصاص یک شنونده رویداد به ویژگی `oneventname` این رابط استفاده کنید.

- {{domxref("MediaRecorder/dataavailable_event", "dataavailable")}}
  - : به صورت دوره‌ای هر بار که `timeslice` میلی‌ثانیه از رسانه ضبط شده است (یا زمانی که کل رسانه ضبط شده است، اگر `timeslice` مشخص نشده باشد) فعال می‌شود. این رویداد از نوع {{domxref("BlobEvent")}} است و رسانه ضبط‌شده را در ویژگی {{domxref("BlobEvent.data", "data")}} خود دارد.
- {{domxref("MediaRecorder/error_event", "error")}}
  - : زمانی که خطاهای مهلکی رخ می‌دهد که ضبط را متوقف می‌کنند، فعال می‌شود. رویداد دریافت‌شده بر اساس رابط {{domxref("MediaRecorderErrorEvent")}} است که ویژگی {{domxref("MediaRecorderErrorEvent.error", "error")}} آن حاوی یک {{domxref("DOMException")}} است که خطای واقعی رخ‌داده را توصیف می‌کند.
- {{domxref("MediaRecorder/pause_event", "pause")}}
  - : زمانی که ضبط رسانه متوقف می‌شود، فعال می‌شود.
- {{domxref("MediaRecorder/resume_event", "resume")}}
  - : زمانی که ضبط رسانه پس از توقف دوباره از سر گرفته می‌شود، فعال می‌شود.
- {{domxref("MediaRecorder/start_event", "start")}}
  - : زمانی که ضبط رسانه شروع می‌شود، فعال می‌شود.
- {{domxref("MediaRecorder/stop_event", "stop")}}
  - : زمانی که ضبط رسانه به پایان می‌رسد، چه به دلیل پایان {{domxref("MediaStream")}} یا پس از فراخوانی روش {{domxref("MediaRecorder.stop()")}}، فعال می‌شود.

## مثال

```js
if (navigator.mediaDevices) {
  console.log("getUserMedia supported.");

  const constraints = { audio: true };
  let chunks = [];

  navigator.mediaDevices
    .getUserMedia(constraints)
    .then((stream) => {
      const mediaRecorder = new MediaRecorder(stream);

      record.onclick = () => {
        mediaRecorder.start();
        console.log(mediaRecorder.state);
        console.log("recorder started");
        record.style.background = "red";
        record.style.color = "black";
      };

      stop.onclick = () => {
        mediaRecorder.stop();
        console.log(mediaRecorder.state);
        console.log("recorder stopped");
        record.style.background = "";
        record.style.color = "";
      };

      mediaRecorder.onstop = (e) => {
        console.log("data available after MediaRecorder.stop() called.");

        const clipName = prompt("Enter a name for your sound clip");

        const clipContainer = document.createElement("article");
        const clipLabel = document.createElement("p");
        const audio = document.createElement("audio");
        const deleteButton = document.createElement("button");
        const mainContainer = document.querySelector("body");

        clipContainer.classList.add("clip");
        audio.setAttribute("controls", "");
        deleteButton.textContent = "Delete";
        clipLabel.textContent = clipName;

        clipContainer.appendChild(audio);
        clipContainer.appendChild(clipLabel);
        clipContainer.appendChild(deleteButton);
        mainContainer.appendChild(clipContainer);

        audio.controls = true;
        const blob = new Blob(chunks, { type: "audio/ogg; codecs=opus" });
        chunks = [];
        const audioURL = URL.createObjectURL(blob);
        audio.src = audioURL;
        console.log("recorder stopped");

        deleteButton.onclick = (e) => {
          const evtTgt = e.target;
          evtTgt.parentNode.parentNode.removeChild(evtTgt.parentNode);
        };
      };

      mediaRecorder.ondataavailable = (e) => {
        chunks.push(e.data);
      };
    })
    .catch((err) => {
      console.error(`The following error occurred: ${err}`);
    });
}
```

> [!NOTE]
> این نمونه کد برگرفته از دموی Web Dictaphone است. برخی خطوط برای اختصار حذف شده‌اند؛ برای کد کامل [به منبع مراجعه کنید](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone).

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API ضبط جریان رسانه‌ای](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [Web Dictaphone](https://mdn.github.io/dom-examples/media/web-dictaphone/): دموی تجسم MediaRecorder + getUserMedia + Web Audio API، توسط [Chris Mills](https://github.com/chrisdavidmills) ([منبع در GitHub](https://github.com/mdn/dom-examples/tree/main/media/web-dictaphone)).
- [ضبط یک عنصر رسانه](/en-US/docs/Web/API/MediaStream_Recording_API/Recording_a_media_element)
- [دموی ضبط جریان رسانه‌ای simpl.info](https://simpl.info/mediarecorder/)، توسط [Sam Dutton](https://github.com/samdutton).
- {{domxref("MediaDevices.getUserMedia()")}}
- [OpenLang](https://github.com/chrisjohndigital/OpenLang): برنامه وب آزمایشگاه ویدیوی زبان با استفاده از MediaDevices و API ضبط جریان رسانه‌ای برای ضبط ویدیو ([منبع در GitHub](https://github.com/chrisjohndigital/OpenLang))