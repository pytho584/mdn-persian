---
title: "EditContext: EditContext() constructor"
short-title: EditContext()
slug: Web/API/EditContext/EditContext
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.EditContext.EditContext
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

سازندهی **`EditContext()`** یک شیء جدید {{DOMxRef("EditContext")}} می‌سازد و برمی‌گرداند.

## نحو

```js-nolint
new EditContext()
new EditContext(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء اختیاری با ویژگی‌های زیر:
    - `text`
      - : یک رشته (string) که متن اولیه‌ی `EditContext` را تنظیم می‌کند.
    - `selectionStart`
      - : یک عدد که نقطه‌ی شروع انتخاب اولیه‌ی `EditContext` را تنظیم می‌کند.
    - `selectionEnd`
      - : یک عدد که نقطه‌ی پایان انتخاب اولیه‌ی `EditContext` را تنظیم می‌کند.

## نمونه‌ها

### ایجاد یک شیء `EditContext`

مثال زیر یک شیء `EditContext` جدید با متن اولیه‌ی «Hello world!» و انتخاب اولیه‌ای که کل متن را پوشش می‌دهد ایجاد می‌کند.

```html
<div id="editor"></div>
```

```js
const initialText = "Hello world!";

const editContext = new EditContext({
  text: initialText,
  selectionStart: 0,
  selectionEnd: initialText.length,
});

const editorElement = document.getElementById("editor");
editorElement.editContext = editContext;

console.log(
  `EditContext object ready. Text: ${editContext.text}. Selection: ${editContext.selectionStart} - ${editContext.selectionEnd}.`,
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("EditContext")}} که این سازنده به آن تعلق دارد.
