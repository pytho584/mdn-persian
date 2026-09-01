---
title: "CustomElementRegistry: initialize() method"
short-title: initialize()
slug: Web/API/CustomElementRegistry/initialize
page-type: web-api-instance-method
browser-compat: api.CustomElementRegistry.initialize
---

{{APIRef("Web Components")}}

متد **`initialize()`** در رابط {{domxref("CustomElementRegistry")}} این رجیستری را با یک زیردرخت DOM مرتبط می‌کند، ویژگی {{domxref("Element.customElementRegistry", "customElementRegistry")}} را برای هر نواده‌ای که هنوز آن را ندارد (شامل خود `root`) تنظیم می‌کند، و سعی می‌کند هر [عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) یافت‌شده را ارتقا دهد.

## نحو

```js-nolint
initialize(root)
```

### پارامترها

- `root`
  - : یک شیء {{domxref("Node")}} (معمولاً یک {{domxref("Document")}}، {{domxref("ShadowRoot")}} یا {{domxref("Element")}}) که نوادگانِ شاملِ آن با این رجیستری مرتبط خواهند شد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر این `CustomElementRegistry` حوزه‌بندی‌شده نباشد (یعنی با `new CustomElementRegistry()` ساخته نشده باشد) و یا `root` یک گره {{domxref("Document")}} باشد یا {{domxref("Document.customElementRegistry", "customElementRegistry")}} سندِ گرهِ ریشه (node document) این `CustomElementRegistry` نباشد، پرتاب می‌شود.

## توضیحات

هنگامی که `initialize()` فراخوانی می‌شود، نوادگانِ شاملِ `root` را به ترتیب درخت پیمایش می‌کند. برای هر عنصر (یا خودِ ریشه اگر `Document`/`ShadowRoot` باشد) که {{domxref("Element.customElementRegistry", "customElementRegistry")}} آن `null` باشد، آن را روی این `CustomElementRegistry` تنظیم می‌کند. سپس سعی می‌کند هر عنصری را که `customElementRegistry` آن با این رجیستری مطابقت دارد [ارتقا](/en-US/docs/Web/API/CustomElementRegistry/upgrade) دهد.

پس از اینکه `customElementRegistry` یک گره روی یک شیء `CustomElementRegistry` تنظیم شد، دیگر قابل تغییر نیست. این بدان معناست که `initialize()` فقط می‌تواند رجیستری را روی گره‌هایی تنظیم کند که همچنان `null` هستند. با این حال، همچنان سعی می‌کند هر عنصری را که `customElementRegistry` آن از قبل با این رجیستری مطابقت دارد ارتقا دهد، نه فقط عناصری که تازه اختصاص داده شده‌اند.

گره‌ها در چندین وضعیت دارای رجیستری عنصر سفارشی `null` هستند، از جمله:

- سندهایی که توسط {{domxref("DOMImplementation.createHTMLDocument()")}} ایجاد شده‌اند، که رجیستری عنصر سفارشی آن‌ها به‌طور پیش‌فرض `null` است. عناصر ایجادشده در چنین سندهایی نیز رجیستری `null` دارند.
- ریشه‌های سایه (Shadow roots) که با `customElementRegistry` تنظیم‌شده روی `null` از طریق {{domxref("Element.attachShadow()")}} ایجاد شده‌اند.
- ریشه‌های سایه اعلانی (Declarative shadow roots) که از یک عنصر {{HTMLElement("template")}} با ویژگی `shadowrootcustomelementregistry` ایجاد شده‌اند، که به تجزیه‌گر HTML دستور می‌دهد رجیستری عنصر سفارشی ریشه سایه را به‌صورت `null` نگه دارد.

## مثال‌ها

### مقداردهی یک ریشه سایه با رجیستری حوزه‌بندی‌شده

این مثال یک ریشه سایه بدون رجیستری عنصر سفارشی ایجاد می‌کند، HTML حاوی یک عنصر سفارشی اضافه می‌کند، و سپس `initialize()` را برای مرتبط کردن یک رجیستری حوزه‌بندی‌شده فراخوانی می‌کند. عنصر `<my-element>` زمانی ارتقا می‌یابد که `initialize()` رجیستری را روی ریشه سایه و نوادگان آن تنظیم کند.

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

// Create the shadow DOM structure without a registry
const shadow = host.attachShadow({
  mode: "open",
  customElementRegistry: null,
});
shadow.innerHTML = "<my-element></my-element>";

// Later, associate the scoped registry and upgrade custom elements
myRegistry.initialize(shadow);

console.log(shadow.querySelector("my-element").textContent);
// "Hello from scoped registry!"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements)
- سازنده {{domxref("CustomElementRegistry.CustomElementRegistry()", "CustomElementRegistry()")}}
- {{domxref("CustomElementRegistry.define()")}}
- {{domxref("CustomElementRegistry.upgrade()")}}