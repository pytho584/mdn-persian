---
title: "MutationRecord: type property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/MutationRecord/type"
---

---
title: "MutationRecord: type property"
short-title: type
slug: Web/API/MutationRecord/type
page-type: web-api-instance-property
browser-compat: api.MutationRecord.type
---

{{APIRef("DOM")}}

ویژگی فقط‌خواندنی **`type`** از {{domxref("MutationRecord")}}، نوع رکورد جهش (MutationRecord) مشاهده‌شده توسط یک {{domxref("MutationObserver")}} است.

## مقدار

این ویژگی به صورت رشته‌ای، نوع جهش را مشخص می‌کند. مقدار می‌تواند یکی از موارد زیر باشد:

- `attributes` اگر جهش از نوع تغییر ویژگی (attribute) بوده باشد.

- `characterData` اگر جهش روی یک گره {{domxref("CharacterData")}} رخ داده باشد.

- `childList` اگر جهش روی درخت گره‌ها (تغییر در لیست فرزندان) بوده باشد.

## مثال‌ها

### ثبت نوع یک جهش

مثال زیر دو دکمه برای دستکاری DOM در اختیار شما قرار می‌دهد. دکمه اول یک گره جدید به مثال اضافه می‌کند و دکمه دوم ویژگی `color` همه گره‌های اضافه‌شده را تغییر می‌دهد. یک {{domxref("MutationObserver")}} برای مشاهده همه این تغییرات ساخته می‌شود و مشاهده‌گر طوری تنظیم شده که نوع رکورد جهش را در `#log` ثبت کند.

خواهید دید که وقتی یک گره اضافه می‌کنید، `type` برابر با `childList` است و وقتی ویژگی `color` را تغییر می‌دهید، `type` برابر با `attributes` است.

#### HTML

```html
<button id="add-nodes">Add a node</button>
<button id="set-attribute">Change the color</button>

<button id="reset">Reset</button>

<pre id="log">Mutation type:</pre>
<div id="target"><p>Node #0</p></div>
```

```css hidden
#log {
  border: 1px dotted black;
  padding: 0.5rem;
}

.blue {
  color: blue;
}

.red {
  color: red;
}
```

#### JavaScript

```js
const addNodes = document.querySelector("#add-nodes");
const setAttribute = document.querySelector("#set-attribute");
const reset = document.querySelector("#reset");
const log = document.querySelector("#log");
const target = document.querySelector("#target");
let nodeNumber = 1;

addNodes.addEventListener("click", () => {
  const newPara = document.createElement("p");
  newPara.textContent = `Node #${nodeNumber}`;
  nodeNumber++;
  target.appendChild(newPara);
});

setAttribute.addEventListener("click", () => {
  if (target.getAttribute("class") === "red") {
    target.setAttribute("class", "blue");
  } else {
    target.setAttribute("class", "red");
  }
});

reset.addEventListener("click", () => self.location.reload());

function logMutationType(records) {
  for (const record of records) {
    log.textContent = `Mutation type: ${record.type}`;
  }
}

const observer = new MutationObserver(logMutationType);
observer.observe(target, { childList: true, attributes: true, subtree: true });
```

#### نتیجه

{{EmbedLiveSample("Log the type of a mutation", "", 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}