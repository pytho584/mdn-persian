---
title: "Element: setPointerCapture() method"
short-title: setPointerCapture()
slug: Web/API/Element/setPointerCapture
page-type: web-api-instance-method
browser-compat: api.Element.setPointerCapture
---

{{APIRef("DOM")}}

متد **`setPointerCapture()`** از رابط {{domxref("Element")}} برای تعیین یک عنصر خاص به‌عنوان _هدفِ دریافتِ_ رویدادهای آیندهٔ اشاره‌گر استفاده می‌شود. رویدادهای بعدیِ این اشاره‌گر، تا وقتی که ضبط آزاد شود (از طریق {{domxref("Element.releasePointerCapture()")}} یا با رخ دادن رویداد {{domxref("Element/pointerup_event", "pointerup")}})، به همین عنصرِ ضبط‌کننده هدایت می‌شوند.

برای مروری کلی و مثال‌هایی دربارهٔ چگونگی کارِ ضبطِ اشاره‌گر، به [رویدادهای اشاره‌گر](/en-US/docs/Web/API/Pointer_events#pointer_capture) مراجعه کنید.

## Syntax

```js-nolint
setPointerCapture(pointerId)
```

### Parameters

- `pointerId`
  - : {{domxref("PointerEvent.pointerId", "pointerId")}} مربوط به یک شیء {{domxref("PointerEvent")}}.

### Return value

هیچ ({{jsxref("undefined")}}).

### Exceptions

- `NotFoundError` {{domxref("DOMException")}}
  - : اگر `pointerId` با هیچ اشاره‌گرِ فعالی مطابقت نداشته باشد پرتاب می‌شود.

## Examples

این مثال، ضبطِ اشاره‌گر را روی یک {{HtmlElement("div")}} زمانی که روی آن فشار دهید، فعال می‌کند. این امکان را می‌دهد که عنصر را به‌صورت افقی بلغزانید، حتی وقتی نشانگر شما از مرزهای آن خارج می‌شود.

### HTML

```html
<div id="slider">SLIDE ME</div>
```

### CSS

```css
div {
  width: 140px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #ffbbee;
  touch-action: none;
}
```

### JavaScript

```js
const slider = document.getElementById("slider");

function beginSliding(e) {
  slider.onpointermove = slide;
  slider.setPointerCapture(e.pointerId);
}

function stopSliding(e) {
  slider.onpointermove = null;
  slider.releasePointerCapture(e.pointerId);
}

function slide(e) {
  slider.style.transform = `translate(${e.clientX - 70}px)`;
}

slider.onpointerdown = beginSliding;
slider.onpointerup = stopSliding;
```

### Result

{{EmbedLiveSample("Examples")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Element.hasPointerCapture","Element.hasPointerCapture()")}}
- {{domxref("Element.releasePointerCapture","Element.releasePointerCapture()")}}
- [رویدادهای اشاره‌گر](/en-US/docs/Web/API/Pointer_events)