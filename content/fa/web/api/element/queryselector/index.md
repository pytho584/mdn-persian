```
---
title: "Element: querySelector() method"
short-title: querySelector()
slug: Web/API/Element/querySelector
page-type: web-api-instance-method
browser-compat: api.Element.querySelector
---

{{APIRef("DOM")}}

متد **`querySelector()`** در رابط {{domxref("Element")}}، اولین عنصری را برمی‌گرداند که از نوادگان (descendant) عنصری است که این متد روی آن فراخوانی شده و با گروه انتخابگرهای (selectors) مشخص‌شده مطابقت داشته باشد.

## Syntax

```js-nolint
querySelector(selectors)
```

### Parameters

- `selectors`
  - : یک رشته (string) شامل یک یا چند انتخابگر برای مطابقت. این رشته باید یک رشته انتخابگر CSS معتبر باشد؛ در غیر این صورت، یک استثنای `SyntaxError` پرتاب می‌شود.

    توجه داشته باشید که مشخصات HTML الزام نمی‌کند که مقادیر ویژگی‌ها (attribute values) شناسه‌های CSS معتبری باشند. اگر مقدار ویژگی [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) یا [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یک شناسه CSS معتبر نباشد، باید قبل از استفاده از آن در یک انتخابگر، آن را escape کنید، یا با فراخوانی {{domxref("CSS.escape_static", "CSS.escape()")}} روی مقدار، یا با استفاده از یکی از تکنیک‌های شرح‌داده‌شده در [Escape کردن کاراکترها](/en-US/docs/Web/CSS/Reference/Values/ident#escaping_characters). برای مثال، [Escape کردن مقادیر ویژگی‌ها](#escaping_attribute_values) را ببینید.

### Return value

اولین عنصر نسل (descendant) از `baseElement` که با گروه مشخص‌شده از `selectors` مطابقت دارد. هنگام تطبیق، کل سلسله‌مراتب عناصر در نظر گرفته می‌شود، از جمله عناصری که خارج از مجموعه عناصر شامل `baseElement` و نوادگان آن هستند؛ به عبارت دیگر، `selectors` ابتدا به کل سند اعمال می‌شود، نه به `baseElement`، تا یک لیست اولیه از عناصر بالقوه تولید شود. سپس عناصر حاصل بررسی می‌شوند تا ببینیم آیا از نوادگان `baseElement` هستند یا خیر. اولین تطابق از آن عناصر باقی‌مانده توسط متد `querySelector()` بازگردانده می‌شود.

اگر هیچ تطبیقی یافت نشود، مقدار بازگشتی `null` است.

### Exceptions

- `SyntaxError` {{domxref("DOMException")}}
  - : در صورتی که `selectors` مشخص‌شده نامعتبر باشند، پرتاب می‌شود.

## Examples

بیایید چند مثال را بررسی کنیم.

### یافتن یک عنصر خاص با مقادیر مشخص از یک ویژگی

در این مثال اول، اولین عنصر {{HTMLElement("style")}} که یا هیچ نوع (type) ندارد یا نوع آن "text/css" است در بدنه سند HTML بازگردانده می‌شود:

```js
const el = document.body.querySelector(
  "style[type='text/css'], style:not([type])",
);
```

### دریافت نوادگان مستقیم با استفاده از شبه‌کلاس :scope

این مثال از شبه‌کلاس {{cssxref(":scope")}} برای بازیابی فرزندان مستقیم عنصر `parentElement` استفاده می‌کند.

#### HTML

```html
<div>
  <h6>Page Title</h6>
  <div id="parent">
    <span>Love is Kind.</span>
    <span>
      <span>Love is Patient.</span>
    </span>
    <span>
      <span>Love is Selfless.</span>
    </span>
  </div>
</div>
```

#### CSS

```css
span {
  display: block;
  margin-bottom: 5px;
}
.red span {
  background-color: red;
  padding: 5px;
}
```

#### JavaScript

```js
const parentElement = document.querySelector("#parent");
let allChildren = parentElement.querySelectorAll(":scope > span");
allChildren.forEach((item) => item.classList.add("red"));
```

#### Result

{{ EmbedLiveSample('Get_direct_descendants_using_the_scope_pseudo-class', 600, 160) }}

### کل سلسله‌مراتب اهمیت دارد

این مثال نشان می‌دهد که هنگام اعمال `selectors`، سلسله‌مراتب کل سند در نظر گرفته می‌شود، به طوری که سطوح خارج از `baseElement` مشخص‌شده همچنان هنگام مکان‌یابی تطابق‌ها در نظر گرفته می‌شوند.

#### HTML

```html
<div>
  <h5>Original content</h5>
  <p>
    inside paragraph
    <span>inside span</span>
    inside paragraph
  </p>
</div>
<div>
  <h5>Output</h5>
  <div id="output"></div>
</div>
```

#### JavaScript

```js
const baseElement = document.querySelector("p");
document.getElementById("output").textContent =
  baseElement.querySelector("div span").textContent;
```

#### Result

نتیجه به این شکل است:

{{ EmbedLiveSample('The_entire_hierarchy_counts', 600, 160) }}

توجه کنید که انتخابگر `"div span"` چگونه همچنان با موفقیت با عنصر {{HTMLElement("span")}} مطابقت پیدا می‌کند، حتی اگر گره‌های فرزند `baseElement` شامل عنصر {{HTMLElement("div")}} نباشند (این عنصر همچنان بخشی از انتخابگر مشخص‌شده است).

### Escape کردن مقادیر ویژگی‌ها

این مثال نشان می‌دهد که اگر یک سند HTML شامل یک [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) باشد که یک [شناسه CSS](/en-US/docs/Web/CSS/Reference/Values/ident) معتبر نیست، باید مقدار ویژگی را قبل از استفاده از آن در `querySelector()` escape کنیم.

#### HTML

در کد زیر، یک عنصر {{htmlelement("div")}} دارای `id` برابر با `"this?element"` است که یک شناسه CSS معتبر نیست، زیرا کاراکتر `"?"` در شناسه‌های CSS مجاز نیست.

ما همچنین سه دکمه و یک عنصر {{htmlelement("pre")}} برای ثبت خطاها داریم.

```html
<div id="container">
  <div id="this?element"></div>
</div>

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

هر سه دکمه، هنگامی که کلیک می‌شوند، سعی می‌کنند `<div>` را انتخاب کرده و سپس رنگ پس‌زمینه آن را به یک مقدار تصادفی تغییر دهند.

- دکمه اول مستقیماً از مقدار `"this?element"` استفاده می‌کند.
- دکمه دوم مقدار را با استفاده از {{domxref("CSS.escape_static", "CSS.escape()")}} escape می‌کند.
- دکمه سوم به طور صریح کاراکتر `"?""` را با استفاده از یک بک‌اسلش escape می‌کند. توجه داشته باشید که ما همچنین باید خود بک‌اسلش را با استفاده از یک بک‌اسلش دیگر escape کنیم، به این صورت: `"\\?"`.

```js
const container = document.querySelector("#container");
const log = document.querySelector("#log");

function random(number) {
  return Math.floor(Math.random() * number);
}

function setBackgroundColor(id) {
  log.textContent = "";

  try {
    const element = container.querySelector(`#${id}`);
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

#### Result

با کلیک بر روی دکمه اول یک خطا دریافت می‌کنید، در حالی که دکمه‌های دوم و سوم به درستی کار می‌کنند.

{{embedlivesample("escaping_attribute_values", "", 200)}}

### مثال‌های بیشتر

برای مثال‌های بیشتر در مورد فرمت صحیح `selectors`، به {{domxref("Document.querySelector()")}} مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Selection and traversal on the DOM tree](/en-US/docs/Web/API/Document_Object_Model/Selection_and_traversal_on_the_DOM_tree)
- [Attribute selectors](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) در راهنمای CSS
- [Attribute selectors](/en-US/docs/Learn_web_development/Core/Styling_basics/Attribute_selectors) در بخش آموزش MDN
- {{domxref("Element.querySelectorAll()")}}
- {{domxref("Document.querySelector()")}} و {{domxref("Document.querySelectorAll()")}}
- {{domxref("DocumentFragment.querySelector()")}} و {{domxref("DocumentFragment.querySelectorAll()")}}
- متدهای دیگری که انتخابگر می‌گیرند: {{domxref("element.closest()")}} و {{domxref("element.matches()")}}.
```