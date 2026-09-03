---
title: "Node: replaceChild() method"
short-title: replaceChild()
slug: Web/API/Node/replaceChild
page-type: web-api-instance-method
browser-compat: api.Node.replaceChild
---

{{APIRef("DOM")}}

متد **`replaceChild()`** در رابط {{domxref("Node")}}، یک گرهٔ فرزند را درون گرهٔ والدِ داده‌شده جایگزین می‌کند.

## Syntax

```js-nolint
replaceChild(newChild, oldChild)
```

### Parameters

- `newChild`
  - : گرهٔ جدیدی که قرار است جایگزین `oldChild` شود.
    > [!WARNING]
    > اگر گرهٔ جدید از قبل در جای دیگری از DOM وجود داشته باشد، ابتدا از آن موقعیت حذف می‌شود.
- `oldChild`
  - : فرزندی که قرار است جایگزین شود.

> [!NOTE]
> ترتیب پارامترها، _new_ قبل از _old_، غیرعادی است.
> متد [`Element.replaceWith()`](/en-US/docs/Web/API/Element/replaceWith) که فقط روی گره‌های عنصر اعمال می‌شود،
> ممکن است خواناتر و آسان‌تر باشد.

### Return value

گرهٔ {{domxref("Node")}} جایگزین‌شده. این همان گرهٔ `oldChild` است.

### Exceptions

- `HierarchyRequestError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که محدودیت‌های درخت DOM نقض شود، یعنی اگر یکی از موارد زیر رخ دهد:
    - اگر والدِ `oldChild` یک {{domxref("Document")}}، {{domxref("DocumentFragment")}} یا {{domxref("Element")}} نباشد.
    - اگر جایگزینی `oldChild` با `newChild` منجر به ایجاد چرخه شود، یعنی اگر `newChild` یکی از اجداد گره باشد.
    - اگر `newChild` یک {{domxref("DocumentFragment")}}، {{domxref("DocumentType")}}، {{domxref("Element")}} یا {{domxref("CharacterData")}} نباشد.
    - اگر گرهٔ فعلی یک {{domxref("Text")}} باشد و والدِ آن یک {{domxref("Document")}} باشد.
    - اگر گرهٔ فعلی یک {{domxref("DocumentType")}} باشد و والدِ آن _نه_ یک {{domxref("Document")}} باشد، زیرا _doctype_ باید همیشه فرزند مستقیم یک _document_ باشد.
    - اگر والدِ گره یک {{domxref("Document")}} باشد و `newChild` یک {{domxref("DocumentFragment")}} با بیش از یک فرزند {{domxref("Element")}} باشد، یا دارای یک فرزند {{domxref("Text")}} باشد.
    - اگر جایگزینی `oldChild` با `newChild` منجر به {{domxref("Document")}} با بیش از یک {{domxref("Element")}} به عنوان فرزند شود.
    - اگر جایگزینی `oldChild` با `newChild` منجر به وجود یک گرهٔ {{domxref("Element")}} قبل از یک گرهٔ {{domxref("DocumentType")}} شود.
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر والدِ `oldChild` گرهٔ فعلی نباشد پرتاب می‌شود.

## Example

```js
// Given:
// <div>
//  <span id="childSpan">foo bar</span>
// </div>

// Create an empty element node
// without an ID, any attributes, or any content
const sp1 = document.createElement("span");

// Give it an id attribute called 'newSpan'
sp1.id = "newSpan";

// Create some content for the new element.
const sp1Content = document.createTextNode("new replacement span element.");

// Apply that content to the new element
sp1.appendChild(sp1Content);

// Build a reference to the existing node to be replaced
const sp2 = document.getElementById("childSpan");
const parentDiv = sp2.parentNode;

// Replace existing node sp2 with the new span element sp1
parentDiv.replaceChild(sp1, sp2);

// Result:
// <div>
//   <span id="newSpan">new replacement span element.</span>
// </div>
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Node.removeChild")}}
- {{domxref("Element.replaceWith")}}