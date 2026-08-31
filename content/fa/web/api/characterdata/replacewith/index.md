---
title: "CharacterData: replaceWith() method"
short-title: replaceWith()
slug: Web/API/CharacterData/replaceWith
page-type: web-api-instance-method
browser-compat: api.CharacterData.replaceWith
---

{{APIRef("DOM")}}

متد **`replaceWith()`** از رابط {{domxref("CharacterData")}} این گره را در فهرست فرزندان والدش با مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته جایگزین می‌کند.

رشته‌ها به‌عنوان گره‌های {{domxref("Text")}} درج می‌شوند؛ این رشته به‌عنوان آرگومان به سازنده {{domxref("Text/Text", "Text()")}} ارسال می‌شود.

## سینتکس

```js-nolint
replaceWith(...nodes)
```

### پارامترها

- `nodes` {{optional_inline}}
  - : فهرستی با جداکننده کاما از اشیاء {{domxref("Node")}} یا رشته‌هایی که جایگزین گره فعلی خواهند شد.

> [!NOTE]
> اگر هیچ آرگومانی ارسال نشود، این متد گره را از درخت DOM حذف می‌کند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی که گره را نتوان در نقطه مشخص‌شده در سلسله‌مراتب درج کرد، پرتاب می‌شود.

## مثال‌ها

```html
<p id="myText">Some text</p>
```

```js
let text = document.getElementById("myText").firstChild;
let em = document.createElement("em");
em.textContent = "Italic text";

text.replaceWith(em); // Replace `Some text` by `Italic text`
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CharacterData.replaceData()")}}
- {{domxref("DocumentType.replaceWith()")}}
- {{domxref("Element.replaceWith()")}}