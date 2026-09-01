---
title: "Element: focus event"
short-title: focus
slug: Web/API/Element/focus_event
page-type: web-api-event
browser-compat: api.Element.focus_event
---

{{APIRef("UI Events")}}

رویداد **`focus`** زمانی رخ می‌دهد که یک عنصر (element) فوکوس (focus) دریافت کرده باشد. این رویداد به بالا انتشار نمی‌یابد (bubble)، اما رویداد مرتبط {{domxref("Element/focusin_event", "focusin")}} که پس از آن می‌آید، به بالا انتشار می‌یابد.

مقابل رویداد `focus`، رویداد {{domxref("Element/blur_event", "blur")}} است که زمانی رخ می‌دهد که عنصر فوکوس خود را _از دست داده_ باشد.

رویداد `focus` قابل لغو (cancelable) نیست.

## دستور زبان

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("focus", (event) => { })

onfocus = (event) => { }
```

## نوع رویداد

یک {{domxref("FocusEvent")}} که از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث برده است.

{{InheritanceDiagram("FocusEvent")}}

## مثال‌ها

### مثال ساده

#### HTML

```html
<form id="form">
  <label>
    مقداری متن:
    <input type="text" placeholder="ورودی متن" />
  </label>
  <label>
    رمز عبور:
    <input type="password" placeholder="رمز عبور" />
  </label>
</form>
```

#### JavaScript

```js
const password = document.querySelector('input[type="password"]');

password.addEventListener("focus", (event) => {
  event.target.style.background = "pink";
});

password.addEventListener("blur", (event) => {
  event.target.style.background = "";
});
```

#### نتیجه

{{EmbedLiveSample("Simple_example", '100%', '50px')}}

### واگذاری رویداد (Event delegation)

دو روش برای پیاده‌سازی واگذاری رویداد برای این رویداد وجود دارد: با استفاده از رویداد {{domxref("Element/focusin_event", "focusin")}}، یا با تنظیم پارامتر `useCapture` در {{domxref("EventTarget.addEventListener()", "addEventListener()")}} به `true`.

#### HTML

```html
<form id="form">
  <label>
    مقداری متن:
    <input type="text" placeholder="ورودی متن" />
  </label>
  <label>
    رمز عبور:
    <input type="password" placeholder="رمز عبور" />
  </label>
</form>
```

#### JavaScript

```js
const form = document.getElementById("form");

form.addEventListener(
  "focus",
  (event) => {
    event.target.style.background = "pink";
  },
  true,
);

form.addEventListener(
  "blur",
  (event) => {
    event.target.style.background = "";
  },
  true,
);
```

#### نتیجه

{{EmbedLiveSample("Event_delegation", '100%', '50px')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- روش {{domxref("HTMLElement.focus()")}}
- رویدادهای مرتبط: {{domxref("Element/blur_event", "blur")}}، {{domxref("Element/focusin_event", "focusin")}}، {{domxref("Element/focusout_event", "focusout")}}
- این رویداد در اهداف `Window`: رویداد {{domxref("Window/focus_event", "focus")}}
- [فوکوس کردن: focus/blur](https://javascript.info/focus-blur)