---
title: "Node: getRootNode() method"
short-title: getRootNode()
slug: Web/API/Node/getRootNode
page-type: web-api-instance-method
browser-compat: api.Node.getRootNode
---

{{APIRef("DOM")}}

متد **`getRootNode()`** از رابط {{domxref("Node")}} ریشهٔ شیء زمینه را برمی‌گرداند که در صورت وجود، شامل shadow root نیز می‌شود.

## نحو (Syntax)

```js-nolint
getRootNode()
getRootNode(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : شیءای که گزینه‌های دریافت ریشه را تنظیم می‌کند. گزینه‌های موجود عبارتند از:
    - `composed`: یک مقدار بولی که مشخص می‌کند آیا shadow root باید برگردانده شود (`false`، مقدار پیش‌فرض)، یا ریشه‌ای فراتر از shadow root (`true`).

### مقدار بازگشتی

شیءای که از {{domxref('Node')}} ارث‌بری می‌کند. شکل دقیق آن بسته به جایی که `getRootNode()` را فراخوانی می‌کنید متفاوت است؛ برای مثال:

- فراخوانی آن روی یک عنصر در یک صفحهٔ وب استاندارد، یک شیء {{domxref("HTMLDocument")}} برمی‌گرداند که کل صفحه (یا {{HTMLElement("iframe")}}) را نشان می‌دهد.
- فراخوانی آن روی یک عنصر در داخل shadow DOM، {{domxref("ShadowRoot")}} مرتبط را برمی‌گرداند.
- فراخوانی آن روی عنصری که به یک سند یا درخت shadow متصل نیست، ریشهٔ درخت DOM ای که به آن تعلق دارد را برمی‌گرداند.

## مثال‌ها

### مثال ۱

این مثال ساده ارجاعی به گره HTML/سند برمی‌گرداند:

```js
const rootNode = node.getRootNode();
```

### مثال ۲

این مثال پیچیده‌تر تفاوت بین برگرداندن ریشهٔ معمولی و ریشهٔ شامل shadow root را نشان می‌دهد:

```html
<div class="parent">
  <div class="child"></div>
</div>
<div class="shadowHost">shadowHost</div>
<pre id="output">Output: </pre>
```

```js
const parent = document.querySelector(".parent");
const child = document.querySelector(".child");
const shadowHost = document.querySelector(".shadowHost");
const output = document.getElementById("output");

output.innerText += `\nparent's root: ${parent.getRootNode().nodeName}\n`; // #document
output.innerText += `child's  root: ${child.getRootNode().nodeName}\n\n`; // #document

// create a ShadowRoot
const shadowRoot = shadowHost.attachShadow({ mode: "open" });
shadowRoot.innerHTML =
  '<style>div{background:#2bb8aa;}</style><div class="shadowChild">shadowChild</div>';
const shadowChild = shadowRoot.querySelector(".shadowChild");

// The default value of composed is false
output.innerText += `shadowChild.getRootNode() === shadowRoot : ${
  shadowChild.getRootNode() === shadowRoot
}\n`; // true
output.innerText += `shadowChild.getRootNode({ composed:false }) === shadowRoot : ${
  shadowChild.getRootNode({ composed: false }) === shadowRoot
}\n`; // true
output.innerText += `shadowChild.getRootNode({ composed:true }).nodeName : ${
  shadowChild.getRootNode({ composed: true }).nodeName
}\n`; // #document
```

{{ EmbedLiveSample('Example 2', '100%', '200px') }}

### مثال ۳

این مثال ریشهٔ درخت جدا از سند (unmounted tree) را برمی‌گرداند. توجه کنید که `element` در اینجا ریشهٔ درخت است (چون والد ندارد)، بنابراین طبق تعریف ریشهٔ آن خودش است:

```js
const element = document.createElement("p");
const child = document.createElement("span");

element.append(child);

const rootNode = child.getRootNode(); // <p><span></span></p>

element === rootNode; // true
element === element.getRootNode(); // true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}