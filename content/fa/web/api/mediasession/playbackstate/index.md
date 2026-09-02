---
title: "MediaSession: playbackState property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MediaSession/playbackState"
---

---
title: "MediaSession: playbackState property"
short-title: playbackState
slug: Web/API/MediaSession/playbackState
page-type: web-api-instance-property
browser-compat: api.MediaSession.playbackState
---

{{APIRef("Media Session API")}}

ویژگی **`playbackState`** از رابط {{domxref("MediaSession")}} نشان می‌دهد که آیا جلسه رسانه‌ای فعلی در حال پخش است یا متوقف شده است.

## مقدار

یک رشته (string) که وضعیت پخش فعلی جلسه رسانه‌ای را نشان می‌دهد. مقدار می‌تواند یکی از موارد زیر باشد:

- `none`
  - : زمینه مرورگر (browsing context) در حال حاضر وضعیت پخش را نمی‌داند، یا وضعیت پخش در این لحظه در دسترس نیست.
- `paused`
  - : جلسه رسانه‌ای مرورگر در حال حاضر متوقف است. پخش ممکن است از سر گرفته شود.
- `playing`
  - : جلسه رسانه‌ای مرورگر در حال حاضر در حال پخش رسانه است که می‌تواند متوقف شود.

## مثال

مثال زیر دو تابع برای پخش و توقف تنظیم می‌کند و سپس از آن‌ها به عنوان تابع بازخورد (callback) همراه با کنترل‌کننده‌های اکشن مربوطه استفاده می‌کند. هر تابع از ویژگی `playbackState` برای نشان دادن اینکه آیا صدا در حال پخش است یا متوقف شده استفاده می‌کند.

```js
const actionHandlers = [
  // play
  [
    "play",
    async () => {
      // play our audio
      await audioEl.play();
      // set playback state
      navigator.mediaSession.playbackState = "playing";
      // update our status element
      updateStatus(allMeta[index], "Action: play  |  Track is playing…");
    },
  ],
  [
    "pause",
    () => {
      // pause out audio
      audioEl.pause();
      // set playback state
      navigator.mediaSession.playbackState = "paused";
      // update our status element
      updateStatus(allMeta[index], "Action: pause  |  Track has been paused…");
    },
  ],
];

for (const [action, handler] of actionHandlers) {
  try {
    navigator.mediaSession.setActionHandler(action, handler);
  } catch (error) {
    console.log(`The media session action "${action}" is not supported yet.`);
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}