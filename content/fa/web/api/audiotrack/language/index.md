---
title: "AudioTrack: language property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioTrack/language"
translated_by: "n8n + AI"
---

---
title: "AudioTrack: language property"
short-title: language
slug: Web/API/AudioTrack/language
page-type: web-api-instance-property
browser-compat: api.AudioTrack.language
---

{{APIRef("HTML DOM")}}

ویژگی **`language`** (فقط‌خواندنی) در {{domxref("AudioTrack")}}، رشته‌ای را برمی‌گرداند که زبان استفاده‌شده در تراک صوتی را مشخص می‌کند.

برای تراک‌هایی که شامل چند زبان هستند (مانند فیلمی به زبان انگلیسی که چند جمله به زبان‌های دیگر در آن گفته می‌شود)، این مقدار باید زبان اصلی ویدیو باشد.

## مقدار

رشته‌ای که {{glossary("BCP 47 language tag")}} زبان اصلی استفاده‌شده در تراک صوتی را مشخص می‌کند، یا رشتهٔ خالی (`""`) اگر زبان مشخص یا شناخته‌شده نباشد، یا اگر تراک شامل گفتار نباشد.

به عنوان مثال، اگر زبان اصلی استفاده‌شده در تراک انگلیسی ایالات متحده باشد، این مقدار `"en-US"` خواهد بود. برای پرتغالی برزیلی، مقدار `"pt-BR"` خواهد بود.

## مثال‌ها

این مثال تمام تراک‌های صوتی زبان اصلی و ترجمه‌شدهٔ یک المان رسانه را پیدا می‌کند و فهرستی از اشیاء حاوی {{domxref("AudioTrack.id", "id")}}، {{domxref("AudioTrack.kind", "kind")}} و `language` هر یک از آن تراک‌ها را برمی‌گرداند.

سپس می‌توان از آن برای ساخت رابط کاربری برای انتخاب زبانی که کاربر می‌خواهد هنگام تماشای فیلم به آن گوش دهد استفاده کرد، به عنوان مثال.

```js
function getAvailableLanguages(el) {
  const trackList = [];
  const wantedKinds = ["main", "translation"];

  el.audioTracks.forEach((track) => {
    if (wantedKinds.includes(track.kind)) {
      trackList.push({
        id: track.id,
        kind: track.kind,
        language: track.language,
      });
    }
  });
  return trackList;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}