---
title: "DOMImplementation: createDocument() method"
short-title: createDocument()
slug: Web/API/DOMImplementation/createDocument
page-type: web-api-instance-method
browser-compat: api.DOMImplementation.createDocument
---

{{ApiRef("DOM")}}

روش **`createDocument()`** از رابط {{domxref("DOMImplementation")}} یک {{domxref("XMLDocument")}} ایجاد و برمی‌گرداند.

## Syntax

```js-nolint
createDocument(namespaceURI, qualifiedName)
createDocument(namespaceURI, qualifiedName, documentType)
```

### پارامترها

- `namespaceURI`
  - : یک رشته شامل URI فضای نام سند مورد نظر برای ایجاد، یا `null` اگر سند متعلق به هیچ فضای نامی نیست.
- `qualifiedName`
  - : یک رشته شامل نام واجد شرایط سند مورد نظر برای ایجاد.
    مقدار [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) مانند رشته خالی (`""`) در نظر گرفته می‌شود.

    قالب نام واجد شرایط به صورت `prefix:localName` یا `localName` است، که اجزای آن به صورت زیر تعریف می‌شوند:
    - `prefix` {{optional_inline}}
      - : یک «نام مستعار کوتاه» برای فضای نام.
        پیشوند اختیاری است، اما اگر مشخص شود، پارامتر `namespaceURI` نیز باید مشخص شود.
        اگر پیشوند به `xml` یا `xmlns` تنظیم شود، `namespaceURI` باید به ترتیب به `http://www.w3.org/XML/1998/namespace` یا `http://www.w3.org/2000/xmlns/` تنظیم شود.
        پیش‌فرض `null` است.

    - `localName`
      - : نام محلی سند.

- `documentType` {{optional_inline}}
  - : {{domxref("DocumentType")}} سند مورد نظر برای ایجاد. پیش‌فرض `null` است.

### مقدار بازگشتی

{{domxref("XMLDocument")}} تازه ایجاد شده.

### استثناها

- `NamespaceError` {{domxref("DOMException")}}
  - : در صورتی که مقدار [`namespaceURI`](#namespaceuri) یکی از موارد زیر باشد پرتاب می‌شود:
    - یک URI فضای نام معتبر نباشد.
    - وقتی `prefix` مقداری دارد، به رشته خالی تنظیم شده باشد.
    - وقتی [`prefix`](#prefix) به `xml` یا `xmlns` تنظیم شده است، به ترتیب مقدار `http://www.w3.org/XML/1998/namespace` یا `http://www.w3.org/2000/xmlns/` نباشد.
- `InvalidCharacterError` {{domxref("DOMException")}}
  - : در صورتی که `prefix` یا `localName` معتبر نباشند پرتاب می‌شود:
    - `prefix` باید حداقل یک کاراکتر داشته باشد و نمی‌تواند شامل فضای خالی ASCII، `NULL`، `/` یا `>` (به ترتیب U+0000، U+002F یا U+003E) باشد.
    - `localName` یک نام عنصر معتبر است اگر طول آن حداقل 1 باشد و:
      - با یک کاراکتر الفبایی شروع شود و شامل فضای خالی ASCII، `NULL`، `/` یا `>` (به ترتیب U+0000، U+002F یا U+003E) نباشد.
      - با `:` (U+003A)، `_` (U+005F) یا هر کاراکتری در محدوده U+0080 تا U+10FFFF (شامل) شروع شود، _و_ نقاط کد باقی‌مانده فقط شامل همان کاراکترها به همراه کاراکترهای الفبایی-عددی ASCII، `-` (U+002D) و `.` (U+002E) باشند.

    > [!NOTE]
    > نسخه‌های قبلی مشخصات محدودیت‌های بیشتری داشتند و نیاز داشتند که `qualifiedName` یک [نام XML](https://www.w3.org/TR/xml/#dt-name) معتبر باشد.

## مثال‌ها

### استفاده پایه

```js
const doc = document.implementation.createDocument(
  "http://www.w3.org/1999/xhtml",
  "html",
  null,
);
const body = document.createElementNS("http://www.w3.org/1999/xhtml", "body");
body.setAttribute("id", "abc");
doc.documentElement.appendChild(body);
alert(doc.getElementById("abc")); // [object HTMLBodyElement]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("DOMImplementation")}} که این متد به آن تعلق دارد.