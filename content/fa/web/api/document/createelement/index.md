---
title: "Document: createElement() method"
---

---
title: "Document: createElement() method"
short-title: createElement()
slug: Web/API/Document/createElement
page-type: web-api-instance-method
browser-compat: api.Document.createElement
---

{{APIRef("DOM")}}

متد **`createElement()`** در رابط {{domxref("Document")}} یک {{domxref("HTMLElement")}} جدید ایجاد می‌کند که `localName` مشخص‌شده را دارد.

اگر `localName` شناسایی نشود، متد یک {{domxref("HTMLUnknownElement")}} می‌سازد.

## سینتکس

```js-nolint
createElement(localName)
createElement(localName, options)
```

### پارامترها

- `localName`
  - : رشته‌ای که نوع عنصر مورد ایجاد را مشخص می‌کند. در این متد از نام‌های دارای پیشوند (مانند «html:a») استفاده نکنید. وقتی روی یک سند HTML فراخوانی شود، `createElement()` قبل از ایجاد عنصر، `localName` را به حروف کوچک تبدیل می‌کند. در Firefox، Opera و Chrome، `createElement(null)` مانند `createElement("null")` عمل می‌کند.
- `options` {{Optional_Inline}}
  - : یک شی با ویژگی‌های اختیاری زیر (توجه داشته باشید که فقط یکی از `is` و `customElementRegistry` می‌تواند تنظیم شود):
    - `is` {{Optional_Inline}}
      - : رشته‌ای که نام تگ را برای یک عنصر سفارشی که قبلاً با {{domxref("CustomElementRegistry/define", "customElements.define()")}} تعریف شده است، تعیین می‌کند. عنصر جدید یک ویژگی `is` دریافت می‌کند که مقدار آن نام تگ عنصر سفارشی است. برای جزئیات بیشتر به [مثال کامپوننت وب](#web_component_example) مراجعه کنید.
    - `customElementRegistry` {{Optional_Inline}}
      - : یک {{domxref("CustomElementRegistry")}} که [ثبت‌کننده عنصر سفارشی محدوده‌دار](/en-US/docs/Web/API/Web_components/Using_custom_elements#scoped_custom_element_registries) یک عنصر سفارشی را تنظیم می‌کند.

### مقدار بازگشتی

عنصر جدید {{domxref("Element")}}.

> [!NOTE]
> اگر سند یک {{domxref("HTMLDocument", "HTMLDocument", "", "1")}} باشد (که معمول‌ترین حالت است)، یک {{domxref("HTMLElement", "HTMLElement", "", "1")}} جدید بازگردانده می‌شود. در غیر این صورت یک {{domxref("Element","Element","","1")}} جدید بازگردانده می‌شود.

### استثناها

- `InvalidCharacterError` {{domxref("DOMException")}}
  - : اگر مقدار [`localName`](#localname) نام عنصر معتبری نباشد، پرتاب می‌شود. یک رشته نام عنصر معتبر است اگر طول آن حداقل ۱ باشد و:
    - با یک حرف الفبا شروع شود و شامل فضای خالی ASCII، `NULL`، `/` یا `>` (به ترتیب U+0000، U+002F یا U+003E) نباشد.
    - با `:` (U+003A)، `_` (U+005F) یا هر کاراکتری در محدوده U+0080 تا U+10FFFF (شامل) شروع شود، _و_ بقیه کدپوینت‌ها فقط شامل همان کاراکترها به همراه کاراکترهای الفبایی-عددی ASCII، `-` (U+002D) و `.` (U+002E) باشند.

    > [!NOTE]
    > نسخه‌های قبلی مشخصات محدودتر بودند و نیاز داشتند که `localName` یک [نام XML](https://www.w3.org/TR/xml/#dt-name) معتبر باشد.

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر هر دو گزینه [`is`](#is) و [`customElementRegistry`](#customelementregistry) مشخص شده باشند، پرتاب می‌شود.

## مثال‌ها

### مثال پایه

این مثال یک `<div>` جدید ایجاد می‌کند و آن را قبل از عنصری با شناسه `div1` درج می‌کند.

#### HTML

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Working with elements</title>
  </head>
  <body>
    <div id="div1">The text above has been created dynamically.</div>
  </body>
</html>
```

#### JavaScript

```js
function addElement() {
  // create a new div element
  const newDiv = document.createElement("div");

  // and give it some content
  const newContent = document.createTextNode("Hi there and greetings!");

  // add the text node to the newly created div
  newDiv.appendChild(newContent);

  // add the newly created element and its content into the DOM
  const currentDiv = document.getElementById("div1");
  document.body.insertBefore(newDiv, currentDiv);
}

addElement();
```

#### نتیجه

{{EmbedLiveSample("Basic_example", 500, 80)}}

### مثال کامپوننت وب

> [!NOTE]
> برای پشتیبانی، بخش [سازگاری مرورگر](#browser_compatibility) را بررسی کنید، و برای نکات مربوط به واقعیت پیاده‌سازی عناصر داخلی سفارشی‌شده، به مرجع ویژگی [`is`](/en-US/docs/Web/HTML/Reference/Global_attributes/is) مراجعه کنید.

قطعه کد مثال زیر از مثال [expanding-list-web-component](https://github.com/mdn/web-components-examples/tree/main/expanding-list-web-component) ما گرفته شده است ([همچنین نسخه زنده آن را ببینید](https://mdn.github.io/web-components-examples/expanding-list-web-component/)). در این مورد، عنصر سفارشی ما از {{domxref("HTMLUListElement")}} ارث می‌برد که عنصر {{htmlelement("ul")}} را نمایش می‌دهد.

```js
// Create a class for the element
class ExpandingList extends HTMLUListElement {
  constructor() {
    // Always call super first in constructor
    super();

    // constructor definition left out for brevity
    // …
  }
}

// Define the new element
customElements.define("expanding-list", ExpandingList, { extends: "ul" });
```

اگر بخواهیم نمونه‌ای از این عنصر را به صورت برنامه‌نویسی ایجاد کنیم، از فراخوانی‌ای به شکل زیر استفاده می‌کنیم:

```js
let expandingList = document.createElement("ul", { is: "expanding-list" });
```

عنصر جدید یک ویژگی [`is`](/en-US/docs/Web/HTML/Reference/Global_attributes/is) دریافت می‌کند که مقدار آن نام تگ عنصر سفارشی است.

> [!NOTE]
> برای سازگاری با عقب، برخی مرورگرها به شما اجازه می‌دهند به جای یک شیء، یک رشته در اینجا پاس دهید، که مقدار رشته نام تگ عنصر سفارشی است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.removeChild()")}}
- {{domxref("Node.replaceChild()")}}
- {{domxref("Node.appendChild()")}}
- {{domxref("Node.insertBefore()")}}
- {{domxref("Node.hasChildNodes()")}}
- {{domxref("document.createElementNS()")}} — برای مشخص کردن صریح URI فضای نام عنصر.