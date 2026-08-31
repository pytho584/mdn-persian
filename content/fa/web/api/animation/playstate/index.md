---
title: "Animation: playState property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/playState"
translated_by: "n8n + AI"
---

---
title: "Animation: playState property"
short-title: playState
slug: Web/API/Animation/playState
page-type: web-api-instance-property
browser-compat: api.Animation.playState
---

{{APIRef("Web Animations")}}

خاصیت فقط خواندنی **`Animation.playState`** از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) یک مقدار شمارشی را برمی‌گرداند که وضعیت پخش یک انیمیشن را توصیف می‌کند.

## مقدار

- `idle`
  - : زمان جاری انیمیشن نامشخص است و هیچ کار در انتظاری وجود ندارد.
- `running`
  - : انیمیشن در حال اجراست.
- `paused`
  - : انیمیشن متوقف شده است و خاصیت {{domxref("Animation.currentTime")}} به‌روز نمی‌شود.
- `finished`
  - : انیمیشن به یکی از مرزهای خود رسیده است و خاصیت {{domxref("Animation.currentTime")}} به‌روز نمی‌شود.

پیشتر، Web Animations یک مقدار **`pending`** را تعریف کرده بود برای نشان دادن اینکه برخی عملیات ناهمگام مانند شروع پخش هنوز کامل نشده است. اکنون این با خاصیت جداگانه {{domxref("Animation.pending")}} نشان داده می‌شود.

## مثال‌ها

در مثال [بازی رشد/کوچک شدن آلیس](https://codepen.io/rachelnabors/pen/PNYGZQ?editors=0010)، بازیکنان می‌توانند به پایانی برسند که [آلیس در یک استخر اشک گریه می‌کند](https://codepen.io/rachelnabors/pen/EPJdJx?editors=0010). در بازی، به دلایل عملکرد، اشک‌ها فقط زمانی باید متحرک شوند که قابل مشاهده هستند. بنابراین به محض اینکه متحرک شدند باید متوقف شوند مانند زیر:

```js
// Setting up the tear animations

tears.forEach((el) => {
  el.animate(tearsFalling, {
    delay: getRandomMsRange(-1000, 1000), // randomized for each tear
    duration: getRandomMsRange(2000, 6000), // randomized for each tear
    iterations: Infinity,
    easing: "cubic-bezier(0.6, 0.04, 0.98, 0.335)",
  });
  el.pause();
});

// Play the tears falling when the ending needs to be shown.

tears.forEach((el) => {
  el.play();
});

// Reset the crying tears animations and pause them.

tears.forEach((el) => {
  el.pause();
  el.currentTime = 0;
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}} برای سایر متدها و خاصیت‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.