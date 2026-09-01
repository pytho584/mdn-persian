---
title: "Document: createProcessingInstruction() method"
short-title: createProcessingInstruction()
slug: Web/API/Document/createProcessingInstruction
page-type: web-api-instance-method
browser-compat: api.Document.createProcessingInstruction
---

{{APIRef("DOM")}}

`createProcessingInstruction()` یک گرهٔ [processing instruction](/en-US/docs/Web/API/ProcessingInstruction) جدید می‌سازد و آن را بازمی‌گرداند.

معمولاً این گرهٔ جدید برای اینکه بتوان از آن استفاده کرد، در یک سند XML درج می‌شود؛ برای مثال با کمک {{ domxref("node.insertBefore") }}.

## سینتکس

```js-nolint
createProcessingInstruction(target, data)
```

### پارامترها

- `piNode`
  - : گرهٔ حاصل از نوع {{ domxref("ProcessingInstruction") }}.
- `target`
  - : رشته‌ای که بخش نخست دستور پردازش را شامل می‌شود (یعنی `<?target … ?>`).
- `data`
  - : رشته‌ای شامل هرگونه اطلاعاتی که دستور پردازش باید پس از target به‌همراه داشته باشد. انتخاب داده‌ها با خودتان است، اما نمی‌تواند شامل `?>` باشد، چون این دنباله دستور پردازش را می‌بندد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidCharacterError` {{domxref("DOMException")}}
  - : در صورت برقراری هر یک از شرایط زیر پرتاب می‌شود:
    - مقدار [`target`](#target) یک [نام XML](https://www.w3.org/TR/xml/#dt-name) معتبر نیست؛ برای مثال، با عدد، خط تیره یا نقطه شروع می‌شود، یا حاوی نویسه‌هایی غیر از نویسه‌های الفبایی-عددی، زیرخط، خط تیره یا نقطه است.
    - _دنبالهٔ پایانی دستور پردازش_ (`?>`) بخشی از مقدار [`data`](#data) باشد.

## مثال‌ها

```js
const doc = new DOMParser().parseFromString("<foo />", "application/xml");
const pi = doc.createProcessingInstruction(
  "xml-stylesheet",
  'href="mycss.css"',
);

doc.insertBefore(pi, doc.firstChild);

console.log(new XMLSerializer().serializeToString(doc));
// Displays: <?xml-stylesheet href="mycss.css" type="text/css"?><foo/>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}