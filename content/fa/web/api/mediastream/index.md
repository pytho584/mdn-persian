---
title: "MediaStream"
---

---
title: MediaStream
slug: Web/API/MediaStream
page-type: web-api-interface
browser-compat: api.MediaStream
---

{{APIRef("Media Capture and Streams")}}

رابط **`MediaStream`** از {{domxref("Media Capture and Streams API", "", "", "nocode")}} نمایانگر یک جریان محتوای رسانه‌ای است. یک جریان از چندین **ترک** (track) مانند ترک ویدیو یا ترک صوتی تشکیل شده است. هر ترک به‌صورت یک نمونه از {{domxref("MediaStreamTrack")}} مشخص می‌شود.

شما می‌توانید یک شیء `MediaStream` را یا با استفاده از سازنده (constructor) و یا با فراخوانی توابعی مانند {{domxref("MediaDevices.getUserMedia()")}}، {{domxref("MediaDevices.getDisplayMedia()")}}، یا {{domxref("HTMLCanvasElement.captureStream()")}} و {{domxref("HTMLMediaElement.captureStream()")}} به دست آورید.

{{InheritanceDiagram}}

## سازنده

- {{domxref("MediaStream.MediaStream", "MediaStream()")}}
  - : یک شیء `MediaStream` جدید می‌سازد و آن را برمی‌گرداند. می‌توانید یک جریان خالی، یک جریان مبتنی بر یک جریان موجود، یا جریانی که شامل فهرست مشخصی از ترک‌ها است (به‌صورت آرایه‌ای از اشیاء {{domxref("MediaStreamTrack")}} مشخص شده‌اند) ایجاد کنید.

## ویژگی‌های نمونه

_این رابط ویژگی‌هایی را از والد خود، {{domxref("EventTarget")}} به ارث می‌برد._

- {{domxref("MediaStream.active")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که اگر `MediaStream` فعال باشد `true` و در غیر این صورت `false` برمی‌گرداند.
- {{domxref("MediaStream.id")}} {{ReadOnlyInline}}
  - : یک رشته شامل شناسه یکتای عمومی ۳۶ کاراکتری ({{Glossary("UUID")}}) برای آن شیء.

## روش‌های نمونه

_این رابط روش‌هایی را از والد خود، {{domxref("EventTarget")}} به ارث می‌برد._

- {{domxref("MediaStream.addTrack()")}}
  - : یک کپی از {{domxref("MediaStreamTrack")}} ارسال‌شده به‌عنوان آرگومان را ذخیره می‌کند. اگر ترک قبلاً به شیء `MediaStream` اضافه شده باشد، هیچ اتفاقی رخ نمی‌دهد.
- {{domxref("MediaStream.clone()")}}
  - : یک نسخهٔ کلون از شیء `MediaStream` برمی‌گرداند. با این حال، کلون مقدار یکتایی برای {{domxref("MediaStream.id", "id")}} خواهد داشت.
- {{domxref("MediaStream.getAudioTracks()")}}
  - : فهرستی از اشیاء {{domxref("MediaStreamTrack")}} ذخیره‌شده در شیء `MediaStream` را برمی‌گرداند که ویژگی `kind` آن‌ها روی `audio` تنظیم شده است. ترتیب این فهرست تعریف نشده است و نه‌تنها ممکن است از مرورگری به مرورگر دیگر، بلکه از یک فراخوانی به فراخوانی دیگر نیز متفاوت باشد.
- {{domxref("MediaStream.getTrackById()")}}
  - : ترکی را برمی‌گرداند که شناسه آن با شناسه داده‌شده در پارامتر یعنی `trackId` مطابقت دارد. اگر پارامتری داده نشود، یا ترکی با آن شناسه وجود نداشته باشد، `null` برمی‌گرداند. اگر چندین ترک دارای شناسه یکسان باشند، اولین ترک را برمی‌گرداند.
- {{domxref("MediaStream.getTracks()")}}
  - : فهرستی از تمام اشیاء {{domxref("MediaStreamTrack")}} ذخیره‌شده در شیء `MediaStream` را برمی‌گرداند، صرف‌نظر از مقدار ویژگی `kind`. ترتیب تعریف نشده است و ممکن است نه‌تنها بین مرورگرها، بلکه از یک فراخوانی به فراخوانی دیگر متفاوت باشد.
- {{domxref("MediaStream.getVideoTracks()")}}
  - : فهرستی از اشیاء {{domxref("MediaStreamTrack")}} ذخیره‌شده در شیء `MediaStream` را برمی‌گرداند که ویژگی `kind` آن‌ها روی `"video"` تنظیم شده است. ترتیب تعریف نشده است و ممکن است نه‌تنها بین مرورگرها، بلکه از یک فراخوانی به فراخوانی دیگر متفاوت باشد.
- {{domxref("MediaStream.removeTrack()")}}
  - : {{domxref("MediaStreamTrack")}} داده‌شده به‌عنوان آرگومان را حذف می‌کند. اگر ترک بخشی از شیء `MediaStream` نباشد، هیچ اتفاقی رخ نمی‌دهد.

## رویدادها

- {{domxref("MediaStream/addtrack_event", "addtrack")}}
  - : هنگامی که یک شیء جدید از {{domxref("MediaStreamTrack")}} اضافه می‌شود، این رویداد صادر می‌شود.
- {{domxref("MediaStream/removetrack_event", "removetrack")}}
  - : هنگامی که یک شیء {{domxref("MediaStreamTrack")}} حذف شود، این رویداد صادر می‌شود.
- {{domxref("MediaStream/active_event", "active")}} {{Non-standard_Inline}}
  - : زمانی که MediaStream فعال می‌شود، این رویداد صادر می‌شود.
- {{domxref("MediaStream/inactive_event", "inactive")}} {{Non-standard_Inline}}
  - : زمانی که MediaStream غیرفعال می‌شود، این رویداد صادر می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API/Using_the_MediaStream_Recording_API)
- [WebRTC API](/en-US/docs/Web/API/WebRTC_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)
- {{domxref("MediaStreamTrack")}}