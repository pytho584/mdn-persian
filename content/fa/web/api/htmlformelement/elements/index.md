---
title: "HTMLFormElement: elements property"
short-title: elements
slug: Web/API/HTMLFormElement/elements
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.elements
---

{{APIRef("HTML DOM")}}

ویژگی **`elements`** در رابط {{domxref("HTMLFormElement")}} یک {{domxref("HTMLFormControlsCollection")}} برمی‌گرداند که همهٔ کنترل‌های فرم فهرست‌شدهٔ مرتبط با عنصر {{HTMLElement("form")}} را فهرست می‌کند.

می‌توانید با استفاده از یک اندیس یا ویژگی‌های `name` یا `id` عنصر، به یک کنترل فرم خاص در مجموعهٔ بازگشتی دسترسی پیدا کنید.

پیش از HTML 5، شیء بازگشتی یک {{domxref("HTMLCollection")}} بود که `HTMLFormControlsCollection` بر پایهٔ آن ساخته شده است.

به‌طور مستقل، می‌توانید فقط تعداد کنترل‌های فرم مرتبط را با استفاده از ویژگی {{domxref("HTMLFormElement.length", "length")}} به دست آورید. همچنین می‌توانید فهرستی از همهٔ فرم‌های موجود در یک سند را با استفاده از ویژگی {{domxref("Document.forms", "forms")}} سند دریافت کنید.

## مقدار

یک {{domxref("HTMLFormControlsCollection")}} شامل همهٔ کنترل‌های غیرتصویری مرتبط با فرم.
این یک مجموعهٔ زنده است؛ اگر کنترل‌های فرم به فرم متصل یا از آن جدا شوند، این مجموعه برای انعکاس تغییر به‌روزرسانی می‌شود.

کنترل‌های فرم در مجموعهٔ بازگشتی به همان ترتیبی هستند که در سند ظاهر می‌شوند، با دنبال کردن پیمایش پیشوندی (preorder) و عمق‌اول از درخت.
به این ترتیب **ترتیب درختی** (tree order) گفته می‌شود.

فقط کنترل‌های فرم زیر بازگردانده می‌شوند:

- {{HTMLElement("button")}}
- {{HTMLElement("fieldset")}}
- {{HTMLElement("input")}} (به استثنای آنهایی که ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) آن‌ها `"image"` است، که به دلایل تاریخی حذف می‌شوند)
- {{HTMLElement("object")}}
- {{HTMLElement("output")}}
- {{HTMLElement("select")}}
- {{HTMLElement("textarea")}}
- [عناصر سفارشی مرتبط با فرم](https://html.spec.whatwg.org/multipage/custom-elements.html#form-associated-custom-element)

## مثال‌ها

### مثال نحوهٔ نوشتار سریع

در این مثال، می‌بینیم که چگونه فهرست کنترل‌های فرم را به دست آوریم و همچنین چگونه به اعضای آن با اندیس و با نام یا شناسه دسترسی داشته باشیم.

```html
<form id="my-form">
  <label>
    Username:
    <input type="text" name="username" />
  </label>
  <label>
    Full name:
    <input type="text" name="full-name" />
  </label>
  <label>
    Password:
    <input type="password" name="password" />
  </label>
</form>
```

```js
const inputs = document.getElementById("my-form").elements;
const inputByIndex = inputs[0];
const inputByName = inputs["username"];
```

### کنترل‌های فرم مرتبط

این مثال نشان می‌دهد که چگونه {{domxref("HTMLFormControlsCollection")}} شامل کنترل‌های فرم مرتبط با فرم است، نه کنترل‌هایی که به‌طور فیزیکی درون `<form>` قرار گرفته‌اند.

فرم اول کامل است و چهار کنترل فرم دارد: یک عنصر {{htmlelement("fieldset")}} و سه عنصر {{htmlelement("input")}}. عناصر {{htmlelement("legend")}} و {{htmlelement("label")}} کنترل‌های فرم فهرست‌شده نیستند. فرم دوم پراکنده است و فقط یک کنترل فرم تو در تو دارد: یک عنصر {{htmlelement("object")}}. همهٔ کنترل‌های فرم در فرم کامل، از طریق ویژگی `form` خود با فرم پراکنده مرتبط شده‌اند.

```html
<form id="fullForm">
  This form looks full, but it has no associated form controls
  <fieldset form="sparseForm">
    <legend>This is a legend</legend>
    <label>A form control: <input form="sparseForm" /></label>
    <label>Another form control: <input form="sparseForm" /></label>
    <label>Yet another form control: <input form="sparseForm" /></label>
  </fieldset>
</form>

<form id="sparseForm">
  <object data="lone-form-control.jpg">Lone form control</object>
</form>
```

ما از ویژگی `elements` برای دریافت `HTMLFormControlsCollection` مربوط به هر فرم استفاده می‌کنیم.

```js
const sparse = document.getElementById("sparseForm").elements;
const full = document.getElementById("fullForm").elements;
```

مجموعه شامل کنترل‌های فرم مرتبط با عنصر فرم است، به این معنی که همهٔ عناصر {{HTMLElement("button")}}، {{HTMLElement("fieldset")}}، {{HTMLElement("input")}}، {{HTMLElement("object")}}، {{HTMLElement("output")}}، {{HTMLElement("select")}}، {{HTMLElement("textarea")}} و عناصر سفارشی مرتبط با فرم که با فرم مرتبط هستند را شامل می‌شود، حتی اگر آن عناصر در فرم دیگری تودرتو شده باشند یا در هیچ فرمی تودرتو نباشند.

```js
console.log(`sparse form: ${sparse.length}`); // sparse form: 5
console.log(`full form: ${full.length}`); // full form: 0
```

کنترل‌های فرم مجموعه به همان ترتیبی هستند که در سند ظاهر می‌شوند.

```js
console.log(`first member: ${sparse[0].tagName}`); // first member: FIELDSET
console.log(`last member: ${sparse[sparse.length - 1].tagName}`); // last member: OBJECT
```

### دسترسی به کنترل‌های فرم

این مثال فهرست عناصر فرم را دریافت می‌کند، سپس روی فهرست پیمایش می‌کند و به دنبال عناصر {{HTMLElement("input")}} با [`type`](/en-US/docs/Web/HTML/Reference/Elements/input/text) برابر با `"text"` می‌گردد تا بتوان نوعی پردازش روی آن‌ها انجام داد.

```js
const inputs = document.getElementById("my-form").elements;

// Iterate over the form controls
for (const input of inputs) {
  if (input.nodeName === "INPUT" && input.type === "text") {
    // Update text input
    input.value = input.value.toLocaleUpperCase();
  }
}
```

### غیرفعال کردن کنترل‌های فرم

```js
const inputs = document.getElementById("my-form").elements;

// Iterate over the form controls
for (const input of inputs) {
  // Disable all form controls
  input.setAttribute("disabled", "");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}