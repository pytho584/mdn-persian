---
title: "Animation: persist() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Animation/persist"
translated_by: "n8n + AI"
---

---
title: "Animation: persist() method"
short-title: persist()
slug: Web/API/Animation/persist
page-type: web-api-instance-method
browser-compat: api.Animation.persist
---

{{APIRef("Web Animations")}}

متد `persist()` از رابط {{domxref("Animation")}} در [Web Animations API](/en-US/docs/Web/API/Web_Animations_API) به‌طور صریح یک انیمیشن را ماندگار می‌کند و از [حذف خودکار](/en-US/docs/Web/API/Web_Animations_API/Using_the_Web_Animations_API#automatically_removing_filling_animations) آن هنگام جایگزینی با انیمیشن دیگر جلوگیری می‌کند.

## نحو

```js-nolint
persist()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### استفاده از `persist()`

در این مثال، سه دکمه داریم:

- دکمه «افزودن انیمیشن ماندگار» و «افزودن انیمیشن گذرا» هر کدام یک انیمیشن تبدیل جدید به مربع قرمز اضافه می‌کنند. انیمیشن‌ها جهت متناوب دارند: به طوری که اولی از چپ به راست، دومی از راست به چپ و به همین ترتیب است. «افزودن انیمیشن ماندگار» روی انیمیشنی که می‌سازد، `persist()` را فراخوانی می‌کند.
- دکمه سوم، «لغو یک انیمیشن»، آخرین انیمیشن اضافه‌شده را لغو می‌کند.

این مثال فهرستی از همه انیمیشن‌هایی که لغو نشده‌اند را به ترتیب اضافه‌شدن، همراه با `replaceState` هر انیمیشن نمایش می‌دهد.

#### HTML

```html
<div id="animation-target"></div>
<button id="start-persistent">Add persistent animation</button>
<button id="start-transient">Add transient animation</button>
<button id="cancel">Cancel an animation</button>
<ol id="stack"></ol>
```

```html hidden
<template id="list-item-template">
  <li>
    <span class="replaceState"></span>,
    <span class="description"></span>
  </li>
</template>
```

#### CSS

```css
div {
  width: 100px;
  height: 100px;
  background: red;
  transform: translate(100px);
}
```

#### JavaScript

```js
const target = document.getElementById("animation-target");
const persistentButton = document.getElementById("start-persistent");
const transientButton = document.getElementById("start-transient");
const cancelButton = document.getElementById("cancel");
persistentButton.addEventListener("click", () => startAnimation(true));
transientButton.addEventListener("click", () => startAnimation(false));
cancelButton.addEventListener("click", cancelTop);
const stack = [];

let offset = -100;

function startAnimation(persist) {
  offset = -offset;
  const animation = target.animate(
    { transform: `translate(${100 + offset}px)` },
    { duration: 500, fill: "forwards" },
  );
  stack.push(animation);
  if (persist) {
    animation.persist();
  }
  // Add the animation to the displayed stack (implementation not shown)
  show(animation, offset);
}

function cancelTop() {
  stack.pop()?.cancel();
}
```

```js hidden
const stackDisplay = document.getElementById("stack");
const template =
  document.getElementById("list-item-template").content.firstElementChild;
const nodes = new Map();

function show(animation, offset) {
  const direction = offset < 0 ? "left" : "right";
  const li = template.cloneNode(true);
  const description = li.querySelector(".description");
  const replaceState = li.querySelector(".replaceState");
  description.textContent = direction;
  replaceState.textContent = animation.replaceState;
  nodes.set(animation, { li, description, replaceState });
  stackDisplay.append(li);
  animation.addEventListener("cancel", () => {
    nodes.get(animation).li.remove();
    nodes.delete(animation);
  });
  animation.addEventListener("remove", () => {
    nodes.get(animation).replaceState.textContent = animation.replaceState;
  });
}
```

#### نتیجه

توجه داشته باشید که افزودن یک انیمیشن گذرا جدید، هر انیمیشن گذرای قبلی را جایگزین می‌کند. آن انیمیشن‌ها به‌طور خودکار حذف می‌شوند و `replaceState` آن‌ها `"removed"` خواهد بود. با این حال، انیمیشن‌های ماندگار حذف نخواهند شد.

همچنین توجه کنید که انیمیشن‌های حذف‌شده روی نمایش تأثیری ندارند؛ موقعیت {{htmlelement("div")}} توسط آخرین انیمیشن فعال یا ماندگار تعیین می‌شود.

{{EmbedLiveSample("using_persist","",300)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Animations API](/en-US/docs/Web/API/Web_Animations_API)
- {{domxref("Animation")}} برای سایر متدها و ویژگی‌هایی که می‌توانید برای کنترل انیمیشن صفحه وب استفاده کنید.
- {{domxref("Animation.replaceState")}}
- رویداد {{domxref("Animation.remove_event","remove")}}