---
title: "Animation: ready property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/ready"
translated_by: "n8n + AI"
---

---
title: "Animation: ready property"
short-title: ready
slug: Web/API/Animation/ready
page-type: web-api-instance-property
browser-compat: api.Animation.ready
---

{{ APIRef("Web Animations") }}

ویژگی فقط‌خواندنی **`Animation.ready`** در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) یک {{jsxref("Promise")}} برمی‌گرداند که وقتی انیمیشن آمادهٔ پخش باشد resolved می‌شود. یک promise جدید هر بار که انیمیشن وارد وضعیت `"pending"` [play state](/en-US/docs/Web/API/Animation/playState) می‌شود و همچنین زمانی که انیمیشن لغو می‌شود ساخته می‌شود، زیرا در هر دوی این حالت‌ها، انیمیشن آماده است تا دوباره شروع شود.

> [!NOTE]
> از آنجا که از همان {{jsxref("Promise")}} برای هر دو درخواست در انتظار `play` و در انتظار `pause` استفاده می‌شود، به نویسندگان توصیه می‌شود هنگام resolved شدن promise وضعیت انیمیشن را بررسی کنند.

## مقدار

یک {{jsxref("Promise")}} که وقتی انیمیشن آمادهٔ پخش باشد resolved می‌شود. معمولاً هنگام استفاده از promise آماده، از ساختاری مشابه این استفاده می‌کنید:

```js
animation.ready.then(() => {
  // Do whatever needs to be done when
  // the animation is ready to run
});
```

## مثال‌ها

در مثال زیر، وضعیت انیمیشن زمانی که **Promise آمادهٔ فعلی** resolved شود، `running` خواهد بود، زیرا انیمیشن بین فراخوانی‌های `pause` و `play` حالت `pending` را ترک نمی‌کند و بنابراین **Promise آمادهٔ فعلی** تغییر نمی‌کند.

```js
animation.pause();
animation.ready.then(() => {
  // Displays 'running'
  alert(animation.playState);
});
animation.play();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}
- {{domxref("Animation.playState")}}