---
title: "Animation: cancel() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/cancel"
translated_by: "n8n + AI"
---

---
title: "Animation: cancel() method"
short-title: cancel()
slug: Web/API/Animation/cancel
page-type: web-api-instance-method
browser-compat: api.Animation.cancel
---

{{ APIRef("Web Animations") }}

متد **`cancel()`** از [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) در رابط {{domxref("Animation")}}، تمام {{domxref("KeyframeEffect")}}هایی را که توسط این انیمیشن ایجاد شده‌اند پاک می‌کند و پخش آن را متوقف می‌کند.

> [!NOTE]
> هنگامی که یک انیمیشن لغو می‌شود، {{domxref("Animation.startTime", "startTime")}} و {{domxref("Animation.currentTime", "currentTime")}} آن به `null` تنظیم می‌شوند.

## نحو (Syntax)

```js-nolint
cancel()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

این متد به طور مستقیم استثنا پرتاب نمی‌کند؛ با این حال، اگر {{domxref("Animation.playState", "playState")}} انیمیشن در هنگام لغو چیزی غیر از `"idle"` باشد، {{domxref("Animation.finished", "پرامیس پایان فعلی", "", 1)}} با یک {{domxref("DOMException")}} به نام `AbortError` رد می‌شود.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("KeyframeEffect")}}
- {{domxref("Animation")}}
- {{domxref("Animation.playState")}}
- {{domxref("Animation.finished")}} پرامیس را برمی‌گرداند که اگر `playState` انیمیشن `"idle"` نباشد، این عمل آن را رد خواهد کرد.