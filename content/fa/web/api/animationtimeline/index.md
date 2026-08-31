---
title: "AnimationTimeline"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationTimeline"
translated_by: "n8n + AI"
---

---
title: AnimationTimeline
slug: Web/API/AnimationTimeline
page-type: web-api-interface
browser-compat: api.AnimationTimeline
---

{{ APIRef("Web Animations") }}

رابطهٔ `AnimationTimeline` از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) خط زمانی یک انیمیشن را نشان می‌دهد. این رابط برای تعریف ویژگی‌های خط زمانی وجود دارد که توسط سایر انواع خط‌های زمانی به ارث برده می‌شود:

- {{domxref("DocumentTimeline")}}
- {{domxref("ScrollTimeline")}}
- {{domxref("ViewTimeline")}}

## ویژگی‌های نمونه

- {{domxref("AnimationTimeline.currentTime", "currentTime")}} {{ReadOnlyInline}}
  - : مقدار زمانی را بر حسب میلی‌ثانیه برای این خط زمانی برمی‌گرداند، یا اگر این خط زمانی غیرفعال باشد `null` را برمی‌گرداند.
- {{domxref("AnimationTimeline.duration", "duration")}} {{ReadOnlyInline}}
  - : حداکثر مقدار را برای این خط زمانی برمی‌گرداند، یا `null`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DocumentTimeline")}}, {{domxref("ScrollTimeline")}}, {{domxref("ViewTimeline")}}
- {{domxref("Document.timeline")}}
- [API انیمیشن‌های وب](/en-US/docs/Web/API/Web_Animations_API)
- [انیمیشن‌های مبتنی بر اسکرول CSS](/en-US/docs/Web/CSS/Guides/Scroll-driven_animations)