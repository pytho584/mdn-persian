---
title: "MediaStreamTrackProcessor: totalFrames property"
short-title: totalFrames
slug: Web/API/MediaStreamTrackProcessor/totalFrames
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.MediaStreamTrackProcessor.totalFrames
---

{{APIRef("Insertable Streams for MediaStreamTrack API")}}{{SeeCompatTable}}

ویژگی **`totalFrames`** در رابط {{domxref("MediaStreamTrackProcessor")}} عددی را برمی‌گرداند که نشان می‌دهد در مجموع چه تعداد فریم توسط پردازنده دریافت شده است.

## مقدار

یک عدد.

## مثال‌ها

### استفاده پایه

```js
async function init() {
  try {
    const stream = await navigator.mediaDevices.getUserMedia({ video: true });
    const [track] = stream.getVideoTracks();

    const processor = new MediaStreamTrackProcessor({
      track,
      maxBufferSize: 1,
    });
    const reader = processor.readable.getReader();

    while (true) {
      const { value: frame, done } = await reader.read();
      if (done) break;

      // Do something with frame...
      frame.close();

      console.log(
        `total: ${processor.totalFrames}, discarded: ${processor.discardedFrames}`,
      );
    }
  } catch (e) {
    console.error(e.name, e.message);
  }
}

document.querySelector("button").addEventListener("click", init);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("MediaStreamTrackProcessor.discardedFrames")}}