---
title: "MediaStreamTrack: mute event"
short-title: mute
slug: Web/API/MediaStreamTrack/mute_event
page-type: web-api-event
browser-compat: api.MediaStreamTrack.mute_event
---

{{APIRef("Media Capture and Streams")}}

رویداد **`mute`** زمانی به یک {{domxref("MediaStreamTrack")}} ارسال می‌شود که منبع آن ردیاب به‌طور موقت قادر به ارائه داده‌های رسانه‌ای نباشد.

زمانی که ردیاب دوباره بتواند خروجی رسانه‌ای تولید کند، رویداد {{domxref("MediaStreamTrack/unmute_event", "unmute")}} ارسال می‌شود.

در فاصله بین رویداد `mute` و رویداد `unmute`، مقدار ویژگی {{domxref("MediaStreamTrack.muted", "muted")}} ردیاب برابر با `true` است.

> [!NOTE]
> وضعیتی که بیشتر افراد آن را «بی‌صدا بودن» می‌دانند (یعنی حالتی که کاربر با اختیار خود یک ردیاب را ساکت می‌کند) در واقع با استفاده از ویژگی {{domxref("MediaStreamTrack.enabled")}} مدیریت می‌شود که برای آن هیچ رویدادی وجود ندارد.

این رویداد قابل لغو (cancelable) نیست و bubble نمی‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("mute", (event) => { })

onmute = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

در این مثال، مدیریت‌کننده‌های رویداد برای رویدادهای `mute` و {{domxref("MediaStreamTrack.unmute_event", "unmute")}} تنظیم شده‌اند تا زمانی که رسانه از منبع برای {{domxref("MediaStreamTrack")}} ارجاع‌داده‌شده توسط `musicTrack` جریان نداشته باشد، شناسایی شود.

```js
musicTrack.addEventListener("mute", (event) => {
  const widget = document.getElementById("timeline-widget");
  widget.style.backgroundColor = "#aaaaaa";
});

musicTrack.addEventListener("unmute", (event) => {
  document.getElementById("timeline-widget").style.backgroundColor = "white";
});
```

با وجود این مدیریت‌کننده‌های رویداد، وقتی ردیاب `musicTrack` وارد حالت {{domxref("MediaStreamTrack.muted", "muted")}} می‌شود، رنگ پس‌زمینه عنصر با شناسه `timeline-widget` به `#aaaaaa` تغییر می‌کند. وقتی ردیاب از حالت بی‌صدا خارج می‌شود — که با رسیدن رویداد `unmute` شناسایی می‌شود — رنگ پس‌زمینه به سفید بازنشانی می‌شود.

همچنین می‌توانید از ویژگی مدیریت‌کننده رویداد `onmute` برای تنظیم یک مدیریت‌کننده برای این رویداد استفاده کنید؛ به‌طور مشابه، ویژگی مدیریت‌کننده رویداد {{domxref("MediaStreamTrack.unmute_event", "onunmute")}} برای تنظیم مدیریت‌کننده رویداد `unmute` در دسترس است. مثال زیر این را نشان می‌دهد:

```js
musicTrack.onmute = (event) => {
  document.getElementById("timeline-widget").style.backgroundColor = "#aaaaaa";
};

musicTrack.onunmute = (event) => {
  document.getElementById("timeline-widget").style.backgroundColor = "white";
};
```

### بی‌صدا کردن ردیاب‌ها از طریق گیرنده‌ها (receivers)

مثال زیر نحوه بی‌صدا کردن ردیاب‌ها با استفاده از گیرنده‌ها را نشان می‌دهد.

```js
// همتای ۱ (فرستنده)
const transceivers = peer.getTransceivers();

const audioTrack = transceivers[0];
audioTrack.direction = "recvonly";

const videoTrack = transceivers[1];
videoTrack.direction = "recvonly";

// همتای ۲ (گیرنده)
audioTrack.addEventListener("mute", (event) => {
  // کاری در رابط کاربری انجام دهید
});

videoTrack.addEventListener("mute", (event) => {
  // کاری در رابط کاربری انجام دهید
});
```

`transceivers` آرایه‌ای از {{domxref("RTCRtpTransceiver")}} است که می‌توانید ردیاب صوتی یا تصویری ارسال‌شده و دریافت‌شده را در آن بیابید. برای اطلاعات بیشتر، مقاله {{domxref("RTCRtpTransceiver.direction", "direction")}} را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("MediaStreamTrack/unmute_event", "unmute")}}
- {{domxref("RTCRtpTransceiver.direction", "direction")}}