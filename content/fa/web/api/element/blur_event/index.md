---
title: "Element: blur event"
short-title: blur
slug: Web/API/Element/blur_event
page-type: web-api-event
browser-compat: api.Element.blur_event
---

{{APIRef("UI Events")}}

رویداد **`blur`** زمانی فعال می‌شود که یک عنصر focus (تمرکز) خود را از دست بدهد. این رویداد به بیرون انتشار نمی‌یابد (bubble نمی‌کند)، اما رویداد مرتبط {{domxref("Element/focusout_event", "focusout")}} که پس از آن رخ می‌دهد، انتشار می‌یابد.

یک عنصر در صورتی focus خود را از دست می‌دهد که عنصر دیگری انتخاب شود. همچنین اگر سبکی که اجازه focus نمی‌دهد اعمال شود، مانند `hidden`، یا اگر عنصر از سند حذف شود، عنصر focus خود را از دست می‌دهد — در هر دو مورد focus به عنصر `body` (viewport) منتقل می‌شود. توجه داشته باشید که رفتار مرورگرها هنگام حذف یک عنصر متمرکز متفاوت است. در مرورگرهای مبتنی بر Chromium، حذف یک عنصر متمرکز باعث فعال شدن رویداد `blur` می‌شود، در حالی که در Firefox این اتفاق نمی‌افتد.

<!-- Prior to FF110 elements did not lose focus if the style changed to hidden (say) -->

مخالف `blur` رویداد {{domxref("Element/focus_event", "focus")}} است که زمانی فعال می‌شود که عنصر focus را _دریافت_ کرده است.

رویداد `blur` قابل لغو (cancel) نیست.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("blur", (event) => { })

onblur = (event) => { }
```

## Event type

یک {{domxref("FocusEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("FocusEvent")}}

## Examples

### Simple example

#### HTML

```html
<form id="form">
  <label>
    Some text:
    <input type="text" placeholder="text input" />
  </label>
  <label>
    Password:
    <input type="password" placeholder="password" />
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

#### Result

{{EmbedLiveSample("Simple_example", '100%', '50px')}}

### Event delegation

دو روش برای پیاده‌سازی واگذاری رویداد (event delegation) برای این رویداد وجود دارد: با استفاده از رویداد {{domxref("Element/focusout_event", "focusout")}}، یا با تنظیم پارامتر `useCapture` در {{domxref("EventTarget.addEventListener()", "addEventListener()")}} روی `true`.

#### HTML

```html
<form id="form">
  <label>
    Some text:
    <input type="text" placeholder="text input" />
  </label>
  <label>
    Password:
    <input type="password" placeholder="password" />
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

#### Result

{{EmbedLiveSample("Event_delegation", '100%', '50px')}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

مقدار {{DOMxRef("Document.activeElement")}} در مرورگرهای مختلف در هنگام پردازش این رویداد متفاوت است ([اشکال Firefox 452307](https://bugzil.la/452307)): IE10 آن را به عنصری که focus به سمت آن حرکت می‌کند تنظیم می‌کند، در حالی که Firefox و Chrome اغلب آن را روی `body` سند تنظیم می‌کنند.

## See also

- The {{domxref("HTMLElement.blur()")}} method
- رویدادهای مرتبط: {{domxref("Element/focus_event", "focus")}}, {{domxref("Element/focusin_event", "focusin")}}, {{domxref("Element/focusout_event", "focusout")}}
- این رویداد روی اهداف `Window`: رویداد {{domxref("Window/blur_event", "blur")}}
- [Focusing: focus/blur](https://javascript.info/focus-blur)