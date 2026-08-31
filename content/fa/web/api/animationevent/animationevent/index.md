---
title: "AnimationEvent: AnimationEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationEvent/AnimationEvent"
translated_by: "n8n + AI"
---

---
title: "AnimationEvent: AnimationEvent() constructor"
short-title: AnimationEvent()
slug: Web/API/AnimationEvent/AnimationEvent
page-type: web-api-constructor
browser-compat: api.AnimationEvent.AnimationEvent
---

{{APIRef("Web Animations")}}

سازندهی **`AnimationEvent()`** یک شیء جدید {{domxref("AnimationEvent")}} برمیگرداند که نمایانگر یک رویداد در ارتباط با یک انیمیشن است.

## سینتکس

```js-nolint
new AnimationEvent(type)
new AnimationEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته حاوی نام نوع `AnimationEvent`.
    این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها آن را به `animationstart`، `animationend` یا `animationiteration` تنظیم میکنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگیهای تعریفشده در {{domxref("Event/Event", "Event()")}}_، ویژگیهای زیر را دارد:
    - `animation` {{optional_inline}}
      - : یک {{domxref("CSSAnimation")}} شامل انیمیشن مرتبط با رویداد.
        بهطور پیشفرض `null` است.
    - `animationName` {{optional_inline}}
      - : یک رشته حاوی مقدار ویژگی CSS {{cssxref("animation-name")}} مرتبط با انتقال. بهطور پیشفرض `""` است.
    - `elapsedTime` {{optional_inline}}
      - : یک `float` که مقدار زمان انیمیشن را بر حسب ثانیه هنگام رخ دادن این رویداد میدهد، بهجز مدتی که انیمیشن مکث شده است.
        برای رویداد `animationstart`، مقدار `elapsedTime` برابر با `0.0` است مگر اینکه مقدار منفی برای {{cssxref("animation-delay")}} وجود داشته باشد،
        در این صورت رویداد با `elapsedTime` حاوی `(-1 * delay)` فعال میشود. بهطور پیشفرض `0.0` است.
    - `pseudoElement` {{optional_inline}}
      - : یک رشته که با `"::"` شروع میشود و حاوی نام [pseudo-element](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) مورد نظر برای اجرای انیمیشن است. اگر انیمیشن روی یک شبهعنصر اجرا نمیشود بلکه روی خود عنصر اجرا میشود، یک رشته خالی: `""` مشخص کنید. بهطور پیشفرض `""` است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using CSS animations](/en-US/docs/Web/CSS/Guides/Animations/Using)
- ویژگیها و قواعد CSS مرتبط با انیمیشن: {{cssxref("animation")}},
  {{cssxref("animation-delay")}}, {{cssxref("animation-direction")}},
  {{cssxref("animation-duration")}}, {{cssxref("animation-fill-mode")}},
  {{cssxref("animation-iteration-count")}}, {{cssxref("animation-name")}},
  {{cssxref("animation-play-state")}}, {{cssxref("animation-timing-function")}},
  {{cssxref("@keyframes")}}
- رابط {{domxref("AnimationEvent")}} که به آن تعلق دارد.