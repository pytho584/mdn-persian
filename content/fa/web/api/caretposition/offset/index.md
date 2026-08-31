---
title: "CaretPosition: offset property"
short-title: offset
slug: Web/API/CaretPosition/offset
page-type: web-api-instance-property
browser-compat: api.CaretPosition.offset
---

{{APIRef("CSSOM view API")}}

ویژگی **`offset`** از رابط {{domxref("CaretPosition")}} یک عدد صحیح برمی‌گرداند که افست انتخاب در گره موقعیت مکان‌نما را نشان می‌دهد.

این مقدار، افست نویسه در یک گره متنی یا ایندکس گره فرزند انتخاب‌شده در یک گره عنصر است.

## مقدار

یک عدد صحیح.

## مثال

این مثال، `offsetNode` و `offset` موقعیت مکان‌نما را هنگام کلیک درون فیلد ورودی ثبت می‌کند.

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node")}}
- {{domxref("Document.caretPositionFromPoint()")}}