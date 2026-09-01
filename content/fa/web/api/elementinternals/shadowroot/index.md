---
title: "ElementInternals: shadowRoot property"
---

---
title: "ElementInternals: shadowRoot property"
short-title: shadowRoot
slug: Web/API/ElementInternals/shadowRoot
page-type: web-api-instance-property
browser-compat: api.ElementInternals.shadowRoot
---

{{APIRef("Web Components")}}

ویژگی فقط‌خواندنی **`shadowRoot`** در رابط {{domxref("ElementInternals")}}، {{domxref("ShadowRoot")}} مربوط به این عنصر را برمی‌گرداند.

## مقدار

در صورتی که عنصر دارای shadow root باشد، یک {{domxref("ShadowRoot")}} برمی‌گرداند؛ در غیر این صورت `null` برمی‌گرداند.

## مثال‌ها

در مثال زیر، مقدار `shadowRoot` بلافاصله پس از فراخوانی {{domxref("HTMLElement.attachInternals()")}} در کنسول چاپ می‌شود. در این لحظه مقدار آن `null` است. پس از فراخوانی {{domxref("Element.attachShadow()")}}، عنصر دارای Shadow Root می‌شود و `shadowRoot` آبجکتِ متناظر با آن را بازمی‌گرداند.

```js
class MyCustomElement extends HTMLElement {
  constructor() {
    super();
    this.internals_ = this.attachInternals();

    console.log(this.internals_.shadowRoot); // null

    this.attachShadow({ mode: "open" });

    console.log(this.internals_.shadowRoot); // a ShadowRoot object
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}