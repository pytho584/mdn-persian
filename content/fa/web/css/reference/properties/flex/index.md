---
title: "flex CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/flex"
translated_by: "n8n + AI"
---

# `flex` CSS property

ویژگی **`flex`** یک [خصوصیت خلاصه‌شده](/en-US/docs/Web/CSS/Guides/Cascade/Shorthand_properties) در CSS است که نحوهٔ رشد یا کوچک‌شدن یک flex item را برای پر کردن فضای موجود در flex container تعیین می‌کند.

## ویژگی‌های تشکیل‌دهنده

این ویژگی خلاصه‌ای از خصوصیات زیر است:

- [`flex-grow`](/en-US/docs/Web/CSS/flex-grow)
- [`flex-shrink`](/en-US/docs/Web/CSS/flex-shrink)
- [`flex-basis`](/en-US/docs/Web/CSS/flex-basis)

## Syntax

```css
/* مقدار کلیدی */
flex: none; /* معادل 0 0 auto */

/* یک مقدار، عدد بدون واحد: flex-grow
   در این حالت flex-basis برابر با 0% می‌شود */
flex: 2; /* 2 1 0% */

/* یک مقدار، width/height: flex-basis */
flex: auto; /* 1 1 auto */
flex: 10em; /* 1 1 10em */
flex: 30%;
flex: min-content;

/* دو مقدار: flex-grow | flex-basis */
flex: 1 30px; /* 1 1 30px */

/* دو مقدار: flex-grow | flex-shrink */
flex: 2 2; /* 2 2 0% */

/* سه مقدار: flex-grow | flex-shrink | flex-basis */
flex: 2 2 10%;

/* مقادیر سراسری */
flex: inherit;
flex: initial; /* 0 1 auto */
flex: revert;
flex: revert-layer;
flex: unset;
```

ویژگی `flex` را می‌توان با یک، دو یا سه مقدار مشخص کرد.

- **نحو تک‌مقداری:** مقدار باید یکی از موارد زیر باشد:
  - یک مقدار معتبر برای `flex-grow`: در این صورت خلاصه به `flex: <flex-grow> 1 0%` گسترش می‌یابد.
  - یک مقدار معتبر برای `flex-basis`: در این صورت خلاصه به `flex: 1 1 <flex-basis>` گسترش می‌یابد.
  - کلیدواژهٔ `none` یا یکی از کلیدواژه‌های سراسری.

- **نحو دومقداری:**
  - مقدار اول باید یک مقدار معتبر برای `flex-grow` باشد.
  - مقدار دوم باید یکی از موارد زیر باشد:
    - یک مقدار معتبر برای `flex-shrink`: در این صورت خلاصه به `flex: <flex-grow> <flex-shrink> 0%` گسترش می‌یابد.
    - یک مقدار معتبر برای `flex-basis`: در این صورت خلاصه به `flex: <flex-grow> 1 <flex-basis>` گسترش می‌یابد.

- **نحو سه‌مقداری:** مقادیر باید به ترتیب زیر باشند:
  1. یک مقدار معتبر برای `flex-grow`.
  2. یک مقدار معتبر برای `flex-shrink`.
  3. یک مقدار معتبر برای `flex-basis`.

### مقادیر

- `<'flex-grow'>`
  - : مقدار `flex-grow` را برای flex item تعیین می‌کند. مقادیر منفی نامعتبر هستند. در صورت حذف، پیش‌فرض آن `1` می‌شود (مقدار اولیه `0` است).
- `<'flex-shrink'>`
  - : مقدار `flex-shrink` را برای flex item تعیین می‌کند. مقادیر منفی نامعتبر هستند. در صورت حذف، پیش‌فرض آن `1` می‌شود (مقدار اولیه `1` است).
- `<'flex-basis'>`
  - : مقدار `flex-basis` را برای flex item تعیین می‌کند. در صورت حذف، پیش‌فرض آن `0%` می‌شود. مقدار اولیه `auto` است.
- `none`
  - : اندازه item بر اساس ویژگی‌های `width` و `height` خودش تعیین می‌شود. این item کاملاً غیرقابل انعطاف است: یعنی نسبت به flex container نه رشد می‌کند و نه کوچک می‌شود. این معادل تنظیم `flex: 0 0 auto` است.

برای دستیابی به جلوه‌های رایج flexbox می‌توان از مقادیر زیر برای `flex` استفاده کرد:

- `initial`: آیتم flex رشد نمی‌کند اما می‌تواند کوچک شود. این مقدار پیش‌فرض به `flex: 0 1 auto` بسط پیدا می‌کند. اندازه آیتم بر اساس ویژگی‌های `width` یا `height` و متناسب با `flex-direction` تعیین می‌شود. اگر فضای منفی در container وجود داشته باشد، آیتم تا حداقل اندازه خود جمع می‌شود تا درون container جا بگیرد، ولی برای جذب فضای مثبت اضافی رشد نخواهد کرد.
- `auto`: آیتم flex هم می‌تواند رشد کند و هم کوچک شود. این مقدار به `flex: 1 1 auto` بسط پیدا می‌کند. اندازه آیتم طبق ویژگی‌های `width` یا `height` و با توجه به `flex-direction` است، اما فضای مثبت خالی درون container را پر می‌کند و در صورت فضای منفی تا حداقل اندازه خود جمع می‌شود. آیتم flex کاملاً انعطاف‌پذیر است.
- `none`: آیتم flex نه رشد می‌کند و نه کوچک می‌شود. این مقدار به `flex: 0 0 auto` بسط پیدا می‌کند. اندازه آیتم بر اساس ویژگی‌های `width` یا `height` و جهت container تعیین می‌شود. آیتم flex کاملاً غیرقابل انعطاف است.
- `flex: <number [1,∞]>`: اندازه اصلی آیتم flex متناسب با عدد تنظیم‌شده خواهد بود. این مقدار به `flex: <number> 1 0%` بسط پیدا می‌کند و `flex-basis` را روی `0%` قرار داده و آیتم را انعطاف‌پذیر می‌کند. آیتم حداقل به اندازه حداقل ابعاد خود بوده و فضای مثبت container به نسبت ضرایب رشد این آیتم و آیتم‌های هم‌خواهر (sibling) توزیع می‌شود. اگر تمام آیتم‌ها از این الگو استفاده کنند، اندازه همگی متناسب با مقادیر عددی آن‌ها خواهد بود.

## توضیحات

در بیشتر موارد، باید مقدار `flex` را یکی از مقادیر زیر قرار دهید: `auto`، `initial`، `none` یا یک عدد مثبت بدون واحد. برای مشاهده تأثیر این مقادیر می‌توانید containerهای flex زیر را با تغییر اندازه امتحان کنید:

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

به‌طور پیش‌فرض آیتم‌های flex کمتر از اندازه `min-content` خود جمع نمی‌شوند. برای تغییر این رفتار، ویژگی `min-width` یا `min-height` را برای آیتم تنظیم کنید.

## مثال‌ها

### تنظیم flex: auto

این مثال نشان می‌دهد که چگونه یک آیتم flex با `flex: auto` رشد می‌کند تا فضای خالی درون container را پر کند.

#### HTML

```html
<div id="flex-container">
  <div id="flex-auto">
    flex: auto (برای افزودن/حذف آیتم `flex: initial` کلیک کنید)
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

فلاکس کانتینر شامل دو آیتم flex است:

- آیتم `#flex-auto` دارای مقدار `flex` برابر با `auto` است. مقدار `auto` معادل `1 1 auto` می‌شود؛ یعنی این آیتم اجازهٔ بزرگ‌تر شدن دارد.
- آیتم `#default` هیچ مقداری برای `flex` ندارد، بنابراین به مقدار `initial` پیش‌فرض می‌کند. مقدار `initial` معادل `0 1 auto` است؛ یعنی این آیتم اجازهٔ بزرگ‌تر شدن ندارد.

آیتم `#default` فقط به اندازهٔ عرض مورد نیاز خود فضا می‌گیرد و فضای اضافه‌تری را اشغال نمی‌کند. تمام فضای باقی‌مانده توسط آیتم `#flex-auto` گرفته می‌شود.

وقتی روی آیتم `#flex-auto` کلیک می‌کنید، ویژگی `display` آیتم `#default` را به `none` تنظیم می‌کنیم و آن را از صفحه حذف می‌کنیم. سپس آیتم `#flex-auto` کل فضای در دسترس کانتینر را پر می‌کند. با کلیک دوباره روی `#flex-auto`، آیتم `#default` دوباره به صفحه اضافه می‌شود.

## مشخصات فنی

## سازگاری با مرورگرها

## همچنین ببینید

- [مفاهیم پایه‌ای flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [کنترل نسبت‌های آیتم‌های flex در امتداد محور اصلی](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Controlling_flex_item_ratios)
- [ماژول چیدمان جعبه انعطاف‌پذیر CSS](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)