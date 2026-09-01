---
title: "EventTarget: EventTarget() constructor"
short-title: EventTarget()
slug: Web/API/EventTarget/EventTarget
page-type: web-api-constructor
browser-compat: api.EventTarget.EventTarget
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

سازندهی **`EventTarget()`** یک نمونهی جدید از شیء {{domxref("EventTarget")}} ایجاد میکند.

> [!NOTE]
> فراخوانی صریح این سازنده نسبتاً نادر است. در بیشتر موارد، این سازنده در درون سازندهی یک شیء که از رابط {{domxref("EventTarget")}} ارث میبرد، با استفاده از کلیدواژهی [`super`](/en-US/docs/Web/JavaScript/Reference/Operators/super) استفاده میشود.

## نحو

```js-nolint
new EventTarget()
```

### پارامترها

پارامتری ندارد.

### مقدار بازگشتی

یک نمونهی جدید از شیء {{domxref("EventTarget")}}.

## مثالها

### پیادهسازی یک شمارنده

این مثال کلاس `Counter` را با متدهای `increment()` و `decrement()` پیادهسازی میکند. زمانی که هر یک از این متدها فراخوانی شود، یک رویداد سفارشی `"valuechange"` صادر میشود.

#### HTML

```html
<button id="dec" aria-label="Decrement">-</button>
<span id="currentValue">0</span>
<button id="inc" aria-label="Increment">+</button>
```

#### JavaScript

```js
class Counter extends EventTarget {
  constructor(initialValue = 0) {
    super();
    this.value = initialValue;
  }

  #emitChangeEvent() {
    this.dispatchEvent(new CustomEvent("valuechange", { detail: this.value }));
  }

  increment() {
    this.value++;
    this.#emitChangeEvent();
  }

  decrement() {
    this.value--;
    this.#emitChangeEvent();
  }
}

const initialValue = 0;
const counter = new Counter(initialValue);
document.querySelector("#currentValue").innerText = initialValue;

counter.addEventListener("valuechange", (event) => {
  document.querySelector("#currentValue").innerText = event.detail;
});

document.querySelector("#inc").addEventListener("click", () => {
  counter.increment();
});

document.querySelector("#dec").addEventListener("click", () => {
  counter.decrement();
});
```

#### نتیجه

{{EmbedLiveSample("Implementing a counter")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("EventTarget")}}