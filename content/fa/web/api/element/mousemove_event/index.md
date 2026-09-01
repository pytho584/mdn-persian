---
title: "Element: mousemove event"
short-title: mousemove
slug: Web/API/Element/mousemove_event
page-type: web-api-event
browser-compat: api.Element.mousemove_event
---

{{APIRef("UI Events")}}

رویداد `mousemove` زمانی روی یک عنصر صادر می‌شود که یک دستگاهِ اشاره‌گر (معمولاً ماوس) در حالی جابه‌جا شود که نقطه‌ی داغ نشانگر داخل آن عنصر قرار دارد.

این رویدادها صرف‌نظر از فشرده بودن یا نبودن دکمه‌های ماوس رخ می‌دهند. ممکن است با نرخ بسیار بالایی صادر شوند؛ این نرخ به سرعت حرکت ماوس توسط کاربر، سرعت دستگاه، و سایر وظایف و فرآیندهای در حال اجرا بستگی دارد.

## Syntax

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده‌ی رویداد تنظیم کنید.

```js-nolint
addEventListener("mousemove", (event) => { })

onmousemove = (event) => { }
```

## Event type

یک {{domxref("MouseEvent")}} که از {{domxref("UIEvent")}} و {{domxref("Event")}} ارث می‌برد.

{{InheritanceDiagram("MouseEvent")}}

## Examples

مثال زیر از رویدادهای {{domxref("Element/mousedown_event", "mousedown")}}، `mousemove` و {{domxref("Element/mouseup_event", "mouseup")}} استفاده می‌کند تا به کاربر اجازه دهد روی [canvas](/en-US/docs/Web/API/Canvas_API) HTML نقاشی بکشد. عملکرد آن ساده است: ضخامت خط روی ۱ تنظیم شده و رنگ همیشه سیاه است.

هنگام بارگذاری صفحه، ثابت‌های `myPics` و `context` ایجاد می‌شوند تا ارجاعی به canvas و بافت دوبعدی که برای رسم استفاده خواهیم کرد ذخیره کنند.

رسم زمانی آغاز می‌شود که رویداد `mousedown` صادر شود. ابتدا مختصات x و y اشاره‌گر ماوس را در متغیرهای `x` و `y` ذخیره می‌کنیم و سپس `isDrawing` را برابر `true` قرار می‌دهیم.

با حرکت ماوس روی صفحه، رویداد `mousemove` صادر می‌شود. اگر `isDrawing` برابر `true` باشد، کنترل‌کننده‌ی رویداد تابع `drawLine` را فراخوانی می‌کند تا خطی از مقادیر ذخیره‌شده‌ی `x` و `y` تا مکان فعلی رسم کند.

وقتی تابع `drawLine()` برمی‌گردد، مختصات را به‌روزرسانی کرده و سپس آن‌ها را در `x` و `y` ذخیره می‌کنیم.

رویداد `mouseup` بخش پایانی خط را رسم می‌کند، `x` و `y` را روی `0` تنظیم می‌کند، و با قرار دادن `isDrawing` برابر `false` از ادامه‌ی رسم جلوگیری می‌کند.

### HTML

```html
<h1>Drawing with mouse events</h1>
<canvas id="myPics" width="560" height="360"></canvas>
```

### CSS

```css
canvas {
  border: 1px solid black;
  width: 560px;
  height: 360px;
}
```

### JavaScript

```js
// When true, moving the mouse draws on the canvas
let isDrawing = false;
let x = 0;
let y = 0;

const myPics = document.getElementById("myPics");
const context = myPics.getContext("2d");

// event.offsetX, event.offsetY gives the (x,y) offset from the edge of the canvas.

// Add the event listeners for mousedown, mousemove, and mouseup
myPics.addEventListener("mousedown", (e) => {
  x = e.offsetX;
  y = e.offsetY;
  isDrawing = true;
});

myPics.addEventListener("mousemove", (e) => {
  if (isDrawing) {
    drawLine(context, x, y, e.offsetX, e.offsetY);
    x = e.offsetX;
    y = e.offsetY;
  }
});

window.addEventListener("mouseup", (e) => {
  if (isDrawing) {
    drawLine(context, x, y, e.offsetX, e.offsetY);
    x = 0;
    y = 0;
    isDrawing = false;
  }
});

function drawLine(context, x1, y1, x2, y2) {
  context.beginPath();
  context.strokeStyle = "black";
  context.lineWidth = 1;
  context.moveTo(x1, y1);
  context.lineTo(x2, y2);
  context.stroke();
  context.closePath();
}
```

### Result

{{EmbedLiveSample("Examples", 640, 450)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Learn: Introduction to events](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- {{domxref("Element/mousedown_event", "mousedown")}}
- {{domxref("Element/mouseup_event", "mouseup")}}
- {{domxref("Element/click_event", "click")}}
- {{domxref("Element/dblclick_event", "dblclick")}}
- {{domxref("Element/mouseover_event", "mouseover")}}
- {{domxref("Element/mouseout_event", "mouseout")}}
- {{domxref("Element/mouseenter_event", "mouseenter")}}
- {{domxref("Element/mouseleave_event", "mouseleave")}}
- {{domxref("Element/contextmenu_event", "contextmenu")}}
- {{domxref("Element/pointermove_event", "pointermove")}}