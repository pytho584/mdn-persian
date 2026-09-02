---
title: MouseEvent
slug: Web/API/MouseEvent
page-type: web-api-interface
browser-compat: api.MouseEvent
---

{{APIRef("Pointer Events")}}

رابط **`MouseEvent`** رویدادهایی را نشان می‌دهد که در اثر تعامل کاربر با یک دستگاه اشاره‌گر (مانند ماوس) رخ می‌دهند. رویدادهای رایجی که از این رابط استفاده می‌کنند شامل {{domxref("Element/click_event", "click")}}، {{domxref("Element/dblclick_event", "dblclick")}}، {{domxref("Element/mouseup_event", "mouseup")}} و {{domxref("Element/mousedown_event", "mousedown")}} هستند.

`MouseEvent` از {{domxref("UIEvent")}} مشتق می‌شود که خود از {{domxref("Event")}} مشتق شده است. اگرچه روش {{domxref("MouseEvent.initMouseEvent()")}} برای سازگاری با نسخه‌های قبلی حفظ شده است، اما ایجاد یک شیء `MouseEvent` باید با استفاده از سازنده {{domxref("MouseEvent.MouseEvent", "MouseEvent()")}} انجام شود.

چندین رویداد خاص‌تر دیگر بر اساس `MouseEvent` هستند، از جمله {{domxref("WheelEvent")}}، {{domxref("DragEvent")}} و {{domxref("PointerEvent")}}.

{{InheritanceDiagram}}

## سازنده

- {{domxref("MouseEvent.MouseEvent", "MouseEvent()")}}
  - : یک شیء `MouseEvent` ایجاد می‌کند.

## ویژگی‌های ایستا

- {{domxref("MouseEvent.WEBKIT_FORCE_AT_MOUSE_DOWN_static", "MouseEvent.WEBKIT_FORCE_AT_MOUSE_DOWN")}} {{non-standard_inline}} {{ReadOnlyInline}}
  - : حداقل نیروی لازم برای یک کلیک معمولی.
- {{domxref("MouseEvent.WEBKIT_FORCE_AT_FORCE_MOUSE_DOWN_static", "MouseEvent.WEBKIT_FORCE_AT_FORCE_MOUSE_DOWN")}} {{non-standard_inline}} {{ReadOnlyInline}}
  - : حداقل نیروی لازم برای یک کلیک فشاری.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌های والدین خود، {{domxref("UIEvent")}} و {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("MouseEvent.altKey")}} {{ReadOnlyInline}}
  - : اگر کلید <kbd>alt</kbd> هنگام شلیک رویداد ماوس پایین بود، `true` برمی‌گرداند.
- {{domxref("MouseEvent.button")}} {{ReadOnlyInline}}
  - : شماره دکمه‌ای که هنگام شلیک رویداد ماوس فشرده یا رها شده است (در صورت وجود).
- {{domxref("MouseEvent.buttons")}} {{ReadOnlyInline}}
  - : دکمه‌هایی که هنگام شلیک رویداد ماوس فشرده شده‌اند (در صورت وجود).
- {{domxref("MouseEvent.clientX")}} {{ReadOnlyInline}}
  - : مختصات X اشاره‌گر ماوس در [مختصات viewport](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems#viewport).
- {{domxref("MouseEvent.clientY")}} {{ReadOnlyInline}}
  - : مختصات Y اشاره‌گر ماوس در [مختصات viewport](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems#viewport).
- {{domxref("MouseEvent.ctrlKey")}} {{ReadOnlyInline}}
  - : اگر کلید <kbd>control</kbd> هنگام شلیک رویداد ماوس پایین بود، `true` برمی‌گرداند.
- {{domxref("MouseEvent.layerX")}} {{Non-standard_inline}} {{ReadOnlyInline}}
  - : مختصات افقی رویداد را نسبت به لایه جاری برمی‌گرداند.
- {{domxref("MouseEvent.layerY")}} {{Non-standard_inline}} {{ReadOnlyInline}}
  - : مختصات عمودی رویداد را نسبت به لایه جاری برمی‌گرداند.
- {{domxref("MouseEvent.metaKey")}} {{ReadOnlyInline}}
  - : اگر کلید <kbd>meta</kbd> هنگام شلیک رویداد ماوس پایین بود، `true` برمی‌گرداند.
- {{domxref("MouseEvent.movementX")}} {{ReadOnlyInline}}
  - : مختصات X اشاره‌گر ماوس نسبت به موقعیت آخرین رویداد حرکت از همان نوع (یک {{domxref("Element/mousemove_event", "mousemove")}}، {{domxref("Element/pointermove_event", "pointermove")}} یا {{domxref("Element/pointerrawupdate_event", "pointerrawupdate")}}).
- {{domxref("MouseEvent.movementY")}} {{ReadOnlyInline}}
  - : مختصات Y اشاره‌گر ماوس نسبت به موقعیت آخرین رویداد حرکت از همان نوع (یک {{domxref("Element/mousemove_event", "mousemove")}}، {{domxref("Element/pointermove_event", "pointermove")}} یا {{domxref("Element/pointerrawupdate_event", "pointerrawupdate")}}).
- {{domxref("MouseEvent.offsetX")}} {{ReadOnlyInline}}
  - : مختصات X اشاره‌گر ماوس نسبت به موقعیت لبه padding گره هدف.
- {{domxref("MouseEvent.offsetY")}} {{ReadOnlyInline}}
  - : مختصات Y اشاره‌گر ماوس نسبت به موقعیت لبه padding گره هدف.
- {{domxref("MouseEvent.pageX")}} {{ReadOnlyInline}}
  - : مختصات X اشاره‌گر ماوس نسبت به کل سند.
- {{domxref("MouseEvent.pageY")}} {{ReadOnlyInline}}
  - : مختصات Y اشاره‌گر ماوس نسبت به کل سند.
- {{domxref("MouseEvent.relatedTarget")}} {{ReadOnlyInline}}
  - : هدف ثانویه برای رویداد، در صورت وجود.
- {{domxref("MouseEvent.screenX")}} {{ReadOnlyInline}}
  - : مختصات X اشاره‌گر ماوس در [مختصات screen](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems#screen).
- {{domxref("MouseEvent.screenY")}} {{ReadOnlyInline}}
  - : مختصات Y اشاره‌گر ماوس در [مختصات screen](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems#screen).
- {{domxref("MouseEvent.shiftKey")}} {{ReadOnlyInline}}
  - : اگر کلید <kbd>shift</kbd> هنگام شلیک رویداد ماوس پایین بود، `true` برمی‌گرداند.
- {{domxref("MouseEvent.mozInputSource")}} {{non-standard_inline()}} {{ReadOnlyInline}}
  - : نوع دستگاهی که رویداد را تولید کرده است (یکی از ثابت‌های `MOZ_SOURCE_*`). این به شما امکان می‌دهد، برای مثال، تعیین کنید که آیا یک رویداد ماوس توسط یک ماوس واقعی یا توسط یک رویداد لمسی تولید شده است (که ممکن است بر دقت تفسیر مختصات مرتبط با رویداد تأثیر بگذارد).
- {{domxref("MouseEvent.webkitForce")}} {{non-standard_inline()}} {{ReadOnlyInline}}
  - : میزان فشار اعمال شده هنگام کلیک.
- {{domxref("MouseEvent.x")}} {{ReadOnlyInline}}
  - : نام مستعار برای {{domxref("MouseEvent.clientX")}}.
- {{domxref("MouseEvent.y")}} {{ReadOnlyInline}}
  - : نام مستعار برای {{domxref("MouseEvent.clientY")}}.

## روش‌های نمونه

_این رابط همچنین روش‌های والدین خود، {{domxref("UIEvent")}} و {{domxref("Event")}} را به ارث می‌برد._

- {{domxref("MouseEvent.getModifierState()")}}
  - : وضعیت جاری کلید اصلاح‌کننده مشخص‌شده را برمی‌گرداند. برای جزئیات به {{domxref("KeyboardEvent.getModifierState", "KeyboardEvent.getModifierState()")}} مراجعه کنید.
- {{domxref("MouseEvent.initMouseEvent()")}} {{deprecated_inline}}
  - : مقدار یک `MouseEvent` ایجاد شده را مقداردهی اولیه می‌کند. اگر رویداد قبلاً ارسال شده باشد، این روش هیچ کاری انجام نمی‌دهد.

## مثال

این مثال شبیه‌سازی یک کلیک (تولید برنامه‌ای یک رویداد کلیک) روی یک کادر علامت‌گذاری با استفاده از روش‌های DOM را نشان می‌دهد. وضعیت رویداد (لغو شده یا خیر) سپس با مقدار بازگشتی روش {{domxref("EventTarget.dispatchEvent", "EventTarget.dispatchEvent()")}} تعیین می‌شود.

### HTML

```html
<p>
  <label><input type="checkbox" id="checkbox" /> Checked</label>
</p>
<p>
  <button id="button">Click me to send a MouseEvent to the checkbox</button>
</p>
```

### JavaScript

```js
function simulateClick() {
  // Get the element to send a click event
  const cb = document.getElementById("checkbox");

  // Create a synthetic click MouseEvent
  let evt = new MouseEvent("click", {
    bubbles: true,
    cancelable: true,
    view: window,
  });

  // Send the event to the checkbox element
  cb.dispatchEvent(evt);
}
document.getElementById("button").addEventListener("click", simulateClick);
```

### نتیجه

{{EmbedLiveSample('Example')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- والد مستقیم آن، {{domxref("UIEvent")}}
- {{domxref("PointerEvent")}}: برای رویدادهای اشاره‌گر پیشرفته، از جمله لمسی چندگانه