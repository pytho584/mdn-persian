---
title: "EditContext: updateSelection() method"
short-title: updateSelection()
slug: Web/API/EditContext/updateSelection
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.EditContext.updateSelection
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

متد **`updateSelection()`** از رابط {{domxref("EditContext")}}، وضعیت داخلی انتخاب (selection) را در بافت متنی قابل ویرایش به‌روزرسانی می‌کند. این متد برای به‌روزرسانی وضعیت انتخاب زمانی استفاده می‌شود که کاربر با متن رندر شده در عنصر مرتبط با `EditContext` تعامل برقرار می‌کند؛ مثلاً با کلیک کردن، کشیدن ماوس یا استفاده از صفحه‌کلید.

## نحو (Syntax)

```js-nolint
updateSelection(start, end)
```

### پارامترها

- `start`
  - : عددی که نقطه شروع جدید انتخاب را نشان می‌دهد.
- `end`
  - : عددی که نقطه پایان جدید انتخاب را نشان می‌دهد. اگر مقادیر `start` و `end` یکسان باشند، انتخاب معادل یک مکان‌نما (caret) خواهد بود.

### مقدار بازگشتی

هیچ (`undefined`).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر متد با کمتر از دو آرگومان فراخوانی شود، یا هر یک از آرگومان‌ها یک عدد غیرمنفی نباشد، این خطا پرتاب می‌شود.

## مثال‌ها

### به‌روزرسانی انتخاب هنگام تعامل کاربر با متن

این مثال نشان می‌دهد که چگونه می‌توان از متد `updateSelection` برای به‌روزرسانی انتخاب در `EditContext` یک عنصر `canvas` استفاده کرد، زمانی که از کلیدهای جهت‌نما برای حرکت مکان‌نما یا انتخاب متن در ناحیه قابل ویرایش استفاده می‌شود.

```html
<canvas id="editor-canvas"></canvas>
```

```js
const canvas = document.getElementById("editor-canvas");
const editContext = new EditContext();
canvas.editContext = editContext;

canvas.addEventListener("keydown", (e) => {
  if (e.key === "ArrowLeft") {
    const newPosition = Math.max(editContext.selectionStart - 1, 0);

    if (e.shiftKey) {
      editContext.updateSelection(newPosition, editContext.selectionEnd);
    } else {
      editContext.updateSelection(newPosition, newPosition);
    }
  } else if (e.key === "ArrowRight") {
    const newPosition = Math.min(
      editContext.selectionEnd + 1,
      editContext.text.length,
    );

    if (e.shiftKey) {
      editContext.updateSelection(editContext.selectionStart, newPosition);
    } else {
      editContext.updateSelection(newPosition, newPosition);
    }
  }

  console.log(
    `The new EditContext selection is ${editContext.selectionStart}, ${editContext.selectionEnd}`,
  );
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("EditContext")}} که این متد به آن تعلق دارد.