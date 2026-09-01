---
title: "Element: moveBefore() method"
short-title: moveBefore()
slug: Web/API/Element/moveBefore
page-type: web-api-instance-method
browser-compat: api.Element.moveBefore
---

{{APIRef("DOM")}}

متد **`moveBefore()`** در رابط {{domxref("Element")}} یک {{domxref("Node")}} مشخص را به‌عنوان فرزند مستقیم، قبل از یک گره مرجع مشخص، درون گره فراخوانی‌کننده جابه‌جا می‌کند.

## سینتکس

```js-nolint
moveBefore(movedNode, referenceNode)
```

### پارامترها

- `movedNode`
  - : یک {{domxref("Node")}} که نمایانگر گره موردنظر برای جابه‌جایی است. توجه داشته باشید که این گره باید یک {{domxref("Element")}} یا یک گره {{domxref("CharacterData")}} باشد.
- `referenceNode`
  - : یک {{domxref("Node")}} که `movedNode` قبل از آن جابه‌جا می‌شود، یا `null`. اگر مقدار `null` باشد، `movedNode` در انتهای گره‌های فرزند گره فراخوان درج می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر پرتاب می‌شود:
    - `movedNode` مشخص‌شده بخشی از DOM نیست و شما در حال جابه‌جایی آن به داخل گره‌ای هستید که بخشی از DOM است، یا برعکس.
    - `movedNode` مشخص‌شده یک جد (ancestor) برای عنصری است که `moveBefore()` روی آن فراخوانی می‌شود.
    - شما در حال جابه‌جایی `movedNode` بین دو سند متفاوت هستید.
    - `movedNode` مشخص‌شده یک گره {{domxref("Element")}} یا {{domxref("CharacterData")}} نیست.
- `NotFoundError` {{jsxref("TypeError")}}
  - : `referenceNode` مشخص‌شده فرزند گرهی نیست که روی آن `moveBefore()` را فراخوانی می‌کنید؛ یعنی همان گره‌ای که قصد دارید `movedNode` را به داخل آن منتقل کنید.
- `TypeError` {{jsxref("TypeError")}}
  - : آرگومان دوم ارائه نشده است.

## توضیحات

متد `moveBefore()` یک گره مشخص را به جایگاه جدیدی در DOM منتقل می‌کند. این متد عملکردی مشابه متد {{domxref("Node.insertBefore()")}} ارائه می‌دهد، با این تفاوت که گره را حذف و دوباره درج نمی‌کند. این بدان معناست که وضعیت (state) گره — که اگر با `insertBefore()` و سازوکارهای مشابه جابه‌جا می‌شد بازنشانی می‌گردید — پس از جابه‌جایی حفظ می‌شود. این موارد شامل:

- وضعیت [انیمیشن](/en-US/docs/Web/CSS/Guides/Animations) و [transition](/en-US/docs/Web/CSS/Guides/Transitions).
- وضعیت بارگذاری {{htmlelement("iframe")}}.
- وضعیت‌های تعاملی (برای مثال {{cssxref(":focus")}} و {{cssxref(":active")}}).
- وضعیت عنصر [تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API).
- وضعیت باز/بسته شدن [popover](/en-US/docs/Web/API/Popover_API)ها.
- وضعیت modal عناصر {{htmlelement("dialog")}} (دیالوگ‌های modal بسته نخواهند شد).

وضعیت پخش عناصر {{htmlelement("video")}} و {{htmlelement("audio")}} در فهرست بالا گنجانده نشده است، زیرا این عناصر فارغ از سازوکار مورد استفاده، هنگام حذف و درج مجدد وضعیت خود را حفظ می‌کنند.

هنگامی که تغییرات DOM را با استفاده از {{domxref("MutationObserver")}} مشاهده می‌کنید، گره‌هایی که با `moveBefore()` جابه‌جا شده‌اند به صورت یک [گره حذف‌شده](/en-US/docs/Web/API/MutationRecord/removedNodes) و یک [گره افزوده‌شده](/en-US/docs/Web/API/MutationRecord/addedNodes) ثبت خواهند شد.

### محدودیت‌های `moveBefore()`

هنگام استفاده از `moveBefore()` باید از چند محدودیت آگاه باشید:

- این متد تنها زمانی کار می‌کند که گره را در همان سند (document) جابه‌جا کنید.
- اگر بخواهید گره‌ای را که به DOM متصل نیست به والدِ متصل به DOM منتقل کنید، یا برعکس، کار نخواهد کرد.

در چنین مواردی، `moveBefore()` با یک استثنا از نوع `HierarchyRequestError` شکست می‌خورد. اگر محدودیت‌های بالا برای مورد استفاده خاص شما الزامی هستند، بهتر است به جای آن از {{domxref("Node.insertBefore()")}} استفاده کنید، یا از [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) برای مدیریت خطاهای ناشی از چنین مواردی بهره ببرید.

### جابه‌جایی عناصر سفارشی همراه با حفظ وضعیت

هر بار که جایگاه یک [عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) در DOM از طریق `Element.moveBefore()` یا روش‌های مشابهی مانند {{domxref("Node.insertBefore()")}} به‌روزرسانی می‌شود، فراخوان‌های چرخه حیات `disconnectedCallback()` و `connectedCallback()` آن اجرا می‌شوند. از آنجا که این فراخوان‌ها معمولاً برای اجرای هرگونه کد مقداردهی اولیه یا پاک‌سازی لازم در آغاز یا پایان چرخه حیات عنصر استفاده می‌شوند، اجرای آن‌ها هنگام جابه‌جایی عنصر (به جای حذف یا درج) ممکن است باعث بروز مشکل در وضعیت آن شود.

می‌توانید از فراخوان `connectedMoveCallback()` برای حفظ وضعیت عنصر سفارشی استفاده کنید. هنگام استفاده از `moveBefore()` برای جابه‌جایی یک عنصر سفارشی، به جای `connectedCallback()` و `disconnectedCallback()`، فراخوان `connectedMoveCallback()` اجرا می‌شود.

برای اطلاعات بیشتر، [جابه‌جایی عناصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements#lifecycle_callbacks_and_state-preserving_moves) را ببینید.

## نمونه‌ها

### کاربرد پایه `moveBefore()`

در این نمایش، کاربرد پایه `moveBefore()` را نشان می‌دهیم.

#### HTML

HTML شامل یک عنصر {{htmlelement("article")}} است که درون خود یک عنصر {{htmlelement("div")}} و دو عنصر {{htmlelement("section")}} دارد. داخل `<div>` یک {{htmlelement("button")}} قرار دارد که بعداً برای جابه‌جایی آن استفاده می‌کنیم.

```html live-sample___movebefore-basic
<article id="wrapper">
  <div id="mover">
    <button>Move me!</button>
  </div>
  <section id="section1">
    <h2>Section 1</h2>
  </section>
  <section id="section2">
    <h2>Section 2</h2>
  </section>
</article>
```

#### CSS

ما برای ظاهر، حس و فاصله‌گذاری جعبه‌ها استایل‌هایی ابتدایی فراهم کرده‌ایم و از [flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) برای وسط‌چین کردن محتوای آن‌ها استفاده می‌کنیم.

```css live-sample___movebefore-basic
#section1,
#section2,
#mover {
  width: 200px;
  height: 80px;
  border: 5px solid rgb(0 0 0 / 0.25);
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
}

#section1,
#section2 {
  background-color: hotpink;
}

#mover {
  background-color: orange;
}
```

#### JavaScript

در اسکریپت خود، یک شنونده رویداد کلیک را از طریق {{domxref("EventTarget.addEventListener", "addEventListener()")}} به `<button>` متصل می‌کنیم. وقتی دکمه کلیک می‌شود، بررسی می‌کنیم که آیا {{domxref("Element.nextElementSibling", "nextElementSibling")}} مربوط به `<div>` با شناسه `mover`، اولین عنصر `<section>` است یا نه. اگر باشد، `moveBefore()` را روی `<article>` با شناسه `wrapper` فراخوانی کرده و مشخص می‌کنیم که `<div>` قبل از `<section>` دوم منتقل شود. اگر نباشد، از `moveBefore()` برای انتقال `<div>` به قبل از `<section>` اول استفاده می‌کنیم.

```js live-sample___movebefore-basic
const wrapper = document.getElementById("wrapper");
const section1 = document.getElementById("section1");
const section2 = document.getElementById("section2");
const mover = document.getElementById("mover");
const moveBtn = document.querySelector("button");

moveBtn.addEventListener("click", () => {
  if (mover.nextElementSibling === section1) {
    wrapper.moveBefore(mover, section2);
  } else {
    wrapper.moveBefore(mover, section1);
  }
});
```

#### نتیجه

نمونه رندر شده به این شکل است:

{{EmbedLiveSample("movebefore-basic", "100%", "300px")}}

چند بار روی `<button>` کلیک کنید و توجه کنید که چگونه بین دو موقعیت جابه‌جا می‌شود.

### نمایش حفظ وضعیت

در این نمایش، سازوکارهای متعددی برای جابه‌جایی یک عنصر `<div>` حاوی ویدیوی جاسازی‌شده YouTube بین دو ظرف متفاوت ارائه می‌دهیم و نشان می‌دهیم که چگونه `moveBefore()` وضعیت پخش ویدیو را حفظ می‌کند، در حالی که سازوکارهای دیگر چنین نمی‌کنند.

#### HTML

HTML شامل یک عنصر {{htmlelement("article")}} است که دو عنصر {{htmlelement("section")}} را در بر می‌گیرد. عنصر `<section>` اول شامل یک عنصر {{htmlelement("div")}} است که کد جاسازی YouTube در آن قرار دارد. همچنین یک عنصر {{htmlelement("div")}} داریم که سه عنصر {{htmlelement("button")}} را در خود جای داده است؛ بعداً از طریق JavaScript به این دکمه‌ها قابلیت جابه‌جایی `<div>` حاوی ویدیو را بین بخش‌ها اضافه خواهیم کرد.

```html live-sample___movebefore-state
<article id="wrapper">
  <section id="section1">
    <div id="mover">
      <iframe
        width="300"
        height="200"
        src="https://www.youtube.com/embed/XvoENpR9cCQ?si=o2i6MvxugD-O5yyv"
        title="YouTube video player"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        referrerpolicy="strict-origin-when-cross-origin"
        allowfullscreen></iframe>
    </div>
  </section>
  <section id="section2"></section>
</article>
<div id="controls">
  <button id="move-before">move with <code>moveBefore()</code></button>
  <button id="insertbefore">move with <code>insertBefore()</code></button>
  <button id="prepend">move with <code>prepend()</code></button>
</div>
```

#### CSS

برای چیدمان از [flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) استفاده می‌کنیم تا دو عنصر `<section>` کنار هم قرار بگیرند و دکمه‌ها نیز به‌طور یکنواخت درون `<div>` با شناسه `controls` فاصله‌گذاری شوند.

```css live-sample___movebefore-state
#wrapper,
#controls {
  width: 100%;
  display: flex;
}

#wrapper {
  margin-bottom: 10px;
}

iframe {
  border: none;
}

section {
  flex: 1;
  padding: 10px;
}

#controls {
  display: flex;
  justify-content: space-around;
}

#section1 {
  background-color: hotpink;
}

#section2 {
  background-color: orange;
}

#mover {
  max-width: 100%;
  background-color: black;
}
```

#### JavaScript

در اسکریپت خود، شنونده‌های رویداد `click` را از طریق {{domxref("EventTarget.addEventListener", "addEventListener()")}} به هر `<button>` متصل می‌کنیم. وقتی دکمه‌ها کلیک می‌شوند، بررسی می‌کنیم که کدام عنصر `<section>`، {{domxref("Node.parentElement", "parentElement")}} برای `<div>` حاوی ویدیو است و سپس از تابع مربوطه (`moveBefore()`، {{domxref("Node.insertBefore", "insertBefore()")}} یا {{domxref("Element.prepend", "prepend()")}}) استفاده می‌کنیم تا آن را به داخل عنصر `<section>` _دیگر_ منتقل کنیم.

```js live-sample___movebefore-state
const section1 = document.getElementById("section1");
const section2 = document.getElementById("section2");
const mover = document.getElementById("mover");
const moveBeforeBtn = document.getElementById("move-before");
const insertbeforeBtn = document.getElementById("insertbefore");
const prependBtn = document.getElementById("prepend");

moveBeforeBtn.addEventListener("click", () => {
  if (mover.parentElement === section1) {
    section2.moveBefore(mover, null);
  } else {
    section1.moveBefore(mover, null);
  }
});

insertbeforeBtn.addEventListener("click", () => {
  if (mover.parentElement === section1) {
    section2.insertBefore(mover, null);
  } else {
    section1.insertBefore(mover, null);
  }
});

prependBtn.addEventListener("click", () => {
  if (mover.parentElement === section1) {
    section2.prepend(mover);
  } else {
    section1.prepend(mover);
  }
});
```

#### نتیجه

نمونه رندر شده به این شکل است:

{{EmbedLiveSample("movebefore-state", "100%", "260px")}}

ویدیوی جاسازی‌شده YouTube را پخش کنید و سپس چند بار روی هر `<button>` کلیک کنید تا موقعیت عنصر `<div>` روی صفحه از چپ به راست جابه‌جا شود. توجه کنید که در مورد `insertBefore()` و `prepend()`، وضعیت ویدیو پس از هر جابه‌جایی بازنشانی می‌شود و باید دوباره پخش شود. اما در مورد `moveBefore()`، وضعیت پس از هر جابه‌جایی حفظ می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.moveBefore()")}}
- {{domxref("DocumentFragment.moveBefore()")}}
- {{domxref("Node.insertBefore()")}}