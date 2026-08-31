---
title: "ContentVisibilityAutoStateChangeEvent: skipped property"
short-title: skipped
slug: Web/API/ContentVisibilityAutoStateChangeEvent/skipped
page-type: web-api-instance-property
browser-compat: api.ContentVisibilityAutoStateChangeEvent.skipped
---
{{APIRef("CSS Containment")}}

ویژگی فقط‌خواندنی `skipped` از رابط {{ domxref("ContentVisibilityAutoStateChangeEvent") }} مقدار `true` را برمی‌گرداند اگر عامل کاربر [از محتوای عنصر صرف‌نظر کند](/en-US/docs/Web/CSS/Guides/Containment/Using#skips_its_contents)، در غیر این صورت `false` را برمی‌گرداند.

## مقدار

یک مقدار بولی. اگر عامل کاربر از محتوای عنصر صرف‌نظر کند `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

```js
const canvasElem = document.querySelector("canvas");

canvasElem.addEventListener("contentvisibilityautostatechange", stateChanged);
canvasElem.style.contentVisibility = "auto";

function stateChanged(event) {
  if (event.skipped) {
    stopCanvasUpdates(canvasElem);
  } else {
    startCanvasUpdates(canvasElem);
  }
}

// Call this when the canvas updates need to start.
function startCanvasUpdates(canvas) {
  // …
}

// Call this when the canvas updates need to stop.
function stopCanvasUpdates(canvas) {
  // …
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویداد {{domxref("element/contentvisibilityautostatechange_event", "contentvisibilityautostatechange")}}
- [CSS Containment](/en-US/docs/Web/CSS/Guides/Containment)
- ویژگی {{cssxref("content-visibility")}}
- ویژگی {{cssxref("contain")}}