---
title: "Element: customElementRegistry property"
short-title: customElementRegistry
slug: Web/API/Element/customElementRegistry
page-type: web-api-instance-property
browser-compat: api.Element.customElementRegistry
---

{{APIRef("Web Components")}}

خاصیت فقط-خواندنی **`customElementRegistry`** در رابط {{domxref("Element")}}، شیء {{domxref("CustomElementRegistry")}} مرتبط با این عنصر را برمی‌گرداند، یا اگر تنظیم نشده باشد `null` را برمی‌گرداند.

`customElementRegistry` یک عنصر زمانی تنظیم می‌شود که عنصر ایجاد می‌شود (مثلاً از طریق {{domxref("Document.createElement()")}} با گزینه `customElementRegistry`، یا زمانی که در زمینه‌ای که دارای یک ثبت‌نام محدوده‌دار (scoped registry) است تجزیه می‌شود). پس از تنظیم بر روی یک شیء `CustomElementRegistry`، قابل تغییر نیست. این ثبت‌نامه تعیین می‌کند که از کدام تعاریف [عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) هنگامی که عنصر [ارتقا می‌یابد](/en-US/docs/Web/API/CustomElementRegistry/upgrade) استفاده شود.

## مقدار

یک شیء {{domxref("CustomElementRegistry")}}، یا `null`.

## مثال‌ها

### دسترسی به ثبت‌نامه عنصر سفارشی یک عنصر

این مثال یک ثبت‌نامه محدوده‌دار ایجاد می‌کند، آن را به یک ریشه سایه (shadow root) متصل می‌کند و سپس خاصیت `customElementRegistry` را از یک عنصر داخل درخت سایه می‌خواند تا تأیید کند که با ثبت‌نامه محدوده‌دار مطابقت دارد.

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

const el = shadow.querySelector("my-element");
console.log(el.customElementRegistry === myRegistry); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Document.customElementRegistry")}}
- {{domxref("ShadowRoot.customElementRegistry")}}
- {{domxref("CustomElementRegistry")}}
- [استفاده از عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements)