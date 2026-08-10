---
title: "align-items CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/align-items"
translated_by: "n8n + AI"
---

# ویژگی `align-items` در CSS

ویژگی **`align-items`** در CSS مقدار `align-self` را برای تمام فرزندان مستقیم به‌صورت گروهی تنظیم می‌کند. در flexbox، این ویژگی تراز آیتم‌ها را در امتداد cross axis کنترل می‌کند. در grid layout، تراز آیتم‌ها را در امتداد block axis داخل grid area مربوطه کنترل می‌کند.

## نمونه تعاملی

نمونه تعاملی زیر با استفاده از grid layout برخی از مقدارهای این ویژگی را نشان می‌دهد.

```css
align-items: stretch;
```

```css
align-items: center;
```

```css
align-items: start;
```

```css
align-items: end;
```

```html
<section class="default-example" id="default-example">
  <div class="example-container">
    <div class="transition-all" id="example-element">
      <div>One</div>
      <div>Two</div>
      <div>Three</div>
    </div>
  </div>
</section>
```

```css
#example-element {
  border: 1px solid #c5c5c5;
  display: grid;
  width: 200px;
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: 80px;
  grid-gap: 10px;
}

#example-element > div {
  background-color: rgb(0 0 255 / 0.2);
  border: 3px solid blue;
}
```

## نحو (Syntax)

```css
/* کلیدواژه‌های پایه */
align-items: normal;
align-items: stretch;

/* تراز موقعیتی */
/* align-items مقادیر left و right را نمی‌پذیرد */
align-items: center;
align-items: start;
align-items: end;
align-items: flex-start;
align-items: flex-end;
align-items: self-start;
align-items: self-end;
align-items: anchor-center;

/* تراز مبتنی بر baseline */
align-items: baseline;
align-items: first baseline;
align-items: last baseline;

/* تراز سرریز (فقط برای تراز موقعیتی) */
align-items: safe center;
align-items: unsafe center;

/* مقادیر سراسری */
align-items: inherit;
align-items: initial;
align-items: revert;
align-items: revert-layer;
align-items: unset;
```

## مقادیر

این ویژگی یک یا دو کلیدواژه از موارد زیر را می‌پذیرد:

- `normal`
  - : تأثیر این کلیدواژه به حالت چیدمانی که در آن هستیم بستگی دارد:
    - در چیدمان‌های با موقعیت‌دهی مطلق (absolutely-positioned)، این کلیدواژه روی جعبه‌های مطلق replaced مانند `start` عمل می‌کند و روی *تمام جعبه‌های مطلق دیگر* مانند `stretch`.
    - در موقعیت استاتیک چیدمان‌های با موقعیت‌دهی مطلق، مانند `stretch` عمل می‌کند.
    - روی flex items، مانند `stretch` عمل می‌کند.
    - روی grid items، رفتاری شبیه `stretch` دارد، به‌جز جعبه‌هایی که دارای نسبت ابعاد (aspect ratio) یا اندازه ذاتی هستند، که در آن‌ها مانند `start` عمل می‌کند.
    - این ویژگی روی جعبه‌های سطح block و سلول‌های جدول اعمال نمی‌شود.

- `center`
  - : جعبه‌های margin مربوط به flex items در امتداد cross axis در مرکز خط قرار می‌گیرند. اگر اندازه عرضی یک آیتم از flex container بزرگ‌تر باشد، در هر دو جهت به‌طور مساوی سرریز می‌شود.

- `start`
  - : آیتم‌ها به‌صورت چسبیده به لبه شروع محفظه ترازبندی (alignment container) در محور مناسب بسته‌بندی می‌شوند.

- `end`
  - : آیتم‌ها به‌صورت چسبیده به لبه پایان محفظه ترازبندی در محور مناسب بسته‌بندی می‌شوند.

- `self-start`
  - : آیتم‌ها به لبه شروع محفظه ترازبندی – که همان سمت شروع خود آیتم است – در محور مناسب چسبیده می‌شوند.

- `self-end`
  - : آیتم‌ها به لبه پایان محفظه ترازبندی – که همان سمت پایان خود آیتم است – در محور مناسب چسبیده می‌شوند.

- `baseline`, `first baseline`, `last baseline`
  - : همهٔ آیتم‌های flex به‌گونه‌ای تراز می‌شوند که [flex container baselines](https://drafts.csswg.org/css-flexbox-1/#flex-baselines) آن‌ها هم‌راستا شود. آیتمی که بیشترین فاصله را بین لبهٔ margin سمت cross-start و خط پایهٔ خود دارد، به لبهٔ cross-start خط می‌چسبد.

- `stretch`
  - : اگر اندازهٔ cross-size آیتم `auto` باشد، اندازهٔ استفاده‌شده به اندازهٔ طولی تنظیم می‌شود که آیتم را تا حد ممکن به پر کردن container نزدیک کند، با درنظرگرفتن محدودیت‌های عرض و ارتفاع آیتم. اگر آیتم اندازه‌ای غیر از auto داشته باشد، این مقدار به `flex-start` بازمی‌گردد و اگر مقدار {{cssxref("align-content")}} کانتینر `first baseline` (یا `baseline`) یا `last baseline` باشد، به `self-start` یا `self-end` تغییر می‌کند.

- `anchor-center`
  - : در مورد المان‌های [anchor-positioned](/en-US/docs/Web/CSS/Guides/Anchor_positioning)، آیتم‌ها را در جهت block نسبت به مرکز المان anchor مرتبط تراز می‌کند. به [Centering on the anchor using `anchor-center`](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using#centering_on_the_anchor_using_anchor-center) مراجعه کنید.

- `safe`
  - : همراه با یک کلمهٔ کلیدی تراز استفاده می‌شود. اگر کلمهٔ کلیدی انتخاب‌شده باعث سرریز آیتم از alignment container شود و منجر به از دست رفتن داده گردد، آیتم به‌جای آن طوری تراز می‌شود که گویی حالت تراز `start` انتخاب شده است.

- `unsafe`
  - : همراه با یک کلمهٔ کلیدی تراز استفاده می‌شود. صرف‌نظر از اندازه‌های نسبی آیتم و alignment container و اینکه سرریز منجر به از دست رفتن داده بشود یا نشود، مقدار تراز داده‌شده اعمال می‌شود.

همچنین دو مقدار دیگر که برای flexbox تعریف شده و مبتنی بر مفاهیم [flex model axes](/en-US/docs/Learn_web_development/Core/CSS_layout/Flexbox#the_flex_model) هستند، در چیدمان‌های grid نیز کار می‌کنند:

- `flex-start`
  - : فقط در چیدمان flex استفاده می‌شود؛ آیتم‌های flex را به سمت main-start یا cross-start کانتینر flex می‌چسباند. وقتی خارج از یک بستر قالب‌بندی flex استفاده شود، این مقدار مانند `start` رفتار می‌کند.

- `flex-end`
  - : فقط در چیدمان flex استفاده می‌شود؛ آیتم‌های flex را به سمت main-end یا cross-end کانتینر flex می‌چسباند. وقتی خارج از یک بستر قالب‌بندی flex استفاده شود، این مقدار مانند `end` رفتار می‌کند.

## Examples

در این مثال یک container با شش فرزند داریم. یک منوی کشویی {{htmlelement("select")}} امکان تغییر {{cssxref("display")}} کانتینر را بین `grid` و `flex` فراهم می‌کند. یک منوی دوم نیز امکان تغییر مقدار ویژگی `align-items` کانتینر را می‌دهد.

### CSS

ظاهر container و آیتم‌ها را طوری تعریف کرده‌ایم که مطمئن شویم دو سطر یا ستون آیتم داریم. دو کلاس `flex.` و `grid.` تعریف شده‌اند که با جاوااسکریپت به container اعمال می‌شوند. این کلاس‌ها مقدار {{cssxref("display")}} کانتینر را تنظیم کرده و رنگ پس‌زمینه و حاشیهٔ آن را تغییر می‌دهند تا یک نشانهٔ اضافی برای تغییر چیدمان فراهم شود. هر شش آیتم flex دارای رنگ پس‌زمینهٔ متفاوتی هستند؛ آیتم چهارم دو خطی است و آیتم ششم اندازهٔ فونت بزرگ‌تری دارد.

```css
.flex,
.grid {
  height: 200px;
  width: 500px;
  align-items: initial; /* Change the value in the live sample */
  border: solid 5px transparent;
  gap: 3px;
}

.flex {
  display: flex;
  flex-wrap: wrap;
  background-color: #8c8c9f;
  border-color: magenta;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, 100px);
  background-color: #9f8c8c;
  border-color: slateblue;
}

#item1 {
  background-color: #8cffa0;
  min-height: 30px;
}

#item2 {
  background-color: #a0c8ff;
  min-height: 50px;
}

#item3 {
  background-color: #ffa08c;
  min-height: 40px;
}

#item4 {
  background-color: #ffff8c;
  min-height: 60px;
}

#item5 {
  background-color: #ff8cff;
  min-height: 70px;
}

#item6 {
  background-color: #8cffff;
  min-height: 50px;
  font-size: 30px;
}
```

```css hidden
select {
  font-size: 16px;
}

.row {
  margin-top: 10px;
}
```

```css
div > div {
  box-sizing: border-box;
  border: 2px solid white;
  width: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

### HTML

ما یک container از نوع {{htmlelement("div")}} با شش فرزند `<div>` تو در تو قرار داده‌ایم. کد HTML مربوط به فرم و JavaScript که کلاس container را تغییر می‌دهد، به‌خاطر خلاصه‌سازی مخفی شده‌اند.

```html
<div id="container" class="flex">
  <div id="item1">1</div>
  <div id="item2">2</div>
  <div id="item3">3</div>
  <div id="item4">4<br />line 2</div>
  <div id="item5">5</div>
  <div id="item6">6</div>
</div>
```

```html hidden
<div class="row">
  <label for="display">display: </label>
  <select id="display">
    <option value="flex">flex</option>
    <option value="grid">grid</option>
  </select>
</div>

<div class="row">
  <label for="values">align-items: </label>
  <select id="values">
    <option value="normal">normal</option>
    <option value="flex-start">flex-start</option>
    <option value="flex-end">flex-end</option>
    <option value="center" selected>center</option>
    <option value="baseline">baseline</option>
    <option value="stretch">stretch</option>

    <option value="start">start</option>
    <option value="end">end</option>
    <option value="self-start">self-start</option>
    <option value="self-end">self-end</option>

    <option value="first baseline">first baseline</option>
    <option value="last baseline">last baseline</option>

    <option value="safe center">safe center</option>
    <option value="unsafe center">unsafe center</option>
    <option value="safe right">safe right</option>
    <option value="unsafe right">unsafe right</option>
    <option value="safe end">safe end</option>
    <option value="unsafe end">unsafe end</option>
    <option value="safe self-end">safe self-end</option>
    <option value="unsafe self-end">unsafe self-end</option>
    <option value="safe flex-end">safe flex-end</option>
    <option value="unsafe flex-end">unsafe flex-end</option>
  </select>
</div>
```

```js hidden
const values = document.getElementById("values");
const display = document.getElementById("display");
const container = document.getElementById("container");

values.addEventListener("change", (evt) => {
  container.style.alignItems = evt.target.value;
});

display.addEventListener("change", (evt) => {
  container.className = evt.target.value;
});
```

### نتیجه

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{cssxref("align-self")}}
- {{cssxref("align-content")}}
- {{cssxref("justify-items")}}
- {{cssxref("place-items")}} (کوتاه‌نویسی)
- [مفاهیم پایه‌ای flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [ترازبندی آیتم‌ها در یک flex container](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Aligning_items)
- [ترازبندی جعبه‌ها در grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
- [ماژول CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment)
- [ماژول CSS flexible box layout](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)
- [ماژول CSS grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout)