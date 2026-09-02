---
title: "MediaStream: removeTrack() method"
short-title: removeTrack()
slug: Web/API/MediaStream/removeTrack
page-type: web-api-instance-method
browser-compat: api.MediaStream.removeTrack
---

{{APIRef("Media Capture and Streams")}}

متد **`removeTrack()`** از رابط {{domxref("MediaStream")}} یک {{domxref("MediaStreamTrack")}} را از یک استریم حذف می‌کند.

## Syntax

```js-nolint
removeTrack(track)
```

### Parameters

- `track`
  - : یک {{domxref("MediaStreamTrack")}} که از استریم حذف خواهد شد.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

## Examples

مثال زیر نحوه حذف ترک‌های صوتی و تصویری از یک {{domxref("MediaStream")}} را نشان می‌دهد. `fetchStreamFunction` یک کنترل‌کننده رویداد برای `fetchStreamButton` است. هنگامی که دکمه کلیک شود، صدا و تصویر از دستگاه‌های سیستم ضبط می‌شوند. `removeTracksFunction` کنترل‌کننده رویداد برای `removeTracksButton` است. هنگامی که این دکمه کلیک شود، ترک‌های صوتی و تصویری از {{domxref("MediaStream")}} حذف می‌شوند.

```js
let initialStream = null;
let newStream = null;

let fetchStreamButton = document.getElementById("fetchStream");
let removeTracksButton = document.getElementById("removeTracks");

async function fetchStreamFunction() {
  initialStream = await navigator.mediaDevices.getUserMedia({
    video: { width: 620, height: 310 },
    audio: true,
  });
  if (initialStream) {
    await attachToDOM(initialStream);
  }
}

async function attachToDOM(stream) {
  newStream = new MediaStream(stream.getTracks());
  document.querySelector("video").srcObject = newStream;
}

async function removeTracksFunction() {
  let videoTrack = newStream.getVideoTracks()[0];
  let audioTrack = newStream.getAudioTracks()[0];

  newStream.removeTrack(videoTrack);
  newStream.removeTrack(audioTrack);

  // Stream will be empty
  console.log(newStream.getTracks());
}

fetchStreamButton.addEventListener("click", fetchStreamFunction);
removeTracksButton.addEventListener("click", removeTracksFunction);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}