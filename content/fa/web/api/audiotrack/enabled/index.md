---
title: "AudioTrack: enabled property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrack/enabled"
translated_by: "n8n + AI"
---

---
title: "AudioTrack: enabled property"
short-title: enabled
slug: Web/API/AudioTrack/enabled
page-type: web-api-instance-property
browser-compat: api.AudioTrack.enabled
---

{{APIRef("HTML DOM")}}

ویژگی **{{domxref("AudioTrack")}}** با نام **`enabled`** مشخص می‌کند که آیا مسیر صوتی توصیف‌شده در حال حاضر برای استفاده فعال است یا خیر. اگر مسیر با تنظیم `enabled` روی `false` غیرفعال شود، مسیر بی‌صدا می‌شود و صدایی تولید نمی‌کند.

## مقدار

ویژگی `enabled` یک مقدار بولی است که اگر مسیر فعال باشد، مقدار آن `true` است؛ مسیرهای فعال در حین پخش رسانه صدا تولید می‌کنند. تنظیم `enabled` روی `false` عملاً مسیر صوتی را بی‌صدا می‌کند و از مشارکت آن در خروجی صدای رسانه جلوگیری می‌کند.

## مثال

این مثال بین مسیرهای صوتی اصلی و commentary یک عنصر رسانه جابه‌جا می‌شود.

```js
function swapCommentaryMain() {
  const videoElem = document.getElementById("main-video");
  let audioTrackMain;
  let audioTrackCommentary;

  videoElem.audioTracks.forEach((track) => {
    if (track.kind === "main") {
      audioTrackMain = track;
    } else if (track.kind === "commentary") {
      audioTrackCommentary = track;
    }
  });

  if (audioTrackMain && audioTrackCommentary) {
    const commentaryEnabled = audioTrackCommentary.enabled;
    audioTrackCommentary.enabled = audioTrackMain.enabled;
    audioTrackMain.enabled = commentaryEnabled;
  }
}
```

تابع `swapCommentaryMain()` در بالا در میان مسیرهای صوتی عنصر {{HTMLElement("video")}} با شناسه `"main-video"` به دنبال مسیرهایی می‌گردد که مقدار {{domxref("AudioTrack.kind", "kind")}} آن‌ها `"main"` و `"commentary"` است. این مسیرها نشان‌دهنده مسیر صوتی اصلی و مسیر commentary هستند.

> [!NOTE]
> این مثال فرض می‌کند که در ویدیو فقط یک مسیر از هر نوع وجود دارد، اما این لزوماً همیشه صادق نیست.

سپس مسیرهای صوتی عنصر با استفاده از روش جاوااسکریپت {{jsxref("Array.forEach", "forEach()")}} پیمایش می‌شوند (اگرچه ویژگی {{domxref("HTMLMediaElement.audioTracks", "audioTracks")}} یک عنصر رسانه در واقع آرایه جاوااسکریپتی نیست، اما در بیشتر موارد می‌توان مانند یک آرایه به آن دسترسی داشت).

این پیمایش به دنبال مسیرهایی می‌گردد که مقدار {{domxref("AudioTrack.kind", "kind")}} آن‌ها `"main"` و `"commentary"` است و آن اشیاء {{domxref("AudioTrack")}} را به خاطر می‌سپارد. پس از یافتن آن‌ها، مقادیر ویژگی‌های `enabled` دو مسیر با یکدیگر مبادله می‌شوند که منجر به جابه‌جایی مسیر فعال فعلی بین آن دو می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}