---
title: "CharacterData: after() method"
short-title: after()
slug: Web/API/CharacterData/after
page-type: web-api-instance-method
browser-compat: api.CharacterData.after
---

{{APIRef("DOM")}}

متد **`after()`** در رابط {{domxref("CharacterData")}}، مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را در فهرست فرزندان والدِ آن شیء، دقیقاً بعد از خودِ شیء درج می‌کند.

رشته‌ها به‌صورت گره‌های {{domxref("Text")}} درج می‌شوند؛ رشته به‌عنوان آرگومان به سازنده {{domxref("Text/Text", "Text()")}} ارسال می‌شود.

## نحو (Syntax)

```js-nolint
after(...nodes)
```

### پارامترها

- `nodes`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها که باید درج شوند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره‌های جدید نتوانند در نقطه مشخص‌شده در سلسله‌مراتب درج شوند؛ یعنی اگر یکی از شرایط زیر برقرار باشد:
    - اگر درج یکی از گره‌های اضافه‌شده منجر به ایجاد چرخه شود، یعنی اگر یکی از آن‌ها جد (ancestor) این گره {{domxref("CharacterData")}} باشد.
    - اگر یکی از گره‌های اضافه‌شده یک {{domxref("DocumentFragment")}}، {{domxref("DocumentType")}}، {{domxref("Element")}} یا {{domxref("CharacterData")}} نباشد.
    - اگر این گره {{domxref("CharacterData")}} در واقع یک گره {{domxref("Text")}} باشد و والد آن یک {{domxref("Document")}} باشد.
    - اگر والد این گره {{domxref("CharacterData")}} یک {{domxref("Document")}} باشد و یکی از گره‌های درج‌شونده یک {{domxref("DocumentFragment")}} با بیش از یک فرزند {{domxref("Element")}} باشد، یا یک فرزند {{domxref("Text")}} داشته باشد.

## مثال‌ها

متد `after()` به شما امکان می‌دهد گره‌های جدیدی را بعد از یک گره `CharacterData` درج کنید.

```js
const h1TextNode = document.querySelector("h1").firstChild;
h1TextNode.after(" #h1");

h1TextNode.parentElement.childNodes;
// NodeList [#text "CharacterData.after()", #text " #h1"]

h1TextNode.data;
// "CharacterData.after()"
```

> [!NOTE]
> اگر ترجیح می‌دهید متن را به انتهای گره فعلی اضافه کنید،
> متد [`appendData()`](/en-US/docs/Web/API/CharacterData/appendData) به شما امکان می‌دهد به داده‌های گره فعلی اضافه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CharacterData.appendData()")}}
- {{domxref("CharacterData.before()")}}
- {{domxref("DocumentType.after()")}}
- {{domxref("Element.after()")}}
- {{domxref("Element.append()")}}
- {{domxref("Node.appendChild()")}}
- {{domxref("Element.insertAdjacentElement()")}}