---
title: "MediaStreamTrack: unmute event"
short-title: unmute
slug: Web/API/MediaStreamTrack/unmute_event
page-type: web-api-event
browser-compat: api.MediaStreamTrack.unmute_event
---

{{APIRef("Media Capture and Streams")}}

رویداد **`unmute`** به یک {{domxref("MediaStreamTrack")}} ارسال می‌شود هنگامی که منبع آن پس از مدتی که قادر به ارائه داده‌های رسانه‌ای نبود، دوباره بتواند این کار را انجام دهد.

این رویداد به حالت {{domxref("MediaStreamTrack.muted", "muted")}} که با رویداد {{domxref("MediaStreamTrack/mute_event", "mute")}} آغاز شده بود، پایان می‌دهد.

> [!NOTE]
> توجه داشته باشید که شرایطی که بیشتر افراد به عنوان "muted" (یعنی راهی قابل کنترل توسط کاربر برای ساکت کردن یک track) می‌شناسند، در واقع با استفاده از ویژگی {{domxref("MediaStreamTrack.enabled")}} مدیریت می‌شود، که برای آن هیچ رویدادی وجود ندارد.

این رویداد قابل لغو (cancelable) نیست و حباب (bubble) نمی‌زند.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("unmute", (event) => { })

onunmute = (event) => { }
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

در این مثال، کنترل‌کننده‌های رویداد برای رویدادهای {{domxref("MediaStreamTrack/mute_event", "mute")}} و `unmute` تنظیم شده‌اند تا تشخیص دهند که چه زمانی رسانه از منبع {{domxref("MediaStreamTrack")}} ذخیره شده در متغیر `musicTrack` جریان ندارد.

```js
musicTrack.addEventListener("mute", (event) => {
  const widget = document.getElementById("timeline-widget");
  widget.style.backgroundColor = "#aaaaaa";
});

musicTrack.addEventListener("unmute", (event) => {
  document.getElementById("timeline-widget").style.backgroundColor = "white";
});
```

با وجود این کنترل‌کننده‌های رویداد، هنگامی که track `musicTrack` وارد حالت {{domxref("MediaStreamTrack.muted", "muted")}} خود می‌شود، عنصر با شناسه `timeline-widget` رنگ پس‌زمینه خود را به `#aaaaaa` تغییر می‌دهد. هنگامی که track از حالت muted خارج می‌شود - که با رسیدن یک رویداد `unmuted` تشخیص داده می‌شود - رنگ پس‌زمینه به سفید بازگردانده می‌شود.

همچنین می‌توانید از ویژگی کنترل‌کننده رویداد `onunmute` برای تنظیم یک کنترل‌کننده برای این رویداد استفاده کنید؛ به طور مشابه، کنترل‌کننده رویداد {{domxref("MediaStreamTrack.mute_event", "onmute")}} برای تنظیم یک کنترل‌کننده برای رویداد `mute` در دسترس است. مثال زیر این را نشان می‌دهد:

```js
musicTrack.onmute = (event) => {
  document.getElementById("timeline-widget").style.backgroundColor = "#aaaaaa";
};

musicTrack.onunmute = (event) => {
  document.getElementById("timeline-widget").style.backgroundColor = "white";
};
```

### لغو حالت mute tracks از طریق receiverها

مثال زیر نشان می‌دهد که چگونه می‌توان با استفاده از receiverها tracks را از حالت mute خارج کرد.

```js
// Peer 1 (Sender)
const transceivers = peer.getTransceivers();

const audioTrack = transceivers[0];
audioTrack.direction = "sendrecv";

const videoTrack = transceivers[1];
videoTrack.direction = "sendrecv";

// Peer 2 (Receiver)
audioTrack.addEventListener("unmute", (event) => {
  // Do something in UI
});

videoTrack.addEventListener("unmute", (event) => {
  // Do something in UI
});
```

`transceivers` آرایه‌ای از {{domxref("RTCRtpTransceiver")}} است که می‌توانید track صوتی یا تصویری ارسال و دریافت شده را در آن پیدا کنید. برای اطلاعات بیشتر، به مقاله {{domxref("RTCRtpTransceiver.direction", "direction")}} مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- رویداد {{domxref("MediaStreamTrack/mute_event", "mute")}}