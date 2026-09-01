---
title: "Element: mouseover event"
short-title: mouseover
slug: Web/API/Element/mouseover_event
page-type: web-api-event
browser-compat: api.Element.mouseover_event
---

{{APIRef("UI Events")}}

رویداد **`mouseover`** روی یک {{domxref("Element")}} شلیک می‌شود؛ زمانی که یک دستگاه اشاره‌گر (مانند ماوس یا ترک‌پد) نشانگر را روی آن عنصر یا یکی از عناصر فرزندش قرار دهد.

اگر عنصر هدف دارای عناصر فرزند باشد، رویدادهای `mouseover` و `mouseout` هنگام عبور ماوس از مرزهای این فرزندان نیز شلیک می‌شوند، نه فقط هنگام عبور از مرز خود عنصر. معمولاً رفتار رویدادهای `mouseenter` و `mouseleave` مناسب‌تر است؛ زیرا ورود به عناصر فرزند روی آن‌ها تأثیری ندارد.

## نحو

برای شنیدن این رویداد، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به‌کار ببرید یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("mouseover", (event) => { })

onmouseover = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}} که از {{domxref("UIEvent")}} و {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("MouseEvent")}}

## مثال‌ها

مثال زیر تفاوت بین رویدادهای `mouseover` و {{domxref("Element/mouseenter_event", "mouseenter")}} را نشان می‌دهد.

### HTML

```html
<ul id="test">
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
</ul>
```

### JavaScript

```js
const test = document.getElementById("test");

// This handler will be executed only once when the cursor
// moves over the unordered list
test.addEventListener("mouseenter", (event) => {
  // highlight the mouseenter target
  event.target.style.color = "purple";

  // reset the color after a short delay
  setTimeout(() => {
    event.target.style.color = "";
  }, 500);
});

// This handler will be executed every time the cursor
// is moved over a different list item
test.addEventListener("mouseover", (event) => {
  // highlight the mouseover target
  event.target.style.color = "orange";

  // reset the color after a short delay
  setTimeout(() => {
    event.target.style.color = "";
  }, 500);
});
```

### نتیجه

{{EmbedLiveSample('Examples')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/mousemove_event", "mousemove")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mouseout_event", "mouseout")}}
- {{domxref("Element/mouseenter_event", "mouseenter")}}
- {{domxref("Element/mouseleave_event", "mouseleave")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/pointerover_event", "pointerover")}}