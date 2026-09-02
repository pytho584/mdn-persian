---
title: "MutationRecord: nextSibling property"
short-title: nextSibling
slug: Web/API/MutationRecord/nextSibling
page-type: web-api-instance-property
browser-compat: api.MutationRecord.nextSibling
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`nextSibling`** در {{domxref("MutationRecord")}}، هم‌شأن (sibling) بعدیِ گرهٔ فرزندی است که به [`target`](/en-US/docs/Web/API/MutationRecord/target) یک {{domxref("MutationObserver")}} افزوده شده یا از آن حذف شده است.

## مقدار

اگر گره‌ای به [`target`](/en-US/docs/Web/API/MutationRecord/target) یک {{domxref("MutationObserver")}} افزوده یا از آن حذف شود، مقدار این ویژگی، آن {{domxref("Node")}}ای است که هم‌شأنِ بعدیِ گرهٔ افزوده‌شده یا حذف‌شده است؛ یعنی گره‌ای که بلافاصله پس از این گره در فهرست {{domxref("Node.childNodes", "childNodes")}} والد قرار دارد.

اگر هیچ گره‌ای افزوده یا حذف نشده باشد، یا اگر گره، آخرین فرزندِ والد خود باشد، مقدار این ویژگی `null` است.

## مثال‌ها

### ثبت هم‌شأنِ بعدیِ یک تغییر

این مثال هر بار که روی دکمه کلیک کنید یک گره اضافه می‌کند، اما گره را در _ابتدای target_ اضافه می‌کند، نه در انتهای آن. سپس observer، `textContent` متعلق به `nextSibling` گرهٔ افزوده‌شده را در لاگ ثبت می‌کند.

#### HTML

```html
<button id="add-nodes">Add a node</button>
<button id="reset">Reset</button>

<pre id="log" class="log">Next sibling of added node:</pre>
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
  target.insertBefore(newPara, target.firstChild);
});

reset.addEventListener("click", () => self.location.reload());

function logNextSibling(records) {
  for (const record of records) {
    if (record.type === "childList") {
      for (const newNode of record.addedNodes) {
        log.textContent = `Next sibling of added node: ${record.nextSibling?.textContent}`;
      }
    }
  }
}

const observer = new MutationObserver(logNextSibling);
observer.observe(target, { childList: true });
```

#### نتیجه

{{EmbedLiveSample("Log the next sibling of a mutation", "", 250)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}