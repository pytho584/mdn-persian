---
title: "CaretPosition: offsetNode property"
short-title: offsetNode
slug: Web/API/CaretPosition/offsetNode
page-type: web-api-instance-property
browser-compat: api.CaretPosition.offsetNode
---

{{APIRef("CSSOM view API")}}

خاصیت **`offsetNode`** از رابط {{domxref("CaretPosition")}} یک {{domxref("Node")}} را برمی‌گرداند که شامل گره پیدا شده در موقعیت مکان‌نما (caret) است.

## مقدار

یک {{domxref("Node")}}.

## مثال‌ها

این مثال، `offsetNode` و `offset` موقعیت مکان‌نما را هنگام کلیک کردن درون فیلد ورودی، در لاگ ثبت می‌کند.

```html
<input aria-label="text field" value="Click inside this input field" />
```

```html hidden
<pre id="log"></pre>
```

```css hidden
input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  box-sizing: border-box;
}

#log {
  height: 200px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```js
document.querySelector("input").addEventListener("click", (event) => {
  const x = event.clientX;
  const y = event.clientY;

  const caret = document.caretPositionFromPoint?.(x, y);
  if (!caret) {
    log("Not supported");
    return;
  }

  const node = caret.offsetNode;
  const offset = caret.offset;

  log(`offsetNode: ${node}`);
  log(`offset: ${offset}`);
});
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

{{EmbedLiveSample("Examples", "", 300)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Node")}}
- {{domxref("Document.caretPositionFromPoint()")}}