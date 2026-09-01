---
title: "ElementInternals: form property"
short-title: form
slug: Web/API/ElementInternals/form
page-type: web-api-instance-property
browser-compat: api.ElementInternals.form
---

{{APIRef("Web Components")}}

ویژگی فقط خواندنی **`form`** از رابط {{domxref("ElementInternals")}}، {{domxref("HTMLFormElement")}} مرتبط با این عنصر را باز می‌گرداند.

## مقدار

یک {{domxref("HTMLFormElement")}}.

## مثال‌ها

مثال زیر یک کامپوننت چک‌باکس سفارشی را درون یک فرم با شناسه `myForm` نشان می‌دهد. چاپ `form.length` در کنسول، مقدار {{domxref("HTMLFormElement.length")}} را به ما می‌دهد.

```html
<form id="myForm">
  <custom-checkbox id="custom-checkbox"></custom-checkbox>
  <custom-label for="custom-checkbox">Join newsletter</custom-label>
</form>
```

```js
class CustomCheckbox extends HTMLElement {
  static formAssociated = true;
  #internals;

  constructor() {
    super();
    this.#internals = this.attachInternals();
  }

  connectedCallback() {
    console.log(this.#internals.form.length);
  }
}

window.customElements.define("custom-checkbox", CustomCheckbox);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}