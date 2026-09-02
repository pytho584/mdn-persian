---
title: "MutationObserver: MutationObserver() constructor"
short-title: MutationObserver()
slug: Web/API/MutationObserver/MutationObserver
page-type: web-api-constructor
browser-compat: api.MutationObserver.MutationObserver
---

{{APIRef("DOM WHATWG")}}

سازندهٔ **`MutationObserver()`** — که بخشی از رابط {{domxref("MutationObserver")}} است — یک ناظر (observer) جدید ساخته و بازمی‌گرداند که هنگام رخ دادن رویدادهای DOM، تابع callback مشخصی را فراخوانی می‌کند.

مشاهدهٔ DOM بلافاصله آغاز نمی‌شود؛ ابتدا باید متد {{domxref("MutationObserver.observe", "observe()")}} فراخوانی شود تا مشخص کند کدام بخش از DOM و چه نوع تغییراتی باید زیر نظر گرفته شوند.

## سینتکس

```js-nolint
new MutationObserver(callback)
```

### پارامترها

- `callback`
  - : تابعی که برای هر تغییر DOM که با توجه به گره یا زیردرختِ مشاهده‌شده و گزینه‌ها واجد شرایط باشد، فراخوانی می‌شود.

    تابع `callback` دو پارامتر ورودی می‌گیرد:
    1. آرایه‌ای از اشیاء {{domxref("MutationRecord")}} که هر تغییری را که رخ داده توصیف می‌کند.
    2. شیء {{domxref("MutationObserver")}}ای که `callback` را فراخوانی کرده است. این پارامتر بیشتر برای قطع کردن ناظر با استفاده از {{domxref("MutationObserver.disconnect()")}} به کار می‌رود.

    برای جزئیات بیشتر، به [مثال‌های زیر](#examples) مراجعه کنید.

### مقدار بازگشتی

یک شیء جدید {{domxref("MutationObserver")}} که طوری پیکربندی شده است تا هنگام رخ دادن تغییرات در DOM، تابع `callback` مشخص‌شده را فراخوانی کند.

## مثال‌ها

### مشاهدهٔ عناصر فرزند

در این مثال، دکمه‌هایی برای افزودن یک عنصر {{htmlelement("li")}} به فهرست و حذف اولین عنصر `<li>` از فهرست وجود دارد.

ما از یک `MutationObserver` استفاده می‌کنیم تا از تغییرات فهرست باخبر شویم. در تابع callback، موارد افزوده‌شده و حذف‌شده را ثبت (log) می‌کنیم و به محض اینکه فهرست خالی شد، ناظر را قطع می‌کنیم.

دکمهٔ «Reset example» مثال را به حالت اولیه بازمی‌گرداند.

#### HTML

```html
<button id="add">Add child</button>
<button id="remove">Remove child</button>
<button id="reset">Reset example</button>

<ul id="container"></ul>

<pre id="log"></pre>
```

#### CSS

```css
#container,
#log {
  height: 150px;
  overflow: scroll;
}

#container li {
  background-color: paleturquoise;
  margin: 0.5rem;
}
```

#### JavaScript

```js
const add = document.querySelector("#add");
const remove = document.querySelector("#remove");
const reset = document.querySelector("#reset");
const container = document.querySelector("#container");
const log = document.querySelector("#log");

let namePrefix = 0;

add.addEventListener("click", () => {
  const newItem = document.createElement("li");
  newItem.textContent = `item ${namePrefix}`;
  container.appendChild(newItem);
  namePrefix++;
});

remove.addEventListener("click", () => {
  const itemToRemove = document.querySelector("li");
  if (itemToRemove) {
    itemToRemove.parentNode.removeChild(itemToRemove);
  }
});

reset.addEventListener("click", () => {
  document.location.reload();
});

function logChanges(records, observer) {
  for (const record of records) {
    for (const addedNode of record.addedNodes) {
      log.textContent = `Added: ${addedNode.textContent}\n${log.textContent}`;
    }
    for (const removedNode of record.removedNodes) {
      log.textContent = `Removed: ${removedNode.textContent}\n${log.textContent}`;
    }
    if (record.target.childNodes.length === 0) {
      log.textContent = `Disconnected\n${log.textContent}`;
      observer.disconnect();
    }
    console.log(record.target.childNodes.length);
  }
}

const observerOptions = {
  childList: true,
  subtree: true,
};

const observer = new MutationObserver(logChanges);
observer.observe(container, observerOptions);
```

#### نتیجه

برای افزودن آیتم به فهرست روی «Add child» کلیک کنید و برای حذف آن‌ها روی «Remove child» کلیک کنید. تابع callbackِ observer، افزودن‌ها و حذف‌ها را ثبت می‌کند. به محض خالی شدن فهرست، observer پیام «Disconnected» را ثبت کرده و خود را قطع می‌کند.

دکمهٔ «Reset example» مثال را دوباره بارگذاری می‌کند تا بتوانید آن را از نو امتحان کنید.

{{EmbedLiveSample("Observing child elements", 0, 400)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}