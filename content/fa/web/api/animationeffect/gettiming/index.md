---
title: "AnimationEffect: getTiming() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnimationEffect/getTiming"
translated_by: "n8n + AI"
---

---
title: "AnimationEffect: getTiming() method"
short-title: getTiming()
slug: Web/API/AnimationEffect/getTiming
page-type: web-api-instance-method
browser-compat: api.AnimationEffect.getTiming
---

{{ APIRef("Web Animations") }}

متد `AnimationEffect.getTiming()` از رابط {{domxref("AnimationEffect")}} یک شیء شامل ویژگی‌های زمان‌بندی افکت انیمیشن را برمی‌گرداند.

> [!NOTE]
> چندین ویژگی از ویژگی‌های زمان‌بندی بازگردانده‌شده توسط `getTiming()` ممکن است مقدار مکان‌نمای `"auto"` را بگیرند. برای دریافت مقادیر قطعی جهت استفاده در محاسبات زمان‌بندی، به‌جای آن از {{domxref("AnimationEffect.getComputedTiming()")}} استفاده کنید.
>
> در آینده، `"auto"` یا مقادیر مشابه ممکن است به انواع ویژگی‌های زمان‌بندی بیشتری اضافه شوند و انواع جدید {{domxref("AnimationEffect")}} ممکن است `"auto"` را به مقادیر متفاوتی تفسیر کنند.

## سینتکس

```js-nolint
getTiming()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء شامل ویژگی‌های زیر:

- `delay`
  - : تعداد میلی‌ثانیه‌های تأخیر قبل از شروع افکت (`number`).

    (همچنین ببینید: {{cssxref("animation-delay")}}.)

- `direction`
  - : `"normal"`, `"reverse"`, `"alternate"`، یا `"alternate-reverse"`.

    مشخص می‌کند که آیا افکت به جلو (`"normal"`) اجرا می‌شود، به عقب (`"reverse"`) اجرا می‌شود، بعد از هر تکرار جهت را تغییر می‌دهد (`"alternate"`)، یا به عقب اجرا شده و بعد از هر تکرار جهت را تغییر می‌دهد (`"alternate-reverse"`).

    (همچنین ببینید: {{cssxref("animation-direction")}}.)

- `duration`
  - : مقداری از نوع `number` بر حسب میلی‌ثانیه، یا `string` با مقدار `"auto"`.

    مدت زمانی را نشان می‌دهد که یک تکرار از انیمیشن برای تکمیل شدن طول می‌کشد.

    معنای `"auto"` ممکن است بسته به نوع افکت متفاوت باشد؛ برای {{domxref("KeyframeEffect")}}، `"auto"` معادل `0` است.

    (همچنین ببینید: {{cssxref("animation-duration")}}.)

- `easing`
  - : یک `string` نمایانگر {{cssxref("easing-function")}} که نرخ تغییر افکت را در طول زمان توصیف می‌کند.

    (همچنین ببینید: {{cssxref("animation-timing-function")}}.)

- `endDelay`
  - : تعداد میلی‌ثانیه‌های تأخیر پس از پایان افکت (`number`).

    این عمدتاً هنگام ترتیب‌دهی انیمیشن‌ها بر اساس زمان پایان یک انیمیشن دیگر مفید است.

- `fill`
  - : `"none"`, `"forwards"`, `"backwards"`, `"both"`، یا `"auto"`.

    مشخص می‌کند که آیا افکت توسط هدف(های) خود پیش از پخش منعکس می‌شود (`"backwards"`)، پس از تکمیل افکت باقی می‌ماند (`"forwards"`)، هر دو (`"both"`)، یا هیچ‌کدام (`"none"`).

    معنای `"auto"` ممکن است بسته به نوع افکت متفاوت باشد؛ برای {{domxref("KeyframeEffect")}}، `"auto"` معادل `"none"` است.

    (همچنین ببینید: {{cssxref("animation-fill-mode")}}.)

- `iterations`
  - : تعداد (`number`) دفعاتی که افکت تکرار خواهد شد. مقدار {{jsxref("Infinity")}} نشان می‌دهد که افکت به‌طور نامحدود تکرار می‌شود.

    (همچنین ببینید: {{cssxref("animation-iteration-count")}}.)

- `iterationStart`
  - : یک `number` که مشخص می‌کند افکت از چه نقطه‌ای از تکرار شروع می‌شود. برای مثال، افکتی با `iterationStart` برابر با 0.5 و 2 تکرار از نیمه اولین تکرار خود شروع شده و در نیمه یک تکرار سوم پایان می‌یابد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("AnimationEffect")}}