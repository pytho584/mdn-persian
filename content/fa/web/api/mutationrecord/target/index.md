---
title: "MutationRecord: target property"
short-title: target
slug: Web/API/MutationRecord/target
page-type: web-api-instance-property
browser-compat: api.MutationRecord.target
---

{{APIRef("DOM")}}

ویژگی فقطخواندنی **`target`** در {{domxref("MutationRecord")}}، هدف (یعنی گرهٔ تغییرکرده/تغییریافته) در تغییری است که با یک {{domxref("MutationObserver")}} مشاهده شده است.

## مقدار

این مقدار، همان {{domxref("Node")}}ای است که تغییر روی آن رخ داده است.

- اگر {{domxref("MutationRecord.type", "type")}} رکورد برابر `attributes` باشد، این مقدار همان {{domxref("Element")}}ای است که ویژگی‌هایش (attributes) تغییر کرده است.
- اگر {{domxref("MutationRecord.type", "type")}} رکورد برابر `characterData` باشد، این مقدار گرهٔ {{domxref("CharacterData")}} است.
- اگر {{domxref("MutationRecord.type", "type")}} رکورد برابر `childList` باشد، این مقدار همان {{domxref("Node")}}ای است که فرزندانش تغییر کرده‌اند.

## مثال‌ها

### Logging the target of a mutation

در مثال زیر دو div داریم: یک div قرمز (`#red-div`) و یک div آبی (`#blue-div`) که داخل یک div کانتینر با شناسهٔ `#container` قرار گرفته‌اند. یک {{domxref("MutationObserver")}} ساخته می‌شود تا روی کانتینر نظارت کند. این observer تغییرات childList را زیر نظر دارد و همچنین دارای `subtree: true` است؛ بنابراین تغییرات فرزندانِ فرزندانِ کانتینر را نیز مشاهده می‌کند.

تابع callback این observer، مقدار `target` را در رکورد تغییر ثبت می‌کند. وقتی به `#red-div` یا `#blue-div` گره اضافه کنیم، `target` به‌ترتیب برابر با `#red-div` یا `#blue-div` خواهد بود.

#### HTML

```html
<pre id="log">Target of mutation:</pre>
<button id="add-nodes-to-red-div">Add a node to red div</button>
<button id="add-nodes-to-blue-div">Add a node to blue div</button>
<button id="reset">Reset</button>
<div id="container">
  <div id="red-div"></div>
  <div id="blue-div"></div>
</div>
```

```css hidden
#log {
  border: 1px dotted black;
  padding: 0.5rem;
}

#red-div {
  border: 1px solid red;
  margin-top: 0.5rem;
  margin-right: 0.5rem;
  padding: 0.5rem;
  overflow: auto;
}

#blue-div {
  border: 1px solid blue;
  margin-top: 0.5rem;
  margin-left: 0.5rem;
  padding: 0.5rem;
  overflow: auto;
}

#container {
  display: grid;
  grid-template-columns: 50% auto;
}
```

#### JavaScript

```js
const container = document.querySelector("#container");
const redDiv = document.querySelector("#red-div");
const blueDiv = document.querySelector("#blue-div");
const addToRed = document.querySelector("#add-nodes-to-red-div");
const addToBlue = document.querySelector("#add-nodes-to-blue-div");
const reset = document.querySelector("#reset");
const log = document.querySelector("#log");

addToRed.addEventListener("click", () => {
  const newPara = document.createElement("p");
  newPara.textContent = `Current time: ${Date.now()}`;
  redDiv.appendChild(newPara);
});

addToBlue.addEventListener("click", () => {
  const newPara = document.createElement("p");
  newPara.textContent = `Current time: ${Date.now()}`;
  blueDiv.appendChild(newPara);
});

reset.addEventListener("click", () => self.location.reload());

function logMutationTarget(records) {
  for (const record of records) {
    log.textContent = `Target of mutation: ${record.target.id}`;
  }
}

const observer = new MutationObserver(logMutationTarget);
observer.observe(container, { childList: true, subtree: true });
```

#### نتیجه

{{EmbedLiveSample("Logging the target of a mutation", "", 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}