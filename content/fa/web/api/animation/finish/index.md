---
title: "Animation: finish() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/finish"
translated_by: "n8n + AI"
---

{{APIRef("Web Animations")}}

متد **`finish()`** در رابط {{domxref("Animation")}} در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)، زمان پخش فعلی را به پایان انیمیشن، متناسب با جهت پخش فعلی، تنظیم می‌کند.

به عبارت دیگر، اگر انیمیشن در حال پخش به جلو باشد، زمان پخش را به طول توالی انیمیشن تنظیم می‌کند و اگر انیمیشن در حال پخش معکوس باشد (با فراخوانی متد {{domxref("Animation.reverse", "reverse()")}})، زمان پخش را روی ۰ تنظیم می‌کند.

## نحو

```js-nolint
finish()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidState`
  - : نرخ پخش پخش‌کننده ۰ باشد یا نرخ پخش انیمیشن بزرگ‌تر از ۰ باشد و زمان پایان انیمیشن بی‌نهایت باشد.

## مثال‌ها

مثال زیر نحوه استفاده از متد `finish()` و مدیریت خطای `InvalidState` را نشان می‌دهد.

```js
interfaceElement.addEventListener("mousedown", () => {
  try {
    player.finish();
  } catch (e) {
    if (e instanceof InvalidState) {
      console.log("finish() called on paused or finished animation.");
    } else {
      logMyErrors(e); // Pass exception object to error handler
    }
  }
});
```

مثال زیر تمام انیمیشن‌های یک عنصر را بدون توجه به جهت پخش آن‌ها به پایان می‌برد.

```js
elem.getAnimations().forEach((animation) => animation.finish());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}} برای سایر متدها و ویژگی‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.
- {{domxref("Animation.play()")}} برای پخش انیمیشن به جلو.
- {{domxref("Animation.reverse()")}} برای پخش انیمیشن به عقب.