---
title: "EditContext: text property"
short-title: text
slug: Web/API/EditContext/text
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.EditContext.text
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`text`** در رابط {{domxref("EditContext")}} محتوای قابل‌ویرایش عنصر را نمایش می‌دهد.

## مقدار

یک رشته که محتوای قابل‌ویرایش فعلی عنصر متصل به شیء `EditContext` را شامل می‌شود. مقدار اولیهٔ آن، رشتهٔ خالی است.

این رشته ممکن است با مقدار خاصیت {{domxref("Node.textContent", "textContent")}} عنصر DOM مرتبط با `EditContext` برابر باشد یا نباشد. برای مثال، عنصر مرتبط می‌تواند یک عنصر `<canvas>` باشد که خاصیت `textContent` ندارد. یا عنصر مرتبط می‌تواند یک عنصر `<div>` باشد که متنی متفاوت از مقدار `EditContext.text` را برای رندر پیشرفته‌تر در خود جای می‌دهد.

خاصیت `text` شیء `EditContext` می‌تواند به‌عنوان مدل ناحیهٔ متن قابل‌ویرایش استفاده شود. سایر ویژگی‌های شیء `EditContext` مانند `selectionStart` و `selectionEnd` به آفست‌هایی درون رشتهٔ `text` اشاره می‌کنند.

## مثال‌ها

### استفاده از `text` برای رندر کردن متن در یک بوم قابل‌ویرایش

در مثال زیر، از EditContext API برای رندر کردن متنی که کاربر در یک عنصر `<canvas>` وارد می‌کند، استفاده شده است.

```html
<canvas id="editor-canvas"></canvas>
```

```js
const canvas = document.getElementById("editor-canvas");
const ctx = canvas.getContext("2d");
const editContext = new EditContext();
canvas.editContext = editContext;

editContext.addEventListener("textupdate", (e) => {
  // When the user has focus on the <canvas> and enters text,
  // this event is fired, and we use it to re-render the text.
  console.log(
    `The user entered the text: ${e.text}. Re-rendering the full EditContext text`,
  );
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.fillText(editContext.text, 10, 10);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}