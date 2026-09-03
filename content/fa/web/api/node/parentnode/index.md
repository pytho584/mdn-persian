---
title: "Node: parentNode property"
short-title: parentNode
slug: Web/API/Node/parentNode
page-type: web-api-instance-property
browser-compat: api.Node.parentNode
---

{{APIRef("DOM")}}

خاصیت فقط-خواندنی **`parentNode`** از واسط {{domxref("Node")}}، والد گره مشخص‌شده را در درخت DOM برمی‌گرداند.

گره‌های `Document` و `DocumentFragment` هیچ‌گاه نمی‌توانند والد داشته باشند، بنابراین `parentNode` همیشه `null` برمی‌گرداند. همچنین اگر گره تازه ایجاد شده باشد و هنوز به درخت متصل نشده باشد، `null` برمی‌گرداند. از سوی دیگر، {{domxref("Node.parentElement")}} فقط گره‌های `Element` را برمی‌گرداند.

## مقدار

یک {{domxref("Node")}} که والد گره جاری است. والد یک عنصر می‌تواند یک گره `Element`، یک گره `Document` یا یک گره `DocumentFragment` باشد.

## مثال

### استفاده از parentNode

این مثال یک گره را از درخت حذف می‌کند، مگر اینکه از قبل در درخت نباشد.

```js
if (node.parentNode) {
  node.parentNode.removeChild(node);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{Domxref("Node.firstChild")}}
- {{Domxref("Node.lastChild")}}
- {{Domxref("Node.childNodes")}}
- {{Domxref("Node.nextSibling")}}
- {{Domxref("Node.parentElement")}}
- {{Domxref("Node.previousSibling")}}
- {{Domxref("Node.removeChild")}}