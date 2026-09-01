---
title: "EditContext: characterboundsupdate event"
short-title: characterboundsupdate
slug: Web/API/EditContext/characterboundsupdate_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.EditContext.characterboundsupdate_event
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

رویداد `characterboundsupdate` زمانی رخ می‌دهد که سیستم عامل نیاز به دانستن مرزهای (مختصات) برخی نویسه‌ها در ناحیهٔ متنی قابل ویرایشِ شیء `EditContext` داشته باشد.

این وضعیت وقتی پیش می‌آید که سیستم عامل بخواهد یک رابط کاربری مربوط به ویرایش را که مخصوص پلتفرم است، مانند پنجرهٔ {{glossary("Input Method Editor", "ویرایشگر ورودی (IME)")}}، نمایش دهد.

وقتی رویداد `characterboundsupdate` رخ می‌دهد، باید مرزهای نویسه‌ها را برای متن محاسبه کرده و سپس متد {{domxref("EditContext.updateCharacterBounds()")}} را فراخوانی کنید تا اطلاعات مورد نیاز سیستم عامل در اختیارش قرار گیرد.

برای اطلاعات بیشتر دربارهٔ زمان و نحوهٔ استفاده از رویداد `characterboundsupdate`، مستندات متد {{domxref("EditContext.updateCharacterBounds()", "updateCharacterBounds")}} را ببینید.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کنندهٔ رویداد تنظیم کنید.

```js-nolint
addEventListener("characterboundsupdate", (event) => { })

oncharacterboundsupdate = (event) => { }
```

## نوع رویداد

یک {{domxref("CharacterBoundsUpdateEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

## مثال‌ها

### به‌روزرسانی مرزهای نویسه‌ها در صورت نیاز

این مثال نشان می‌دهد چگونه از متد `updateCharacterBounds` برای به‌روزرسانی مرزهای نویسه‌ها در `EditContext` مربوط به یک عنصر `canvas` استفاده کنید، زمانی که سیستم عامل اعلام می‌کند به این اطلاعات نیاز دارد. توجه داشته باشید که فراخوانِ رویداد فقط هنگام استفاده از پنجرهٔ IME یا سایر رابط‌های ویرایش مخصوص پلتفرم برای ترکیب متن فراخوانی می‌شود.

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
  // عرض از ابتدای متن تا نویسهٔ موردنظر را اندازه بگیر.
  const widthBeforeChar = ctx.measureText(
    editContext.text.substring(0, offset),
  ).width;

  // عرض نویسه را اندازه بگیر.
  const charWidth = ctx.measureText(editContext.text[offset]).width;

  const charX = canvas.offsetLeft + widthBeforeChar;
  const charY = canvas.offsetTop;

  // یک DOMRect representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing representing