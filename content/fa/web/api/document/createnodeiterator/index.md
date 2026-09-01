---
title: "Document: createNodeIterator() method"
short-title: createNodeIterator()
slug: Web/API/Document/createNodeIterator
page-type: web-api-instance-method
browser-compat: api.Document.createNodeIterator
---

{{APIRef("DOM")}}

متد **`Document.createNodeIterator()`** یک شیء [`NodeIterator`](/en-US/docs/Web/API/NodeIterator) جدید برمی‌گرداند.

## نحو (Syntax)

```js-nolint
createNodeIterator(root)
createNodeIterator(root, whatToShow)
createNodeIterator(root, whatToShow, filter)
```

### پارامترها

- `root`
  - : گره ریشه‌ای که پیمایش {{ domxref("NodeIterator") }} از آن آغاز می‌شود.

- `whatToShow` {{optional_inline}}
  - : یک `unsigned long` اختیاری که یک bitmask ایجاد شده با ترکیب ثابت‌های `NodeFilter` است. این یک روش مناسب برای فیلتر کردن انواع خاصی از گره‌ها است. به طور پیش‌فرض مقدار `0xFFFFFFFF` را دارد که نمایانگر ثابت `SHOW_ALL` است.

    | ثابت                                                     | مقدار عددی      | توضیحات                                          |
    | -------------------------------------------------------- | --------------- | ------------------------------------------------- |
    | `NodeFilter.SHOW_ALL`                                    | `0xFFFFFFFF`    | همه گره‌ها را نشان می‌دهد.                        |
    | `NodeFilter.SHOW_ATTRIBUTE`                              | `0x2`           | گره‌های {{domxref("Attr")}} را نشان می‌دهد.       |
    | `NodeFilter.SHOW_CDATA_SECTION`                          | `0x8`           | گره‌های {{domxref("CDATASection")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_COMMENT`                                | `0x80`          | گره‌های {{domxref("Comment")}} را نشان می‌دهد.    |
    | `NodeFilter.SHOW_DOCUMENT`                               | `0x100`         | گره‌های {{domxref("Document")}} را نشان می‌دهد.   |
    | `NodeFilter.SHOW_DOCUMENT_FRAGMENT`                      | `0x400`         | گره‌های {{domxref("DocumentFragment")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_DOCUMENT_TYPE`                          | `0x200`         | گره‌های {{domxref("DocumentType")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_ELEMENT`                                | `0x1`           | گره‌های {{domxref("Element")}} را نشان می‌دهد.    |
    | `NodeFilter.SHOW_ENTITY` {{deprecated_inline}}           | `0x20`          | قدیمی، دیگر مؤثر نیست.                            |
    | `NodeFilter.SHOW_ENTITY_REFERENCE` {{deprecated_inline}} | `0x10`          | قدیمی، دیگر مؤثر نیست.                            |
    | `NodeFilter.SHOW_NOTATION` {{deprecated_inline}}         | `0x800`         | قدیمی، دیگر مؤثر نیست.                            |
    | `NodeFilter.SHOW_PROCESSING_INSTRUCTION`                 | `0x40`          | گره‌های {{domxref("ProcessingInstruction")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_TEXT`                                   | `0x4`           | گره‌های {{domxref("Text")}} را نشان می‌دهد.       |

    > [!NOTE]
    > ثابت `NodeFilter.SHOW_ATTRIBUTE` تنها زمانی مؤثر است که ریشه یک گره ویژگی (attribute) باشد. از آنجا که والد هر گره `Attr` همیشه `null` است، {{DOMXref("TreeWalker.nextNode()")}} و {{DOMXref("TreeWalker.previousNode()")}} هرگز یک گره `Attr` را برنمی‌گردانند. برای پیمایش گره‌های `Attr`، از {{DOMXref("Element.attributes")}} استفاده کنید.

- `filter` {{optional_inline}}
  - : یک تابع callback یا یک شیء با متد `acceptNode()`. این تابع یا متد برای هر گره در زیردرخت مبتنی بر ریشه که توسط پرچم whatToShow پذیرفته شده است فراخوانی می‌شود تا مشخص کند که آیا آن گره در فهرست گره‌های قابل پیمایش قرار گیرد یا نه. متد باید یکی از مقادیر `NodeFilter.FILTER_ACCEPT`، `NodeFilter.FILTER_REJECT` یا `NodeFilter.FILTER_SKIP` را برگرداند. به [مثال](#examples) مراجعه کنید.

    برای `createNodeIterator`، مقادیر `NodeFilter.FILTER_REJECT` و `NodeFilter.FILTER_SKIP` معادل هستند. این گره در فهرست گره‌های قابل پیمایش قرار نمی‌گیرد، اما فرزندان آن همچنان پیمایش می‌شوند.

### مقدار بازگشتی

یک شیء [`NodeIterator`](/en-US/docs/Web/API/NodeIterator) جدید.

## مثال‌ها

```js
const nodeIterator = document.createNodeIterator(
  document.body,
  NodeFilter.SHOW_ELEMENT,
  (node) =>
    node.nodeName.toLowerCase() === "p"
      ? NodeFilter.FILTER_ACCEPT
      : NodeFilter.FILTER_REJECT,
);
const pars = [];
let currentNode;

while ((currentNode = nodeIterator.nextNode())) {
  pars.push(currentNode);
}
```

همان مثال، اما با استفاده از یک شیء دارای متد `acceptNode()`:

```js
const nodeIterator = document.createNodeIterator(
  document.body,
  NodeFilter.SHOW_ELEMENT,
  {
    acceptNode(node) {
      return node.nodeName.toLowerCase() === "p"
        ? NodeFilter.FILTER_ACCEPT
        : NodeFilter.FILTER_REJECT;
    },
  },
);
const pars = [];
let currentNode;

while ((currentNode = nodeIterator.nextNode())) {
  pars.push(currentNode);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}