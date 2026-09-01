---
title: "CustomElementRegistry: get() method"
short-title: get()
slug: Web/API/CustomElementRegistry/get
page-type: web-api-instance-method
browser-compat: api.CustomElementRegistry.get
---

{{APIRef("Web Components")}}

متد **`get()`** از رابط {{domxref("CustomElementRegistry")}} سازنده (constructor) یک عنصر سفارشی که قبلاً تعریف شده است را بازمی‌گرداند.

## نحو (Syntax)

```js-nolint
get(name)
```

### پارامترها

- `name`
  - : نام عنصر سفارشی.

### مقدار بازگشتی

سازنده عنصر سفارشی با نام مشخص شده، یا {{jsxref("undefined")}} اگر هیچ عنصر سفارشی با این نام تعریف نشده باشد.

## مثال‌ها

```js
customElements.define(
  "my-paragraph",
  class extends HTMLElement {
    constructor() {
      const template = document.getElementById("custom-paragraph");
      super() // returns element this scope
        .attachShadow({ mode: "open" }) // sets AND returns this.shadowRoot
        .append(document.importNode(template.content, true));
    }
  },
);

// Return a reference to the my-paragraph constructor
const ctor = customElements.get("my-paragraph");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}