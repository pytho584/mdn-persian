---
title: "HTMLElement: command event"
slug: Web/API/HTMLElement/command_event
page-type: web-api-event
browser-compat: api.HTMLElement.command_event
---

{{APIRef("Invoker Commands API")}}

رویداد **`command`** از رابط {{domxref("HTMLElement")}} روی عنصری که توسط یک {{domxref("HTMLButtonElement", "دکمه")}} با مقادیر معتبر {{domxref("HTMLButtonElement.commandForElement", "commandForElement")}} و {{domxref("HTMLButtonElement.command", "command")}} کنترل می‌شود، هر زمان که با دکمه تعامل شود (مثلاً کلیک شود)، فعال می‌گردد.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم یک ویژگی handler رویداد، از روش زیر استفاده کنید.

```js-nolint
addEventListener("command", (event) => { })

oncommand = (event) => { }
```

## نوع رویداد

یک {{domxref("CommandEvent")}} که از {{domxref("Event")}} به ارث برده است.

{{InheritanceDiagram("CommandEvent")}}

## مثال‌ها

### مثال پایه

```js
const popover = document.getElementById("mypopover");

// …

popover.addEventListener("command", (event) => {
  if (event.command === "show-popover") {
    console.log("Popover قرار است نمایش داده شود");
  }
});
```

### ارسال رویداد و لغو آن

نکته قابل توجه این است که رویدادهای `command` روی عنصر فراخوانی‌شده فعال می‌شوند. اگر دکمه کلیک شود، ابتدا یک رویداد `click` ارسال می‌شود که اگر لغو گردد، رویداد `command` فعال نخواهد شد و رفتار پیش‌فرض اجرا نمی‌شود.
علاوه بر لغو رویداد `click` روی دکمه، امکان لغو رویداد `command` نیز وجود دارد.

برای مثال:

```js
button.addEventListener("click", (event) => {
  event.preventDefault(); // رویداد `command` هرگز فعال نخواهد شد
});
```

```js
element.addEventListener("command", (event) => {
  event.preventDefault(); // رویداد `command` فعال می‌شود اما رفتار پیش‌فرض لغو می‌گردد
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Invoker Commands API", "Invoker Commands API", "", "nocode")}}
- {{domxref("HTMLButtonElement.command")}}
- {{domxref("HTMLButtonElement.commandForElement")}}