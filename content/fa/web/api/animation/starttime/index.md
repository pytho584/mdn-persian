```
---
title: "Animation: startTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/startTime"
translated_by: "n8n + AI"
---

---
title: "Animation: startTime property"
short-title: startTime
slug: Web/API/Animation/startTime
page-type: web-api-instance-property
browser-compat: api.Animation.startTime
---

{{ APIRef("Web Animations") }}

ویژگی **`Animation.startTime`** در رابط {{domxref("Animation")}} یک مقدار اعشاری با دقت دوبرابر است که زمان برنامه‌ریزی‌شده‌ی آغاز پخش یک انیمیشن را نشان می‌دهد.

**زمان شروع** یک انیمیشن، مقدار زمانی {{domxref("DocumentTimeline","timeline")}} آن است که {{domxref("KeyframeEffect")}} هدف آن قرار است پخش را آغاز کند. **زمان شروع** یک انیمیشن در ابتدا تعیین‌نشده است (یعنی `null` است چون مقداری ندارد).

## مقدار

یک عدد اعشاری که زمان فعلی را بر حسب میلی‌ثانیه نشان می‌دهد، یا اگر زمانی تنظیم نشده باشد، `null` است. می‌توانید این مقدار را بخوانید تا بفهمید زمان شروع در حال حاضر روی چه مقداری تنظیم شده است، و می‌توانید این مقدار را تغییر دهید تا انیمیشن در زمان دیگری شروع شود.

## مثال‌ها

### همگام‌سازی انیمیشن‌های مختلف

در مثال زیر، می‌توانیم همه‌ی گربه‌های متحرک جدید را با دادن `startTime` یکسان با گربه‌ی در حال اجرای اصلی، همگام‌سازی کنیم. توجه داشته باشید که این کار فقط با Web Animation API امکان‌پذیر است: همگام‌سازی دو انیمیشن جداگانه با انیمیشن‌های CSS غیرممکن است.

```html hidden
<div id="css-cats">
  <h2>Cats animated with<br />CSS Animations</h2>
  <div class="cat with-css"></div>
  <button id="insert-css-cat">Add a Cat</button>
</div>

<div id="waapi-cats">
  <h2>Cats animated with the<br />Web Animation API</h2>
  <div class="cat" id="with-waapi"></div>
  <button id="insert-waapi-cat">Add a Cat</button>
</div>
```

```css
/* All cats have the same dimensions and the same sprite for a background image. */
.cat {
  background: url("/shared-assets/images/examples/web-animations/cat_sprite.png") -600px
    0 no-repeat;
  height: 150px;
  width: 100%;
}

/* The cats animated with CSS have their running animations set with CSS */
.cat.with-css {
  animation: 0.75s steps(13, end) infinite run-cycle;
}

/*
  The keyframes for the CSS running animation.
  This moves the background image sprite around.
*/
@keyframes run-cycle {
  from {
    background-position: -600px 0;
  }
  to {
    background-position: -600px -1950px;
  }
}
```

```css hidden
#css-cats,
#waapi-cats {
  text-align: center;
  vertical-align: top;
  min-width: 300px;
}

body {
  background: #e5e6e9;
  color: #071933;
  font-family: sans-serif;
  display: flex;
  flex-wrap: wrap;
}
```

```js
const cssCats = document.getElementById("css-cats");
const waapiCats = document.getElementById("waapi-cats");
const insertCSSCat = document.getElementById("insert-css-cat");
const insertWAAPICat = document.getElementById("insert-waapi-cat");

// The same information as @keyframes run-cycle
const keyframes = [
  { backgroundPosition: "-600px 0" },
  { backgroundPosition: "-600px -1950px" },
];
// The same information as .cat.with-css
const timing = {
  duration: 750,
  iterations: Infinity,
  easing: "steps(13, end)",
};

const catRunning = document
  .getElementById("with-waapi")
  .animate(keyframes, timing);

function createCat() {
  const newCat = document.createElement("div");
  newCat.classList.add("cat");
  return newCat;
}

insertCSSCat.addEventListener("click", () => {
  const newCat = createCat();
  newCat.classList.add("with-css");
  cssCats.insertBefore(newCat, insertCSSCat);
});

insertWAAPICat.addEventListener("click", () => {
  const newCat = createCat();
  const newAnimationPlayer = newCat.animate(keyframes, timing);
  // set start time to be the same as the original .cat#with-waapi
  newAnimationPlayer.startTime = catRunning.startTime;
  waapiCats.insertBefore(newCat, insertWAAPICat);
});
```

{{EmbedLiveSample("Syncing different animations", "", 600)}}

## کاهش دقت زمان

برای محافظت در برابر حملات زمان‌بندی و [اثر انگشت](/en-US/docs/Glossary/Fingerprinting)، دقت `animation.startTime` ممکن است بسته به تنظیمات مرورگر گرد شود. در فایرفاکس، تنظیم `privacy.reduceTimerPrecision` به‌طور پیش‌فرض فعال است و به‌طور پیش‌فرض 2 میلی‌ثانیه است. همچنین می‌توانید `privacy.resistFingerprinting` را فعال کنید، که در این صورت دقت برابر با 100 میلی‌ثانیه یا مقدار `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`، هر کدام بزرگ‌تر باشد، خواهد بود.

برای مثال، با کاهش دقت زمان، نتیجه‌ی `animation.startTime` همیشه مضربی از 0.002 خواهد بود، یا با فعال بودن `privacy.resistFingerprinting` مضربی از 0.1 (یا `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`).

```js
// reduced time precision (2ms) in Firefox 60
animation.startTime;
// Might be:
// 23.404
// 24.192
// 25.514
// …

// reduced time precision with `privacy.resistFingerprinting` enabled
animation.startTime;
// Might be:
// 49.8
// 50.6
// 51.7
// …
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}
- {{domxref("Animation.currentTime")}} برای زمان جاری انیمیشن.
```