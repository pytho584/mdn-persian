---
title: "AudioTrackList: change event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrackList/change_event"
translated_by: "n8n + AI"
---

---
title: "AudioTrackList: change event"
short-title: change
slug: Web/API/AudioTrackList/change_event
page-type: web-api-event
browser-compat: api.AudioTrackList.change_event
---

{{APIRef("HTML DOM")}}

رویداد `change` زمانی فعال میشود که یک ترک صوتی فعال یا غیرفعال شود، برای مثال با تغییر دادن ویژگی [`enabled`](/en-US/docs/Web/API/AudioTrack/enabled) ترک.

این رویداد غیرقابل لغو است و حباب نمیزند.

## نحو (Syntax)

از نام رویداد در روشهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثالها

استفاده از `addEventListener()`:

```js
const videoElement = document.querySelector("video");
videoElement.audioTracks.addEventListener("change", (event) => {
  console.log(`'${event.type}' event fired`);
});

// changing the value of `enabled` will trigger the `change` event
const toggleTrackButton = document.querySelector(".toggle-track");
toggleTrackButton.addEventListener("click", () => {
  const track = videoElement.audioTracks[0];
  track.enabled = !track.enabled;
});
```

استفاده از ویژگی مدیریت رویداد `onchange`:

```js
const videoElement = document.querySelector("video");
videoElement.audioTracks.onchange = (event) => {
  console.log(`'${event.type}' event fired`);
};

// changing the value of `enabled` will trigger the `change` event
const toggleTrackButton = document.querySelector(".toggle-track");
toggleTrackButton.addEventListener("click", () => {
  const track = videoElement.audioTracks[0];
  track.enabled = !track.enabled;
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: [`addtrack`](/en-US/docs/Web/API/AudioTrackList/addtrack_event)، [`removetrack`](/en-US/docs/Web/API/AudioTrackList/removetrack_event)
- این رویداد روی [`VideoTrackList`](/en-US/docs/Web/API/VideoTrackList) هدف قرار میگیرد: [`change`](/en-US/docs/Web/API/VideoTrackList/change_event)
- [API ضبط و جریان رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [API WebRTC](/en-US/docs/Web/API/WebRTC_API)