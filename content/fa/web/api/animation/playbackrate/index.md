---
title: "Animation: playbackRate property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/playbackRate"
translated_by: "n8n + AI"
---

---
title: "Animation: playbackRate property"
short-title: playbackRate
slug: Web/API/Animation/playbackRate
page-type: web-api-instance-property
browser-compat: api.Animation.playbackRate
---

{{APIRef("Web Animations")}}

**`Animation.playbackRate`** 属性属于 [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)，用于返回或设置动画的播放速率。

动画具有一个**播放速率**，它提供了一个缩放因子，用于将动画的 {{domxref("DocumentTimeline", "timeline")}} 时间值的变化速率映射到动画的当前时间。播放速率初始为 `1`。

## مقدار

接受一个数字，可以是 0、负数或正数。负值会使动画反向播放。该值是一个缩放因子，例如值为 2 会使播放速率加倍。

> [!NOTE]
> 将动画的 `playbackRate` 设置为 `0` 实际上会暂停动画（但是，其 {{domxref("Animation.playState", "playState")}} 不一定会变为 `paused`）。

## مثال‌ها

در مثال [Growing/Shrinking Alice Game](https://codepen.io/rachelnabors/pen/PNYGZQ?editors=0010)، کلیک یا لمس بطری باعث می‌شود انیمیشن رشد آلیس (`aliceChange`) معکوس شود و او کوچک شود:

```js
const shrinkAlice = () => {
  aliceChange.playbackRate = -1;
  aliceChange.play();
};

// با لمس یا کلیک، آلیس کوچک می‌شود.
bottle.addEventListener("mousedown", shrinkAlice);
bottle.addEventListener("touchstart", shrinkAlice);
```

برعکس، کلیک روی کیک باعث می‌شود او «بزرگ شود» و دوباره `aliceChange` را به جلو اجرا کند:

```js
const growAlice = () => {
  aliceChange.playbackRate = 1;
  aliceChange.play();
};

// با لمس یا کلیک، آلیس بزرگ می‌شود.
cake.addEventListener("mousedown", growAlice);
cake.addEventListener("touchstart", growAlice);
```

در مثال دیگر، [Red Queen's Race Game](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#other_useful_methods)، آلیس و ملکه سرخ مدام کند می‌شوند:

```js
setInterval(() => {
  // مطمئن شوید که نرخ پخش هرگز کمتر از 0.4 نمی‌شود
  if (redQueenAlice.playbackRate > 0.4) {
    redQueenAlice.updatePlaybackRate(redQueenAlice.playbackRate * 0.9);
  }
}, 3000);
```

اما کلیک یا لمس روی آن‌ها باعث می‌شود با ضرب کردن `playbackRate` خود سرعت بگیرند:

```js
const goFaster = () => {
  redQueenAlice.updatePlaybackRate(redQueenAlice.playbackRate * 1.1);
};

document.addEventListener("click", goFaster);
document.addEventListener("touchstart", goFaster);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}