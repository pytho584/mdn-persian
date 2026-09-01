---
title: "EditContext: selectionStart property"
---

---
title: "EditContext: selectionStart property"
short-title: selectionStart
slug: Web/API/EditContext/selectionStart
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.EditContext.selectionStart
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`selectionStart`** در رابط {{domxref("EditContext")}} به آفست شروع انتخاب فعلی، درون متن قابل ویرایش، اشاره می‌کند.

## مقدار

یک {{jsxref("Number")}}

## مثال‌ها

### استفاده از `selectionStart` برای نمایش انتخاب کاربر در یک بوم قابل ویرایش

این مثال نشان می‌دهد که چگونه از ویژگی‌های `selectionStart` و `selectionEnd` برای رسم انتخاب فعلی در یک عنصر `<canvas>` که به یک `EditContext` متصل است، استفاده کنیم.

```html
<canvas id="editor-canvas"></canvas>
```

```js
const ANCHOR_X = 10;
const ANCHOR_Y = 30;
const FONT_SIZE = 20;

const canvas = document.getElementById("editor-canvas");
const ctx = canvas.getContext("2d");
ctx.font = `${FONT_SIZE}px Arial`;

const editContext = new EditContext({
  text: "Hello world!",
  selectionStart: 6,
  selectionEnd: 11,
});
canvas.editContext = editContext;

function render() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // ابتدا کل محتوای متن را رسم می‌کنیم.
  ctx.fillStyle = "black";
  ctx.fillText(editContext.text, ANCHOR_X, ANCHOR_Y);

  // عرض از ابتدای متن تا ابتدای انتخاب را به دست می‌آوریم.
  const selectionStartX = ctx.measureText(
    editContext.text.substring(0, editContext.selectionStart),
  );

  // عرض خود انتخاب را به دست می‌آوریم.
  const selectionWidth = ctx.measureText(
    editContext.text.substring(
      editContext.selectionStart,
      editContext.selectionEnd,
    ),
  );

  // یک مستطیل روی متن رسم می‌کنیم تا انتخاب را نمایش دهیم.
  ctx.fillStyle = "blue";
  ctx.fillRect(
    selectionStartX.width + ANCHOR_X,
    ANCHOR_Y - FONT_SIZE,
    selectionWidth.width,
    FONT_SIZE,
  );

  // فقط متن انتخاب‌شده را با رنگ سفید، روی مستطیل، دوباره رسم می‌کنیم.
  ctx.fillStyle = "white";
  ctx.fillText(
    editContext.text.substring(
      editContext.selectionStart,
      editContext.selectionEnd,
    ),
    selectionStartX.width + ANCHOR_X,
    ANCHOR_Y,
  );
}

render();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}