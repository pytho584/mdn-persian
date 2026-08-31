---
title: "AnimationPlaybackEvent: timelineTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationPlaybackEvent/timelineTime"
translated_by: "n8n + AI"
---

---
title: "AnimationPlaybackEvent: timelineTime property"
short-title: timelineTime
slug: Web/API/AnimationPlaybackEvent/timelineTime
page-type: web-api-instance-property
browser-compat: api.AnimationPlaybackEvent.timelineTime
---

{{ APIRef("Web Animations") }}

ویژگی فقط‌خواندنی **`timelineTime`** از رابط {{domxref("AnimationPlaybackEvent")}} مقدار زمانی {{domxref("AnimationTimeline", "timeline")}} انیمیشن را در لحظه‌ای که رویداد در صف قرار می‌گیرد نشان می‌دهد. اگر انیمیشن در زمان تولید رویداد با یک خط زمانی مرتبط نبوده یا خط زمانی مرتبط غیرفعال بوده باشد، این مقدار نامشخص خواهد بود.

## مقدار

عددی که زمان فعلی را بر حسب میلی‌ثانیه نشان می‌دهد، یا `null`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API انیمیشن‌های وب](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationPlayBackEvent")}}
- {{domxref("AnimationTimeline")}}