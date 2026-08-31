---
title: "Animation: play() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/play"
translated_by: "n8n + AI"
---

---
title: "Animation: play() method"
short-title: play()
slug: Web/API/Animation/play
page-type: web-api-instance-method
browser-compat: api.Animation.play
---

{{ APIRef("Web Animations") }}

**`play()`** روشی از رابط {{ domxref("Animation") }} در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) است که پخش یک انیمیشن را شروع یا از سر می‌گیرد. اگر انیمیشن به پایان رسیده باشد، فراخوانی `play()` انیمیشن را دوباره راه‌اندازی کرده و آن را از ابتدا پخش می‌کند.

## نحو

```js-nolint
play()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در مثال [بازی رشد/کوچک‌شدن آلیس](https://codepen.io/rachelnabors/pen/PNYGZQ?editors=0010)، کلیک یا لمس کیک باعث می‌شود انیمیشن رشد آلیس (`aliceChange`) به جلو پخش شود و او بزرگ‌تر شود، همچنین انیمیشن کیک نیز فعال می‌شود. دو `Animation.play()`، یک `EventListener`:

```js
// The cake has its own animation:
const nommingCake = document
  .getElementById("eat-me_sprite")
  .animate(
    [{ transform: "translateY(0)" }, { transform: "translateY(-80%)" }],
    {
      fill: "forwards",
      easing: "steps(4, end)",
      duration: aliceChange.effect.timing.duration / 2,
    },
  );

// Pause the cake's animation so it doesn't play immediately.
nommingCake.pause();

// This function will play when ever a user clicks or taps
const growAlice = () => {
  // Play Alice's animation.
  aliceChange.play();

  // Play the cake's animation.
  nommingCake.play();
};

// When a user holds their mouse down or taps, call growAlice to make all the animations play.
cake.addEventListener("mousedown", growAlice);
cake.addEventListener("touchstart", growAlice);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}} برای سایر روش‌ها و ویژگی‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.
- {{domxref("Animation.pause()")}} برای توقف موقت یک انیمیشن.
- {{domxref("Animation.reverse()")}} برای پخش معکوس یک انیمیشن.
- {{domxref("Animation.finish()")}} برای پایان دادن به یک انیمیشن.
- {{domxref("Animation.cancel()")}} برای لغو یک انیمیشن.