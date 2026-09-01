---
title: "EditContext: selectionEnd property"
short-title: selectionEnd
slug: Web/API/EditContext/selectionEnd
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.EditContext.selectionEnd
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`selectionEnd`** در رابط {{domxref("EditContext")}} به آفست (موقعیت) پایان انتخاب فعلی، درون متن قابل ویرایش اشاره می‌کند.

## مقدار

یک {{jsxref("Number")}}

## مثال‌ها

### استفاده از `selectionEnd` برای نمایش انتخاب کاربر در یک canvas قابل ویرایش

این مثال نحوه استفاده از ویژگی‌های `selectionStart` و `selectionEnd` را برای رسم انتخاب فعلی در یک عنصر `<canvas>` که به یک `EditContext` متصل شده است، نشان می‌دهد.

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

  // ابتدا کل محتوای متن را رسم کنید.
  ctx.fillStyle = "black";
  ctx.fillText(editContext.text, ANCHOR_X, ANCHOR_Y);

  // عرض را از ابتدای متن تا ابتدای انتخاب به دست آورید.
  const selectionStartX = ctx.measureText(
    editContext.text.substring(0, editContext.selectionStart),
  );

  // عرض انتخاب را به دست آورید.
  const selectionWidth = ctx.measureText(
    editContext.text.substring(
      editContext.selectionStart,
      editContext.selectionEnd,
    ),
  );

  // یک مستطیل روی متن رسم کنید تا انتخاب را نشان دهد.
  ctx.fillStyle = "blue";
  ctx.fillRect(
    selectionStartX.width + ANCHOR_X,
    ANCHOR_Y - FONT_SIZE,
    selectionWidth.width,
    FONT_SIZE,
  );

  // فقط متن انتخاب‌شده را با رنگ سفید، روی مستطیل دوباره رسم کنید.
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