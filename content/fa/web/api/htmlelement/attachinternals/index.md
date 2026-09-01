---
title: "HTMLElement: attachInternals() method"
short-title: attachInternals()
slug: Web/API/HTMLElement/attachInternals
page-type: web-api-instance-method
browser-compat: api.HTMLElement.attachInternals
---

{{APIRef("Web Components")}}

متد **`HTMLElement.attachInternals()`** یک شیء {{domxref("ElementInternals")}} برمی‌گرداند. این متد به یک [عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) اجازه می‌دهد در فرم‌های HTML شرکت کند. رابط `ElementInternals` ابزارهایی برای کار با این عناصر به همان روشی که با هر عنصر فرم استاندارد HTML کار می‌کنید فراهم می‌کند و همچنین [Accessibility Object Model](https://wicg.github.io/aom/explainer.html) (مدل شیء دسترسی‌پذیری) را در معرض عنصر قرار می‌دهد.

## Syntax

```js-nolint
attachInternals()
```

### Parameters

هیچکدام.

### Return value

یک شیء {{domxref("ElementInternals")}}.

### Exceptions

- `NotSupportedError` {{domxref("DOMException")}}
  - اگر عنصر یک عنصر سفارشی نباشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - اگر ویژگی «internals» به عنوان بخشی از تعریف عنصر غیرفعال شده باشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - اگر این متد دو بار روی یک عنصر فراخوانی شود، پرتاب می‌شود.

## Examples

مثال زیر نحوه ایجاد یک عنصر سفارشی مرتبط با فرم با استفاده از `HTMLElement.attachInternals` را نشان می‌دهد. سپس ویژگی {{domxref("ElementInternals.form")}} در کنسول چاپ می‌شود تا نشان دهد که یک شیء {{domxref("ElementInternals")}} داریم.

```js
class CustomCheckbox extends HTMLElement {
  static formAssociated = true;

  constructor() {
    super();
    this.internals_ = this.attachInternals();
  }
  // …
}

window.customElements.define("custom-checkbox", CustomCheckbox);

let element = document.getElementById("custom-checkbox");
console.log(element.internals_.form);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [کنترل‌های فرم توانمندتر](https://web.dev/articles/more-capable-form-controls)
- [ایجاد کنترل‌های فرم سفارشی با ElementInternals](https://css-tricks.com/creating-custom-form-controls-with-elementinternals/)