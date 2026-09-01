---
title: "Document: querySelector() method"
short-title: querySelector()
slug: Web/API/Document/querySelector
page-type: web-api-instance-method
browser-compat: api.Document.querySelector
---

{{ApiRef("DOM")}}

متد **`querySelector()`** از {{domxref("Document")}}، نخستین {{domxref("Element")}} درون سند را بازمی‌گرداند که با [سلکتور CSS](/en-US/docs/Web/CSS/Guides/Selectors) یا گروهی از سلکتورهای CSS مشخص‌شده مطابقت دارد. اگر هیچ موردی یافت نشود، مقدار `null` بازگردانده می‌شود.

تطبیق با استفاده از پیمایش پیش‌ترتیبِ عمق-اول روی گره‌های سند انجام می‌شود؛ به این ترتیب که از نخستین عنصر در نشانه‌گذاری سند شروع شده و گره‌های متوالی به‌ترتیب تعداد گره‌های فرزند پیمایش می‌شوند.

اگر سلکتور مشخص‌شده با یک ID مطابقت داشته باشد که به‌طور نادرست بیش از یک بار در سند استفاده شده است، نخستین عنصر دارای آن ID بازگردانده می‌شود.

شبه‌عنصرهای CSS هرگز هیچ عنصری را بازنمی‌گردانند.

## سینتکس

```js-nolint
querySelector(selectors)
```

### پارامترها

- `selectors`
  - : رشته‌ای شامل یک یا چند سلکتور برای تطبیق. این رشته باید یک رشتهٔ سلکتور CSS معتبر باشد؛ در غیر این صورت، استثنای `SyntaxError` پرتاب می‌شود.

    توجه داشته باشید که استاندارد HTML الزامی نمی‌کند که مقادیر ویژگی‌ها شناسه‌های معتبر CSS باشند. اگر مقدار ویژگی [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) یا [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یک شناسهٔ معتبر CSS نباشد، باید قبل از استفاده در سلکتور، آن را escape کنید؛ یا با فراخوانی {{domxref("CSS.escape_static", "CSS.escape()")}} روی مقدار، یا با استفاده از یکی از تکنیک‌های توصیف‌شده در [گریز از کاراکترها](/en-US/docs/Web/CSS/Reference/Values/ident#escaping_characters). برای مثال به [گریز از مقادیر ویژگی](#escaping_attribute_values) مراجعه کنید.

### مقدار بازگشتی

یک شیء {{domxref("Element")}} که نشان‌دهندهٔ نخستین عنصر در سند است و با مجموعهٔ مشخص‌شده از [سلکتورهای CSS](/en-US/docs/Web/CSS/Guides/Selectors) مطابقت دارد، یا اگر هیچ موردی یافت نشود، `null`.

اگر به فهرستی از همهٔ عناصر منطبق با سلکتورهای مشخص‌شده نیاز دارید، باید از {{domxref("Document.querySelectorAll", "querySelectorAll()")}} استفاده کنید.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر نحو (syntax) سلکتورهای مشخص‌شده نامعتبر باشد، پرتاب می‌شود.

## مثال‌ها

### یافتن نخستین عنصر منطبق با یک کلاس

در این مثال، نخستین عنصر در سند که دارای کلاس `myclass` است بازگردانده می‌شود:

```js
const el = document.querySelector(".myclass");
```

### سلکتورهای پیچیده

سلکتورها می‌توانند واقعاً قدرتمند باشند، همان‌طور که در مثال زیر نشان داده شده است. در این‌جا، نخستین عنصر {{HTMLElement("input")}} با نام «login» (`<input name="login"/>`) که در داخل یک {{HTMLElement("div")}} با کلاس «user-panel main» (`<div class="user-panel main">`) در سند قرار دارد، بازگردانده می‌شود:

```js
const el = document.querySelector("div.user-panel.main input[name='login']");
```

### نفی

چون همهٔ رشته‌های سلکتور CSS معتبر هستند، می‌توانید سلکتورها را نیز نفی کنید:

```js
const el = document.querySelector(
  "div.user-panel:not(.main) input[name='login']",
);
```

این کار یک input را انتخاب می‌کند که والد آن یک div با کلاس `user-panel` است اما کلاس `main` را ندارد.

### گریز از مقادیر ویژگی

این مثال نشان می‌دهد که اگر یک سند HTML شامل [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) باشد که یک شناسهٔ معتبر CSS نیست، باید مقدار ویژگی را قبل از استفاده در `querySelector()` escape کنیم.

#### HTML

در کد زیر، یک عنصر {{htmlelement("div")}} دارای `id` برابر با `"this?element"` است که یک شناسهٔ معتبر CSS نیست، زیرا کاراکتر `"?"` در شناسه‌های CSS مجاز نیست.

همچنین سه دکمه و یک عنصر {{htmlelement("pre")}} برای ثبت خطاها داریم.

```html
<div id="this?element"></div>

<button id="no-escape">No escape</button>
<button id="css-escape">CSS.escape()</button>
<button id="manual-escape">Manual escape</button>

<pre id="log"></pre>
```

#### CSS

```css
div {
  background-color: blue;
  margin: 1rem 0;
  height: 100px;
  width: 200px;
}
```

#### JavaScript

هر سه دکمه، هنگام کلیک، سعی می‌کنند `<div>` را انتخاب کرده و سپس رنگ پس‌زمینهٔ آن را به یک مقدار تصادفی تغییر دهند.

- دکمهٔ اول مستقیماً از مقدار `"this?element"` استفاده می‌کند.
- دکمهٔ دوم مقدار را با استفاده از {{domxref("CSS.escape_static", "CSS.escape()")}} escape می‌کند.
- دکمهٔ سوم به‌طور صریح کاراکتر `"?"` را با استفاده از بک‌اسلش escape می‌کند. توجه داشته باشید که باید خود بک‌اسلش را نیز با یک بک‌اسلش دیگر escape کنیم، مانند: `"\\?"`.

```js
const log = document.querySelector("#log");

function random(number) {
  return Math.floor(Math.random() * number);
}

function setBackgroundColor(id) {
  log.textContent = "";

  try {
    const element = document.querySelector(`#${id}`);
    const randomColor = `rgb(${random(255)} ${random(255)} ${random(255)})`;
    element.style.backgroundColor = randomColor;
  } catch (e) {
    log.textContent = e;
  }
}

document.querySelector("#no-escape").addEventListener("click", () => {
  setBackgroundColor("this?element");
});

document.querySelector("#css-escape").addEventListener("click", () => {
  setBackgroundColor(CSS.escape("this?element"));
});

document.querySelector("#manual-escape").addEventListener("click", () => {
  setBackgroundColor("this\\?element");
});
```

#### نتیجه

کلیک روی دکمهٔ اول یک خطا ایجاد می‌کند، در حالی که دکمه‌های دوم و سوم به‌درستی کار می‌کنند.

{{embedlivesample("escaping_attribute_values", "", 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [انتخاب و پیمایش در درخت DOM](/en-US/docs/Web/API/Document_Object_Model/Selection_and_traversal_on_the_DOM_tree)
- {{domxref("Element.querySelector()")}}
- {{domxref("Document.querySelectorAll()")}}
- {{domxref("Element.querySelectorAll()")}}