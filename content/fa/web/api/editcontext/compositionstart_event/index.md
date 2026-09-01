---
title: "EditContext: compositionstart event"
short-title: compositionstart
slug: Web/API/EditContext/compositionstart_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.EditContext.compositionstart_event
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

رویداد `compositionstart` از رابط {{domxref("EditContext")}} زمانی رخ می‌دهد که ترکیب متن با استفاده از پنجرهٔ {{glossary("Input Method Editor")}} (IME) آغاز می‌شود.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی مدیریت‌کنندهٔ رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("compositionstart", (event) => { })

oncompositionstart = (event) => { }
```

## مثال‌ها

### استفاده از `compositionstart` برای تغییر حاشیهٔ ناحیهٔ قابل ویرایش

در مثال زیر، حاشیهٔ ناحیهٔ قابل ویرایش هنگام رخ دادن رویداد `compositionstart` قرمز می‌شود و هنگام رخ دادن رویداد `compositionend` به رنگ مشکی برمی‌گردد. توجه داشته باشید که فراخوانی‌های مدیریت‌کنندهٔ رویداد در این مثال فقط زمانی فراخوانی می‌شوند که از پنجرهٔ IME یا سایر رابط‌های ویرایش مختص پلتفرم برای ترکیب متن استفاده کنید.

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

## سازگاری مرورگر

{{Compat}}