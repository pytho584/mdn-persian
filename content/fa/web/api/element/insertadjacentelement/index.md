---
title: "Element: insertAdjacentElement() method"
short-title: insertAdjacentElement()
slug: Web/API/Element/insertAdjacentElement
page-type: web-api-instance-method
browser-compat: api.Element.insertAdjacentElement
---

{{APIRef("DOM")}}

متد **`insertAdjacentElement()`** از رابط {{domxref("Element")}} یک گره عنصر مشخص را در موقعیتی معین نسبت به عنصری که بر روی آن فراخوانی شده است، درج می‌کند.

## نحو

```js-nolint
insertAdjacentElement(position, element)
```

### پارامترها

- `position`
  - : رشته‌ای که موقعیت را نسبت به `targetElement` مشخص می‌کند. باید (بدون حساسیت به بزرگی/کوچکی حروف) با یکی از رشته‌های زیر مطابقت داشته باشد:
    - `'beforebegin'`: قبل از خود `targetElement`.
    - `'afterbegin'': درست داخل `targetElement`، قبل از اولین فرزند آن.
    - `'beforeend'`: درست داخل `targetElement`، بعد از آخرین فرزند آن.
    - `'afterend'`: بعد از خود `targetElement`.

- `element`
  - : عنصری که قرار است در درخت درج شود.

### مقدار بازگشتی

عنصری که درج شده است، یا `null` در صورت شکست درج.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر `position` مشخص شده یک مقدار شناخته‌شده نباشد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر `element` مشخص شده یک عنصر معتبر نباشد، پرتاب می‌شود.

### نمایش بصری موقعیت‌ها

```html
<!-- beforebegin -->
<p>
  <!-- afterbegin -->
  foo
  <!-- beforeend -->
</p>
<!-- afterend -->
```

> [!NOTE]
> موقعیت‌های `beforebegin` و `afterend` فقط زمانی کار می‌کنند که گره در یک درخت باشد و یک عنصر والد داشته باشد.

## مثال‌ها

### درج قبل و بعد

در این مثال یک ردیف از جعبه‌های مربعی داریم. کاربر می‌تواند با کلیک روی یک جعبه آن را انتخاب کند: این کار یک حاشیه متفاوت به جعبه می‌دهد تا نشان دهد انتخاب شده است.

اگر یک جعبه انتخاب شده باشد و کاربر دکمه‌های "Insert before" یا "Insert after" را فشار دهد، کد یک جعبه جدید ایجاد می‌کند، یک رنگ تصادفی به آن می‌دهد و آن را قبل یا بعد از جعبه انتخاب شده درج می‌کند.

#### HTML

```html
<p>
  Click colored box to select it, then use the first two buttons below to insert
  elements before and after your selection.
</p>

<section>
  <div></div>
  <div></div>
  <div></div>
  <div></div>
</section>

<button class="before">Insert before</button>
<button class="after">Insert after</button>
<button class="reset">Reset demo</button>
```

#### CSS

```css
div {
  width: 50px;
  height: 50px;
  margin: 3px;
  border: 3px solid black;
  display: inline-block;
  background-color: red;
}

.selected {
  border-color: aqua;
}
```

#### JavaScript

```js
let selectedElem;

// Function to select a new element
function selectElement(newSelection) {
  if (selectedElem !== newSelection) {
    if (selectedElem) {
      selectedElem.classList.remove("selected");
    }
    selectedElem = newSelection;
    newSelection.classList.add("selected");
  }
}

// Add click handlers that select the clicked element
const initElems = Array.from(document.querySelectorAll("section div"));
for (const initElem of initElems) {
  initElem.addEventListener("click", (e) => selectElement(e.target));
}

// Add click handlers to "beforeBtn" and "afterBtn"
// to insert a new element before/after the selected element
const beforeBtn = document.querySelector(".before");
const afterBtn = document.querySelector(".after");
beforeBtn.addEventListener("click", () => insertNewElement("beforebegin"));
afterBtn.addEventListener("click", () => insertNewElement("afterend"));

function insertNewElement(position) {
  function random() {
    return Math.floor(Math.random() * 255);
  }

  if (!selectedElem) {
    return;
  }

  const newElement = document.createElement("div");
  const randomColor = `rgb(${random(255)} ${random(255)} ${random(255)})`;
  newElement.style.backgroundColor = randomColor;
  newElement.addEventListener("click", (e) => selectElement(e.target));

  selectedElem.insertAdjacentElement(position, newElement);
}

// Reset the example
const resetBtn = document.querySelector(".reset");
resetBtn.addEventListener("click", () => window.location.reload(true));
```

#### نتیجه

{{embedlivesample("Inserting before and after", "", "200")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.insertAdjacentHTML()")}}
- {{domxref("Element.insertAdjacentText()")}}
- {{domxref("Node.insertBefore()")}} (مشابه `beforebegin`، با آرگومان‌های متفاوت)
- {{domxref("Node.appendChild()")}} (همان اثر `beforeend`)