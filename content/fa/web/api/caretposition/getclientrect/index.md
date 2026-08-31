---
title: "CaretPosition: getClientRect() method"
short-title: getClientRect()
slug: Web/API/CaretPosition/getClientRect
page-type: web-api-instance-method
browser-compat: api.CaretPosition.getClientRect
---

{{APIRef("CSSOM view API")}}

متد `getClientRect()` از رابط {{domxref("CaretPosition")}}، مستطیل کلاینت (client rectangle) مربوط به محدودهٔ محل قرارگیری نشانهٔ درج متن (caret) را برمی‌گرداند.

## Syntax

```js-nolint
getClientRect()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک شیء {{domxref("DOMRect")}}.

## مثال‌ها

### دریافت موقعیت صفحه‌ای نشانهٔ درج متن

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
    log("پشتیبانی نمی‌شود");
    return;
  }

  const rect = caret.getClientRect();

  log(`مستطیل محدودهٔ نشانهٔ درج متن: ${JSON.stringify(rect)}`);
  log(`نشانهٔ درج متن در موقعیت (${rect.x.toFixed(2)}, ${rect.y.toFixed(2)}) قرار دارد.`);
});
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

{{EmbedLiveSample("Get the caret's screen position", "", 300)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("DOMRect")}}
- {{domxref("Document.caretPositionFromPoint()")}}
- {{domxref("Element.getBoundingClientRect()")}}