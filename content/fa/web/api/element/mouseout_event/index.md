---
title: "Element: mouseout event"
short-title: mouseout
slug: Web/API/Element/mouseout_event
page-type: web-api-event
browser-compat: api.Element.mouseout_event
---

{{APIRef("UI Events")}}

رویداد **`mouseout`** روی یک {{domxref("Element")}} زمانی شلیک می‌شود که یک دستگاه اشاره‌گر (معمولاً ماوس) برای حرکت مکان‌نما به‌کار گرفته شود به‌طوری که دیگر درون آن عنصر یا یکی از فرزندانش قرار نگیرد.

`mouseout` همچنین به یک عنصر تحویل داده می‌شود اگر مکان‌نما وارد یک عنصر فرزند شود، زیرا عنصر فرزند ناحیه قابل مشاهدهٔ عنصر را می‌پوشاند.

اگر عنصر هدف دارای عناصر فرزند باشد، رویدادهای `mouseout` و `mouseover` هنگام حرکت ماوس روی مرزهای این عناصر نیز شلیک می‌شوند، نه فقط روی خود عنصر هدف. معمولاً رفتار رویدادهای {{domxref("Element/mouseenter_event", "mouseenter")}} و {{domxref("Element/mouseleave_event", "mouseleave")}} منطقی‌تر است، زیرا تحت تأثیر ورود به عناصر فرزند قرار نمی‌گیرند.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("mouseout", (event) => { })

onmouseout = (event) => { }
```

## نوع رویداد

یک {{domxref("MouseEvent")}}. از {{domxref("UIEvent")}} و {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("MouseEvent")}}

## مثال‌ها

مثال‌های زیر استفاده از رویداد `mouseout` را نشان می‌دهند.

### mouseout و mouseleave

مثال زیر تفاوت بین رویدادهای `mouseout` و {{domxref("Element/mouseleave_event", "mouseleave")}} را نشان می‌دهد. رویداد `mouseleave` به {{HTMLElement("ul")}} اضافه می‌شود تا هرگاه ماوس از `<ul>` خارج شود، لیست به رنگ بنفش درآید. `mouseout` به لیست اضافه می‌شود تا عنصر هدف را هنگام خروج ماوس از آن به رنگ نارنجی درآورد.

وقتی این را امتحان کنید، متوجه خواهید شد که `mouseout` به تک‌تک موارد لیست تحویل داده می‌شود، در حالی که `mouseleave` به کل لیست می‌رود، به دلیل سلسله‌مراتب موارد و این واقعیت که موارد لیست `<ul>` زیرین را می‌پوشانند.

#### HTML

```html
<ul id="test">
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
</ul>
```

#### JavaScript

```js
const test = document.getElementById("test");

// Briefly make the list purple when the mouse moves off the
// <ul> element
test.addEventListener("mouseleave", (event) => {
  // highlight the mouseleave target
  event.target.style.color = "purple";

  // reset the color after a short delay
  setTimeout(() => {
    event.target.style.color = "";
  }, 1000);
});

// Briefly make an <li> orange when the mouse moves off of it
test.addEventListener("mouseout", (event) => {
  // highlight the mouseout target
  event.target.style.color = "orange";

  // reset the color after a short delay
  setTimeout(() => {
    event.target.style.color = "";
  }, 500);
});
```

#### نتیجه

{{EmbedLiveSample("mouseout_and_mouseleave", 640, 200)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [آموزش: مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/mousemove_event", "mousemove")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mouseover_event", "mouseover")}}
- {{domxref("Element/mouseenter_event", "mouseenter")}}
- {{domxref("Element/mouseleave_event", "mouseleave")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/pointerout_event", "pointerout")}}