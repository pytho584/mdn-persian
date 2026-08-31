---
title: "Animation: finish event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/finish_event"
translated_by: "n8n + AI"
---

---
title: "Animation: finish event"
short-title: finish
slug: Web/API/Animation/finish_event
page-type: web-api-event
browser-compat: api.Animation.finish_event
---

{{ APIRef("Web Animations") }}

رویداد **`finish`** از رابط {{domxref("Animation")}} زمانی پرتاب می‌شود که انیمیشن پخش را به پایان می‌رساند؛ چه زمانی که انیمیشن به‌طور طبیعی کامل شود و چه زمانی که متد {{domxref("Animation.finish()")}} برای پایان دادنِ فوری به انیمیشن فراخوانده شود.

> [!NOTE]
> وضعیت پخش `"paused"` بر وضعیت پخش `"finished"` برتری دارد؛ اگر انیمیشن هم مکث‌شده و هم تمام‌شده باشد، وضعیت `"paused"` گزارش داده می‌شود. می‌توانید با تنظیم {{domxref("Animation.startTime", "startTime")}} به `document.timeline.currentTime - (Animation.currentTime * Animation.playbackRate)` انیمیشن را به حالت `"finished"` وادار کنید.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("finish", (event) => { })

onfinish = (event) => { }
```

## نوع رویداد

یک {{domxref("AnimationPlaybackEvent")}}. به ارث‌رفته از {{domxref("Event")}}.

{{InheritanceDiagram("AnimationPlaybackEvent")}}

## مثال‌ها

`Animation.onfinish` چندین بار در [Growing/Shrinking Alice Game](https://codepen.io/rachelnabors/pen/PNYGZQ?editors=0010) در سرزمین Web Animations API استفاده شده است. در اینجا یک نمونه آورده شده است که در آن رویدادهای اشاره‌گر را پس از اینکه انیمیشن شفافیت، عنصر را به‌تدریج نمایان کرده است، دوباره به عنصر اضافه می‌کنیم:

```js
// Add an animation to the game's ending credits
const endingUI = document.getElementById("ending-ui");
const bringUI = endingUI.animate(keysFade, timingFade);

// Pause said animation's credits
bringUI.pause();

// This function removes pointer events on the credits.
hide(endingUI);

// When the credits are later faded in,
// we re-add the pointer events when they're done
bringUI.onfinish = (event) => {
  endingUI.style.pointerEvents = "auto";
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}
- {{domxref("Animation.finish()")}}