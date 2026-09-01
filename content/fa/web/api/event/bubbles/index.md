---
title: "Event: bubbles property"
short-title: bubbles
slug: Web/API/Event/bubbles
page-type: web-api-instance-property
browser-compat: api.Event.bubbles
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

خاصیت فقط-خواندنی **`bubbles`** از رابط {{domxref("Event")}} مشخص می‌کند که آیا رویداد در درخت DOM به بالا منتشر می‌شود یا خیر.

> [!NOTE]
> برای اطلاعات بیشتر درباره انتشار رویداد به بالا، به [حباب زدن رویداد](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) مراجعه کنید.

## مقدار

یک مقدار بولی که اگر رویداد در درخت DOM به بالا منتشر شود، `true` است.

## مثال

```js
function handleInput(e) {
  // Check whether the event bubbles passes the event along
  if (!e.bubbles) {
    passItOn(e);
  }

  // Already bubbling
  doOutput(e);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Event.stopPropagation", "stopPropagation()")}} برای جلوگیری از انتشار بیشتر رویداد جاری در فازهای ثبت و حباب
- {{domxref("Event.stopImmediatePropagation", "stopImmediatePropagation()")}} برای فراخوانی نکردن هیچ شنونده دیگری برای همان رویداد در همان سطح از DOM
- {{domxref("Event.preventDefault", "preventDefault()")}} برای اجازه دادن به ادامه انتشار اما جلوگیری از انجام عمل پیش‌فرض مرورگر در صورتی که هیچ شنونده‌ای رویداد را مدیریت نکند