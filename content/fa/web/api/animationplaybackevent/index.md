---
title: "AnimationPlaybackEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationPlaybackEvent"
translated_by: "n8n + AI"
---

---
title: AnimationPlaybackEvent
slug: Web/API/AnimationPlaybackEvent
page-type: web-api-interface
browser-compat: api.AnimationPlaybackEvent
---

{{ APIRef("Web Animations") }}

رابط `AnimationPlaybackEvent` از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) رویدادهای انیمیشن را نشان می‌دهد.

همانطور که انیمیشن‌ها اجرا می‌شوند، تغییرات {{domxref("Animation.playState", "playState")}} خود را از طریق رویدادهای انیمیشن گزارش می‌دهند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("AnimationPlaybackEvent.AnimationPlaybackEvent", "AnimationPlaybackEvent()")}}
  - : یک نمونه شیء جدید از `AnimationPlaybackEvent` می‌سازد.

## ویژگی‌های نمونه

- {{domxref("AnimationPlaybackEvent.currentTime")}} {{ReadOnlyInline}}
  - : زمان جاری انیمیشنی که رویداد را تولید کرده است.
- {{domxref("AnimationPlaybackEvent.timelineTime")}} {{ReadOnlyInline}}
  - : مقدار زمانی خط زمانی انیمیشنی که رویداد را تولید کرده است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation.playState")}}