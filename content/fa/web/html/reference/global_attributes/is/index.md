---
title: "is HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/is"
translated_by: "n8n + AI"
---

> [!NOTE]
> [سافاری برنامه‌ای برای پشتیبانی از customized built-in elements ندارد](https://github.com/WebKit/standards-positions/issues/97) و [فروشندگان مرورگر در حال بررسی راه‌حل‌های جایگزین برای سفارشی‌سازی built-in ها هستند](https://github.com/WICG/webcomponents/issues/1029). برای اطلاعات پشتیبانی، بخش [سازگاری مرورگر](#سازگاری-مرورگر) را ببینید.

**`is`** یک [global attribute](/en-US/docs/Web/HTML/Reference/Global_attributes) است که به شما امکان می‌دهد مشخص کنید یک عنصر استاندارد HTML باید مانند یک customized built-in element تعریف‌شده رفتار کند (برای جزئیات بیشتر، [استفاده از custom elements](/en-US/docs/Web/API/Web_components/Using_custom_elements) را ببینید).

این attribute فقط زمانی قابل استفاده است که نام custom element مشخص‌شده با موفقیت در سند فعلی [تعریف شده](/en-US/docs/Web/API/CustomElementRegistry/define) باشد و نوع عنصری را که روی آن اعمال می‌شود گسترش دهد.

## مثال‌ها

کد زیر از مثال [word-count-web-component](https://github.com/mdn/web-components-examples/tree/main/word-count-web-component) گرفته شده است ([نسخهٔ زنده را هم ببینید](https://mdn.github.io/web-components-examples/word-count-web-component/)).

```js
// Create a class for the element
class WordCount extends HTMLParagraphElement {
  constructor() {
    // Always call super first in constructor
    super();

    // Constructor contents omitted for brevity
    // …
  }
}

// Define the new element
customElements.define("word-count", WordCount, { extends: "p" });
```

```html
<p is="word-count"></p>
```

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- همهٔ [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).