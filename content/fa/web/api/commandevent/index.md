---
title: CommandEvent
source: "https://developer.mozilla.org/en-US/docs/Web/API/CommandEvent"
---

---
title: CommandEvent
slug: Web/API/CommandEvent
page-type: web-api-interface
browser-compat: api.CommandEvent
---

{{APIRef("Invoker Commands API")}}

رابطهٔ **`CommandEvent`** رویدادی را نشان می‌دهد که زمانی به کاربر اطلاع می‌دهد که یک عنصر {{domxref("HTMLButtonElement", "دکمه")}} با ویژگی‌های معتبر {{domxref("HTMLButtonElement.commandForElement", "commandForElement")}} و {{domxref("HTMLButtonElement.command", "command")}} در آستانهٔ فراخوانی یک عنصر تعاملی است.

این شیء رویداد برای رویداد `command` عنصر `HTMLElement` ({{domxref("HTMLElement.command_event", "رویداد command")}}) است که عملی از یک کنترل فراخوان (Invoker Control) را هنگام فراخوانی (برای مثال هنگام کلیک یا فشردن) نشان می‌دهد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CommandEvent.CommandEvent", "CommandEvent()")}}
  - : یک شیء `CommandEvent` می‌سازد.

## ویژگی‌های نمونه

_این رابط ویژگی‌های والد خود، {{DOMxRef("Event")}} را به ارث می‌برد._

- {{domxref("CommandEvent.source")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLButtonElement")}} که دکمهٔ منجر به این فراخوانی را نشان می‌دهد.
- {{domxref("CommandEvent.command")}} {{ReadOnlyInline}}
  - : یک رشته که مقدار {{domxref("HTMLButtonElement.command", "command")}} دکمهٔ مبدأ را نشان می‌دهد.

## مثال‌ها

### مثال پایه

```html
<button commandfor="mypopover" command="show-popover">Show popover</button>

<div popover id="mypopover" role="[declare appropriate ARIA role]">
  <!-- popover content here -->
  <button commandfor="mypopover" command="hide-popover">Hide popover</button>
</div>
```

```js
const popover = document.getElementById("mypopover");

// …

popover.addEventListener("command", (event) => {
  if (event.command === "show-popover") {
    console.log("Popover is about to be shown");
  }
});
```

### استفاده از مقادیر سفارشی برای دستورها

در این مثال سه دکمه با [`دستورهایی با مقادیر سفارشی`](/en-US/docs/Web/HTML/Reference/Elements/button#custom_values) ساخته شده‌اند.

```html
<div class="controls">
  <button commandfor="the-image" command="--rotate-left">Rotate Left</button>
  <button commandfor="the-image" command="--reset">Reset</button>
  <button commandfor="the-image" command="--rotate-right">Rotate Right</button>
</div>

<img
  id="the-image"
  src="/shared-assets/images/examples/dino.svg"
  alt="dinosaur head rotated 0 degrees" />
```

```css hidden
.controls {
  margin-block-end: 20px;
}
```

یک شنوندهٔ رویداد با استفاده از [رویداد `command`](/en-US/docs/Web/API/HTMLElement/command_event) به تصویر متصل شده است. وقتی یکی از دکمه‌ها کلیک می‌شود، شنونده کدی را بر اساس مقدار سفارشی `command` اختصاص‌داده‌شده به دکمه اجرا می‌کند، تصویر را می‌چرخاند و متن `alt` آن را نیز به‌روزرسانی می‌کند تا زاویهٔ جدید تصویر را نشان دهد.

```js
const image = document.getElementById("the-image");

image.addEventListener("command", (event) => {
  let rotate = parseInt(event.target.style.rotate || "0", 10);
  if (event.command === "--reset") {
    rotate = 0;
    event.target.style.rotate = `${rotate}deg`;
  } else if (event.command === "--rotate-left") {
    rotate = rotate === -270 ? 0 : rotate - 90;
    event.target.style.rotate = `${rotate}deg`;
  } else if (event.command === "--rotate-right") {
    rotate = rotate === 270 ? 0 : rotate + 90;
    event.target.style.rotate = `${rotate}deg`;
  }
  event.target.alt = `dinosaur head rotated ${rotate} degrees`;
});
```

{{EmbedLiveSample('using_custom_values_for_commands', '100%', "220")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Invoker Commands API", "Invoker Commands API", "", "nocode")}}
- {{domxref("HTMLButtonElement.command")}}
- {{domxref("HTMLButtonElement.commandForElement")}}