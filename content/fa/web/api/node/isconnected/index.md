---
title: "Node: isConnected property"
short-title: isConnected
slug: Web/API/Node/isConnected
page-type: web-api-instance-property
browser-compat: api.Node.isConnected
---

{{APIRef("DOM")}}

خاصیتِ فقط‌خواندنی **`isConnected`** در رابط {{domxref("Node")}} یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا گره به صورت مستقیم یا غیرمستقیم به یک شیء {{domxref("Document")}} متصل است یا نه.

## مقدار

یک مقدار بولین که اگر گره به شیء زمینه‌ی مرتبط خود متصل باشد `true` است و در غیر این صورت `false`.

> [!NOTE]
> یک گره {{domxref("Attr")}} همیشه برای `isConnected` مقدار `false` برمی‌گرداند، حتی وقتی {{domxref("Attr.ownerElement", "ownerElement")}} آن متصل باشد.
> دلیل این است که اگرچه یک ویژگی (attribute) از طریق `ownerElement` با یک عنصر مرتبط است، اما بخشی از درخت گره نیست — هیچ گره والد ندارد و خودش گره ریشه‌ی خودش است.
> از آنجا که `isConnected` فقط زمانی `true` است که ریشه‌ی یک گره یک سند (document) باشد، یک گره `Attr` هرگز متصل در نظر گرفته نمی‌شود.

## مثال‌ها

### DOM استاندارد

یک مثال DOM استاندارد:

```js
let test = document.createElement("p");
console.log(test.isConnected); // Returns false
document.body.appendChild(test);
console.log(test.isConnected); // Returns true
```

### Shadow DOM

یک مثال Shadow DOM:

```js
// Create a shadow root
const shadow = this.attachShadow({ mode: "open" });

// Create some CSS to apply to the shadow DOM
const style = document.createElement("style");
console.log(style.isConnected); // returns false

style.textContent = `
.wrapper {
  position: relative;
}

.info {
  font-size: 0.8rem;
  width: 200px;
  display: inline-block;
  border: 1px solid black;
  padding: 10px;
  background: white;
  border-radius: 10px;
  opacity: 0;
  transition: 0.6s all;
  positions: absolute;
  bottom: 20px;
  left: 10px;
  z-index: 3
}
`;

// Attach the created style element to the shadow DOM

shadow.appendChild(style);
console.log(style.isConnected); // Returns true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}