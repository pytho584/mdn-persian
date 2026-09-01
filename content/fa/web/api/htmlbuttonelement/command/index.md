---
title: "HTMLButtonElement: command property"
short-title: command
slug: Web/API/HTMLButtonElement/command
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.command
---

{{APIRef("Invoker Commands API")}}

ویژگی **`command`** در رابط {{domxref("HTMLButtonElement")}}، عملیاتی را که قرار است روی عنصری که توسط این دکمه کنترل می‌شود انجام شود، دریافت و تنظیم می‌کند. برای اینکه این ویژگی اثر داشته باشد، باید [`commandfor`](/en-US/docs/Web/HTML/Reference/Elements/button#commandfor) تنظیم شده باشد.

این ویژگی، ویژگی HTML [`command`](/en-US/docs/Web/HTML/Reference/Elements/button#command) را بازتاب می‌دهد.

## مقدار

یک رشته (string). برای مقادیر معتبر، به ویژگی [`command`](/en-US/docs/Web/HTML/Reference/Elements/button#command) مراجعه کنید.

## مثال‌ها

### مثال پایه

```html
<button id="toggleBtn" commandfor="mypopover" command="toggle-popover">
  Toggle popover
</button>

<div popover id="mypopover">
  <button commandfor="mypopover" command="hide-popover">Hide popover</button>
</div>
```

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

toggleBtn.command = "show-popover";
```

### استفاده از مقادیر سفارشی برای فرمان‌ها

در این مثال، سه دکمه با استفاده از [مقادیر سفارشی](/en-US/docs/Web/HTML/Reference/Elements/button#custom_values) برای `command` ساخته شده‌اند.
هر دکمه با استفاده از ویژگی `commandfor` به همان تصویر اشاره می‌کند.

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

یک شنونده رویداد (event listener) با استفاده از [رویداد `command`](/en-US/docs/Web/API/CommandEvent) به تصویر متصل شده است.
وقتی یکی از دکمه‌ها کلیک می‌شود، شنونده کدی را بر اساس مقدار سفارشی `command` اختصاص‌یافته به دکمه اجرا می‌کند، تصویر را می‌چرخاند و متن `alt` آن را نیز برای نشان دادن زاویه جدید تصویر به‌روزرسانی می‌کند.

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
- {{domxref("HTMLButtonElement.commandForElement")}}
- {{domxref("CommandEvent")}}
- [ویژگی `command` در `<button>`](/en-US/docs/Web/HTML/Reference/Elements/button#command)