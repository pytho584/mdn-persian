---
title: "Document: querySelectorAll() method"
short-title: querySelectorAll()
slug: Web/API/Document/querySelectorAll
page-type: web-api-instance-method
browser-compat: api.Document.querySelectorAll
---

{{APIRef("DOM")}}

متد **`querySelectorAll()`** از {{domxref("Document")}} یک {{domxref("NodeList")}} ایستا (نه زنده) برمی‌گرداند که لیستی از عناصر سند را نشان می‌دهد که با گروه انتخابگرهای مشخص شده مطابقت دارند.

## نحو

```js-nolint
querySelectorAll(selectors)
```

### پارامترها

- `selectors`
  - : یک رشته شامل یک یا چند انتخابگر برای تطبیق. این رشته باید یک رشته انتخابگر CSS معتبر باشد؛ در غیر این صورت، یک استثنای `SyntaxError` پرتاب می‌شود.

    توجه داشته باشید که مشخصات HTML الزامی نمی‌کند که مقادیر ویژگی‌ها شناسه‌های CSS معتبر باشند. اگر مقدار یک ویژگی [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) یا [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یک شناسه CSS معتبر نباشد، باید قبل از استفاده از آن در یک انتخابگر، آن را escape کنید، یا با فراخوانی {{domxref("CSS.escape_static", "CSS.escape()")}} روی مقدار، یا با استفاده از یکی از تکنیک‌های توضیح داده شده در [escape کردن کاراکترها](/en-US/docs/Web/CSS/Reference/Values/ident#escaping_characters). برای مثال به [escape کردن مقادیر ویژگی‌ها](#escaping_attribute_values) مراجعه کنید.

### مقدار بازگشتی

یک {{domxref("NodeList")}} غیر زنده که شامل یک شی {{domxref("Element")}} برای هر عنصری است که با حداقل یکی از انتخابگرهای مشخص شده مطابقت دارد، یا یک {{domxref("NodeList")}} خالی در صورت عدم تطابق. عناصر به ترتیب سند هستند – یعنی والدین قبل از فرزندان، خواهر و برادرهای قبلی قبل از بعدی.

> [!NOTE]
> اگر `selectors` مشخص شده شامل یک [شبه‌عنصر CSS](/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-elements) باشد، لیست برگشتی همیشه خالی است.

### استثناها

- `SyntaxError` {{domxref("DOMException")}}
  - : اگر نحو رشته `selectors` مشخص شده معتبر نباشد، پرتاب می‌شود.

## مثال‌ها

### به دست آوردن لیستی از تطابق‌ها

برای به دست آوردن یک {{domxref("NodeList")}} از تمام عناصر {{HTMLElement("p")}} در سند:

```js
const matches = document.querySelectorAll("p");
```

این مثال لیستی از تمام عناصر {{HTMLElement("div")}} درون سند را با کلاس `note` یا `alert` برمی‌گرداند:

```js
const matches = document.querySelectorAll("div.note, div.alert");
```

در اینجا، ما لیستی از عناصر `<p>` را دریافت می‌کنیم که عنصر والد بلافصل آنها یک {{HTMLElement("div")}} با کلاس `highlighted` است و درون یک ظرف با شناسه `test` قرار دارند.

```js
const container = document.querySelector("#test");
const matches = container.querySelectorAll("div.highlighted > p");
```

این مثال از یک [انتخگر ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) برای برگرداندن لیستی از عناصر {{HTMLElement("iframe")}} در سند استفاده می‌کند که دارای ویژگی به نام `data-src` هستند:

```js
const matches = document.querySelectorAll("iframe[data-src]");
```

در اینجا، یک انتخابگر ویژگی برای برگرداندن لیستی از موارد لیست موجود در یک لیست با شناسه `user-list` استفاده می‌شود که دارای ویژگی `data-active` با مقدار `1` هستند:

```js
const container = document.querySelector("#user-list");
const matches = container.querySelectorAll("li[data-active='1']");
```

### دسترسی به تطابق‌ها

هنگامی که {{domxref("NodeList")}} از عناصر منطبق برگردانده شد، می‌توانید آن را مانند هر آرایه‌ای بررسی کنید. اگر آرایه خالی باشد (یعنی ویژگی `length` آن 0 باشد)، هیچ تطابقی یافت نشده است.

در غیر این صورت، می‌توانید از نماد استاندارد آرایه برای دسترسی به محتویات لیست استفاده کنید. می‌توانید از هر عبارت حلقه‌ای رایج مانند:

```js
const highlightedItems = userList.querySelectorAll(".highlighted");

highlightedItems.forEach((userItem) => {
  deleteUser(userItem);
});
```

### escape کردن مقادیر ویژگی‌ها

این مثال نشان می‌دهد که اگر یک سند HTML شامل یک [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) باشد که یک [شناسه CSS](/en-US/docs/Web/CSS/Reference/Values/ident) معتبر نیست، باید قبل از استفاده از آن در `querySelectorAll()`، مقدار ویژگی را escape کنیم.

#### HTML

در کد زیر، یک عنصر {{htmlelement("div")}} دارای `id` با مقدار `"this?element"` است که یک شناسه CSS معتبر نیست، زیرا کاراکتر `"?"` در شناسه‌های CSS مجاز نیست.

ما همچنین سه دکمه و یک عنصر {{htmlelement("pre")}} برای ثبت خطاها داریم.

```html
<div id="this?element"></div>

<button id="no-escape">بدون escape</button>
<button id="css-escape">CSS.escape()</button>
<button id="manual-escape">escape دستی</button>

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

هر سه دکمه، هنگام کلیک، سعی می‌کنند `<div>` را انتخاب کرده و سپس رنگ پس‌زمینه آن را به یک مقدار تصادفی تنظیم کنند.

- دکمه اول مستقیماً از مقدار `"this?element"` استفاده می‌کند.
- دکمه دوم مقدار را با استفاده از {{domxref("CSS.escape_static", "CSS.escape()")}} escape می‌کند.
- دکمه سوم به طور صریح کاراکتر `"?"` را با استفاده از یک بک‌اسلش escape می‌کند. توجه داشته باشید که باید خود بک‌اسلش را نیز با استفاده از یک بک‌اسلش دیگر escape کنیم، مانند: `"\\?"`.

```js
const log = document.querySelector("#log");

function random(number) {
  return Math.floor(Math.random() * number);
}

function setBackgroundColor(id) {
  log.textContent = "";

  try {
    const elements = document.querySelectorAll(`#${id}`);
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

کلیک روی دکمه اول یک خطا می‌دهد، در حالی که دکمه دوم و سوم به درستی کار می‌کنند.

{{embedlivesample("escaping_attribute_values", "", 200)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [انتخاب و پیمایش درخت DOM](/en-US/docs/Web/API/Document_Object_Model/Selection_and_traversal_on_the_DOM_tree)
- [انتخابگرهای ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) در راهنمای CSS
- [انتخابگرهای ویژگی](/en-US/docs/Learn_web_development/Core/Styling_basics/Attribute_selectors) در منطقه یادگیری MDN
- {{domxref("Element.querySelector()")}} و {{domxref("Element.querySelectorAll()")}}
- {{domxref("Document.querySelector()")}}
- {{domxref("DocumentFragment.querySelector()")}} و
  {{domxref("DocumentFragment.querySelectorAll()")}}