---
title: "AnimationEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationEvent"
translated_by: "n8n + AI"
---

---
title: AnimationEvent
slug: Web/API/AnimationEvent
page-type: web-api-interface
browser-compat: api.AnimationEvent
---

{{APIRef("Web Animations")}}

رابط **`AnimationEvent`** رویدادهایی را نمایش می‌دهد که اطلاعات مرتبط با [animations](/en-US/docs/Web/CSS/Guides/Animations/Using) را فراهم می‌کنند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("AnimationEvent.AnimationEvent", "AnimationEvent()")}}
  - : یک رویداد `AnimationEvent` را با پارامترهای داده‌شده ایجاد می‌کند.

## ویژگی‌های نمونه

_همچنین ویژگی‌هایی را از والد خود {{domxref("Event")}} به ارث می‌برد._

- {{domxref("AnimationEvent.animation")}} {{ReadOnlyInline}}
  - : یک ویژگی فقط‌خواندنی {{domxref("CSSAnimation")}} که انیمیشن مرتبط با رویداد را نشان می‌دهد.
- {{domxref("AnimationEvent.animationName")}} {{ReadOnlyInline}}
  - : رشته‌ای حاوی مقدار {{cssxref("animation-name")}} که انیمیشن را ایجاد کرده است.
- {{domxref("AnimationEvent.elapsedTime")}} {{ReadOnlyInline}}
  - : یک `float` که مقدار زمان اجرای انیمیشن را بر حسب ثانیه هنگام فعال‌شدن این رویداد می‌دهد، به استثنای هر زمانی که انیمیشن مکث شده است. برای رویداد `animationstart`، `elapsedTime` برابر با `0.0` است مگر اینکه مقدار منفی برای {{cssxref("animation-delay")}} وجود داشته باشد؛ در این صورت رویداد با `elapsedTime` شامل `(-1 * delay)` فعال می‌شود.
- {{domxref("AnimationEvent.pseudoElement")}} {{ReadOnlyInline}}
  - : رشته‌ای که با `'::'` شروع می‌شود و شامل نام [pseudo-element](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) است که انیمیشن روی آن اجرا می‌شود. اگر انیمیشن روی یک pseudo-element اجرا نشود بلکه روی خود عنصر اجرا شود، یک رشته خالی: `''`.

## روش‌های نمونه

_روش‌هایی را از والد خود، {{domxref("Event")}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using CSS animations](/en-US/docs/Web/CSS/Guides/Animations/Using)
- ویژگی‌ها و قواعد at مرتبط با انیمیشن CSS: {{cssxref("animation")}}, {{cssxref("animation-composition")}}, {{cssxref("animation-delay")}}, {{cssxref("animation-direction")}}, {{cssxref("animation-duration")}}, {{cssxref("animation-fill-mode")}}, {{cssxref("animation-iteration-count")}}, {{cssxref("animation-name")}}, {{cssxref("animation-play-state")}}, {{cssxref("animation-timing-function")}}, {{cssxref("@keyframes")}}.