---
title: "CustomElementRegistry: getName() method"
short-title: getName()
slug: Web/API/CustomElementRegistry/getName
page-type: web-api-instance-method
browser-compat: api.CustomElementRegistry.getName
---

{{APIRef("Web Components")}}

متد **`getName()`** از رابط {{domxref("CustomElementRegistry")}} نام یک عنصر سفارشی که قبلاً تعریف شده است را بازمی‌گرداند.

## نحو

```js-nolint
getName(constructor)
```

### پارامترها

- `constructor`
  - سازنده (constructor) عنصر سفارشی.

### مقدار بازگشتی

نام عنصر سفارشی که قبلاً تعریف شده است، یا `null` اگر هیچ عنصر سفارشی با این سازنده تعریف نشده باشد.

## مثال‌ها

```js
class MyParagraph extends HTMLElement {
  constructor() {
    const template = document.getElementById("custom-paragraph");
    super() // returns element this scope
      .attachShadow({ mode: "open" }) // sets AND returns this.shadowRoot
      .append(document.importNode(template.content, true));
  }
}

customElements.define("my-paragraph", MyParagraph);

// Return a reference to the my-paragraph constructor
customElements.getName(MyParagraph) === "my-paragraph";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}