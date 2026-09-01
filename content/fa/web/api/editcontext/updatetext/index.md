---
title: "EditContext: updateText() method"
---

---
title: "EditContext: updateText() method"
short-title: updateText()
slug: Web/API/EditContext/updateText
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.EditContext.updateText
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

متد **`updateText()`** از رابط {{domxref("EditContext")}}، محتوای متنی داخلی یک شیء `EditContext` را به‌روزرسانی می‌کند.

هنگامی که کاربر متنی را در عنصر مرتبط تایپ می‌کند، نیازی به استفاده از این متد نیست. شیء `EditContext` به‌طور خودکار محتوای متنی داخلی خود را به‌روزرسانی کرده و در صورت نیاز رویدادهای {{domxref("EditContext.textupdate_event", "textupdate")}} را فعال می‌کند.

با این حال، زمانی که کاربر به روش‌های دیگری با محتوای متنی تعامل دارد، مانند چسباندن متن از کلیپ‌بورد، می‌توان از این متد استفاده کرد.

## نحو

```js-nolint
updateText(rangeStart, rangeEnd, text)
```

### پارامترها

- `rangeStart`
  - : عددی که شروع محدوده متنی را که باید جایگزین شود، نشان می‌دهد.
- `rangeEnd`
  - : عددی که پایان محدوده متنی را که باید جایگزین شود، نشان می‌دهد.
- `text`
  - : رشته‌ای که محتوای متنی جدید را نشان می‌دهد.

### مقدار بازگشتی

هیچ مقدار (`undefined`).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر متد با کمتر از سه آرگومان فراخوانده شود، پرتاب می‌شود.

## مثال‌ها

### به‌روزرسانی ویرایشگر هنگام چسباندن متن توسط کاربر

این مثال نشان می‌دهد که چگونه می‌توان از متد `updateText` برای به‌روزرسانی محتوای متنی در `EditContext` یک عنصر `<canvas>` استفاده کرد، زمانی که کاربر میان‌بر <kbd>Ctrl</kbd>/<kbd>Cmd</kbd> + <kbd>V</kbd> را برای چسباندن متن فشار می‌دهد.

این مثال همچنین از متد {{domxref("Clipboard.readText()")}} برای خواندن متن از کلیپ‌بورد استفاده می‌کند.

```html
<canvas id="editor-canvas"></canvas>
```

```js
const canvas = document.getElementById("editor-canvas");
const ctx = canvas.getContext("2d");

const editContext = new EditContext();
canvas.editContext = editContext;

function render() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.fillText(editContext.text, 0, 40);
}

editContext.addEventListener("textupdate", (e) => {
  render();
});

canvas.addEventListener("keydown", async (e) => {
  if (e.key === "v" && (e.ctrlKey || e.metaKey)) {
    const pastedText = await navigator.clipboard.readText();
    console.log(
      `The user pasted the text: ${pastedText}. Updating the EditContext text.`,
    );

    editContext.updateText(
      editContext.selectionStart,
      editContext.selectionEnd,
      pastedText,
    );

    editContext.updateSelection(
      editContext.selectionStart + pastedText.length,
      editContext.selectionStart + pastedText.length,
    );

    render();
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("EditContext")}} که این متد به آن تعلق دارد.