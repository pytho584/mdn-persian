---
title: "EditContext: textformatupdate event"
short-title: textformatupdate
slug: Web/API/EditContext/textformatupdate_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.EditContext.textformatupdate_event
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

رویداد `textformatupdate` از رابط {{domxref("EditContext")}} زمانی فعال می‌شود که ترکیب (composition) با استفاده از یک پنجرهٔ {{glossary("Input Method Editor")}} (IME) در حال انجام باشد.

این رویداد زمانی فعال می‌شود که IME تشخیص دهد برخی قسمت‌های متن در حال ترکیب باید به‌طور متفاوتی قالب‌بندی شوند تا وضعیت ترکیب را نشان دهند.

تصویر زیر نمونه‌ای از متنی را نشان می‌دهد که با استفاده از IME ژاپنی در برنامه Notepad در ویندوز نوشته شده است. متن با یک خط زیر ضخیم فرمت شده است تا نشان دهد که از یکی از پیشنهادهای IME ترکیب شده است.

![Notepad در ویندوز با متنی ژاپنی که از پنجره IME ترکیب شده است](./ime-notepad.png)

به‌عنوان یک توسعه‌دهنده وب، باید به رویداد `textformatupdate` گوش دهید و قالب‌بندی متن نمایش‌داده‌شده در ناحیه قابل ویرایش خود را بر اساس آن به‌روزرسانی کنید.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم نمایید.

```js-nolint
addEventListener("textformatupdate", (event) => { })

ontextformatupdate = (event) => { }
```

## Event type

یک {{domxref("TextFormatUpdateEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

## Examples

### رندر کردن قالب‌بندی متن ترکیب IME

در مثال زیر، از رویداد `textformatupdate` برای به‌روزرسانی قالب‌بندی متن در ناحیه قابل ویرایش استفاده شده است. توجه داشته باشید که فراخوانی (callback) شنونده رویداد در این مثال فقط زمانی فراخوانی می‌شود که از یک پنجره IME یا سایر سطوح رابط کاربری ویرایش مختص پلتفرم برای ترکیب متن استفاده می‌کنید.

```html
<canvas id="editor-canvas"></canvas>
```

```js
const TEXT_X = 10;
const TEXT_Y = 10;

const canvas = document.getElementById("editor-canvas");
const ctx = canvas.getContext("2d");

const editContext = new EditContext();
canvas.editContext = editContext;

editContext.addEventListener("textformatupdate", (e) => {
  // Clear the canvas.
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  // Render the text.
  ctx.fillText(editContext.text, TEXT_X, TEXT_Y);

  // Get the text formats that the IME window wants to apply.
  const formats = e.getTextFormats();

  // Iterate over the text formats
  for (const format of formats) {
    const { rangeStart, rangeEnd, underlineStyle, underlineThickness } = format;

    const underlineXStart = ctx.measureText(
      editContext.text.substring(0, rangeStart),
    ).width;
    const underlineXEnd = ctx.measureText(
      editContext.text.substring(0, rangeEnd),
    ).width;
    const underlineY = TEXT_Y + 3;

    // For brevity, this example only draws a simple underline.
    // You should use the underlineStyle and underlineThickness values to draw the underline.

    ctx.beginPath();
    ctx.moveTo(TEXT_X + underlineXStart, underlineY);
    ctx.lineTo(TEXT_X + underlineXEnd, underlineY);
    ctx.stroke();
  }
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}