---
title: "CSSStyleDeclaration: setProperty() method"
short-title: setProperty()
slug: Web/API/CSSStyleDeclaration/setProperty
page-type: web-api-instance-method
browser-compat: api.CSSStyleDeclaration.setProperty
---

{{ APIRef("CSSOM") }}

متود **`CSSStyleDeclaration.setProperty()`** مقدار جدیدی را برای یک ویژگی در شیء اعلان سبک CSS تنظیم می‌کند.

## Syntax

```js-nolint
setProperty(propertyName, value)
setProperty(propertyName, value, priority)
```

### پارامترها

- `propertyName`
  - : رشته‌ای که نام ویژگی CSS (با خط تیره) مورد نظر برای تغییر را مشخص می‌کند.
- `value` {{optional_inline}}
  - : رشته‌ای شامل مقدار جدید ویژگی. اگر مشخص نشود، به‌عنوان رشته خالی در نظر گرفته می‌شود. مقدار [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) نیز همانند رشته خالی (`""`) رفتار می‌کند.
    > [!NOTE]
    > `value` نباید شامل `"!important"` باشد؛ این کار باید با استفاده از پارامتر `priority` انجام شود.
- `priority` {{optional_inline}}
  - : رشته‌ای که به‌کمک آن می‌توان اولویت CSS را به حالت important تنظیم کرد. تنها مقادیر زیر پذیرفته می‌شوند:
    - `"important"` (بدون حساسیت به بزرگی/کوچکی حروف) برای تنظیم ویژگی به‌صورت `!important`؛
    - `""`، `undefined` یا `null` برای حذف پرچم `!important` در صورت وجود.

    هر مقدار دیگری باعث می‌شود متود زودتر بازگردد و هیچ تغییری اعمال نشود (مگر اینکه `value` خالی باشد، که در این صورت ویژگی بدون توجه به مقدار `priority` حذف می‌شود). برای مثال، `false` مقدار معتبری برای `priority` نیست.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `NoModificationAllowedError` {{domxref('DOMException')}}
  - : اگر ویژگی یا بلوک اعلان فقط‌خواندنی باشد، پرتاب می‌شود.

## کاربرد جایگزین

اگر بتوان `priority` را حذف کرد، جاوااسکریپت نحو ساده‌تری برای تنظیم یک ویژگی CSS روی شیء اعلان سبک دارد:

```js
style.cssPropertyName = "value";
```

## مثال‌ها

### تنظیم ویژگی‌های جعبه

در این مثال سه دکمه داریم که با فشردن آن‌ها می‌توانیم به‌صورت پویا حاشیه، رنگ پس‌زمینه و رنگ متن پاراگراف داخل جعبه را به مقادیر تصادفی تغییر دهیم (مثال زنده را در انتهای این بخش ببینید).

زیرساخت [نمونه زنده](/en-US/docs/MDN/Writing_guidelines/Page_structures/Live_samples) MDN تمام بلوک‌های CSS موجود در مثال را در یک سبک درون‌خطی واحد با شناسه `css-output` ترکیب می‌کند، بنابراین ابتدا با {{domxref("document.getElementById()")}} آن برگه سبک را پیدا می‌کنیم.

سپس روی قوانین مختلف موجود درون استایل‌شیت که در آرایه [`stylesheet.cssRules`](/en-US/docs/Web/API/CSSStyleSheet/cssRules) قرار دارند حلقه می‌زنیم. برای هر قانون بررسی می‌کنیم که آیا [`CSSStyleRule.selectorText`](/en-US/docs/Web/API/CSSStyleRule/selectorText) آن برابر با انتخابگر `.box p` است یا نه؛ زیرا این همان قانونی است که می‌خواهیم.

اگر برابر بود، ارجاعی از این شیء `CSSStyleRule` را در یک متغیر ذخیره می‌کنیم. سپس از سه تابع برای تولید مقادیر تصادفی برای ویژگی‌های موردنظر استفاده کرده و قانون را با این مقادیر به‌روزرسانی می‌کنیم. در هر مورد، این کار با متود `setProperty()` انجام می‌شود، مثلاً `boxParaRule.style.setProperty('border', newBorder);`.

### HTML

```html
<div class="controls">
  <button class="border">Border</button>
  <button class="bgcolor">Background</button>
  <button class="color">Text</button>
</div>
<div class="box">
  <p>Box</p>
</div>
```

### CSS

```css
html {
  background: orange;
  font-family: sans-serif;
  height: 100%;
}

body {
  height: inherit;
  width: 80%;
  min-width: 500px;
  max-width: 1000px;
  margin: 0 auto;
}

.controls {
  display: flex;
  justify-content: space-around;
  align-items: center;
}

div button {
  flex: 1;
  margin: 20px;
  height: 30px;
  line-height: 30px;
}

.box {
  display: flex;
  justify-content: center;
  align-items: center;
  height: calc(100% - 70px);
}

.box p {
  width: 50%;
  text-align: center;
  font-weight: bold;
  font-size: 40px;
  height: 150px;
  line-height: 150px;
  background: red;
  border: 5px solid purple;
  color: white;
  transition: all 1s;
}
```

### JavaScript

```js
const borderBtn = document.querySelector(".border");
const bgColorBtn = document.querySelector(".bgcolor");
const colorBtn = document.querySelector(".color");
const box = document.querySelector(".box");

function random(min, max) {
  const num = Math.floor(Math.random() * (max - min)) + min;
  return num;
}

function randomColor() {
  return `rgb(${random(0, 255)} ${random(0, 255)} ${random(0, 255)})`;
}

// Find the inline stylesheet generated for MDN live samples
const stylesheet = document.getElementById("css-output").sheet;

const boxParaRule = [...stylesheet.cssRules].find(
  (r) => r.selectorText === ".box p",
);

function setRandomBorder() {
  const newBorder = `${random(1, 50)}px solid ${randomColor()}`;
  boxParaRule.style.setProperty("border", newBorder);
}

function setRandomBgColor() {
  const newBgColor = randomColor();
  boxParaRule.style.setProperty("background-color", newBgColor);
}

function setRandomColor() {
  const newColor = randomColor();
  boxParaRule.style.setProperty("color", newColor);
}

borderBtn.addEventListener("click", setRandomBorder);
bgColorBtn.addEventListener("click", setRandomBgColor);
colorBtn.addEventListener("click", setRandomColor);
```

### نتیجه

{{EmbedLiveSample('Examples', '100%', 400)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}