---
title: "Document: createAttributeNS() method"
short-title: createAttributeNS()
slug: Web/API/Document/createAttributeNS
page-type: web-api-instance-method
browser-compat: api.Document.createAttributeNS
---

{{ ApiRef("DOM") }}

متد **`createAttributeNS()`** از رابط {{domxref("Document")}} یک گره ویژگی جدید با URI فضای نام و نام واجد شرایط مشخص شده ایجاد می‌کند.

شیء ایجاد شده یک گره است که رابط {{domxref("Attr")}} را پیاده‌سازی می‌کند. DOM در این روش نوع ویژگی‌هایی که می‌توان به یک عنصر خاص اضافه کرد را محدود نمی‌کند.

## نحو

```js-nolint
createAttributeNS(namespaceURI, qualifiedName)
```

### پارامترها

- `namespaceURI`
  - : یک رشته که {{DOMxRef("Attr.namespaceURI", "namespaceURI")}} مرتبط با ویژگی را مشخص می‌کند، یا یک رشته خالی. در اسناد HTML، بیشتر ویژگی‌ها در **فضای نام null** هستند — برای این موارد از رشته خالی استفاده کنید. فقط زمانی از یک URI فضای نام خاص استفاده کنید که یک ویژگی دارای فضای نام مانند `xml:lang` یا `xml:space` ایجاد می‌کنید. برخی از URIهای فضای نام عبارتند از:
    - XML: `http://www.w3.org/XML/1998/namespace` (برای `xml:lang`, `xml:space`)
    - XMLNS: `http://www.w3.org/2000/xmlns/` (برای `xmlns`, `xmlns:*`)
    - XLink: `http://www.w3.org/1999/xlink` (برای `xlink:href`, `xlink:title`, و غیره)
- `qualifiedName`
  - : یک رشته حاوی نام واجد شرایط ویژگی جدید. ویژگی {{DOMxRef("Attr.name", "name")}} ویژگی ایجاد شده با این مقدار مقداردهی اولیه می‌شود. قالب نام واجد شرایط به صورت `prefix:localName` یا `localName` است، که بخش‌ها به صورت زیر تعریف می‌شوند:
    - `prefix` {{optional_inline}}
      - : یک «نام مستعار کوتاه» برای فضای نام. پیشوند اختیاری است، اما اگر مشخص شود، پارامتر `namespaceURI` نیز باید مشخص شود. اگر پیشوند به `xml` یا `xmlns` تنظیم شود، `namespaceURI` باید به ترتیب به `http://www.w3.org/XML/1998/namespace` یا `http://www.w3.org/2000/xmlns/` تنظیم شود. این مقدار برای مقداردهی اولیه ویژگی {{DOMxRef("Attr.prefix", "prefix")}} ویژگی جدید استفاده می‌شود. پیش‌فرض `null` است.
    - `localName`
      - : نام محلی ویژگی. این مقدار برای مقداردهی اولیه ویژگی {{DOMxRef("Attr.localName", "localName")}} ویژگی جدید استفاده می‌شود.

### مقدار بازگشتی

گره {{domxref("Attr")}} جدید.

### استثناها

- `NamespaceError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که مقدار [`namespaceURI`](#namespaceuri) دارای شرایط زیر باشد:
    - یک URI فضای نام معتبر نباشد.
    - وقتی `prefix` مقداری دارد، به رشته خالی تنظیم شده باشد.
    - وقتی [`prefix`](#prefix) به ترتیب به `xml` یا `xmlns` تنظیم شده است، برابر با `http://www.w3.org/XML/1998/namespace` یا `http://www.w3.org/2000/xmlns/` نباشد.
- `InvalidCharacterError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که `prefix` یا `localName` معتبر نباشند:
    - `prefix` باید حداقل یک کاراکتر داشته باشد و نمی‌تواند شامل فاصله سفید ASCII، `NULL`، `/`، یا `>` باشد (به ترتیب U+0000، U+002F، یا U+003E).
    - `localName` باید حداقل یک کاراکتر داشته باشد و نمی‌تواند شامل فاصله سفید ASCII، `NULL`، `/`، `=` یا `>` باشد (به ترتیب U+0000، U+002F، U+003D، یا U+003E).

    > [!NOTE]
    > نسخه‌های قبلی مشخصات محدودیت بیشتری داشتند و نیاز داشتند که `localName` یک [نام XML](https://www.w3.org/TR/xml/#dt-name) معتبر باشد.

## مثال‌ها

### ایجاد یک ویژگی دارای فضای نام

این مثال یک ویژگی `xml:lang` با فضای نام XML ایجاد می‌کند و آن را به یک عنصر پاراگراف متصل می‌کند. این ویژگی زبان محتوای عنصر را برای پردازش XML مشخص می‌کند.

```html
<p id="greeting">Bonjour!</p>
```

```js
const el = document.getElementById("greeting");
const attr = document.createAttributeNS(
  "http://www.w3.org/XML/1998/namespace",
  "xml:lang",
);
attr.value = "fr";
el.setAttributeNode(attr);
```

### ایجاد یک ویژگی بدون پیشوند

در اسناد HTML، ویژگی‌های بدون پیشوند (مانند ویژگی‌های نمایشی SVG مانند `viewBox`) در فضای نام null هستند. برای تطبیق با این موضوع، از رشته خالی برای پارامتر `namespaceURI` استفاده کنید.

```html
<svg id="svg"></svg>
```

```js
const svg = document.getElementById("svg");
const attr = document.createAttributeNS("", "viewBox");
attr.value = "0 0 100 100";
svg.setAttributeNode(attr);
console.log(svg.getAttribute("viewBox")); // "0 0 100 100"
```

توجه داشته باشید که در بیشتر موارد، می‌توانید از {{domxref("Element.setAttribute()")}} به جای `createAttributeNS()` برای ویژگی‌های بدون پیشوند استفاده کنید:

```js
svg.setAttribute("viewBox", "0 0 100 100");
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.createAttribute()")}}
- {{domxref("Document.createElementNS()")}}
- {{domxref("Element.setAttributeNS()")}}
- {{domxref("Element.setAttributeNode()")}}
- {{domxref("Element.setAttributeNodeNS()")}}