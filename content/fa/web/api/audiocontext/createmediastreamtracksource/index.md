---
title: "AudioContext: createMediaStreamTrackSource() method"
short-title: createMediaStreamTrackSource()
slug: Web/API/AudioContext/createMediaStreamTrackSource
page-type: web-api-instance-method
browser-compat: api.AudioContext.createMediaStreamTrackSource
---

{{ APIRef("Web Audio API") }}

**`createMediaStreamTrackSource()`** روشی از interface {{domxref("AudioContext")}} است که یک {{domxref("MediaStreamTrackAudioSourceNode")}} ایجاد و برمی‌گرداند که منبع صوتی است که داده‌های آن از {{domxref("MediaStreamTrack")}} مشخص‌شده می‌آید.

این روش با {{domxref("AudioContext.createMediaStreamSource", "createMediaStreamSource()")}} تفاوت دارد؛后者 یک {{domxref("MediaStreamAudioSourceNode")}} ایجاد می‌کند که صدای آن از track صوتی در یک {{domxref("MediaStream")}} مشخص می‌آید که {{domxref("MediaStreamTrack.id", "id")}} آن به ترتیب واژه‌نامه‌ای (الفبایی) اول است.

## نحو

```js-nolint
createMediaStreamTrackSource(track)
```

### پارامترها

- `track`
  - : {{domxref("MediaStreamTrack")}} که به عنوان منبع تمام داده‌های صوتی برای گره جدید استفاده می‌شود.

### مقدار بازگشتی

یک شیء {{domxref("MediaStreamTrackAudioSourceNode")}} که به عنوان منبعی برای داده‌های صوتی موجود در track صوتی مشخص‌شده عمل می‌کند.

## مثال‌ها

در این مثال، از {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} برای درخواست دسترسی به میکروفون کاربر استفاده می‌شود. پس از دستیابی به این دسترسی، یک زمینه صوتی (audio context) ایجاد می‌شود و یک {{domxref("MediaStreamTrackAudioSourceNode")}} با استفاده از `createMediaStreamTrackSource()` ساخته می‌شود که صدای خود را از اولین track صوتی در stream برگشتی از `getUserMedia()` می‌گیرد.

سپس یک {{domxref("BiquadFilterNode")}} با استفاده از {{domxref("BaseAudioContext/createBiquadFilter", "createBiquadFilter()")}} ایجاد می‌شود و به دلخواه برای اجرای یک فیلتر lowshelf روی صدای ورودی از منبع پیکربندی می‌شود. خروجی میکروفون به فیلتر biquad جدید هدایت می‌شود و خروجی فیلتر نیز به نوبه خود به {{domxref("BaseAudioContext/destination", "destination")}} زمینه صوتی هدایت می‌شود.

```js
navigator.mediaDevices
  .getUserMedia({ audio: true, video: false })
  .then((stream) => {
    audio.srcObject = stream;
    audio.onloadedmetadata = (e) => {
      audio.play();
      audio.muted = true;
    };

    const audioCtx = new AudioContext();
    const audioTracks = stream.getAudioTracks();
    const source = audioCtx.createMediaStreamTrackSource(audioTracks[0]);

    const biquadFilter = audioCtx.createBiquadFilter();
    biquadFilter.type = "lowshelf";
    biquadFilter.frequency.value = 3000;
    biquadFilter.gain.value = 20;

    source.connect(biquadFilter);
    biquadFilter.connect(audioCtx.destination);
  })
  .catch((err) => {
    // Handle getUserMedia() error
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- Web Audio API
- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("MediaStreamTrackAudioSourceNode")}}