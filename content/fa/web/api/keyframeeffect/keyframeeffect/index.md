---
title: "KeyframeEffect: KeyframeEffect() constructor"
short-title: KeyframeEffect()
slug: Web/API/KeyframeEffect/KeyframeEffect
page-type: web-api-constructor
browser-compat: api.KeyframeEffect.KeyframeEffect
---

{{ APIRef("Web Animations") }}

سازنده **`KeyframeEffect()`** از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) یک نمونه جدید از شیء {{domxref("KeyframeEffect")}} را برمی‌گرداند و همچنین به شما امکان می‌دهد که یک نمونه شیء اثر کلیدفریم موجود را کلون کنید.

## نحو

```js-nolint
new KeyframeEffect(target, keyframes)
new KeyframeEffect(target, keyframes, options)
new KeyframeEffect(sourceKeyFrames)
```

### پارامترها

سازنده چند-آرگومانی (در بالا ببینید) یک نمونه شیء کاملاً جدید از {{domxref("KeyframeEffect")}} ایجاد می‌کند. پارامترهای آن عبارتند از:

- `target`
  - : عنصر DOM که باید متحرک شود، یا `null`.
- `keyframes`
  - : یک [شیء کلیدفریم](/en-US/docs/Web/API/Web_Animations_API/Keyframe_Formats) یا `null`.
- `options` {{optional_inline}}
  - : یا یک عدد صحیح که نشان‌دهنده طول مدت انیمیشن (به میلی‌ثانیه) است، یا یک شیء حاوی یک یا چند مورد از موارد زیر:
    - `delay` {{optional_inline}}
      - : تعداد میلی‌ثانیه‌ای که شروع انیمیشن را به تأخیر می‌اندازد. پیش‌فرض 0.
    - `direction` {{optional_inline}}
      - : آیا انیمیشن به جلو اجرا می‌شود (`normal`)، به عقب (`reverse`)، بعد از هر تکرار جهت را عوض می‌کند (`alternate`)، یا به عقب اجرا می‌شود و بعد از هر تکرار جهت را عوض می‌کند (`alternate-reverse`). پیش‌فرض `"normal"`.
    - `duration` {{optional_inline}}
      - : تعداد میلی‌ثانیه‌ای که هر تکرار انیمیشن برای تکمیل شدن طول می‌کشد. پیش‌فرض 0. اگرچه از نظر فنی اختیاری است، به خاطر داشته باشید که اگر این مقدار 0 باشد، انیمیشن شما اجرا نخواهد شد.
    - `easing` {{optional_inline}}
      - : نرخ تغییر انیمیشن در طول زمان. یک {{cssxref("easing-function")}} مانند `"linear"`، `"ease-in"`، `"step-end"` یا `"cubic-bezier(0.42, 0, 0.58, 1)"` را می‌پذیرد. پیش‌فرض `"linear"`.
    - `endDelay` {{optional_inline}}
      - : تعداد میلی‌ثانیه‌ای که بعد از پایان یک انیمیشن به تأخیر می‌اندازد. این عمدتاً در زمان توالی‌بندی انیمیشن‌ها بر اساس زمان پایان یک انیمیشن دیگر مفید است. پیش‌فرض 0.
    - `fill` {{optional_inline}}
      - : تعیین می‌کند که آیا اثرات انیمیشن باید قبل از پخش توسط عنصر(ها) منعکس شود (`"backwards"`)، بعد از اتمام پخش انیمیشن حفظ شود (`"forwards"`)، یا `both`. پیش‌فرض `"none"`.
    - `iterationStart` {{optional_inline}}
      - : نقطه شروع انیمیشن در تکرار را توصیف می‌کند. برای مثال 0.5 نشان‌دهنده شروع از نیمه اولین تکرار است، و با تنظیم این مقدار، یک انیمیشن با 2 تکرار در نیمه یک تکرار سوم به پایان می‌رسد. پیش‌فرض 0.0.
    - `iterations` {{optional_inline}}
      - : تعداد دفعاتی که انیمیشن باید تکرار شود. پیش‌فرض `1` است، و همچنین می‌تواند مقدار {{jsxref("Infinity")}} را بگیرد تا تا زمانی که عنصر وجود دارد تکرار شود.
    - `composite` {{optional_inline}}
      - : تعیین می‌کند که چگونه مقادیر بین این انیمیشن و سایر انیمیشن‌های جداگانه‌ای که عملیات ترکیب خاص خود را مشخص نمی‌کنند، ترکیب شوند. پیش‌فرض `replace`.
        - `add` یک اثر افزایشی را تعیین می‌کند، جایی که هر تکرار متوالی بر روی تکرار قبلی بنا می‌شود. به عنوان مثال با `transform`، یک `translateX(-200px)` مقدار قبلی `rotate(20deg)` را بازنویسی نمی‌کند بلکه نتیجه `translateX(-200px) rotate(20deg)` می‌شود.
        - `accumulate` مشابه است اما کمی هوشمندتر: `blur(2)` و `blur(5)` به `blur(7)` تبدیل می‌شوند، نه `blur(2) blur(5)`.
        - `replace` مقدار قبلی را با مقدار جدید جایگزین می‌کند.

    - `iterationComposite` {{optional_inline}}
      - : تعیین می‌کند که چگونه مقادیر از تکرار به تکرار در این انیمیشن ساخته می‌شوند. می‌تواند به `accumulate` یا `replace` تنظیم شود (در بالا ببینید). پیش‌فرض `replace`.
    - `pseudoElement` {{optional_inline}}
      - : یک `string` حاوی یک انتخابگر {{cssxref("pseudo-elements","pseudo-element")}} مانند `"::before"`. اگر وجود داشته باشد، اثر به جای خود `target` به شبه‌عنصر انتخاب شده از `target` اعمال می‌شود.

سازنده تک-آرگومانی (در بالا ببینید) یک کلون از یک نمونه شیء {{domxref("KeyframeEffect")}} موجود ایجاد می‌کند. پارامتر آن به شرح زیر است:

- `sourceKeyFrames`
  - : یک شیء {{domxref("KeyframeEffect")}} که می‌خواهید آن را کلون کنید.

## مثال‌ها

در مثال زیر، از سازنده KeyframeEffect برای ایجاد مجموعه‌ای از کلیدفریم‌ها استفاده شده است که نحوه غلتیدن ایموجی روی زمین را تعیین می‌کند:

```js
const emoji = document.querySelector("div"); // element to animate

const rollingKeyframes = new KeyframeEffect(
  emoji,
  [
    { transform: "translateX(0) rotate(0)" }, // keyframe
    { transform: "translateX(200px) rotate(1.3turn)" }, // keyframe
  ],
  {
    // keyframe options
    duration: 2000,
    direction: "alternate",
    easing: "ease-in-out",
    iterations: "Infinity",
  },
);

const rollingAnimation = new Animation(rollingKeyframes, document.timeline);
rollingAnimation.play();
```

```html
<div>🤣</div>
```

```css hidden
body {
  box-shadow: 0 5px 5px pink;
}

div {
  width: fit-content;
  margin-left: calc(50% - 132px);
  font-size: 64px;
  user-select: none;
  margin-top: 1rem;
}
```

{{ EmbedLiveSample("Examples", "100%", "120") }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [رابط KeyframeEffect](/en-US/docs/Web/API/KeyframeEffect)
- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}