---
title: "Event: stopImmediatePropagation() method"
short-title: stopImmediatePropagation()
slug: Web/API/Event/stopImmediatePropagation
page-type: web-api-instance-method
browser-compat: api.Event.stopImmediatePropagation
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

متد **`stopImmediatePropagation()`** از رابط {{domxref("Event")}} از فراخوانی شنوندگان (listeners) دیگر همان رویداد جلوگیری می‌کند.

اگر چندین شنونده به یک عنصر برای یک نوع رویداد یکسان متصل شده باشند، آنها به ترتیبی که اضافه شده‌اند فراخوانی می‌شوند. اگر `stopImmediatePropagation()` در حین یکی از این فراخوانی‌ها فراخوانده شود، هیچ‌یک از شنوندگان باقی‌مانده، چه روی آن عنصر و چه روی هر عنصر دیگر، فراخوانی نخواهند شد.

## Syntax

```js-nolint
stopImmediatePropagation()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### مقایسه توابع توقف رویداد

مثال زیر شامل سه دکمه درون سه div تو در تو است. هر دکمه سه شنونده رویداد برای رویدادهای کلیک ثبت کرده است، و هر div نیز یک شنونده رویداد برای رویدادهای کلیک دارد.

- دکمه بالایی امکان انتشار عادی رویداد را می‌دهد.
- دکمه وسطی در اولین کنترل‌کننده رویداد خود `stopPropagation()` را فراخوانی می‌کند.
- دکمه پایینی در اولین کنترل‌کننده رویداد خود `stopImmediatePropagation()` را فراخوانی می‌کند.

#### HTML

```html
<h2>Click on the buttons</h2>
<div>
  outer div<br />
  <div>
    middle div<br />
    <div>
      inner div<br />
      <button>allow propagation</button><br />
      <button id="stopPropagation">stop propagation</button><br />
      <button id="stopImmediatePropagation">immediate stop propagation</button>
    </div>
  </div>
</div>
<pre></pre>
```

#### CSS

```css
div {
  display: inline-block;
  padding: 10px;
  background-color: white;
  border: 2px solid black;
  margin: 10px;
}

button {
  width: 100px;
  color: #000088;
  padding: 5px;
  background-color: white;
  border: 2px solid black;
  border-radius: 30px;
  margin: 5px;
}
```

#### JavaScript

```js
const outElem = document.querySelector("pre");

/* Clear the output */
document.addEventListener(
  "click",
  () => {
    outElem.textContent = "";
  },
  true,
);

/* Set event listeners for the buttons */
document.querySelectorAll("button").forEach((elem) => {
  for (let i = 1; i <= 3; i++) {
    elem.addEventListener("click", (evt) => {
      /* Do any propagation stopping in first event handler */
      if (i === 1 && elem.id) {
        evt[elem.id]();
        outElem.textContent += `Event handler for event 1 calling ${elem.id}()\n`;
      }

      outElem.textContent += `Click event ${i} processed on "${elem.textContent}" button\n`;
    });
  }
});

/* Set event listeners for the divs */
document
  .querySelectorAll("div")
  .forEach((elem) =>
    elem.addEventListener(
      "click",
      (evt) =>
        (outElem.textContent += `Click event processed on "${elem.firstChild.data.trim()}"\n`),
    ),
  );
```

#### نتیجه

هر کنترل‌کننده رویداد کلیک هنگام فراخوانی یک پیام وضعیت نمایش می‌دهد. اگر دکمه وسطی را فشار دهید، خواهید دید که `stopPropagation()` به همه کنترل‌کننده‌های رویداد ثبت‌شده برای کلیک روی آن دکمه اجازه اجرا می‌دهد، اما از اجرای کنترل‌کننده‌های رویداد کلیک برای divها که معمولاً به دنبال آن می‌آیند جلوگیری می‌کند. با این حال، اگر دکمه پایینی را فشار دهید، `stopImmediatePropagation()` تمام انتشار پس از رویدادی که آن را فراخوانی کرد متوقف می‌کند.

{{ EmbedLiveSample("Comparing event-stopping functions", 500, 550) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}