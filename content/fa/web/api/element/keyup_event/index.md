---
title: "Element: keyup event"
short-title: keyup
slug: Web/API/Element/keyup_event
page-type: web-api-event
browser-compat: api.Element.keyup_event
---

{{APIRef("UI Events")}}

رویداد **`keyup`** زمانی رخ می‌دهد که کلیدی رها می‌شود.

رویدادهای [`keydown`](/en-US/docs/Web/API/Element/keydown_event) و `keyup` کدی را ارائه می‌کنند که نشان می‌دهد کدام کلید فشرده شده است، در حالی که `keypress` نشان می‌دهد کدام نویسه وارد شده است. برای مثال، یک حرف کوچک «a» توسط `keydown` و `keyup` به صورت 65 و توسط `keypress` به صورت 97 گزارش می‌شود. حرف بزرگ «A» در همهٔ رویدادها به صورت 65 گزارش می‌شود.

هدف رویداد یک رویداد کلید، عنصری است که در حال حاضر فوکوس دارد و فعالیت صفحه‌کلید را پردازش می‌کند. این شامل {{HTMLElement("input")}}، {{HTMLElement("textarea")}}، هر چیزی که [`contentEditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) است، و هر چیز دیگری که بتوان با صفحه‌کلید با آن تعامل کرد، مانند {{HTMLElement("a")}}، {{HTMLElement("button")}} و {{HTMLElement("summary")}} می‌شود. اگر هیچ عنصر مناسبی در فوکوس نباشد، هدف رویداد {{HTMLElement("body")}} یا ریشه خواهد بود. این رویداد [حباب‌زنی](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling) می‌کند و می‌تواند به {{domxref("Document")}} و {{domxref("Window")}} برسد.

ممکن است هدف رویداد بین رویدادهای کلیدی مختلف تغییر کند. برای مثال، هدف رویداد `keydown` برای فشردن کلید <kbd>Tab</kbd> با هدف رویداد `keyup` متفاوت خواهد بود، زیرا فوکوس تغییر کرده است.

## Syntax

Use the event name in methods like {{domxref("EventTarget.addEventListener", "addEventListener()")}}, or set an event handler property.

```js-nolint
addEventListener("keyup", (event) => { })

onkeyup = (event) => { }
```

## Event type

A {{domxref("KeyboardEvent")}}. Inherits from {{domxref("UIEvent")}} and {{domxref("Event")}}.

{{InheritanceDiagram("KeyboardEvent")}}

## Examples

### addEventListener keyup example

This example logs the {{domxref("KeyboardEvent.code")}} value whenever you release a key inside the {{HtmlElement("input")}} element.

```html
<input placeholder="Click here, then press and release a key." size="40" />
<p id="log"></p>
```

```js
const input = document.querySelector("input");
const log = document.getElementById("log");

input.addEventListener("keyup", logKey);

function logKey(e) {
  log.textContent += ` ${e.code}`;
}
```

{{EmbedLiveSample("addEventListener_keyup_example")}}

### keyup events with IME

Since Firefox 65, the [`keydown`](/en-US/docs/Web/API/Element/keydown_event) and `keyup` events are now fired during {{glossary("Input method editor")}} composition, to improve cross-browser compatibility for CJKT users ([Firefox bug 354358](https://bugzil.la/354358)). To ignore all `keyup` events that are part of composition, do something like this:

```js
eventTarget.addEventListener("keyup", (event) => {
  if (event.isComposing) {
    return;
  }
  // do something
});
```

> [!NOTE]
> Unlike `keydown`, `keyup` events do not have special {{domxref("KeyboardEvent/keyCode", "keyCode")}} values for IME events. However, like `keydown`, `compositionstart` may fire _after_ `keyup` when typing the first character that opens up the IME, and `compositionend` may fire _before_ `keyup` when typing the last character that closes the IME. In these cases, `isComposing` is false even when the event is part of composition.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [`input`](/en-US/docs/Web/API/Element/input_event)
- [`keydown`](/en-US/docs/Web/API/Element/keydown_event)
- [`keypress`](/en-US/docs/Web/API/Element/keypress_event)
