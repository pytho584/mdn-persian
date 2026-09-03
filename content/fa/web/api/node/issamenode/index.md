---
title: "Node: isSameNode() method"
short-title: isSameNode()
slug: Web/API/Node/isSameNode
page-type: web-api-instance-method
browser-compat: api.Node.isSameNode
---

{{APIRef("DOM")}}

متد **`isSameNode()`** از رابط {{domxref("Node")}} یک نام مستعار قدیمی برای [عملگر تساوی سختگیرانه `===`](/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality) است. به عبارت دیگر، بررسی می‌کند که آیا دو گره یکسان هستند (یعنی آیا به یک شیء اشاره می‌کنند).

> [!NOTE]
> نیازی به استفاده از `isSameNode()` نیست؛ به جای آن از عملگر تساوی سختگیرانه `===` استفاده کنید.

## نحو (Syntax)

```js-nolint
isSameNode(otherNode)
```

### پارامترها

- `otherNode`
  - : {{domxref("Node")}}ای که باید با آن مقایسه شود.
    > [!NOTE]
    > این پارامتر اختیاری نیست، اما می‌توان آن را `null` تنظیم کرد.

### مقدار بازگشتی

یک مقدار بولی که اگر هر دو گره به‌طور سختگیرانه برابر باشند `true` است و در غیر این صورت `false`.

## مثال

در این مثال، سه بلوک {{HTMLElement("div")}} می‌سازیم. اولی و سومی محتوا و ویژگی‌های یکسانی دارند، در حالی که دومی متفاوت است. سپس با استفاده از جاوااسکریپت، گره‌ها را با `isSameNode()` مقایسه کرده و نتایج را نمایش می‌دهیم.

### HTML

```html
<div>This is the first element.</div>
<div>This is the second element.</div>
<div>This is the first element.</div>

<p id="output"></p>
```

```css hidden
#output {
  width: 440px;
  border: 2px solid black;
  border-radius: 5px;
  padding: 10px;
  margin-top: 20px;
  display: block;
}
```

### جاوااسکریپت

```js
const output = document.getElementById("output");
const divList = document.getElementsByTagName("div");

output.innerText += `div 0 same as div 0: ${divList[0].isSameNode(
  divList[0],
)}\n`;
output.innerText += `div 0 same as div 1: ${divList[0].isSameNode(
  divList[1],
)}\n`;
output.innerText += `div 0 same as div 2: ${divList[0].isSameNode(
  divList[2],
)}\n`;
```

### نتایج

{{ EmbedLiveSample('Example', "100%", "205") }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Node.isEqualNode()")}}