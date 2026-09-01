---
title: "Document: customElementRegistry property"
short-title: customElementRegistry
slug: Web/API/Document/customElementRegistry
page-type: web-api-instance-property
browser-compat: api.Document.customElementRegistry
---

{{APIRef("Web Components")}}

ویژگی فقط‌خواندنی **`customElementRegistry`** در رابط {{domxref("Document")}}، شیء {{domxref("CustomElementRegistry")}} مرتبط با این سند را بازمی‌گرداند؛ یا اگر تنظیم نشده باشد، `null` را بازمی‌گرداند.

برای اسنادی که با یک {{domxref("Window")}} مرتبط هستند (مانند سند اصلی یک صفحه)، این همان `CustomElementRegistry` سراسری است که از طریق ویژگی {{domxref("window.customElements")}} نیز قابل دسترسی است. اسنادی که به‌صورت برنامه‌نویسی ایجاد می‌شوند (مثلاً از طریق {{domxref("DOMImplementation.createHTMLDocument()")}})، به‌طور پیش‌فرض رجیستری عناصر سفارشی `null` دارند.

این ویژگی در اشیاء {{domxref("ShadowRoot")}} نیز با همان نام ویژگی {{domxref("ShadowRoot/customElementRegistry","customElementRegistry")}} در دسترس است.

## مقدار

یک شیء {{domxref("CustomElementRegistry")}}، یا `null`.

## مثال‌ها

### دسترسی به رجیستری عناصر سفارشی یک سند

این مثال نشان می‌دهد که `customElementRegistry` سند اصلی همان رجیستری سراسری است که از طریق {{domxref("window.customElements")}} در دسترس است، در حالی که اسنادی که به‌صورت برنامه‌نویسی از طریق {{domxref("DOMImplementation.createHTMLDocument()")}} ایجاد می‌شوند، به‌طور پیش‌فرض رجیستری `null` دارند.

```js
// The main document's registry is the global one:
console.log(document.customElementRegistry === window.customElements); // true (for Window-associated documents)

// Documents created programmatically have a null registry:
const newDoc = document.implementation.createHTMLDocument("New document");
console.log(newDoc.customElementRegistry); // null
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ShadowRoot.customElementRegistry")}}
- {{domxref("Element.customElementRegistry")}}
- {{domxref("CustomElementRegistry")}}
- {{domxref("window.customElements")}}
- [Using custom elements](/en-US/docs/Web/API/Web_components/Using_custom_elements)