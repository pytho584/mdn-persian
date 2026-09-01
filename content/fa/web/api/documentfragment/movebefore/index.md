---
title: "DocumentFragment: moveBefore() method"
---

---
title: "DocumentFragment: moveBefore() method"
short-title: moveBefore()
slug: Web/API/DocumentFragment/moveBefore
page-type: web-api-instance-method
browser-compat: api.DocumentFragment.moveBefore
---

{{APIRef("DOM")}}

متد **`moveBefore()`** در رابط {{domxref("DocumentFragment")}} یک {{domxref("Node")}} داده‌شده را به‌عنوان فرزند مستقیم، قبل از گره مرجع داده‌شده، داخل `DocumentFragment` فراخواننده جابه‌جا می‌کند.

## Syntax

```js-nolint
moveBefore(movedNode, referenceNode)
```

### Parameters

- `movedNode`
  - : یک {{domxref("Node")}} که نشان‌دهندهٔ گره‌ای است که قرار است جابه‌جا شود. توجه داشته باشید که این گره باید یک {{domxref("Element")}} یا یک گره {{domxref("CharacterData")}} باشد.
- `referenceNode`
  - : یک {{domxref("Node")}} که `movedNode` قبل از آن جابه‌جا خواهد شد، یا `null`. اگر مقدار `null` باشد، `movedNode` در انتهای گره‌های فرزندِ `DocumentFragment` فراخواننده درج می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{jsxref("TypeError")}}
  - : در هر یک از شرایط زیر پرتاب می‌شود:
    - `movedNode` مشخص‌شده قبلاً به DOM اضافه شده است و شما در حال تلاش برای جابه‌جایی آن درون یک `DocumentFragment` هستید.
    - شما در حال تلاش برای جابه‌جایی `movedNode` بین دو `DocumentFragment` متفاوت هستید.
    - `movedNode` مشخص‌شده یک گره {{domxref("Element")}} یا {{domxref("CharacterData")}} نیست.
- `NotFoundError` {{jsxref("TypeError")}}
  - : `referenceNode` مشخص‌شده فرزندِ `DocumentFragment`ای نیست که روی آن `moveBefore()` را صدا می‌زنید؛ یعنی قطعه‌ای که می‌خواهید `movedNode` را داخل آن جابه‌جا کنید.
- `TypeError` {{jsxref("TypeError")}}
  - : آرگومان دوم ارائه نشده است.

## توضیحات

متد `moveBefore()` یک گره مشخص را به مکان جدیدی در `DocumentFragment` منتقل می‌کند. این متد عملکردی مشابه متد {{domxref("Node.insertBefore()")}} ارائه می‌دهد، با این تفاوت که گره را حذف و سپس دوباره درج نمی‌کند. این بدان معناست که وضعیت گره (که اگر با `insertBefore()` و سازوکارهای مشابه جابه‌جا می‌شد، بازنشانی می‌شد) پس از جابه‌جایی حفظ می‌شود. این موارد شامل:

- وضعیت [انیمیشن](/en-US/docs/Web/CSS/Guides/Animations) و [ترنزیشن](/en-US/docs/Web/CSS/Guides/Transitions).
- وضعیت بارگذاری {{htmlelement("iframe")}}.
- وضعیت‌های تعاملی (برای مثال {{cssxref(":focus")}} و {{cssxref(":active")}}).
- وضعیت عنصر [تمام‌صفحه](/en-US/docs/Web/API/Fullscreen_API).
- وضعیت باز/بسته بودن [پاپ‌اورها](/en-US/docs/Web/API/Popover_API).
- وضعیت مودال عناصر {{htmlelement("dialog")}} (دیالوگ‌های مودال بسته نخواهند شد).

وضعیت پخش عناصر {{htmlelement("video")}} و {{htmlelement("audio")}} در فهرست بالا گنجانده نشده است، زیرا این عناصر بدون توجه به سازوکار مورد استفاده، هنگام حذف و درج مجدد، وضعیت خود را حفظ می‌کنند.

هنگامی که تغییرات DOM را با استفاده از {{domxref("MutationObserver")}} مشاهده می‌کنید، گره‌هایی که با `moveBefore()` جابه‌جا شده‌اند، به‌صورت یک [گره حذف‌شده](/en-US/docs/Web/API/MutationRecord/removedNodes) و یک [گره افزوده‌شده](/en-US/docs/Web/API/MutationRecord/addedNodes) ثبت خواهند شد.

### محدودیت‌های `moveBefore()`

هنگام استفاده از `moveBefore()` باید از چند محدودیت آگاه باشید:

- این متد فقط زمانی کار می‌کند که گره را در همان `DocumentFragment` جابه‌جا کنید.
- اگر بخواهید گره‌ای را که قبلاً به DOM اضافه شده است، داخل یک `DocumentFragment` جابه‌جا کنید، کار نخواهد کرد.

در چنین مواردی، `moveBefore()` با استثنای `HierarchyRequestError` شکست می‌خورد. اگر محدودیت‌های بالا برای مورد استفاده خاص شما الزامی هستند، به‌جای آن از {{domxref("Node.insertBefore()")}} استفاده کنید، یا برای مدیریت خطاهای ناشی از چنین مواردی از [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) استفاده کنید.

## مثال‌ها

### استفادهٔ پایه از `moveBefore()`

در این نمایش، کاربرد پایهٔ `moveBefore()` را نشان می‌دهیم.

#### HTML

بخش HTML شامل سه عنصر {{htmlelement("button")}} و یک عنصر {{htmlelement("article")}} است. ما از دکمه‌ها برای کنترل درج نمونه‌های `DocumentFragment` درون `<article>` و خالی‌کردن آن استفاده خواهیم کرد.

```html live-sample___movebefore-basic
<button id="insert1">Insert fragment</button>
<button id="insert2">Insert modified fragment</button>
<button id="clear">Clear</button>
<article id="wrapper"></article>
```

#### CSS

ما استایل ابتدایی برای ظاهر و فاصله‌گذاری عناصری فراهم می‌کنیم که بعداً به‌عنوان فرزندان `DocumentFragment`های تولیدشده با جاوااسکریپت در صفحه درج خواهند شد.

```css live-sample___movebefore-basic
#section1,
#section2,
#mover {
  display: inline-block;
  width: 200px;
  height: 30px;
  border: 5px solid rgb(0 0 0 / 0.25);
  margin-top: 10px;
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

در اسکریپت خود، تابعی به نام `createFragment()` تعریف می‌کنیم که یک `DocumentFragment` حاوی یک عنصر {{htmlelement("div")}} و دو عنصر {{htmlelement("section")}} به‌عنوان فرزندان مستقیم ایجاد می‌کند.

سپس با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} یک شنونده رویداد کلیک به هر `<button>` متصل می‌کنیم:

- دکمهٔ اول، `DocumentFragment` را بدون تغییر به عنصر `<article>` با شناسهٔ `#wrapper` اضافه می‌کند.
- دکمهٔ دوم، `DocumentFragment` را به عنصر `<article>` با شناسهٔ `#wrapper` اضافه می‌کند، اما ابتدا از `moveBefore()` استفاده می‌کند تا `<div>` را به‌جای فرزند اول، به‌عنوان فرزند دوم `DocumentFragment` قرار دهد.
- دکمهٔ سوم، عنصر `<article>` با شناسهٔ `#wrapper` را با استفاده از {{domxref("Element.innerHTML", "innerHTML")}} خالی می‌کند.

```js live-sample___movebefore-basic
const wrapper = document.getElementById("wrapper");
const insertBtn1 = document.getElementById("insert1");
const insertBtn2 = document.getElementById("insert2");
const clearBtn = document.getElementById("clear");

function createFragment() {
  const fragment = new DocumentFragment();
  const divElem = document.createElement("div");
  const section1 = document.createElement("section");
  const section2 = document.createElement("section");
  divElem.id = "mover";
  section1.id = "section1";
  section2.id = "section2";
  fragment.appendChild(divElem);
  fragment.appendChild(section1);
  fragment.appendChild(section2);

  return fragment;
}

insertBtn1.addEventListener("click", () => {
  const fragment = createFragment();
  wrapper.appendChild(fragment);
});

insertBtn2.addEventListener("click", () => {
  const fragment = createFragment();
  fragment.moveBefore(
    fragment.querySelector("#mover"),
    fragment.querySelector("#section2"),
  );

  wrapper.appendChild(fragment);
});

clearBtn.addEventListener("click", () => {
  wrapper.innerHTML = "";
});
```

#### نتیجه

نمونهٔ رندر شده به این شکل است:

{{EmbedLiveSample("movebefore-basic", "100%", "300px")}}

چند بار روی دو دکمهٔ اول کلیک کنید و توجه کنید که چگونه ساختار `DocumentFragment` توسط دکمهٔ دوم تغییر می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document.moveBefore()")}}
- {{domxref("Element.moveBefore()")}}
- {{domxref("Node.insertBefore()")}}