---
title: "EditContext: updateControlBounds() method"
---

---
title: "EditContext: updateControlBounds() method"
short-title: updateControlBounds()
slug: Web/API/EditContext/updateControlBounds
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.EditContext.updateControlBounds
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

متد **`EditContext.updateControlBounds()`** از رابط {{domxref("EditContext")}} برای اطلاع‌رسانی به سیستم‌عامل درباره موقعیت و اندازه ناحیه متنی قابل ویرایش آبجکت `EditContext` استفاده می‌شود.

این متد را برای مشخص‌کردن مرزهای ناحیه قابل ویرایش فعلی به سیستم‌عامل صدا بزنید. باید هنگام مقداردهی اولیه `EditContext` و هر زمان که مرزهای ناحیه قابل ویرایش تغییر می‌کند (مثلاً وقتی صفحه وب تغییر اندازه می‌دهد) آن را فراخوانی کنید. این مرزها برای جای‌گذاری سطوح رابط کاربری مرتبط با ویرایش مخصوص پلتفرم، مانند پنجره {{glossary("Input Method Editor")}} (IME)، استفاده می‌شوند.

## سینتکس

```js-nolint
updateControlBounds(controlBounds)
```

### پارامترها

- `controlBounds`
  - : یک شیء {{domxref("DOMRect")}} که مرزهای کنترل جدید را نشان می‌دهد.

### مقدار بازگشتی

هیچ (`undefined`).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر متد بدون آرگومان صدا زده شود یا آرگومان ارائه‌شده یک شیء {{domxref("DOMRect")}} نباشد، پرتاب می‌شود.

## مثال‌ها

### به‌روزرسانی مرزهای کنترل هنگام مقداردهی اولیه ویرایشگر و تغییر اندازه پنجره

این مثال نشان می‌دهد که چگونه از متد `updateControlBounds()` برای اطلاع‌رسانی همیشگی به پلتفرم درباره مکان ناحیه قابل ویرایش استفاده کنید.

```css
#editor {
  border: 1px solid black;
  height: 50vw;
  width: 50vh;
}
```

```html
<div id="editor"></div>
```

```js
const editorEl = document.getElementById("editor");
const editContext = new EditContext();
editorEl.editContext = editContext;

function updateControlBounds() {
  const editorBounds = editorEl.getBoundingClientRect();
  editContext.updateControlBounds(editorBounds);
  console.log(
    `Updated control bounds to ${editorBounds.x}, ${editorBounds.y}, ${editorBounds.width}, ${editorBounds.height}`,
  );
}

// Update the control bounds now.
updateControlBounds();
// And when the page is resized.
window.addEventListener("resize", updateControlBounds);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("EditContext")}} که این متد به آن تعلق دارد.