---
title: "Document: createAttribute() method"
short-title: createAttribute()
slug: Web/API/Document/createAttribute
page-type: web-api-instance-method
browser-compat: api.Document.createAttribute
---

{{ ApiRef("DOM") }}

روش **`createAttribute()`** از رابط {{domxref("Document")}} یک گره صفت جدید ایجاد می‌کند.

شیء ایجاد شده یک گره است که رابط {{domxref("Attr")}} را پیاده‌سازی می‌کند.
DOM محدودیتی برای نوع صفاتی که می‌توان به این روش به یک عنصر خاص اضافه کرد، اعمال نمی‌کند.

> [!NOTE]
> رشته‌ای که به عنوان پارامتر داده می‌شود به حروف کوچک تبدیل می‌شود.

## نحو

```js-nolint
createAttribute(localName)
```

### پارامترها

- `localName`
  - : یک رشته حاوی نام صفت.
    این مقدار برای مقداردهی اولیه ویژگی {{DOMxRef("Attr.localName", "localName")}} صفت جدید استفاده می‌شود.

### مقدار بازگشتی

یک گره {{domxref("Attr")}}.

### استثناها

- `InvalidCharacterError` {{domxref("DOMException")}}
  - : اگر مقدار [`localName`](#localname) یک نام صفت معتبر نباشد، پرتاب می‌شود.
    باید حداقل یک کاراکتر داشته باشد و نمی‌تواند شامل فاصله‌های خالی ASCII، `NULL`، `/`، `=` یا `>` (به ترتیب U+0000، U+002F، U+003D، یا U+003E) باشد.

    > [!NOTE]
    > نسخه‌های قبلی مشخصات محدودتر بودند و نیاز داشتند که `localName` یک [نام XML](https://www.w3.org/TR/xml/#dt-name) معتبر باشد.

## مثال‌ها

### مثال پایه

```js
const node = document.getElementById("div1");
const a = document.createAttribute("my_attrib");
a.value = "newVal";
node.setAttributeNode(a);
console.log(node.getAttribute("my_attrib")); // "newVal"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.createAttributeNS()")}}
- {{domxref("Document.createElement()")}}
- {{domxref("Element.setAttribute()")}}
- {{domxref("Element.setAttributeNode()")}}