---
title: "Animation: cancel event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/cancel_event"
translated_by: "n8n + AI"
---

---
title: "Animation: cancel event"
short-title: cancel
slug: Web/API/Animation/cancel_event
page-type: web-api-event
browser-compat: api.Animation.cancel_event
---

{{ APIRef("Web Animations") }}

رویداد **`cancel`** از رابط {{domxref("Animation")}} زمانی شلیک می‌شود که متد {{domxref("Animation.cancel()")}} فراخوانی شود یا زمانی که انیمیشن از حالت دیگری وارد وضعیت پخش `"idle"` شود، مانند زمانی که انیمیشن قبل از پایان پخش از یک عنصر حذف می‌شود.

> [!NOTE]
> ساخت یک انیمیشن جدید که در ابتدا در حالت بیکار قرار دارد، رویداد `cancel` را روی انیمیشن جدید فعال نمی‌کند.

## دستور زبان

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("cancel", (event) => { })

oncancel = (event) => { }
```

## نوع رویداد

یک {{domxref("AnimationPlaybackEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("AnimationPlaybackEvent")}}

## مثال‌ها

اگر این انیمیشن لغو شود، عنصر آن را حذف کنید.

```js
animation.oncancel = (event) => {
  animation.effect.target.remove();
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}}