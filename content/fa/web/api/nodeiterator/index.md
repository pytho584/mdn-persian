---
title: "NodeIterator"
---

---
title: NodeIterator
slug: Web/API/NodeIterator
page-type: web-api-interface
browser-compat: api.NodeIterator
---

{{APIRef("DOM")}}

رابطهٔ **`NodeIterator`** یک تکرارکننده (iterator) را نشان می‌دهد که برای پیمایش گره‌های یک زیردرخت DOM به ترتیب سند استفاده می‌شود.

یک `NodeIterator` را می‌توان با استفاده از متد {{domxref("Document.createNodeIterator()")}} به شکل زیر ایجاد کرد:

```js
const nodeIterator = document.createNodeIterator(root, whatToShow, filter);
```

## ویژگی‌های نمونه

_این رابط هیچ ویژگی‌ای را به ارث نمی‌برد._

- {{domxref("NodeIterator.root")}} {{ReadOnlyInline}}
  - : یک {{domxref("Node")}} را برمی‌گرداند که گره ریشه را نشان می‌دهد، همان‌طور که هنگام ایجاد `NodeIterator` مشخص شده است.
- {{domxref("NodeIterator.whatToShow")}} {{ReadOnlyInline}}
  - : یک بیت‌ماسک (bitmask) از نوع `unsigned long` را برمی‌گرداند که انواع {{domxref("Node")}}هایی را که باید مطابقت داده شوند توصیف می‌کند. گره‌های نامطابق رد می‌شوند، اما گره‌های فرزند مرتبط ممکن است شامل شوند.
- {{domxref("NodeIterator.filter")}} {{ReadOnlyInline}}
  - : یک `NodeFilter` را برمی‌گرداند که برای انتخاب گره‌های مرتبط استفاده می‌شود.
- {{domxref("NodeIterator.referenceNode")}} {{ReadOnlyInline}}
  - : {{domxref("Node")}}ای را برمی‌گرداند که تکرارکننده به آن متصل است.
- {{domxref("NodeIterator.pointerBeforeReferenceNode")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا `NodeIterator` _قبل از_ {{domxref("NodeIterator.referenceNode")}} متصل است یا خیر. اگر `false` باشد، نشان می‌دهد که تکرارکننده _بعد از_ گره مرجع متصل است.

## روش‌های نمونه

_این رابط هیچ روشی را به ارث نمی‌برد._

- {{domxref("NodeIterator.detach()")}} {{deprecated_inline}}
  - : این یک روش قدیمی است و دیگر هیچ اثری ندارد. قبلاً برای علامت‌گذاری یک `NodeIterator` به عنوان غیرفعال استفاده می‌شد تا بتواند توسط جمع‌آوری زباله (garbage collection) بازیابی شود.
- {{domxref("NodeIterator.previousNode()")}}
  - : گره {{domxref("Node")}} قبلی را در سند برمی‌گرداند، یا اگر وجود نداشته باشد `null` را برمی‌گرداند.
- {{domxref("NodeIterator.nextNode()")}}
  - : گره {{domxref("Node")}} بعدی را در سند برمی‌گرداند، یا اگر وجود نداشته باشد `null` را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- روش ایجادکننده: {{domxref("Document.createNodeIterator()")}}.
- رابط مرتبط: {{domxref("TreeWalker")}}