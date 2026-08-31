---
title: "CharacterData: before() method"
short-title: before()
slug: Web/API/CharacterData/before
page-type: web-api-instance-method
browser-compat: api.CharacterData.before
---

{{APIRef("DOM")}}

متد **`before()`** در رابط {{domxref("CharacterData")}}، مجموعه‌ای از اشیاء {{domxref("Node")}} و رشته‌ها را در فهرست فرزندانِ والدِ `CharacterData`، دقیقاً قبل از گره `CharacterData` درج می‌کند.

رشته‌ها به‌صورت گره‌های {{domxref("Text")}} درج می‌شوند؛ رشته به‌عنوان آرگومان به سازندهٔ {{domxref("Text/Text", "Text()")}} ارسال می‌شود.

## نحو (Syntax)

```js-nolint
before(...nodes)
```

### پارامترها

- `nodes`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها برای درج.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره‌های جدید نتوانند در نقطه‌ٔ مشخص‌شده در سلسله‌مراتب درج شوند، یعنی اگر یکی از شرایط زیر برقرار باشد:
    - اگر درج یکی از گره‌های اضافه‌شده منجر به چرخه (cycle) شود، یعنی اگر یکی از آن‌ها جد (ancestor) این گرهٔ {{domxref("CharacterData")}} باشد.
    - اگر یکی از گره‌های اضافه‌شده یک {{domxref("DocumentFragment")}}، {{domxref("DocumentType")}}، {{domxref("Element")}} یا {{domxref("CharacterData")}} نباشد.
    - اگر این گرهٔ {{domxref("CharacterData")}} در واقع یک گرهٔ {{domxref("Text")}} باشد و والد آن یک {{domxref("Document")}} باشد.
    - اگر والد این گرهٔ {{domxref("CharacterData")}} یک {{domxref("Document")}} باشد و یکی از گره‌هایی که قرار است درج شود، یک {{domxref("DocumentFragment")}} با بیش از یک فرزند {{domxref("Element")}} باشد، یا یک فرزند {{domxref("Text")}} داشته باشد.

## مثال‌ها

متد `before()` به شما امکان می‌دهد گره‌های جدیدی را قبل از یک گرهٔ `CharacterData` درج کنید، بدون اینکه داده‌های گرهٔ فعلی تغییر کند.

```js
const h1TextNode = document.querySelector("h1").firstChild;
h1TextNode.before("h1# ");

h1TextNode.parentElement.childNodes;
// NodeList [#text "h1# ", #text "CharacterData.before()"]

h1TextNode.data;
// "CharacterData.before()"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("CharacterData.appendData()")}}
- {{domxref("CharacterData.after()")}}
- {{domxref("DocumentType.before()")}}
- {{domxref("Element.before()")}}
- {{domxref("Element.append()")}}
- {{domxref("Node.appendChild()")}}
- {{domxref("Element.insertAdjacentElement()")}}