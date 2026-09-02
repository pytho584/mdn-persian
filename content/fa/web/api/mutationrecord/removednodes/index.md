---
title: "MutationRecord: removedNodes property"
short-title: removedNodes
slug: Web/API/MutationRecord/removedNodes
page-type: web-api-instance-property
browser-compat: api.MutationRecord.removedNodes
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`removedNodes`** از {{domxref("MutationRecord")}} یک {{domxref("NodeList")}} از گره‌هایی است که توسط یک جهش (mutation) مشاهده‌شده با {{domxref("MutationObserver")}} از یک گره هدف حذف شده‌اند.

## مقدار

یک {{domxref("NodeList")}} شامل گره‌هایی که از هدف جهش مشاهده‌شده توسط {{domxref("MutationObserver")}} حذف شده‌اند.

## مثال‌ها

### مشاهده گره‌های حذف‌شده

در مثال زیر، دو دکمه وجود دارد: یکی برای افزودن گره‌های جدید به یک گره هدف و دیگری برای حذف آن‌ها. یک {{domxref("MutationObserver")}} برای مشاهده تغییرات گره هدف استفاده می‌شود؛ وقتی تغییری شناسایی شود، ناظر تابعی به نام `logRemovedNodes()` را فراخوانی می‌کند.

تابع `logRemovedNodes()` بررسی می‌کند که `type` رکورد جهش برابر با `childList` باشد، یعنی فرزندان گره هدف تغییر کرده‌اند. اگر type برابر با `childList` باشد، تابع تعداد کل گره‌های حذف‌شده را به‌روزرسانی می‌کند. توجه داشته باشید که کلیک روی دکمه «Add a node» تعداد کل گره‌های حذف‌شده را افزایش نمی‌دهد، زیرا در این حالت طول `record.removedNodes` برابر با `0` خواهد بود.

#### HTML

```html
<button id="add-nodes">Add a node</button>
<button id="remove-nodes">Remove a node</button>
<button id="reset">Reset</button>

<pre id="counter">Total removed nodes: 0</pre>
<div id="target"></div>
```

```css hidden
#counter {
  border: 1px dotted black;
  padding: 0.5rem;
}
```

#### JavaScript

```js
const addNodes = document.querySelector("#add-nodes");
const removeNodes = document.querySelector("#remove-nodes");
const reset = document.querySelector("#reset");
const counter = document.querySelector("#counter");
const target = document.querySelector("#target");
let totalRemovedNodes = 0;

addNodes.addEventListener("click", () => {
  const newPara = document.createElement("p");
  newPara.textContent = `Current time: ${Date.now()}`;
  target.appendChild(newPara);
});

removeNodes.addEventListener("click", () => {
  const lastChild = target.lastChild;
  if (lastChild) {
    target.removeChild(lastChild);
  }
});

reset.addEventListener("click", () => self.location.reload());

function logRemovedNodes(records) {
  for (const record of records) {
    // Check if the childList of the target node has been mutated
    if (record.type === "childList") {
      totalRemovedNodes += record.removedNodes.length;
      // Log the number of nodes removed
      counter.textContent = `Total removed nodes: ${totalRemovedNodes}`;
    }
  }
}

const observer = new MutationObserver(logRemovedNodes);
observer.observe(target, { childList: true });
```

#### نتیجه

{{EmbedLiveSample("Observing removed nodes")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}