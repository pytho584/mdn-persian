---
title: "MutationRecord: addedNodes property"
short-title: addedNodes
slug: Web/API/MutationRecord/addedNodes
page-type: web-api-instance-property
browser-compat: api.MutationRecord.addedNodes
---

{{APIRef("DOM")}}

خاصیت فقط-خواندنی **`addedNodes`** از {{domxref("MutationRecord")}}، یک {{domxref("NodeList")}} از گره‌هایی است که در اثر یک جهش (mutation) مشاهده‌شده با {{domxref("MutationObserver")}} به یک گره هدف اضافه شده‌اند.

## مقدار

یک {{domxref("NodeList")}} شامل گره‌هایی که به هدف جهش مشاهده‌شده توسط {{domxref("MutationObserver")}} اضافه شده‌اند.

## مثال‌ها

### به‌روزرسانی هنگام افزودن یک گره

در مثال زیر، دو دکمه وجود دارد: یکی برای افزودن گره‌های جدید به یک گره هدف، و دیگری برای حذف آن‌ها. یک {{domxref("MutationObserver")}} برای مشاهده تغییرات گره هدف استفاده می‌شود؛ هنگامی که تغییری تشخیص داده شود، observer تابع `logNewNodes()` را فراخوانی می‌کند.

تابع `logNewNodes()` بررسی می‌کند که `type` رکورد MutationRecord برابر با `childList` باشد، به این معنی که فرزندان گره هدف تغییر کرده‌اند. اگر نوع برابر با `childList` باشد، تابع تعداد کل گره‌های جدید اضافه شده را به‌روزرسانی می‌کند. با این حال، توجه داشته باشید که کلیک روی دکمه «حذف یک گره» تعداد کل گره‌های جدید را افزایش نمی‌دهد، زیرا در این حالت `record.addedNodes` طولی برابر با `0` خواهد داشت.

#### HTML

```html
<button id="add-nodes">Add a node</button>
<button id="remove-nodes">Remove a node</button>
<button id="reset">Reset</button>

<pre id="counter">Total added nodes: 0</pre>
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
let totalAddedNodes = 0;

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

function logNewNodes(records) {
  for (const record of records) {
    // Check if the childList of the target node has been mutated
    if (record.type === "childList") {
      totalAddedNodes += record.addedNodes.length;
      // Log the number of nodes added
      counter.textContent = `Total added nodes: ${totalAddedNodes}`;
    }
  }
}

const observer = new MutationObserver(logNewNodes);
observer.observe(target, { childList: true });
```

#### نتیجه

{{EmbedLiveSample("Update when adding a node")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}