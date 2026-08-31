---
title: "AudioScheduledSourceNode: ended event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioScheduledSourceNode/ended_event"
translated_by: "n8n + AI"
---

---
title: "AudioScheduledSourceNode: ended event"
short-title: ended
slug: Web/API/AudioScheduledSourceNode/ended_event
page-type: web-api-event
browser-compat: api.AudioScheduledSourceNode.ended_event
---

{{APIRef("Web Audio API")}}

رویداد `ended` از رابط {{domxref("AudioScheduledSourceNode")}} زمانی فعال می‌شود که گره منبع پخش خود را متوقف کرده است.

این رویداد زمانی رخ می‌دهد که یک {{domxref("AudioScheduledSourceNode")}} پخش خود را متوقف کرده است، خواه به دلیل رسیدن به زمان توقف از پیش تعیین‌شده، اجرای کامل مدت زمان صوتی، یا پخش کامل بافر باشد.

این رویداد قابل لغو نیست و منتشر نمی‌شود (bubble نمی‌کند).

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("ended", (event) => { })

onended = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

در این مثال ساده، یک شنونده رویداد برای رویداد `ended` تنظیم شده است تا دکمه "شروع" را در رابط کاربری زمانی که گره پخش را متوقف می‌کند، فعال کند:

```js
node.addEventListener("ended", () => {
  document.getElementById("startButton").disabled = false;
});
```

همچنین می‌توانید کنترل‌کننده رویداد را با استفاده از ویژگی `onended` تنظیم کنید:

```js
node.onended = () => {
  document.getElementById("startButton").disabled = false;
};
```

برای مشاهده یک مثال از رویداد ended در عمل، به [مثال audio-buffer ما در GitHub](https://mdn.github.io/webaudio-examples/audio-buffer/) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## رویدادهای مرتبط

- [audioprocess](/en-US/docs/Web/API/ScriptProcessorNode/audioprocess_event)
- [complete](/en-US/docs/Web/API/OfflineAudioContext/complete_event)

## همچنین ببینید

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}
- رویداد {{domxref("HTMLMediaElement.ended_event", 'ended')}} در HTMLMediaElement
- رویداد {{domxref("MediaStreamTrack.ended_event", 'ended')}} در MediaStreamTrack