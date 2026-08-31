---
title: "CommandEvent: source property"
short-title: source
slug: Web/API/CommandEvent/source
page-type: web-api-instance-property
browser-compat: api.CommandEvent.source
---

{{APIRef("Invoker Commands API")}}

ویژگی فقط‌خواندنی **`source`** در رابط {{domxref("CommandEvent")}} یک {{domxref("EventTarget")}} برمی‌گرداند که نمایانگر کنترلی است که فرمان داده‌شده را فراخوانی کرده است.

## مقدار

یک شیء {{domxref("EventTarget")}}. معمولاً یک {{domxref("HTMLButtonElement")}}.

## مثال‌ها

در مثال ساده زیر، یک شنونده رویداد تنظیم کرده‌ایم که هنگام یک CommandEvent یک کلاس موقت به عنصر دکمه اضافه می‌کند:

```js
document.body.addEventListener(
  "command",
  (event) => {
    const theButton = event.source;

    theButton.classList.add("just-pressed");

    setTimeout(() => {
      theButton.classList.remove("just-pressed");
    }, 1000);
  },
  { capture: true },
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Invoker Commands API", "Invoker Commands API", "", "nocode")}}
- {{domxref("HTMLButtonElement.command")}}
- {{domxref("HTMLButtonElement.commandForElement")}}