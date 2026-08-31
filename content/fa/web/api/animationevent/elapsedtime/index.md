---
title: "AnimationEvent: elapsedTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationEvent/elapsedTime"
translated_by: "n8n + AI"
---

---
title: "AnimationEvent: elapsedTime property"
short-title: elapsedTime
slug: Web/API/AnimationEvent/elapsedTime
page-type: web-api-instance-property
browser-compat: api.AnimationEvent.elapsedTime
---

{{APIRef("Web Animations")}}

خصوصیت فقط-خواندنی **`AnimationEvent.elapsedTime`** یک `float` است که مقدار زمان اجرای انیمیشن را بر حسب ثانیه، هنگام فعال شدن این رویداد، به‌جز زمان‌هایی که انیمیشن مکث شده، برمی‌گرداند. برای رویداد {{domxref("Element/animationstart_event", "animationstart")}}، `elapsedTime` برابر `0.0` است مگر اینکه مقدار منفی برای {{cssxref("animation-delay")}} وجود داشته باشد، که در آن صورت رویداد با `elapsedTime` حاوی `(-1 * delay)` فراخوانی می‌شود.

## مقدار

یک `float` که مقدار زمان را بر حسب ثانیه می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از انیمیشن‌های CSS](/en-US/docs/Web/CSS/Guides/Animations/Using)
- خصوصیات و قواعد CSS مرتبط با انیمیشن: {{cssxref("animation")}}، {{cssxref("animation-delay")}}، {{cssxref("animation-direction")}}، {{cssxref("animation-duration")}}، {{cssxref("animation-fill-mode")}}، {{cssxref("animation-iteration-count")}}، {{cssxref("animation-name")}}، {{cssxref("animation-play-state")}}، {{cssxref("animation-timing-function")}}، {{cssxref("@keyframes")}}.
- رابط {{domxref("AnimationEvent")}} که این خصوصیت به آن تعلق دارد.