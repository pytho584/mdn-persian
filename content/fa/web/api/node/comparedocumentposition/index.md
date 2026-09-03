---
title: "Node: compareDocumentPosition() method"
short-title: compareDocumentPosition()
slug: Web/API/Node/compareDocumentPosition
page-type: web-api-instance-method
browser-compat: api.Node.compareDocumentPosition
---

{{APIRef("DOM")}}

متد **`compareDocumentPosition()`** در رابط {{domxref("Node")}} موقعیت گرهٔ آرگومان را نسبت به گره‌ای که روی آن فراخوانی شده است گزارش می‌دهد.

## نحو (Syntax)

```js-nolint
compareDocumentPosition(otherNode)
```

### پارامترها

- `otherNode`
  - : گرهٔ {{domxref("Node")}} که موقعیت آن باید نسبت به این گره گزارش شود.

### مقدار بازگشتی

یک مقدار صحیح که موقعیت `otherNode` را نسبت به `node` به صورت [bitmask](<https://en.wikipedia.org/wiki/Mask_(computing)>) نشان می‌دهد و ترکیبی از ثابت‌های زیر در {{domxref("Node")}} است، یا اگر `otherNode` همان این گره باشد مقدار `0` برمی‌گردد:

- `Node.DOCUMENT_POSITION_DISCONNECTED` (`1`)
  - : هر دو گره در اسناد متفاوت یا درخت‌های متفاوت در همان سند قرار دارند.
- `Node.DOCUMENT_POSITION_PRECEDING` (`2`)
  - : `otherNode` قبل از این گره قرار دارد، یا در یک [پیمایش عمقی پیش‌ترتیبی](https://en.wikipedia.org/wiki/Tree_traversal#Pre-order,_NLR) از درختی که شامل هر دو است (مثلاً به عنوان جد، خواهر/برادر قبلی، یا فرزند یک خواهر/برادر قبلی یا خواهر/برادر قبلی یک جد)، یا (اگر از هم جدا باشند) در یک ترتیب دلخواه اما سازگار.
- `Node.DOCUMENT_POSITION_FOLLOWING` (`4`)
  - : `otherNode` بعد از این گره قرار دارد، یا در یک [پیمایش عمقی پیش‌ترتیبی](https://en.wikipedia.org/wiki/Tree_traversal#Pre-order,_NLR) از درختی که شامل هر دو است (مثلاً به عنوان فرزند، خواهر/برادر بعدی، یا فرزند یک خواهر/برادر بعدی یا خواهر/برادر بعدی یک جد)، یا (اگر از هم جدا باشند) در یک ترتیب دلخواه اما سازگار.
- `Node.DOCUMENT_POSITION_CONTAINS` (`8`)
  - : `otherNode` جدِ این گره است.
- `Node.DOCUMENT_POSITION_CONTAINED_BY` (`16`)
  - : `otherNode` از نوادگان این گره است.
- `Node.DOCUMENT_POSITION_IMPLEMENTATION_SPECIFIC` (`32`)
  - : نتیجه به رفتار دلخواه و/یا وابسته به پیاده‌سازی بستگی دارد و قابل حمل بودن آن تضمین نمی‌شود.

بسته به اینکه کدام سناریوها صدق می‌کنند، صفر یا چند بیت می‌توانند تنظیم شوند.
برای مثال، اگر `otherNode` در سند **_زودتر_** قرار داشته باشد **_و_** همچنین شامل گره‌ای باشد که `compareDocumentPosition()` روی آن فراخوانی شده است، آنگاه هر دو بیت `DOCUMENT_POSITION_CONTAINS` و `DOCUMENT_POSITION_PRECEDING` تنظیم می‌شوند و مقدار `10` (`0x0A`) تولید می‌شود.

## مثال

```js
const head = document.head;
const body = document.body;

if (head.compareDocumentPosition(body) & Node.DOCUMENT_POSITION_FOLLOWING) {
  console.log("Well-formed document");
} else {
  console.error("<head> is not before <body>");
}
```

> [!NOTE]
> از آنجا که نتیجهٔ بازگشتی توسط `compareDocumentPosition()` یک bitmask است، برای دریافت نتایج معنادار باید از [عملگر بیتی AND](/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_AND) استفاده شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMxRef("Node.contains()")}}