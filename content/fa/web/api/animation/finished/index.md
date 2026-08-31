---
title: "Animation: finished property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/finished"
translated_by: "n8n + AI"
---

---
title: "Animation: finished property"
short-title: finished
slug: Web/API/Animation/finished
page-type: web-api-instance-property
browser-compat: api.Animation.finished
---

{{ APIRef("Web Animations") }}

خاصیت فقط‌خواندنی **`Animation.finished`** در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) یک {{jsxref("Promise")}} برمی‌گرداند که پس از پایان یافتن پخش انیمیشن resolve می‌شود.

> [!NOTE]
> هر بار که انیمیشن از حالت پخش `finished` خارج می‌شود (یعنی دوباره شروع به پخش کند)، یک `Promise` جدید برای این خاصیت ایجاد می‌شود. `Promise` جدید پس از تکمیل توالی جدید انیمیشن resolve خواهد شد.

## مقدار

یک شی {{jsxref("Promise")}} که پس از پایان یافتن پخش انیمیشن resolve می‌شود.

## مثال‌ها

کد زیر منتظر می‌ماند تا همه انیمیشن‌های در حال اجرا روی عنصر `elem` تمام شوند، سپس عنصر را از درخت DOM حذف می‌کند:

```js
Promise.all(elem.getAnimations().map((animation) => animation.finished)).then(
  () => elem.remove(),
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("KeyframeEffect")}}
- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}