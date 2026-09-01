---
title: "Document: getElementsByClassName() method"
short-title: getElementsByClassName()
slug: Web/API/Document/getElementsByClassName
page-type: web-api-instance-method
browser-compat: api.Document.getElementsByClassName
---

{{APIRef("DOM")}}

متد **`getElementsByClassName`** از رابط {{domxref("Document")}} یک شیء شبیه به آرایه از تمام عناصر فرزندی برمی‌گرداند که همهٔ نام کلاس(های) داده‌شده را داشته باشند.

وقتی روی شیء {{domxref("document")}} فراخوانی شود، کل سند جستجو می‌شود، از جمله گره ریشه. همچنین می‌توانید {{domxref("Element.getElementsByClassName", "getElementsByClassName()")}} را روی هر عنصری فراخوانی کنید؛ در این صورت فقط عناصری برگردانده می‌شوند که از نوادگان عنصر ریشهٔ مشخص‌شده باشند و نام کلاس(های) داده‌شده را داشته باشند.

> [!WARNING]
> این یک {{domxref("HTMLCollection")}} زنده است. تغییرات در DOM همان‌طور که رخ می‌دهند در آرایه منعکس می‌شوند. اگر عنصری که توسط این آرایه انتخاب شده دیگر شرایط انتخاب‌گر را نداشته باشد، به‌طور خودکار حذف می‌شود. هنگام پیمایش این نکته را در نظر داشته باشید.

## نحو (Syntax)

```js-nolint
getElementsByClassName(names)
```

### پارامترها

- `names`
  - : رشته‌ای که نام کلاس(های) موردنظر برای تطبیق را نشان می‌دهد؛ چند نام کلاس با فاصله (whitespace) از هم جدا می‌شوند.

### مقدار بازگشتی

یک {{domxref("HTMLCollection")}} زنده از عناصر یافت‌شده.

## مثال‌ها

دریافت همهٔ عناصری که کلاس «test» را دارند:

```js
document.getElementsByClassName("test");
```

دریافت همهٔ عناصری که هر دو کلاس «red» و «test» را دارند:

```js
document.getElementsByClassName("red test");
```

دریافت همهٔ عناصری که کلاس «test» را دارند، داخل عنصری که شناسهٔ «main» دارد:

```js
document.getElementById("main").getElementsByClassName("test");
```

دریافت اولین عنصر با کلاس «test»، یا `undefined` اگر هیچ عنصر منطبقی وجود نداشته باشد:

```js
document.getElementsByClassName("test")[0];
```

ما همچنین می‌توانیم از متدهای Array.prototype روی هر {{domxref("HTMLCollection")}} استفاده کنیم، با ارسال `HTMLCollection` به‌عنوان مقدار _this_ متد. در اینجا همهٔ عناصر div را می‌یابیم که کلاس «test» را دارند:

```js
const testElements = document.getElementsByClassName("test");
const testDivs = Array.prototype.filter.call(
  testElements,
  (testElement) => testElement.nodeName === "DIV",
);
```

### دریافت اولین عنصری که کلاس آن «test» است

این رایج‌ترین روش استفاده است.

```html
<div id="parent-id">
  <p>hello world 1</p>
  <p class="test">hello world 2</p>
  <p>hello world 3</p>
  <p>hello world 4</p>
</div>
```

```js
const parentDOM = document.getElementById("parent-id");

const test = parentDOM.getElementsByClassName("test"); // فهرستی از عناصر منطبق، *نه* خود عنصر
console.log(test); // HTMLCollection[1]

const testTarget = parentDOM.getElementsByClassName("test")[0]; // اولین عنصر، همان‌طور که می‌خواستیم
console.log(testTarget); // <p class="test">hello world 2</p>
```

### مثال چند کلاسه

`document.getElementsByClassName` بسیار شبیه به `document.querySelector` و `document.querySelectorAll` عمل می‌کند. فقط عناصری انتخاب می‌شوند که همهٔ نام کلاس‌های مشخص‌شده را داشته باشند.

#### HTML

```html
<span class="orange fruit">Orange Fruit</span>
<span class="orange juice">Orange Juice</span>
<span class="apple juice">Apple Juice</span>
<span class="foo bar">Something Random</span>
<textarea id="resultArea"></textarea>
```

```css hidden
#resultArea {
  width: 98%;
  height: 7em;
}
```

#### JavaScript

```js
// getElementsByClassName فقط عناصری را انتخاب می‌کند که هر دو کلاس داده‌شده را داشته باشند
const allOrangeJuiceByClass = document.getElementsByClassName("orange juice");
let result = "document.getElementsByClassName('orange juice')";
for (const el of allOrangeJuiceByClass) {
  result += `\n  ${el.textContent}`;
}

// querySelector فقط تطابق‌های کامل را انتخاب می‌کند
const allOrangeJuiceQuery = document.querySelectorAll(".orange.juice");
result += "\n\ndocument.querySelectorAll('.orange.juice')";
for (const el of allOrangeJuiceQuery) {
  result += `\n  ${el.textContent}`;
}

document.getElementById("resultArea").value = result;
```

#### نتیجه

{{EmbedLiveSample('Multiple_Classes_Example', '100%', 200)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}