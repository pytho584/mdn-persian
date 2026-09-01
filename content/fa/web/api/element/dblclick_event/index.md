---
title: "Element: dblclick event"
---

---
title: "Element: dblclick event"
short-title: dblclick
slug: Web/API/Element/dblclick_event
page-type: web-api-event
browser-compat: api.Element.dblclick_event
---

{{APIRef("UI Events")}}

رویداد **`dblclick`** زمانی رخ می‌دهد که دکمه‌ای از دستگاه اشاره‌گر (مانند دکمه اصلی ماوس) دوبار کلیک شود؛ یعنی دو بار پشت سر هم و در بازه زمانی بسیار کوتاه روی یک عنصر کلیک شود.

رویداد `dblclick` پس از دو رویداد {{domxref("Element/click_event", "click")}} فعال می‌شود (و به‌تبع آن، پس از دو جفت رویداد {{domxref("Element.mousedown_event", "mousedown")}} و {{domxref("Element.mouseup_event", "mouseup")}}).

## سینتکس

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("dblclick", (event) => { })

ondblclick = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}} است. از {{domxref("UIEvent")}} و {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("MouseEvent")}}

## مثال‌ها

در این مثال، اندازه یک کارت با دوبار کلیک کردن روی آن تغییر می‌کند (بین دو حالت جابه‌جا می‌شود).

### JavaScript

```js
const card = document.querySelector("aside");

card.addEventListener("dblclick", (e) => {
  card.classList.toggle("large");
});
```

### HTML

```html
<aside>
  <h3>My Card</h3>
  <p>Double click to resize this object.</p>
</aside>
```

### CSS

```css
aside {
  background: #ffee99;
  border-radius: 1em;
  display: inline-block;
  padding: 1em;
  transform: scale(0.9);
  transform-origin: 0 0;
  transition: transform 0.6s;
  user-select: none;
}

.large {
  transform: scale(1.3);
}
```

### نتیجه

{{EmbedLiveSample("Examples", 700, 200)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Learn: Introduction to events](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/auxclick_event", "auxclick")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/pointerdown_event", "pointerdown")}}
- {{domxref("Element/pointerup_event", "pointerup")}}