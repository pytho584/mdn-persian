---
title: "EditContext: compositionend event"
---

---
title: "EditContext: compositionend event"
short-title: compositionend
slug: Web/API/EditContext/compositionend_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.EditContext.compositionend_event
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

رویداد `compositionend` در رابط {{domxref("EditContext")}} زمانی رخ می‌دهد که فرایند ترکیب متن با استفاده از یک پنجرهٔ ویرایشگر روش ورودی ({{glossary("Input Method Editor")}} به‌اختصار IME) به پایان برسد.

## نحو

برای استفاده از این رویداد، می‌توانید نام آن را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید یا یک ویژگی مدیریت‌کنندهٔ رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("compositionend", (event) => { })

oncompositionend = (event) => { }
```

## مثال‌ها

### استفاده از `compositionend` برای تغییر حاشیهٔ ناحیهٔ قابل ویرایش

در مثال زیر، وقتی رویداد `compositionstart` رخ می‌دهد، رنگ حاشیهٔ ناحیهٔ قابل ویرایش قرمز می‌شود و با رخ دادن رویداد `compositionend` دوباره به سیاه تغییر می‌کند. توجه داشته باشید که فراخوانی‌های شنوندهٔ رویداد (event listener callbacks) در این مثال فقط زمانی فراخوانی می‌شوند که برای ترکیب متن از یک پنجرهٔ IME یا سایر رابط‌های کاربری ویرایش ویژهٔ پلتفرم استفاده کنید.

```css
#text-editor {
  border: 1px solid black;
}
#text-editor.is-composing {
  border-color: red;
}
```

```html
<div id="text-editor"></div>
```

```js
const editorElement = document.getElementById("text-editor");
const editContext = new EditContext();
editorElement.editContext = editContext;

editContext.addEventListener("compositionstart", (event) => {
  editorElement.classList.add("is-composing");
});

editContext.addEventListener("compositionend", (event) => {
  editorElement.classList.remove("is-composing");
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}