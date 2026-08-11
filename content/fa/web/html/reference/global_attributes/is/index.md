---
title: "is HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/is"
translated_by: "n8n + AI"
---

> **توجه:**  
> Safari برنامه‌ای برای پشتیبانی از `customized built-in elements` ندارد (به [این issue](https://github.com/WebKit/standards-positions/issues/97) مراجعه کنید) و مرورگرهای دیگر در حال بررسی راه‌حل‌های جایگزین برای سفارشی‌سازی عناصر داخلی هستند (ببینید: [این discussion](https://github.com/WICG/webcomponents/issues/1029)). برای اطلاعات پشتیبانی، بخش [سازگاری مرورگرها](#browser_compatibility) را بررسی کنید.

ویژگی سراسری **`is`** به شما امکان می‌دهد مشخص کنید که یک عنصر HTML استاندارد باید مانند یک عنصر داخلی سفارشی‌سازی‌شده‌ (customized built-in element) رفتار کند (برای جزئیات بیشتر، [استفاده از عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) را ببینید).

این ویژگی فقط زمانی قابل استفاده است که نام عنصر سفارشی مشخص‌شده در سند جاری با موفقیت [تعریف شده](/en-US/docs/Web/API/CustomElementRegistry/define) باشد و نوع عنصری که به آن اعمال می‌شود را گسترش دهد.

## مثال‌ها

کد زیر از مثال [word-count-web-component](https://github.com/mdn/web-components-examples/tree/main/word-count-web-component) گرفته شده است (همچنین [مشاهده نسخه زنده](https://mdn.github.io/web-components-examples/word-count-web-component/)).

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

## سازگاری مرورگرها

## همچنین ببینید

- تمام [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes)