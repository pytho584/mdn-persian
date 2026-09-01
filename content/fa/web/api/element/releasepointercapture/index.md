---
title: "Element: releasePointerCapture() method"
short-title: releasePointerCapture()
slug: Web/API/Element/releasePointerCapture
page-type: web-api-instance-method
browser-compat: api.Element.releasePointerCapture
---

{{APIRef("DOM")}}

متد **`releasePointerCapture()`** از رابط {{domxref("Element")}}، [گرفتن اشارهگر](/en-US/docs/Web/API/Pointer_events#pointer_capture) (*pointer capture*) را که قبلاً برای یک *اشارهگر* خاص ({{domxref("PointerEvent")}}) تنظیم شده بود، رها (متوقف) می‌کند.

## نحو

```js-nolint
releasePointerCapture(pointerId)
```

### پارامترها

- `pointerId`
  - : {{domxref("PointerEvent.pointerId", "pointerId")}} یک شیء {{domxref("PointerEvent")}}.

### مقدار بازگشتی

هیچ مقداری ({{jsxref("undefined")}}).

### استثناها

- `NotFoundError` {{domxref("DOMException")}}
  - : در صورتی که `pointerId` با هیچ اشاره‌گر فعالی مطابقت نداشته باشد، پرتاب می‌شود.

## مثال‌ها

این مثال، هنگام فشار دادن روی یک {{HtmlElement("div")}}، گرفتن اشاره‌گر را روی آن تنظیم می‌کند. این کار به شما امکان می‌دهد عنصر را به‌صورت افقی بلغزانید، حتی زمانی که اشاره‌گر شما از مرزهای آن خارج می‌شود.

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

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{ domxref("Element.hasPointerCapture","Element.hasPointerCapture()") }}
- {{ domxref("Element.setPointerCapture","Element.setPointerCapture()") }}
- [رویدادهای اشاره‌گر](/en-US/docs/Web/API/Pointer_events)