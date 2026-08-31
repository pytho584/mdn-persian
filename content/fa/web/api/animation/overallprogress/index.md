---
title: "Animation: overallProgress property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/overallProgress"
translated_by: "n8n + AI"
---

---
title: "Animation: overallProgress property"
short-title: overallProgress
slug: Web/API/Animation/overallProgress
page-type: web-api-instance-property
browser-compat: api.Animation.overallProgress
---

{{APIRef("Web Animations")}}

ویژگی خواندنی **`overallProgress`** از رابط {{domxref("Animation")}} عددی بین `0` و `1` برمی‌گرداند که پیشرفت کلی انیمیشن را به سمت حالت تکمیل‌شده نشان می‌دهد. این پیشرفت کلی در تمام تکرارهای انیمیشن است، نه هر تکرار به‌تنهایی.

`overallProgress` به‌طور مداوم در تمام انیمیشن‌ها کار می‌کند، صرف‌نظر از نوع {{domxref("AnimationTimeline", "timeline")}}.

## مقدار

عددی بین `0` و `1`، یا `null` اگر انیمیشن فاقد timeline باشد، غیرفعال باشد یا هنوز پخش نشده باشد، یا اگر {{domxref("Animation/currentTime", "currentTime")}} آن روی یک مقدار غیر زمانی تنظیم شده باشد.

اگر ویژگی [`iterations`](/en-US/docs/Web/API/KeyframeEffect/KeyframeEffect#iterations) انیمیشن روی `Infinity` تنظیم شده باشد، یا اگر {{domxref("Animation/currentTime", "currentTime")}} آن روی یک مقدار منفی تنظیم شده باشد، `overallProgress` مقدار `0` برمی‌گرداند.

اگر [`duration`](/en-US/docs/Web/API/KeyframeEffect/KeyframeEffect#duration) انیمیشن روی `0` تنظیم شده باشد، `overallProgress` مقدار `1` برمی‌گرداند.

## مثال‌ها

### نمایش درصد پیشرفت

این نمایش، از `overallProgress` برای ایجاد یک نمایشگر «درصد پیشرفت» استفاده می‌کند که در حین اجرای انیمیشن روی صفحه نمایش داده می‌شود.

### HTML

HTML شامل یک {{htmlelement("button")}} برای فشار دادن و شروع انیمیشن، یک {{htmlelement("p")}} برای نمایش درصد پیشرفت، و یک {{htmlelement("div")}} که قرار است متحرک شود است.

```html
<button>Run animation</button>
<p class="progress">Progress: 0%</p>
<div class="box"></div>
```

CSS این نمایش، استایل‌های اولیه‌ای فراهم می‌کند که برای درک نحوه کار جاوااسکریپت مهم نیستند، بنابراین برای اختصار آن را پنهان کرده‌ایم.

```css hidden
* {
  box-sizing: border-box;
}

html {
  font-family: "Helvetica", "Arial", sans-serif;
}

body {
  width: 500px;
  margin: 0 auto;
  padding: 20px;
}

.progress {
  font-weight: bold;
}

.box {
  width: 100px;
  height: 100px;
  border-radius: 40px 20px;
  border: 10px solid black;
  background: lightseagreen;
  margin: 0 auto;
}
```

### JavaScript

در جاوااسکریپت، ما با گرفتن ارجاع به عناصر {{htmlelement("button")}}، {{htmlelement("p")}} و {{htmlelement("div")}} شروع می‌کنیم.

سپس می‌سازیم:

- یک متغیر `animation` که به انیمیشن اشاره خواهد کرد، پس از ایجاد آن
- یک آرایه [keyframes](/en-US/docs/Web/API/Web_Animations_API/Keyframe_Formats)
- یک شیء options شامل ویژگی‌های زمان‌بندی.

```js
const btn = document.querySelector("button");
const progress = document.querySelector(".progress");
const box = document.querySelector(".box");

let animation;

const keyframes = [{ rotate: "0deg" }, { rotate: "360deg" }];

const timingProps = {
  duration: 3000,
  iterations: 1,
};
```

سپس یک شنونده رویداد `"click"` به `<button>` از طریق [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) اضافه می‌کنیم تا هنگام فشار دادن:

1. انیمیشن را با استفاده از {{domxref("Element.animate()")}} شروع کند، keyframes و گزینه‌های تعریف‌شده قبلی را به آن ارسال کرده و نمونه {{domxref("Animation")}} برگشتی را به متغیر `animation` اختصاص دهد.
2. تابعی به نام `updateProgress()` را از طریق روش {{domxref("Window.requestAnimationFrame", "requestAnimationFrame()")}} اجرا کند که مسئول به‌روزرسانی نمایش درصد پیشرفت است.

```js
btn.addEventListener("click", () => {
  // Animate the box
  animation = box.animate(keyframes, timingProps);
  // Start updating the progress percentage via rAF()
  requestAnimationFrame(updateProgress);
});
```

حالا تابع `updateProgress()` را تعریف می‌کنیم. این تابع {{domxref("Animation.playState")}} را بررسی می‌کند تا ببیند آیا انیمیشن تمام نشده است. اگر تمام نشده باشد، مقدار فعلی `overallProgress` را می‌گیرد، آن را در 100 ضرب می‌کند و نتیجه را به پایین گرد می‌کند تا به یک درصد کامل تبدیل شود، سپس مقدار {{domxref("Node.textContent", "textContent")}} عنصر `<p>` را با آن به‌روزرسانی می‌کند. سپس دوباره `requestAnimationFrame(updateProgress)` را فراخوانی می‌کند تا به‌روزرسانی درصد پیشرفت دوباره اجرا شود.

اگر انیمیشن تمام شده باشد، درصد پیشرفت را با پیام «Finished!» جایگزین می‌کنیم و `requestAnimationFrame(updateProgress)` را فراخوانی نمی‌کنیم، بنابراین به‌روزرسانی درصد پیشرفت متوقف می‌شود.

```js
function updateProgress() {
  // Check if the animation is finished
  if (animation.playState !== "finished") {
    // Convert overallProgress to a whole number percentage
    const progressPercentage = Math.floor(animation.overallProgress * 100);
    // Update the progress paragraph with the percentage
    progress.textContent = `Progress: ${progressPercentage}%`;
    // Only request the next frame if the animation is not finished
    requestAnimationFrame(updateProgress);
  } else {
    progress.textContent = "Finished!";
  }
}
```

### نتیجه

خروجی به این شکل است. دکمه را فشار دهید تا انیمیشن و نشانگر پیشرفت مرتبط با آن را ببینید.

{{ EmbedLiveSample("Displaying a percentage progress", "100%", 250) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Animation")}} برای سایر روش‌ها و ویژگی‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.
- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)