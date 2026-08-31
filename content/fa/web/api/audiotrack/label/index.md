---
title: "AudioTrack: label property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrack/label"
translated_by: "n8n + AI"
---

---
title: "AudioTrack: label property"
short-title: label
slug: Web/API/AudioTrack/label
page-type: web-api-instance-property
browser-compat: api.AudioTrack.label
---

{{APIRef("HTML DOM")}}

ویژگی فقط خواندنی **`label`** از {{domxref("AudioTrack")}} یک رشته را برمی‌گرداند که برچسب قابل خواندن برای انسان مسیر صوتی را مشخص می‌کند، در صورت وجود؛ در غیر این صورت، یک رشته خالی برمی‌گرداند.

## مقدار

یک رشته که برچسب قابل خواندن برای انسان مسیر را مشخص می‌کند، در صورت وجود در فراداده‌های مسیر. در غیر این صورت، یک رشته خالی (`""`) برگردانده می‌شود.

برای مثال، یک مسیر که {{domxref("AudioTrack.kind", "kind")}} آن `"commentary"` است ممکن است `label` ای مانند `"Commentary with director Mark Markmarkimark and star Donna Donnalidon"` داشته باشد.

## مثال‌ها

این مثال یک آرایه از انواع و برچسب‌های مسیر را برای استفاده بالقوه در یک رابط کاربری برای انتخاب مسیرهای صوتی برای یک عنصر رسانه مشخص برمی‌گرداند. این فهرست فیلتر می‌شود تا فقط انواع خاصی از مسیرها مجاز باشند.

```js
function getTrackList(el) {
  const trackList = [];
  const wantedKinds = [
    "main",
    "alternative",
    "main-desc",
    "translation",
    "commentary",
  ];

  el.audioTracks.forEach((track) => {
    if (wantedKinds.includes(track.kind)) {
      trackList.push({
        id: track.id,
        kind: track.kind,
        label: track.label,
      });
    }
  });
  return trackList;
}
```

`trackList` حاصل شامل یک آرایه از مسیرهای صوتی است که `kind` آن‌ها یکی از موارد موجود در آرایه `wantedKinds` است، و هر ورودی {{domxref("AudioTrack.id", "id")}}، {{domxref("AudioTrack.kind", "kind")}} و `label` مسیر را ارائه می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}