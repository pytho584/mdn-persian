---
title: "CustomElementRegistry: CustomElementRegistry() constructor"
short-title: CustomElementRegistry()
slug: Web/API/CustomElementRegistry/CustomElementRegistry
page-type: web-api-constructor
browser-compat: api.CustomElementRegistry.CustomElementRegistry
---

{{APIRef("Web Components")}}

سازندهی **`CustomElementRegistry()`** یک شیء جدید {{domxref("CustomElementRegistry")}} برای استفادهی محدودشده (scoped) ایجاد می‌کند.

این سازنده به‌طور خاص برای ایجاد رجیستری‌های محدودشده استفاده می‌شود که تعریف [custom element](/en-US/docs/Web/API/Web_components/Using_custom_elements) را به یک حوزهی خاص، مانند یک عنصر یا {{domxref("ShadowRoot")}} محدود می‌کنند.

> [!NOTE]
> شیء سراسری `CustomElementRegistry` مرتبط با یک {{domxref("Window")}} با استفاده از این سازنده ساخته نمی‌شود؛ این شیء به‌طور خودکار هنگام راه‌اندازی پنجره ایجاد می‌شود و از طریق ویژگی {{domxref("window.customElements")}} در دسترس است.

## Syntax

```js-nolint
new CustomElementRegistry()
```

### Parameters

هیچ‌کدام.

### Return value

یک شیء جدید {{domxref("CustomElementRegistry")}}.

## Description

وقتی یک `CustomElementRegistry` را با استفاده از `new CustomElementRegistry()` می‌سازید، رجیستری حاصل به‌عنوان _محدودشده_ در نظر گرفته می‌شود. این یعنی:

- تعریف‌های عناصر سفارشی که با استفاده از {{domxref("CustomElementRegistry.define", "define()")}} به آن اضافه می‌شوند، به‌صورت سراسری در دسترس نیستند. آن‌ها فقط روی گره‌هایی اعمال می‌شوند که با این رجیستری مرتبط شده‌اند.
- این رجیستری از گزینهی `extends` در `define()` پشتیبانی نمی‌کند (برای ایجاد [customized built-in elements](/en-US/docs/Web/API/Web_components/Using_custom_elements#types_of_custom_element)). تلاش برای استفاده از `extends` با یک رجیستری محدودشده، یک `NotSupportedError` {{domxref("DOMException")}} پرتاب می‌کند.

برای مرتبط‌کردن یک رجیستری محدودشده با یک زیردرخت DOM، می‌توانید از متد {{domxref("CustomElementRegistry.initialize()", "initialize()")}} استفاده کنید، آن را به {{domxref("Element.attachShadow()")}} ارسال کنید، یا از گزینهی `customElementRegistry` متد {{domxref("Document.createElement()")}} استفاده کنید.

## Examples

### Creating a scoped custom element registry

این مثال یک رجیستری محدودشده ایجاد می‌کند، یک عنصر سفارشی روی آن تعریف می‌کند و رجیستری را به {{domxref("Element.attachShadow()")}} ارسال می‌کند. وقتی HTML حاوی `<my-element>` به ریشهی سایه اضافه می‌شود، عنصر با استفاده از تعریف رجیستری محدودشده ارتقا می‌یابد.

```js
const myRegistry = new CustomElementRegistry();

myRegistry.define(
  "my-element",
  class extends HTMLElement {
    connectedCallback() {
      this.textContent = "Hello from scoped registry!";
    }
  },
);

const host = document.createElement("div");
document.body.appendChild(host);
const shadow = host.attachShadow({
  mode: "open",
  customElementRegistry: myRegistry,
});
shadow.innerHTML = "<my-element></my-element>";

console.log(shadow.querySelector("my-element").textContent);
// "Hello from scoped registry!"
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using custom elements](/en-US/docs/Web/API/Web_components/Using_custom_elements)
- {{domxref("CustomElementRegistry.initialize()")}}
- {{domxref("CustomElementRegistry.define()")}}