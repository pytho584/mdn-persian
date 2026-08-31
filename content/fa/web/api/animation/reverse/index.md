---
title: "Animation: reverse() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/reverse"
translated_by: "n8n + AI"
---

---
title: "Animation: reverse() method"
short-title: reverse()
slug: Web/API/Animation/reverse
page-type: web-api-instance-method
browser-compat: api.Animation.reverse
---

{{APIRef("Web Animations")}}

متد **`Animation.reverse()`** از رابط {{ domxref("Animation") }} جهت پخش را معکوس می‌کند، به این معنی که انیمیشن در نقطه شروع خود به پایان می‌رسد. اگر بر روی یک انیمیشن اجرا نشده فراخوانی شود، کل انیمیشن به سمت عقب پخش می‌شود. اگر بر روی یک انیمیشن متوقف شده فراخوانی شود، انیمیشن به صورت معکوس ادامه می‌یابد.

## Syntax

```js-nolint
reverse()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در مثال [بازی آلیس در حال رشد/کوچک شدن](https://codepen.io/rachelnabors/pen/PNYGZQ?editors=0010)، کلیک یا ضربه زدن بر روی بطری باعث می‌شود انیمیشن رشد آلیس (`aliceChange`) به سمت عقب پخش شده و او کوچک‌تر شود. این کار با تنظیم {{ domxref("Animation.playbackRate") }} متعلق به `aliceChange` به `-1` انجام می‌شود، به این صورت:

```js
const shrinkAlice = () => {
  // play Alice's animation in reverse
  aliceChange.playbackRate = -1;
  aliceChange.play();

  // play the bottle's animation
  drinking.play();
};
```

اما می‌توانست با فراخوانی `reverse()` بر روی `aliceChange` نیز انجام شود، به این صورت:

```js
const shrinkAlice = () => {
  // play Alice's animation in reverse
  aliceChange.reverse();

  // play the bottle's animation
  drinking.play();
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}} برای سایر روش‌ها و ویژگی‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.
- {{domxref("Animation.pause()")}} برای توقف یک انیمیشن.
- {{domxref("Animation.play()")}} برای حرکت رو به جلوی یک انیمیشن.