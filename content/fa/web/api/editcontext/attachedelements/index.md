---
title: "EditContext: attachedElements() method"
short-title: attachedElements()
slug: Web/API/EditContext/attachedElements
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.EditContext.attachedElements
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

متد **`attachedElements()`** در واسط {{domxref("EditContext")}} یک {{jsxref("Array")}} برمی‌گرداند که فقط یک آیتم دارد. این آیتم عنصری است که با شیء `EditContext` مرتبط شده است.

## نحو (Syntax)

```js-nolint
attachedElements()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Array")}} شامل یک شیء {{domxref("HTMLElement")}}.

فقط یک عنصر می‌تواند با یک نمونه `EditContext` مرتبط شود، بنابراین آرایه بازگشتی همیشه فقط یک عنصر خواهد داشت. اگر در آینده این API گسترش یابد تا از چند عنصر مرتبط پشتیبانی کند، مقدار بازگشتی آرایه‌ای شامل چند عنصر خواهد بود.

## مثال‌ها

### دریافت عنصر مرتبط با یک نمونه `EditContext`

این مثال نحوه استفاده از متد `attachedElements` را برای دریافت عنصر مرتبط با یک نمونه `EditContext` نشان می‌دهد.

```html
<canvas id="editor-canvas"></canvas>
```

```js
const canvas = document.getElementById("editor-canvas");
const editContext = new EditContext();
canvas.editContext = editContext;

const attachedElements = editContext.attachedElements();
console.log(attachedElements[0] === canvas); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- واسط {{DOMxRef("EditContext")}} که این متد به آن تعلق دارد.