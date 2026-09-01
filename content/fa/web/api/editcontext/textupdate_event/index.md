---
title: "EditContext: textupdate event"
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

رویداد `textupdate` از رابط {{domxref("EditContext")}} زمانی رخ می‌دهد که کاربر تغییراتی در متن یا انتخاب (selection) یک ناحیه قابل ویرایش که به یک نمونه `EditContext` متصل است، ایجاد کرده باشد.

این رویداد امکان رندر کردن متن و انتخاب به‌روز شده در رابط کاربری (UI) را در پاسخ به ورودی کاربر فراهم می‌کند.

## Syntax

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی event handler تنظیم کنید.

```js-nolint
addEventListener("textupdate", (event) => { })

ontextupdate = (event) => { }
```

## Event type

یک {{domxref("TextUpdateEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

## Examples

### رندر کردن متن به‌روز شده در `textupdate`

در مثال زیر، از رویداد `textupdate` API EditContext برای رندر کردن متنی که کاربر در یک عنصر `<canvas>` قابل ویرایش وارد می‌کند، استفاده شده است.

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
    `The user entered the text: ${e.text} at ${e.updateRangeStart}. Re-rendering the full EditContext text`,
  );
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.fillText(editContext.text, 10, 10);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}