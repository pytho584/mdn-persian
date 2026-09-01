---
title: "Document: createElementNS() method"
short-title: createElementNS()
slug: Web/API/Document/createElementNS
page-type: web-api-instance-method
browser-compat: api.Document.createElementNS
---

{{APIRef("DOM")}}

متد **`createElementNS()`** در رابط {{domxref("Document")}} یک عنصر جدید با شناسه‌ی فضای نام (namespace URI) و نام واجد شرایط (qualified name) مشخص ایجاد می‌کند.

این متد در اسنادی که چند فضای نام دارند، مانند SVG یا MathML تعبیه‌شده در HTML مفید است، جایی که تجزیه‌گر (parser) نمی‌تواند به‌طور مطمئن فضای نام را استنتاج کند.

اگر می‌خواهید یک عنصر HTML ساده ایجاد کنید، متد {{DOMxRef("Document.createElement()", "createElement()")}} ساده‌تر است.

## نحو (Syntax)

```js-nolint
createElementNS(namespaceURI, qualifiedName)
createElementNS(namespaceURI, qualifiedName, options)
```

### پارامترها

- `namespaceURI`
  - : رشته‌ای که {{DOMxRef("element.namespaceURI", "namespaceURI")}} مرتبط با عنصر را مشخص می‌کند. برخی از شناسه‌های فضای نام مهم عبارتند از:
    - [HTML](/en-US/docs/Web/HTML)
      - : `http://www.w3.org/1999/xhtml`
    - [SVG](/en-US/docs/Web/SVG)
      - : `http://www.w3.org/2000/svg`
    - [MathML](/en-US/docs/Web/MathML)
      - : `http://www.w3.org/1998/Math/MathML`

- `qualifiedName`
  - : رشته‌ای شامل نام واجد شرایط عنصر جدید.
    ویژگی {{DOMxRef("node.nodeName", "nodeName")}} عنصر ایجادشده با این مقدار مقداردهی اولیه می‌شود.

    قالب نام واجد شرایط به شکل `prefix:localName` یا `localName` است که اجزای آن به این صورت تعریف می‌شوند:
    - `prefix` {{optional_inline}}
      - : یک «نام مستعار کوتاه» برای فضای نام.
        پیشوند اختیاری است، اما اگر مشخص شود، پارامتر `namespaceURI` نیز باید مشخص شود.
        اگر پیشوند روی `xml` یا `xmlns` تنظیم شود، `namespaceURI` باید به ترتیب `http://www.w3.org/XML/1998/namespace` یا `http://www.w3.org/2000/xmlns/` باشد.

        این مقدار برای مقداردهی اولیه ویژگی {{DOMxRef("Element/prefix", "prefix")}} عنصر جدید استفاده می‌شود.
        به‌طور پیش‌فرض `null` است.

    - `localName`
      - : نام محلی عنصر.
        این مقدار برای مقداردهی اولیه ویژگی {{DOMxRef("Element.localName", "localName")}} عنصر جدید استفاده می‌شود.

- `options` {{Optional_Inline}}
  - : شیءای با ویژگی‌های اختیاری زیر (توجه داشته باشید که فقط یکی از `is` و `customElementRegistry` می‌تواند تنظیم شود):
    - `is` {{Optional_Inline}}
      - : رشته‌ای که نام تگ عنصر سفارشی را که قبلاً با {{domxref("CustomElementRegistry/define", "customElements.define()")}} تعریف شده است، مشخص می‌کند.
        عنصر جدید یک ویژگی `is` دریافت می‌کند که مقدار آن نام تگ عنصر سفارشی است.
    - `customElementRegistry` {{Optional_Inline}}
      - : یک {{domxref("CustomElementRegistry")}} که [ثبت‌نامه عناصر سفارشی محدود (scoped custom element registry)](/en-US/docs/Web/API/Web_components/Using_custom_elements#scoped_custom_element_registries) یک عنصر سفارشی را تنظیم می‌کند.

    برای سازگاری با نسخه‌های قبلی، برخی مرورگرها به شما اجازه می‌دهند به‌جای شیء، یک رشته در اینجا ارسال کنید که مقدار رشته نام تگ عنصر سفارشی است.
    برای اطلاعات بیشتر در مورد نحوه استفاده از این پارامتر، به [افزودن قابلیت به عناصر HTML بومی](https://web.dev/articles/web-components) مراجعه کنید.

### مقدار بازگشتی

{{DOMxRef("Element")}} جدید.

### استثناها (Exceptions)

- `NamespaceError` {{domxref("DOMException")}}
  - : اگر مقدار [`namespaceURI`](#namespaceuri) به‌صورت زیر باشد پرتاب می‌شود:
    - یک شناسه فضای نام معتبر نباشد.
    - وقتی `prefix` مقدار دارد، رشته خالی باشد.
    - وقتی [`prefix`](#prefix) روی `xml` یا `xmlns` تنظیم شده باشد، مقدار آن به ترتیب `http://www.w3.org/XML/1998/namespace` یا `http://www.w3.org/2000/xmlns/` نباشد.
- `InvalidCharacterError` {{domxref("DOMException")}}
  - : اگر `prefix` یا `localName` معتبر نباشد پرتاب می‌شود:
    - `prefix` باید حداقل یک نویسه داشته باشد و نمی‌تواند شامل فضای خالی ASCII، `NULL`، `/` یا `>` باشد (به ترتیب U+0000، U+002F یا U+003E).
    - `localName` اگر طول آن حداقل 1 باشد و یکی از شرایط زیر برقرار باشد، یک نام عنصر معتبر است:
      - با یک نویسه الفبایی شروع شود و شامل فضای خالی ASCII، `NULL`، `/` یا `>` نباشد (به ترتیب U+0000، U+002F یا U+003E).
      - با `:` (U+003A)، `_` (U+005F) یا هر نویسه‌ای در محدوده U+0080 تا U+10FFFF (شامل) شروع شود، _و_ نقطه‌های کد باقی‌مانده فقط شامل همان نویسه‌ها به همراه نویسه‌های الفبایی-عددی ASCII، `-` (U+002D) و `.` (U+002E) باشند.

    > [!NOTE]
    > نسخه‌های قبلی مشخصات محدودیت‌های بیشتری داشتند و لازم بود که `qualifiedName` یک [نام XML معتبر](https://www.w3.org/TR/xml/#dt-name) باشد.

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر هر دو گزینه [`is`](#is) و [`customElementRegistry`](#customelementregistry) مشخص شوند پرتاب می‌شود.

## مثال‌ها

### استفاده پایه

این مثال نحوه ایجاد یک عنصر جدید `<div>` در فضای نام {{Glossary("XHTML")}} را نشان می‌دهد.

```js
const divElementXHTML = document.createElementNS(
  "http://www.w3.org/1999/xhtml",
  "div",
);

// این معادل است!
const divElementHTML = document.createElement("div");
```

### ایجاد یک عنصر SVG

این مثال نشان می‌دهد که چگونه می‌توانید یک عنصر SVG ({{domxref("SVGSVGElement")}}) ایجاد کنید و آن را به عنصر `<body>` در HTML اضافه کنید.

استفاده از `createElementNS()` با فضای نام SVG هنگام کار با یک سند HTML ضروری است.
اگر با {{DOMxRef("Document.createElement()", "createElement(\"svg\")")}} تماس بگیرید، یک {{domxref("HTMLUnknownElement")}} برگردانده می‌شود و SVG رندر نمی‌شود.

```js
const svgNS = "http://www.w3.org/2000/svg";

const svg = document.createElementNS(svgNS, "svg");
svg.setAttribute("width", "100");
svg.setAttribute("height", "100");

const circle = document.createElementNS(svgNS, "circle");
circle.setAttribute("cx", "50");
circle.setAttribute("cy", "50");
circle.setAttribute("r", "40");
circle.setAttribute("fill", "steelblue");

svg.appendChild(circle);
document.body.appendChild(svg);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("document.createElement()")}}
- {{DOMxRef("document.createTextNode()")}}
- {{DOMxRef("Element.namespaceURI")}}