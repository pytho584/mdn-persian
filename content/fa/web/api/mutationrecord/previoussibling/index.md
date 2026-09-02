---
title: "MutationRecord: previousSibling property"
short-title: previousSibling
slug: Web/API/MutationRecord/previousSibling
page-type: web-api-instance-property
browser-compat: api.MutationRecord.previousSibling
---

{{APIRef("DOM")}}

خاصیت فقط خواندنی **`previousSibling`** از {{domxref("MutationRecord")}}، خواهر/برادر قبلی یک گره فرزند که به [`target`](/en-US/docs/Web/API/MutationRecord/target) یک {{domxref("MutationObserver")}} اضافه یا از آن حذف شده است را نشان می‌دهد.

## مقدار

اگر گره‌ای به [`target`](/en-US/docs/Web/API/MutationRecord/target) یک {{domxref("MutationObserver")}} اضافه یا از آن حذف شود، مقدار این خاصیت، {{domxref("Node")}}ای است که خواهر/برادر قبلی گره اضافه‌شده یا حذف‌شده است: یعنی گره‌ای که بلافاصله قبل از این گره در لیست {{domxref("Node.childNodes", "childNodes")}} والد قرار دارد.

اگر هیچ گره اضافه یا حذف شده‌ای وجود نداشته باشد، یا اگر گره، اولین فرزند والد خود باشد، مقدار `null` است.

## مثال‌ها

### ثبت خواهر/برادر قبلی یک جهش

این مثال هر بار که روی دکمه کلیک می‌کنید، یک گره اضافه می‌کند. سپس observer، `textContent` مربوط به `previousSibling` گره اضافه‌شده را ثبت می‌کند.

#### HTML

```html
<button id="add-nodes">Add a node</button>
<button id="reset">Reset</button>

<pre id="log" class="log">Previous sibling of added node:</pre>
<div id="target"><p>Node #0</p></div>
```

```css hidden
.log {
  border: 1px dotted black;
  padding: 0.5rem;
}
```

#### JavaScript

```js
const addNodes = document.querySelector("#add-nodes");
const reset = document.querySelector("#reset");
const target = document.querySelector("#target");
let nodeNumber = 1;

addNodes.addEventListener("click", () => {
  const newPara = document.createElement("p");
  newPara.textContent = `Node #${nodeNumber}`;
  nodeNumber++;
  target.appendChild(newPara);
});

reset.addEventListener("click", () => self.location.reload());

function logPreviousSibling(records) {
  for (const record of records) {
    if (record.type === "childList") {
      for (const newNode of record.addedNodes) {
        log.textContent = `Previous sibling of added node: ${newNode.previousSibling?.textContent}`;
      }
    }
  }
}

const observer = new MutationObserver(logPreviousSibling);
observer.observe(target, { childList: true });
```

#### نتیجه

{{EmbedLiveSample("Log the previous sibling of a mutation", "", 250)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}