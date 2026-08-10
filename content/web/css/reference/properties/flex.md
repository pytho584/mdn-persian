---
title: "flex CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/flex"
translated_by: "n8n + AI"
---

The **`flex`** shorthand property مشخص می‌کند که یک آیتم فلکس (flex item) چگونه در کانتینر فلکس خودش برای پر کردن فضای موجود، رشد یا کوچک شود.

```css interactive-example-choice
flex: 1;
```

```css interactive-example-choice
flex: 2;
```

```css interactive-example-choice
flex: 1 30px;
```

```css interactive-example-choice
flex: 1 1 100px;
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="transition-all" id="example-element">Change me</div>
  <div>flex: 1</div>
  <div>flex: 1</div>
</section>
```

```css interactive-example
.default-example {
  border: 1px solid #c5c5c5;
  width: auto;
  max-height: 300px;
  display: flex;
}

.default-example > div {
  background-color: rgb(0 0 255 / 0.2);
  border: 3px solid blue;
  margin: 10px;
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 0;
}

#example-element {
  background-color: rgb(255 0 200 / 0.2);
  border: 3px solid rebeccapurple;
}
```

## خواص تشکیل‌دهنده

این خصوصیت یک شورت‌هند برای خصوصیات CSS زیر است:

- `flex-grow`
- `flex-shrink`
- `flex-basis`

## سینتکس

```css
/* Keyword value */
flex: none; /* 0 0 auto */

/* One value, unitless number: flex-grow
flex-basis is then equal to 0%. */
flex: 2; /* 2 1 0% */

/* One value, width/height: flex-basis */
flex: auto; /* 1 1 auto */
flex: 10em; /* 1 1 10em */
flex: 30%;
flex: min-content;

/* Two values: flex-grow | flex-basis */
flex: 1 30px; /* 1 1 30px */

/* Two values: flex-grow | flex-shrink */
flex: 2 2; /* 2 2 0% */

/* Three values: flex-grow | flex-shrink | flex-basis */
flex: 2 2 10%;

/* Global values */
flex: inherit;
flex: initial; /* 0 1 auto */
flex: revert;
flex: revert-layer;
flex: unset;
```

مقدار `flex` می‌تواند با یک، دو، یا سه مقدار مشخص شود.

- یک‌مقداره (One-value syntax): مقدار باید یکی از موارد زیر باشد:
  - یک مقدار معتبر برای `flex-grow`: در این صورت شورت‌هند به `flex: <flex-grow> 1 0%` تبدیل می‌شود.
  - یک مقدار معتبر برای `flex-basis`: در این صورت شورت‌هند به `flex: 1 1 <flex-basis>` تبدیل می‌شود.
  - کلیدواژه `none` یا یکی از کلیدواژه‌های سراسری (global keywords).

- دو‌مقداره (Two-value syntax):
  - مقدار اول باید یک مقدار معتبر برای `flex-grow` باشد.
  - مقدار دوم باید یکی از موارد زیر باشد:
    - یک مقدار معتبر برای `flex-shrink`: در این صورت شورت‌هند به `flex: <flex-grow> <flex-shrink> 0%` تبدیل می‌شود.
    - یک مقدار معتبر برای `flex-basis`: در این صورت شورت‌هند به `flex: <flex-grow> 1 <flex-basis>` تبدیل می‌شود.

- سه‌مقداره (Three-value syntax): مقادیر باید به ترتیب زیر باشند:
  1. یک مقدار معتبر برای `flex-grow`.
  2. یک مقدار معتبر برای `flex-shrink`.
  3. یک مقدار معتبر برای `flex-basis`.

### مقادیر

- `<'flex-grow'>`
  - : مقدار `flex-grow` آیتم فلکس را تعیین می‌کند. مقادیر منفی نامعتبر در نظر گرفته می‌شوند. هنگام حذف، مقدار پیش‌فرض برابر `1` است. (مقدار اولیه `0` است)
- `<'flex-shrink'>`
  - : مقدار `flex-shrink` آیتم فلکس را تعیین می‌کند. مقادیر منفی نامعتبر در نظر گرفته می‌شوند. هنگام حذف، مقدار پیش‌فرض برابر `1` است. (مقدار اولیه `1` است)
- `<'flex-basis'>`
  - : مقدار `flex-basis` آیتم فلکس را تعیین می‌کند. هنگام حذف، مقدار پیش‌فرض برابر `0%` است. مقدار اولیه `auto` است.
- `none`
  - : آیتم بر اساس خصوصیات `width` و `height` خودش اندازه می‌گیرد. این حالت کاملاً غیرقابل انعطاف است: نه می‌کاهد و نه رشد می‌کند. این معادل تنظیم `flex: 0 0 auto` است.

اثرهای رایج فلکس‌باکس را معمولاً می‌توان با مقادیر `flex` زیر به‌دست آورد:

- `initial`: آیتم فلکس رشد نمی‌کند اما می‌تواند کوچک شود. این مقدار به `flex: 0 1 auto` گسترش می‌یابد. آیتم بر اساس `width` یا `height` خودش (بسته به `flex-direction`) اندازه می‌گیرد. اگر فضای موجود منفی باشد، آیتم تا حداقل اندازه‌اش کوچک می‌شود تا درون کانتینر جا بگیرد، اما برای جذب فضای مثبت موجود رشد نمی‌کند.
- `auto`: آیتم فلکس می‌تواند رشد و کوچک شود. این مقدار به `flex: 1 1 auto` گسترش می‌یابد. آیتم بر اساس `width` یا `height` خودش اندازه می‌گیرد، اما برای جذب فضای مثبت موجود در کانتینر رشد می‌کند و در صورت فضای منفی تا حداقل اندازه‌اش کوچک می‌شود. آیتم فلکس کاملاً انعطاف‌پذیر است.
- `none`: آیتم فلکس نه رشد می‌کند و نه کوچک می‌شود. این مقدار به `flex: 0 0 auto` گسترش می‌یابد. آیتم بر اساس `width` یا `height` خودش اندازه می‌گیرد و کاملاً غیرقابل انعطاف است.
- `flex: <number [1,∞]>`: اندازهٔ اصلی آیتم فلکس متناسب با عدد تعیین‌شده خواهد بود. این مقدار به `flex: <number> 1 0%` گسترش می‌یابد. این باعث می‌شود `flex-basis` برابر `0%` شود و آیتم فلکس انعطاف‌پذیر باشد. آیتم حداقل به اندازهٔ حداقل اندازه‌اش خواهد بود و فضای مثبت موجود کانتینر به‌صورت تناسبی بر اساس فاکتورهای رشد این آیتم و آیتم‌های هم‌رده آن توزیع می‌شود. اگر همهٔ آیتم‌های فلکس از این الگو استفاده کنند، همهٔ آن‌ها به تناسب مقادیر عددی‌شان اندازه‌گیری می‌شوند.

## توضیحات

برای اغلب موارد، نویسندگان باید `flex` را به یکی از مقادیر زیر تنظیم کنند: `auto`، `initial`، `none`، یا یک عدد واحد بدون واحد مثبت. برای دیدن اثر این مقادیر، تغییر اندازهٔ کانتینرهای فلکس زیر را امتحان کنید:

```html hidden
<div class="flex-container">
  <div class="item auto">auto</div>
  <div class="item auto">auto</div>
  <div class="item auto">auto</div>
</div>

<div class="flex-container">
  <div class="item auto">auto</div>
  <div class="item initial">initial</div>
  <div class="item initial">initial</div>
</div>

<div class="flex-container">
  <div class="item auto">auto</div>
  <div class="item auto">auto</div>
  <div class="item none">none</div>
</div>

<div class="flex-container">
  <div class="item initial">initial</div>
  <div class="item none">none</div>
  <div class="item none">none</div>
</div>

<div class="flex-container">
  <div class="item four">4</div>
  <div class="item two">2</div>
  <div class="item one">1</div>
</div>
```

```css hidden
* {
  box-sizing: border-box;
}

.flex-container {
  background-color: #f4f7f8;
  resize: horizontal;
  overflow: hidden;
  display: flex;
  margin: 1em;
}

.item {
  margin: 1em;
  padding: 0.5em;
  width: 110px;
  min-width: 0;
  background-color: #1b5385;
  color: white;
  font-family: monospace;
  font-size: 13px;
}

.initial {
  flex: initial;
}

.auto {
  flex: auto;
}

.none {
  flex: none;
}

.four {
  flex: 4;
}

.two {
  flex: 2;
}

.one {
  flex: 1;
}
```

به طور پیش‌فرض آیتم‌های فلکس از اندازهٔ `min-content` کوچکتر نمی‌شوند. برای تغییر این رفتار، `min-width` یا `min-height` آیتم را تنظیم کنید.

## تعریف رسمی

## نحو رسمی

## مثال‌ها

### تنظیم `flex: auto`

این مثال نشان می‌دهد که چگونه یک آیتم فلکس با `flex: auto` برای جذب فضای آزاد موجود در کانتینر رشد می‌کند.

#### HTML

```html
<div id="flex-container">
  <div id="flex-auto">
    flex: auto (click to remove/add the `flex: initial` box)
  </div>
  <div id="default">flex: initial</div>
</div>
```

#### CSS

```css hidden
body * {
  padding: 1rem;
  user-select: none;
  box-sizing: border-box;
  font-family: "Consolas", "Arial", sans-serif;
}
```

```css
#flex-container {
  border: 2px dashed gray;
  display: flex;
}

#flex-auto {
  cursor: pointer;
  background-color: wheat;

  flex: auto;
}

#default {
  background-color: lightblue;
}
```

#### JavaScript

```js
const flexAutoItem = document.getElementById("flex-auto");
const defaultItem = document.getElementById("default");
flexAutoItem.addEventListener("click", () => {
  defaultItem.style.display =
    defaultItem.style.display === "none" ? "block" : "none";
});
```

#### نتیجه

کانتینر فلکس شامل دو آیتم فلکس است:

- آیتم `#flex-auto` مقدار `flex` برابر `auto` دارد. مقدار `auto` به `1 1 auto` گسترش می‌یابد، یعنی آیتم مجاز به گسترش است.
- آیتم `#default` مقدار `flex` ندارد، بنابراین به مقدار `initial` بازمی‌گردد. مقدار `initial` به `0 1 auto` گسترش می‌یابد، یعنی آیتم مجاز به گسترش نیست.

آیتم `#default` به اندازه‌ای که عرضش لازم دارد فضا می‌گیرد، اما برای اشغال فضای بیشتر رشد نمی‌کند. تمام فضای باقی‌مانده توسط آیتم `#flex-auto` گرفته می‌شود.

وقتی روی آیتم `#flex-auto` کلیک می‌کنید، ما مقدار `display` آیتم `#default` را به `none` تنظیم می‌کنیم و آن را از چیدمان حذف می‌کنیم. سپس آیتم `#flex-auto` گسترش یافته و تمام فضای موجود در کانتینر را اشغال می‌کند. بار دیگر کلیک کردن آیتم `#flex-auto` آیتم `#default` را به کانتینر اضافه می‌کند.

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- [Basic concepts of flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [Controlling ratios of flex items along the main axis](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Controlling_flex_item_ratios)
- [CSS flexible box layout](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) module