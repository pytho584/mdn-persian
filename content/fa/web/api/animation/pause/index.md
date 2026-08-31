---
title: "Animation: pause() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/pause"
translated_by: "n8n + AI"
---

---
title: "Animation: pause() method"
short-title: pause()
slug: Web/API/Animation/pause
page-type: web-api-instance-method
browser-compat: api.Animation.pause
---

{{ APIRef("Web Animations") }}

**`pause()`** متد رابط {{domxref("Animation")}} در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) پخش انیمیشن را به حالت تعلیق درمی‌آورد.

## نحو

```js-nolint
pause()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Animation.currentTime", "currentTime")}} انیمیشن `unresolved` باشد (شاید هنوز پخش شروع نشده است) و زمان پایان انیمیشن بی‌نهایت مثبت باشد، پرتاب می‌شود.

## مثال

`Animation.pause()` در بازی [Growing/Shrinking Alice Game](https://codepen.io/rachelnabors/pen/PNYGZQ?editors=0010) در Alice in Web Animations API Land چندین بار استفاده شده است، عمدتاً به این دلیل که انیمیشن‌های ایجاد شده با روش {{domxref("Element.animate()")}} بلافاصله پخش را شروع می‌کنند و اگر بخواهید از آن اجتناب کنید، باید به صورت دستی متوقف (pause) شوند.

```js
// animation of the cupcake slowly getting eaten up
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

// doesn't actually need to be eaten until a click event, so pause it initially:
nommingCake.pause();
```

علاوه بر این، هنگام بازنشانی:

```js
// An all-purpose function to pause the animations on Alice, the cupcake, and the bottle that reads "drink me."
const stopPlayingAlice = () => {
  aliceChange.pause();
  nommingCake.pause();
  drinking.pause();
};

// When the user releases the cupcake or the bottle, pause the animations.
cake.addEventListener("mouseup", stopPlayingAlice);
bottle.addEventListener("mouseup", stopPlayingAlice);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}} برای سایر روش‌ها و ویژگی‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.
- {{domxref("Animation.reverse()")}} برای پخش معکوس یک انیمیشن.
- {{domxref("Animation.finish()")}} برای پایان دادن به یک انیمیشن.
- {{domxref("Animation.cancel()")}} برای لغو یک انیمیشن.