---
title: "EditContext: updateCharacterBounds() method"
short-title: updateCharacterBounds()
slug: Web/API/EditContext/updateCharacterBounds
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.EditContext.updateCharacterBounds
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

متد **`EditContext.updateCharacterBounds()`** از رابط {{domxref("EditContext")}} باید به‌عنوان پاسخی به رویداد {{domxref("EditContext.characterboundsupdate_event", "characterboundsupdate")}} فراخوانی شود تا موقعیت و اندازه کاراکترهای موجود در شیء `EditContext` را به سیستم‌عامل اطلاع دهد.

رویداد `characterboundsupdate` تنها زمانی است که باید متد `updateCharacterBounds()` را فراخوانی کنید.

اطلاعات مرزهای کاراکتر سپس توسط سیستم‌عامل برای موقعیت‌دهی صحیح پنجره {{glossary("Input Method Editor")}} (IME) در صورت نیاز استفاده می‌شود. این موضوع به‌ویژه در شرایطی اهمیت دارد که سیستم‌عامل قادر به تشخیص خودکار موقعیت و اندازه کاراکترها نیست، مانند زمانی که متن در یک عنصر `<canvas>` رندر می‌شود.

## نحو

```js-nolint
updateCharacterBounds(rangeStart, characterBounds)
```

### پارامترها

- `rangeStart`
  - : عددی که شروع محدوده متنی را که مرزهای کاراکتر برای آن ارائه شده است، مشخص می‌کند.
- `characterBounds`
  - : یک {{jsxref("Array")}} شامل اشیاء {{domxref("DOMRect")}} که مرزهای کاراکتر را نشان می‌دهد.

### مقدار بازگشتی

هیچ (`undefined`).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر متد با کمتر از دو آرگومان فراخوانی شود، یا اگر آرگومان اول عدد نباشد یا آرگومان دوم یک تکرارپذیر (مانند آرایه) نباشد، پرتاب می‌شود.

## نکات استفاده

### جلوگیری از پرش‌های ناگهانی در موقعیت پنجره IME

محاسبه مرزهای کاراکتر و فراخوانی `updateCharacterBounds` به‌صورت همزمان، درون رویداد `characterboundsupdate` تضمین می‌کند که سیستم‌عامل هنگام نمایش پنجره IME اطلاعات لازم را در اختیار دارد. اگر `updateCharacterBounds()` را به‌صورت همزمان درون کنترل‌کننده رویداد فراخوانی نکنید، کاربران ممکن است مشاهده کنند که پنجره IME ابتدا در موقعیت اشتباه نمایش داده می‌شود و سپس به موقعیت صحیح منتقل می‌شود.

### کدام کاراکترها را شامل شود

متد `updateCharacterBounds()` فقط زمانی باید فراخوانی شود که سیستم‌عامل نشان دهد به این اطلاعات نیاز دارد، و تنها برای کاراکترهایی که در ترکیب IME فعلی قرار دارند.

شیء رویداد ارسالی به کنترل‌کننده رویداد `characterboundsupdate` شامل ویژگی‌های `rangeStart` و `rangeEnd` است که محدوده کاراکترهای در حال ترکیب را نشان می‌دهد. متد `updateCharacterBounds()` فقط باید برای کاراکترهای این محدوده فراخوانی شود.

## مثال‌ها

### به‌روزرسانی مرزهای کاراکتر در صورت نیاز

این مثال نشان می‌دهد چگونه از متد `updateCharacterBounds` برای به‌روزرسانی مرزهای کاراکتر در `EditContext` یک عنصر `<canvas>` استفاده کنید، زمانی که سیستم‌عامل نشان دهد به این اطلاعات نیاز دارد. توجه داشته باشید که فراخوانی تابع کنترل‌کننده رویداد `characterboundsupdate` در این مثال فقط زمانی انجام می‌شود که از یک پنجره IME یا سایر سطوح ویرایشی مخصوص پلتفرم برای ترکیب متن استفاده می‌شود.

```html
<canvas id="editor-canvas"></canvas>
```

```js
const FONT_SIZE = 40;
const FONT = `${FONT_SIZE}px Arial`;

const canvas = document.getElementById("editor-canvas");
const ctx = canvas.getContext("2d");
ctx.font = FONT;

const editContext = new EditContext();
canvas.editContext = editContext;

function computeCharacterBound(offset) {
  // Measure the width from the start of the text to the character.
  const widthBeforeChar = ctx.measureText(
    editContext.text.substring(0, offset),
  ).width;

  // Measure the character width.
  const charWidth = ctx.measureText(editContext.text[offset]).width;

  const charX = canvas.offsetLeft + widthBeforeChar;
  const charY = canvas.offsetTop;

  // Return a DOMRect representing the character bounds.
  return DOMRect.fromRect({
    x: charX,
    y: charY - FONT_SIZE,
    width: charWidth,
    height: FONT_SIZE,
  });
}

editContext.addEventListener("characterboundsupdate", (e) => {
  const charBounds = [];
  for (let offset = e.rangeStart; offset < e.rangeEnd; offset++) {
    charBounds.push(computeCharacterBound(offset));
  }

  editContext.updateCharacterBounds(e.rangeStart, charBounds);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- رابط {{DOMxRef("EditContext")}} که این متد به آن تعلق دارد.