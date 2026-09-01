---
title: "Element: keypress event"
---

---
title: "Element: keypress event"
short-title: keypress
slug: Web/API/Element/keypress_event
page-type: web-api-event
status:
  - deprecated
browser-compat: api.Element.keypress_event
---

{{APIRef("UI Events")}}{{deprecated_header}}

رویداد **`keypress`** زمانی فعال می‌شود که کلیدی از نوع [حروف، اعداد، نقطه‌گذاری یا نمادها](https://w3c.github.io/uievents/#unicode-character-categories) فشرده شود، یا همچنین زمانی که کلید <kbd>Enter</kbd> فشرده شود — از جمله زمانی که کلید <kbd>Enter</kbd> همراه با کلید <kbd>Shift</kbd> یا <kbd>Ctrl</kbd> فشرده شود. در غیر این صورت، وقتی یک کلید اصلاح‌گر مانند <kbd>Alt</kbd>، <kbd>Shift</kbd>، <kbd>Ctrl</kbd>، <kbd>Meta</kbd>، <kbd>Esc</kbd> یا <kbd>Option</kbd> به‌تنهایی فشرده شود، رویداد `keypress` فعال _نمی‌شود_.

> [!WARNING]
> از آنجا که این رویداد منسوخ‌شده است، به جای آن باید از [`beforeinput`](/en-US/docs/Web/API/Element/beforeinput_event) یا [`keydown`](/en-US/docs/Web/API/Element/keydown_event) استفاده کنید.

این رویداد [حباب می‌زند](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) و می‌تواند به {{domxref("Document")}} و {{domxref("Window")}} برسد.

## نحو

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("keypress", (event) => { })

onkeypress = (event) => { }
```

## نوع رویداد

یک {{domxref("KeyboardEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("KeyboardEvent")}}

## مثال

### مثال استفاده از addEventListener برای رویداد keypress

این مثال مقدار {{domxref("KeyboardEvent.code")}} را هر بار که پس از فوکوس کردن عنصر {{htmlelement("input")}} یک کلید را فشار می‌دهید، ثبت می‌کند.

برای اینکه ببینید کدام کلیدها باعث فعال‌شدن رویداد `keypress` می‌شوند و کدام‌ها نمی‌شوند، کلیدهای زیر را امتحان کنید:

- کلیدهای حروف، کلیدهای اعداد و کلیدهای نقطه‌گذاری
- کلیدهای نماد مانند کلیدهای <kbd>$</kbd>، <kbd>+</kbd>، <kbd>=</kbd>، <kbd>%</kbd> و <kbd>+</kbd>
- کلیدهای اصلاح‌گر مانند کلیدهای <kbd>Alt</kbd>، <kbd>Shift</kbd>، <kbd>Ctrl</kbd>، <kbd>Meta</kbd>، <kbd>Esc</kbd>، <kbd>Option</kbd> یا <kbd>⌘</kbd>
- کلید <kbd>Enter</kbd>
- کلید <kbd>Enter</kbd> همراه با کلیدهای <kbd>Shift</kbd> یا <kbd>Ctrl</kbd>
- کلید <kbd>Enter</kbd> همراه با کلیدهای اصلاح‌گر غیر از <kbd>Shift</kbd> یا <kbd>Ctrl</kbd>

```html
<div>
  <label for="sample">Focus the input and type something:</label>
  <input type="text" name="text" id="sample" />
</div>
<p id="log"></p>
```

```js
const log = document.getElementById("log");
const input = document.querySelector("input");

input.addEventListener("keypress", logKey);

function logKey(e) {
  log.textContent += ` ${e.code}`;
}
```

{{EmbedLiveSample("addEventListener_keypress_example")}}

### معادل onkeypress

```js
input.onkeypress = logKey;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- اینترفیس {{domxref("Document")}} که این رویداد همچنین آن را هدف قرار می‌دهد.
- رویدادهای مرتبط:
  - [`input`](/en-US/docs/Web/API/Element/input_event)
  - [`keydown`](/en-US/docs/Web/API/Element/keydown_event)
  - [`keyup`](/en-US/docs/Web/API/Element/keyup_event)