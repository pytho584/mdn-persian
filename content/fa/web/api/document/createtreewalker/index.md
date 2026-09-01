---
title: "Document: createTreeWalker() method"
short-title: createTreeWalker()
slug: Web/API/Document/createTreeWalker
page-type: web-api-instance-method
browser-compat: api.Document.createTreeWalker
---

{{ApiRef("Document")}}

متد **`Document.createTreeWalker()`** یک شیء {{domxref("TreeWalker")}} تازه‌ساخته را بازمی‌گرداند.

## Syntax

```js-nolint
createTreeWalker(root)
createTreeWalker(root, whatToShow)
createTreeWalker(root, whatToShow, filter)
```

### پارامترها

- `root`
  - : یک {{domxref("Node")}} که ریشهٔ شیء `TreeWalker` را نشان می‌دهد و مقدار اولیهٔ {{domxref("TreeWalker.currentNode")}} است.

- `whatToShow` {{optional_inline}}
  - : یک `unsigned long` که یک bitmask را نشان می‌دهد و با ترکیب ثابت‌های [`NodeFilter`](https://dom.spec.whatwg.org/#interface-nodefilter) ساخته می‌شود. این یک روش مناسب برای فیلتر کردن نوع‌های خاصی از گره‌هاست. مقدار پیش‌فرض آن `0xFFFFFFFF` است که ثابت `NodeFilter.SHOW_ALL` را نشان می‌دهد.

    | ثابت                                                     | مقدار عددی      | توضیحات                                         |
    | -------------------------------------------------------- | --------------- | ----------------------------------------------- |
    | `NodeFilter.SHOW_ALL`                                    | `0xFFFFFFFF`    | همهٔ گره‌ها را نشان می‌دهد.                     |
    | `NodeFilter.SHOW_ATTRIBUTE`                              | `0x2`           | گره‌های {{domxref("Attr")}} را نشان می‌دهد.     |
    | `NodeFilter.SHOW_CDATA_SECTION`                          | `0x8`           | گره‌های {{domxref("CDATASection")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_COMMENT`                                | `0x80`          | گره‌های {{domxref("Comment")}} را نشان می‌دهد.  |
    | `NodeFilter.SHOW_DOCUMENT`                               | `0x100`         | گره‌های {{domxref("Document")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_DOCUMENT_FRAGMENT`                      | `0x400`         | گره‌های {{domxref("DocumentFragment")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_DOCUMENT_TYPE`                          | `0x200`         | گره‌های {{domxref("DocumentType")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_ELEMENT`                                | `0x1`           | گره‌های {{domxref("Element")}} را نشان می‌دهد.  |
    | `NodeFilter.SHOW_ENTITY` {{deprecated_inline}}           | `0x20`          | قدیمی، دیگر مؤثر نیست.                          |
    | `NodeFilter.SHOW_ENTITY_REFERENCE` {{deprecated_inline}} | `0x10`          | قدیمی، دیگر مؤثر نیست.                          |
    | `NodeFilter.SHOW_NOTATION` {{deprecated_inline}}         | `0x800`         | قدیمی، دیگر مؤثر نیست.                          |
    | `NodeFilter.SHOW_PROCESSING_INSTRUCTION`                 | `0x40`          | گره‌های {{domxref("ProcessingInstruction")}} را نشان می‌دهد. |
    | `NodeFilter.SHOW_TEXT`                                   | `0x4`           | گره‌های {{domxref("Text")}} را نشان می‌دهد.     |

    > [!NOTE]
    > ثابت `NodeFilter.SHOW_ATTRIBUTE` تنها زمانی مؤثر است که ریشه یک گرهٔ ویژگی (attribute) باشد. از آنجا که والد هر گرهٔ `Attr` همیشه `null` است، {{DOMXref("TreeWalker.nextNode()")}} و {{DOMXref("TreeWalker.previousNode()")}} هرگز یک گرهٔ `Attr` را برنمی‌گردانند. برای پیمایش گره‌های `Attr`، از {{DOMXref("Element.attributes")}} استفاده کنید.

- `filter` {{optional_inline}}
  - : یک تابع callback یا یک شیء با متد `acceptNode()` که یکی از مقادیر `NodeFilter.FILTER_ACCEPT`، `NodeFilter.FILTER_REJECT` یا `NodeFilter.FILTER_SKIP` را برمی‌گرداند. این تابع یا متد برای هر گره در زیردرخت مبتنی بر `root` که توسط پرچم `whatToShow` پذیرفته شده باشد فراخوانی می‌شود تا مشخص شود که آیا آن گره در فهرست گره‌های قابل پیمایش قرار گیرد یا خیر:
    - اگر مقدار بازگشتی `NodeFilter.FILTER_ACCEPT` باشد، این گره شامل می‌شود.
    - اگر مقدار بازگشتی `NodeFilter.FILTER_REJECT` باشد، هیچ گره‌ای در زیردرخت مبتنی بر این گره شامل نمی‌شود.
    - اگر مقدار بازگشتی `NodeFilter.FILTER_SKIP` باشد، این گره شامل نمی‌شود.

### مقدار بازگشتی

یک شیء جدید {{domxref("TreeWalker")}}.

## مثال‌ها

### استفاده از whatToShow

این مثال از `whatToShow` برای تبدیل محتوای متنی به حروف بزرگ استفاده می‌کند. توجه کنید که گره‌های متنی از فرزندان عنصر `#root` نیز پیمایش می‌شوند، با وجود اینکه آن‌ها گره‌های فرزند مستقیم عنصر `#root` نیستند.

#### HTML

```html
<div id="root">
  This is a text node.
  <span>And this is a <code>span</code> element.</span>
</div>
```

#### CSS

```css
span {
  background-color: aqua;
}
```

#### JavaScript

```js
const treeWalker = document.createTreeWalker(
  document.querySelector("#root"),
  NodeFilter.SHOW_TEXT,
);

while (treeWalker.nextNode()) {
  const node = treeWalker.currentNode;
  node.data = node.data.toUpperCase();
}
```

#### نتیجه

{{EmbedLiveSample("using_whattoshow", "100%", 100)}}

### استفاده از filter

این مثال از `filter` برای escaping محتوای متنی استفاده می‌کند. برای هر گرهٔ متنی، اگر آن گره از نوادگان یک عنصر `.escape` باشد اما از نوادگان هیچ عنصر `.no-escape` نباشد، محتوای آن با استفاده از {{JSXref("encodeURI()")}} escaping می‌شود.

#### HTML

```html
<div>
  <div>
    This is not escaped. <span class="escape">But this is escaped.</span>
  </div>
  <div class="escape">This is escaped.</div>
  <div class="no-escape">This is not escaped.</div>
</div>
<hr />
<div class="escape">
  <div>
    This is escaped. <span class="no-escape">But this is not escaped.</span>
  </div>
  <div class="no-escape">This is not escaped.</div>
</div>
<hr />
<div class="no-escape">
  <div>This is not escaped.</div>
  <div class="escape">This is not escaped.</div>
</div>
```

#### CSS

```css hidden
div {
  margin: 0.25em 0;
  padding: 0.25em;
}
span {
  display: inline-block;
}
```

```css
.escape {
  border: dashed;
}
.no-escape {
  border: solid;
}
```

#### JavaScript

```js
const treeWalker = document.createTreeWalker(
  document.body,
  NodeFilter.SHOW_ELEMENT,
  (node) =>
    node.classList.contains("no-escape")
      ? NodeFilter.FILTER_REJECT
      : node.closest(".escape")
        ? NodeFilter.FILTER_ACCEPT
        : NodeFilter.FILTER_SKIP,
);

while (treeWalker.nextNode()) {
  for (const node of treeWalker.currentNode.childNodes) {
    if (node.nodeType === Node.TEXT_NODE && /\S/.test(node.data)) {
      // Exclude whitespace-only text nodes
      node.data = encodeURI(node.data.replace(/\s+/g, " "));
    }
  }
}
```

#### نتیجه

{{EmbedLiveSample("using_filter", "100%", 400)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("TreeWalker")}}: رابط مرتبط
