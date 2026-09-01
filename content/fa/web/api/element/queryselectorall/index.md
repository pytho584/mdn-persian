---
title: "Element: querySelectorAll() method"
---

---
title: "Element: querySelectorAll() method"
short-title: querySelectorAll()
slug: Web/API/Element/querySelectorAll
page-type: web-api-instance-method
browser-compat: api.Element.querySelectorAll
---

{{APIRef("DOM")}}

متد **`querySelectorAll()`** متعلق به {{domxref("Element")}} یک {{domxref("NodeList")}} ایستا (غیرزنده) برمی‌گرداند که فهرستی از عناصر منطبق با گروه مشخصی از انتخابگرها را نشان می‌دهد و همگی از نوادگان عنصری هستند که متد روی آن فراخوانی شده است.

## نحو

```js-nolint
querySelectorAll(selectors)
```

### پارامترها

- `selectors`
  - : رشته‌ای شامل یک یا چند انتخابگر برای تطبیق. این رشته باید یک رشته انتخابگر CSS معتبر باشد؛ اگر معتبر نباشد، یک استثنای `SyntaxError` پرتاب می‌شود.

    توجه داشته باشید که مشخصات HTML الزامی نمی‌کند که مقادیر ویژگی‌ها شناسه‌های معتبر CSS باشند. اگر مقدار ویژگی [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) یا [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یک شناسه معتبر CSS نباشد، باید قبل از استفاده در یک انتخابگر آن را escape کنید؛ یا با فراخوانی {{domxref("CSS.escape_static", "CSS.escape()")}} روی مقدار، یا با استفاده از یکی از روش‌های شرح‌داده‌شده در [escape کردن کاراکترها](/en-US/docs/Web/CSS/Reference/Values/ident#escaping_characters). برای مثال به [escape کردن مقادیر ویژگی](#escaping_attribute_values) مراجعه کنید.

    انتخابگرها به کل سند اعمال می‌شوند، نه فقط به عنصر خاصی که `querySelectorAll()` روی آن فراخوانی شده است. برای محدود کردن انتخابگر به عنصری که `querySelectorAll()` روی آن فراخوانی شده، شبه‌کلاس {{cssxref(":scope")}} را در ابتدای انتخابگر قرار دهید. به مثال [محدوده انتخابگر](#selector_scope) مراجعه کنید.

### مقدار بازگشتی

یک {{domxref("NodeList")}} غیرزنده حاوی یک شیء {{domxref("Element")}} برای هر گره نسل که با حداقل یکی از انتخابگرهای مشخص‌شده مطابقت دارد. عناصر به ترتیب سند مرتب می‌شوند؛ یعنی والدها پیش از فرزندان، و خواهرها و برادرهای قبلی پیش از بعدی‌ها.

> [!NOTE]
> اگر `selectors` مشخص‌شده شامل یک [شبه‌عنصر CSS](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) باشد، فهرست بازگشتی همیشه خالی است.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که نحو رشته `selectors` مشخص‌شده معتبر نباشد.

## مثال‌ها

### دریافت همه عناصر با یک مقدار داده سفارشی

این مثال از [انتخابگر ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) استفاده می‌کند تا چندین عنصر دارای ویژگی داده‌ای `data-name` که حاوی "funnel-chart-percent" است را انتخاب کند.

```html
<section class="box" id="sect1">
  <div data-name="funnel-chart-percent1">10.900%</div>
  <div data-name="funnel-chart-percent2">3700.00%</div>
  <div data-name="funnel-chart-percent3">0.00%</div>
</section>
```

```js
const refs = [
  ...document.querySelectorAll(`[data-name*="funnel-chart-percent"]`),
];
```

### به دست آوردن فهرست موارد منطبق

برای به دست آوردن یک {{domxref("NodeList")}} از همه عناصر {{HTMLElement("p")}} موجود در عنصر `myBox`:

```js
const matches = myBox.querySelectorAll("p");
```

این مثال فهرستی از همه عناصر {{HTMLElement("div")}} درون `myBox` با کلاس `note` یا `alert` برمی‌گرداند:

```js
const matches = myBox.querySelectorAll("div.note, div.alert");
```

در اینجا، فهرستی از عناصر `<p>` سند را به دست می‌آوریم که والد بلافصل آن‌ها یک {{HTMLElement("div")}} با کلاس `"highlighted"` است و در داخل ظرفی با شناسه `"test"` قرار دارند.

```js
const container = document.querySelector("#test");
const matches = container.querySelectorAll("div.highlighted > p");
```

این مثال از [انتخابگر ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) استفاده می‌کند تا فهرستی از عناصر {{HTMLElement("iframe")}} سند را برگرداند که دارای ویژگی‌ای به نام `"data-src"` هستند:

```js
const matches = document.querySelectorAll("iframe[data-src]");
```

در اینجا، یک انتخابگر ویژگی برای برگرداندن فهرستی از آیتم‌های فهرست درون فهرستی با شناسه `"user-list"` استفاده می‌شود که ویژگی `"data-active"` با مقدار `"1"` دارند:

```js
const container = document.querySelector("#user-list");
const matches = container.querySelectorAll("li[data-active='1']");
```

### دسترسی به موارد منطبق

هنگامی که {{domxref("NodeList")}} عناصر منطبق برگردانده شد، می‌توانید آن را مانند هر آرایه‌ای بررسی کنید. اگر آرایه خالی باشد (یعنی ویژگی `length` آن `0` باشد)، هیچ مورد منطبقی یافت نشده است.

در غیر این صورت، می‌توانید از نماد استاندارد آرایه برای دسترسی به محتویات فهرست استفاده کنید. می‌توانید از هر دستور حلقه رایجی استفاده کنید، مانند:

```js
const highlightedItems = userList.querySelectorAll(".highlighted");

highlightedItems.forEach((userItem) => {
  deleteUser(userItem);
});
```

> [!NOTE]
> `NodeList` یک آرایه واقعی نیست؛ یعنی متدهای آرایه مانند `slice`، `some`، `map` و غیره را ندارد. برای تبدیل آن به آرایه، از `Array.from(nodeList)` استفاده کنید.

### محدوده انتخابگر

متد `querySelectorAll()` انتخابگرهای خود را به کل سند اعمال می‌کند؛ آن‌ها به عنصری که متد روی آن فراخوانی شده محدود نمی‌شوند. برای محدود کردن انتخابگرها، شبه‌کلاس {{cssxref(":scope")}} را در ابتدای رشته انتخابگر قرار دهید.

#### HTML

در این مثال، HTML شامل موارد زیر است:

- دو دکمه: `#select` و `#select-scope`
- سه عنصر تودرتوی `<div>`: `#outer`، `#subject` و `#inner`
- یک عنصر `<pre>` که مثال برای خروجی از آن استفاده می‌کند.

```html
<button id="select">Select</button>
<button id="select-scope">Select with :scope</button>

<div id="outer">
  #outer
  <div id="subject">
    #subject
    <div id="inner">#inner</div>
  </div>
</div>

<pre id="output"></pre>
```

```css hidden
div {
  margin: 0.5rem;
  padding: 0.5rem;
  border: 3px lightseagreen solid;
  border-radius: 5px;
  font-family: monospace;
}

pre,
button {
  margin: 0.5rem;
  padding: 0.5rem;
}
```

#### جاوااسکریپت

در بخش جاوااسکریپت، ابتدا عنصر `#subject` را انتخاب می‌کنیم.

وقتی دکمه `#select` فشرده می‌شود، `querySelectorAll()` را روی `#subject` با رشته انتخابگر `"#outer #inner"` فرا می‌خوانیم.

وقتی دکمه `#select-scope` فشرده می‌شود، دوباره `querySelectorAll()` را روی `#subject` فرا می‌خوانیم، اما این بار رشته انتخابگر را `":scope #outer #inner"` ارسال می‌کنیم.

```js
const subject = document.querySelector("#subject");

const select = document.querySelector("#select");
select.addEventListener("click", () => {
  const selected = subject.querySelectorAll("#outer #inner");
  output.textContent = `Selection count: ${selected.length}`;
});

const selectScope = document.querySelector("#select-scope");
selectScope.addEventListener("click", () => {
  const selected = subject.querySelectorAll(":scope #outer #inner");
  output.textContent = `Selection count: ${selected.length}`;
});
```

#### نتیجه

{{EmbedLiveSample("Selector scope", "", 300)}}

وقتی «Select» را فشار دهیم، انتخابگر همه عناصری را انتخاب می‌کند که شناسه `inner` دارند و همچنین جدی با شناسه `outer` دارند. توجه کنید که حتی اگر `#outer` خارج از عنصر `#subject` باشد، همچنان در انتخاب استفاده می‌شود، بنابراین عنصر `#inner` پیدا می‌شود.

وقتی «Select with :scope» را فشار دهیم، شبه‌کلاس `:scope` محدوده انتخابگر را به `#subject` محدود می‌کند، بنابراین `#outer` در تطبیق انتخابگر استفاده نمی‌شود و عنصر `#inner` پیدا نمی‌شود.

### escape کردن مقادیر ویژگی

این مثال نشان می‌دهد که اگر یک سند HTML حاوی یک [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) باشد که [شناسه CSS](/en-US/docs/Web/CSS/Reference/Values/ident) معتبری نیست، باید مقدار ویژگی را قبل از استفاده در `querySelectorAll()` escape کنیم.

#### HTML

در کد زیر، یک عنصر {{htmlelement("div")}} دارای `id` برابر با `"this?element"` است که شناسه CSS معتبری نیست، زیرا کاراکتر `"?"` در شناسه‌های CSS مجاز نیست.

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

#### جاوااسکریپت

هر سه دکمه هنگام کلیک سعی می‌کنند `<div>` را انتخاب کنند و سپس رنگ پس‌زمینه آن را به یک مقدار تصادفی تنظیم کنند.

- دکمه اول مستقیماً از مقدار `"this?element"` استفاده می‌کند.
- دکمه دوم مقدار را با استفاده از {{domxref("CSS.escape_static", "CSS.escape()")}} escape می‌کند.
- دکمه سوم به صراحت کاراکتر `"?"` را با بک‌اسلش escape می‌کند. توجه کنید که باید خود بک‌اسلش را نیز با یک بک‌اسلش دیگر escape کنیم، مانند: `"\\?"`.

```js
const container = document.querySelector("#container");
const log = document.querySelector("#log");

function random(number) {
  return Math.floor(Math.random() * number);
}

function setBackgroundColor(id) {
  log.textContent = "";

  try {
    const elements = container.querySelectorAll(`#${id}`);
    const randomColor = `rgb(${random(255)} ${random(255)} ${random(255)})`;
    elements[0].style.backgroundColor = randomColor;
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

کلیک روی دکمه اول یک خطا ایجاد می‌کند، در حالی که دکمه‌های دوم و سوم به‌درستی کار می‌کنند.

{{embedlivesample("escaping_attribute_values", "", 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [انتخاب و پیمایش در درخت DOM](/en-US/docs/Web/API/Document_Object_Model/Selection_and_traversal_on_the_DOM_tree)
- [انتخابگرهای ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) در راهنمای CSS
- [انتخابگرهای ویژگی](/en-US/docs/Learn_web_development/Core/Styling_basics/Attribute_selectors) در بخش آموزشی MDN
- {{domxref("Element.querySelector()")}}
- {{domxref("Document.querySelector()")}} و {{domxref("Document.querySelectorAll()")}}
- {{domxref("DocumentFragment.querySelector()")}} و {{domxref("DocumentFragment.querySelectorAll()")}}