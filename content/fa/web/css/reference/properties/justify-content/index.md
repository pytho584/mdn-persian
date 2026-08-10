---
title: "justify-content CSS property"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/justify-content"
translated_by: "n8n + AI"
---

The [CSS](/en-US/docs/Web/CSS) **`justify-content`** property تعیین می‌کند مرورگر چگونه فضا را بین آیتم‌های محتوا و اطراف آن‌ها در طول محور اصلی (main axis) یک کانتینر فلکس و محور خطی (inline axis) کانتینرهای گرید و مولتی‌کال اعمال کند.

The interactive example below demonstrates some `justify-content` values using grid layout.

```css interactive-example-choice
justify-content: start;
```

```css interactive-example-choice
justify-content: center;
```

```css interactive-example-choice
justify-content: space-between;
```

```css interactive-example-choice
justify-content: space-around;
```

```css interactive-example-choice
justify-content: space-evenly;
```

```html interactive-example
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

```css interactive-example
#example-element {
  border: 1px solid #c5c5c5;
  width: 220px;
  display: grid;
  grid-template-columns: 60px 60px;
  grid-auto-rows: 40px;
  row-gap: 10px;
}

#example-element > div {
  background-color: rgb(0 0 255 / 0.2);
  border: 3px solid blue;
}
```

## Syntax

```css
/* Positional alignment */
justify-content: center;
justify-content: start;
justify-content: end;
justify-content: flex-start;
justify-content: flex-end;
justify-content: left;
justify-content: right;

/* Normal alignment */
justify-content: normal;

/* Distributed alignment */
justify-content: space-between;
justify-content: space-around;
justify-content: space-evenly;
justify-content: stretch;

/* Overflow alignment (for positional alignment only)*/
justify-content: safe center;
justify-content: unsafe center;

/* Global values */
justify-content: inherit;
justify-content: initial;
justify-content: revert;
justify-content: revert-layer;
justify-content: unset;
```

### Values

این خصوصیت با یکی از مقادیر کلیدی زیر مشخص می‌شود:

- `start`
  - : آیتم‌ها به‌صورت چسبیده به یکدیگر به سمت لبه شروع ظرف تراز (alignment container) در محور اصلی جابه‌جا می‌شوند.

- `end`
  - : آیتم‌ها به‌صورت چسبیده به یکدیگر به سمت لبه پایان ظرف تراز در محور اصلی جابه‌جا می‌شوند.

- `flex-start`
  - : آیتم‌ها به‌صورت چسبیده به یکدیگر به سمت لبه شروع ظرف تراز در سمت main-start کانتینر فلکس قرار می‌گیرند.
    این مقدار فقط برای آیتم‌های لایوت فلکس اعمال می‌شود. برای آیتم‌هایی که فرزند یک کانتینر فلکس نیستند، این مقدار مانند `start` رفتار می‌کند.

- `flex-end`
  - : آیتم‌ها به‌صورت چسبیده به یکدیگر در لبه انتهایی ظرف تراز در سمت main-end کانتینر فلکس قرار می‌گیرند.
    این مقدار فقط برای آیتم‌های لایوت فلکس اعمال می‌شود. برای آیتم‌هایی که فرزند یک کانتینر فلکس نیستند، این مقدار مانند `end` رفتار می‌کند.

- `center`
  - : آیتم‌ها به‌صورت چسبیده به یکدیگر به سمت مرکز ظرف تراز در طول محور اصلی قرار می‌گیرند.

- `left`
  - : آیتم‌ها به‌صورت چسبیده به یکدیگر به سمت لبهٔ چپ ظرف تراز قرار می‌گیرند. وقتی محور افقی این خصوصیت موازی محور خطی (inline axis) نباشد، مانند زمانی که [`flex-direction: column;`](/en-US/docs/Web/CSS/Reference/Properties/flex-direction) تنظیم شده است، این مقدار مانند `start` رفتار می‌کند.

- `right`
  - : آیتم‌ها به‌صورت چسبیده به یکدیگر به سمت لبهٔ راست ظرف تراز در محور مربوطه قرار می‌گیرند. اگر محور این خصوصیت موازی محور خطی (در یک کانتینر گرید) یا محور اصلی (در یک کانتینر فلکس) نباشد، این مقدار مانند `start` رفتار می‌کند.

- `normal`
  - : رفتار می‌کند مانند `stretch`، به جز در مورد کانتینرهای چندستونی (multi-column) که `column-width` آن‌ها غیر از `auto` باشد، در این حالت ستون‌ها عرض مشخص‌شدهٔ `column-width` را می‌گیرند و به‌جای کشیده‌شدن برای پر کردن کانتینر امتداد نمی‌یابند. از آن‌جا که `stretch` در کانتینرهای فلکس مانند `start` رفتار می‌کند، `normal` نیز مانند `start` رفتار می‌کند.

- `space-between`
  - : آیتم‌ها به‌طور یکنواخت درون کانتینر تراز沿 محور اصلی (main axis) توزیع می‌شوند. فاصله بین هر جفت آیتم مجاور یکسان است. اولین آیتم با لبهٔ main-start کاملاً هم‌راستا است و آخرین آیتم با لبهٔ main-end کاملاً هم‌راستا است.

- `space-around`
  - : آیتم‌ها به‌طور یکنواخت درون کانتینر تراز沿 محور اصلی توزیع می‌شوند. فاصله بین هر جفت آیتم مجاور یکسان است. فضای خالی قبل از اولین آیتم و بعد از آخرین آیتم برابر نصف فضای بین هر جفت آیتم مجاور است. اگر تنها یک آیتم وجود داشته باشد، در مرکز قرار می‌گیرد.

- `space-evenly`
  - : آیتم‌ها به‌طور یکنواخت درون کانتینر تراز沿 محور اصلی توزیع می‌شوند. فاصله بین هر جفت آیتم مجاور، فاصله بین لبهٔ main-start و اولین آیتم، و فاصله بین لبهٔ main-end و آخرین آیتم همگی دقیقاً یکسان‌اند.

- `stretch`
  - : اگر اندازهٔ ترکیبی آیتم‌ها沿 محور اصلی کمتر از اندازهٔ کانتینر تراز باشد، هر آیتم‌هایی که اندازهٔ آن‌ها `auto` است به‌طور مساوی (نه نسبتاً) افزایش اندازه می‌یابند، در حالی که هنوز محدودیت‌های اعمال‌شده توسط `max-height`/`max-width` (یا عملکرد معادل) رعایت می‌شود، به‌طوری که اندازهٔ ترکیبی دقیقاً کانتینر تراز را沿 محور اصلی پر کند.

    > [!NOTE]
    > برای [flexboxes](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)، مقدار `stretch` مانند `flex-start` یا `start` رفتار می‌کند. دلیل این است که در فلکس‌باکس‌ها، کشش (stretching) با استفاده از ویژگی `flex-grow` کنترل می‌شود.

- `safe`
  - : اگر آیتم از کانتینر تراز بیرون بزند، آیتم طوری تراز می‌شود که انگار حالت تراز `start` است. تراز دلخواه اجرا نخواهد شد.

- `unsafe`
  - : حتی اگر آیتم از کانتینر تراز بیرون بزند، تراز دلخواه اجرا می‌شود. بر خلاف `safe` که برای جلوگیری از سرریز، تراز دلخواه را نادیده می‌گیرد.

## Description

تعریف‌شده در ماژول [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment)، `justify-content` بر روی کانتینرهای چندستونی (multicol)، کانتینرهای فلکس و کانتینرهای گرید اعمال می‌شود. این ویژگی بر روی کانتینرهای بلاک اعمال نمی‌شود و اثری بر آن‌ها ندارد.

این ویژگی بسیاری از کلیدواژه‌ها را با ویژگی `align-content` مشترک دارد، اما همهٔ آن‌ها را نه! `justify-content` در هم‌ترازی بر اساس baseline دخالتی ندارد، و بنابراین مقادیر baseline را قبول نمی‌کند.

در [قالب‌بندی‌های فلکس](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)، این ویژگی تعیین می‌کند که فضای مثبت آزاد چگونه بین یا دور آیتم‌های فلکس沿 محور اصلی توزیع شود. این ویژگی بر فضای بین عناصر در یک خط تأثیر می‌گذارد، نه بر فضای بین خطوط. تراز پس از اعمال طول‌ها و marginهای اتوماتیک انجام می‌شود، که بدین معنی است که هنگامی که یک یا چند آیتم فلکس در یک خط مقدار `flex-grow` بزرگ‌تر از `0` داشته باشند، این ویژگی بی‌اثر است چون فضایی برای توزیع در آن خط وجود ندارد. همچنین، از آن‌جا که کشش沿 محور اصلی توسط `flex` کنترل می‌شود، مقدار `stretch` مانند `flex-start` رفتار می‌کند.

در [قالب‌بندی گرید](/en-US/docs/Web/CSS/Guides/Grid_layout)، این ویژگی فضای در دسترس را بین یا اطراف ستون‌های گرید (grid columns) توزیع می‌کند، نه بین آیتم‌های گرید. اگر کانتینر گرید بزرگ‌تر از خود گرید باشد، می‌توان از `justify-content` برای تراز کردن گرید沿 محور خطی (inline axis) و هم‌ترازی ستون‌های گرید استفاده کرد.

Grid `auto` track sizes (and only `auto` track sizes) can be stretched by the `align-content` and `justify-content` properties. Therefore by default, an `auto` sized track will take up any remaining space in the grid container. As the grid's inline size has to be less than the grid container's inline size for there to be space to distribute, the property has no effect in this case.

## Formal definition

## Formal syntax

## Examples

### Basic grid example

در این مثال، یک گرید داریم که از کانتینر گرید خود باریک‌تر است، و از `justify-content` برای توزیع فضای در دسترس به‌طور مساوی در اطراف و بین ستون‌های گرید استفاده می‌کنیم.

#### HTML

The {{htmlelement("section")}} container, our grid container to-be, has 16 nested {{htmlelement("div")}}s that will become grid items.

```html
<section class="container">
  <div>A</div>
  <div>B</div>
  <div>C</div>
  <div>D</div>
  <div>E</div>
  <div>F</div>
  <div>G</div>
  <div>H</div>
  <div>I</div>
  <div>J</div>
  <div>K</div>
  <div>L</div>
  <div>M</div>
  <div>N</div>
  <div>O</div>
  <div>P</div>
</section>
```

#### CSS

```css hidden
.container {
  margin: 5px;
  border: 1px solid;
  box-sizing: border-box;
}

div {
  line-height: 2em;
  border: 1px solid;
  box-sizing: border-box;
  text-align: center;
}
```

ما عرض کانتینر را روی `500px` تنظیم می‌کنیم و سه ستون هر کدام `80px` عرض مشخص می‌کنیم، که به این معنی است `260px` فضای قابل توزیع بین یا اطراف آن‌ها وجود دارد. سپس `justify-content: space-evenly` را تنظیم می‌کنیم، که یعنی قبل، بین و بعد از هر ستون `65px` فاصله خواهد بود.

ما عرض‌ها (و رنگ‌های پس‌زمینه) متفاوتی تنظیم می‌کنیم تا نشان دهیم که چطور توجیه (justification) روی ستون‌ها اعمال می‌شود.

```css
.container {
  display: grid;
  grid: auto-flow / repeat(3, 80px);
  width: 500px;
  justify-content: space-evenly;
}

div {
  background-color: pink;
  width: 80px;
}

div:nth-of-type(n + 9) {
  width: 35px;
  background-color: lightgreen;
}

div:nth-last-of-type(3) {
  width: 250px;
  background-color: lightblue;
}
```

#### Result

توجه کنید که `justify-contents` ستون‌ها را تراز می‌کند و تأثیری روی آیتم‌ها یا تراز داخل نواحی گرید ندارد. آیتم‌های گرید، حتی آن‌هایی که از سل گرید خود خارج می‌شوند، بر توجیه ستون‌ها تأثیر نمی‌گذارند.

### The safe keyterm

این مثال کلیدواژه `safe` را نشان می‌دهد. ما چهار آیتم فلکس مرکزی داریم که اجازهٔ پیچش (wrap) ندارند و در نتیجه از تک‌خط کانتینر فلکس خود سرریز می‌کنند. با اضافه کردن `safe` به `center` در `justify-content`، محتوای سرریز شده رفتار می‌کند گویی حالت تراز `start` است.

```html hidden
<p><code>justify-content: center;</code></p>
<section class="container safe">
  <div>A</div>
  <div>B</div>
  <div>C</div>
  <div>D</div>
</section>
<p><code>justify-content: safe center;</code></p>
<section class="container safe-center">
  <div>A</div>
  <div>B</div>
  <div>C</div>
  <div>D</div>
</section>
<p><code>justify-content: safe center;</code> with 3 items</p>
<section class="container safe-center">
  <div>A</div>
  <div>B</div>
  <div>C</div>
</section>
```

```css hidden
.container {
  margin: 5px auto;
  border: 1px dashed;
  box-sizing: border-box;
  background-color: lightblue;
}

div {
  line-height: 1em;
  border: 1px solid;
  box-sizing: border-box;
  text-align: center;
  background-color: pink;
}
```

کانتینر روی `center` تنظیم شده است، و هر کانتینری به جز اولی، کلیدواژه `safe` را اضافه کرده است:

```css
.container {
  align-items: baseline;
  display: flex;
  width: 350px;
  height: 2em;
}

.safe {
  justify-content: center;
}

.safe-center {
  justify-content: safe center;
}

div {
  flex: 0 0 100px;
}
```

#### Result

As an item overflows the alignment container, with `safe` included the alignment mode behaves as `start` and the `center` alignment is not implemented. The `safe` keyterm has no effect if the items do not overflow the container.

### Visualizing flex item distribution

این مثال شامل یک طرح فلکس چندخطی با شکستن (wrapping) است. آیتم دوم فلکس دارای فاکتور رشد مثبت (flex growth factor) است و تمام فضای آزاد در خط اول فلکس را مصرف می‌کند.

#### CSS

```css hidden
#container {
  margin: 5px auto;
  border: 1px dashed black;
  box-sizing: border-box;
}

div {
  line-height: 2em;
  border: 1px solid;
  box-sizing: border-box;
  text-align: center;
}
```

```css
#container {
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between; /* Can be changed in the live sample */
  width: 510px;
}

div {
  line-height: 2em;
  flex: 0 0 120px;
  background-color: pink;
}

div:nth-of-type(2) {
  flex-grow: 1;
  background-color: yellow;
}

div:nth-of-type(n + 9) {
  flex: 0 0 35px;
  background-color: lightgreen;
}
div:last-of-type {
  flex: 0 0 300px;
  background-color: lightblue;
}
```

```html hidden
<section id="container">
  <div>A</div>
  <div>GROW</div>
  <div>C</div>
  <div>D</div>
  <div>E</div>
  <div>F</div>
  <div>G</div>
  <div>H</div>
  <div>I</div>
  <div>J</div>
  <div>K</div>
  <div>L</div>
  <div>M</div>
  <div>N</div>
  <div>O</div>
  <div>P</div>
</section>
<select id="justifyContent">
  <option value="start">start</option>
  <option value="end">end</option>
  <option value="flex-start">flex-start</option>
  <option value="flex-end">flex-end</option>
  <option value="center">center</option>
  <option value="left">left</option>
  <option value="right">right</option>
  <option value="space-between" selected>space-between</option>
  <option value="space-around">space-around</option>
  <option value="space-evenly">space-evenly</option>
  <option value="stretch">stretch</option>
</select>
```

```js hidden
const justifyContent = document.getElementById("justifyContent");
justifyContent.addEventListener("change", (evt) => {
  document.getElementById("container").style.justifyContent = evt.target.value;
});
```

#### Result

Select different keywords from the drop-down menu to visualize the different `justify-content` keyword values. Because an item on the first line can grow, there is no available space on that line for the `justify-content` property to distribute. With the `space-between` value, the first item on each line is flush with the main-start edge, and the last item is flush with the main-end edge. As a result, if a line has only one item, it will be aligned with the main-start edge (as seen in the last line). This is not the case for other `space-*` values, such as `space-evenly` and `space-around`, which center one-item flex-lines.

## Specifications

## Browser compatibility

## See also

- [Basic concepts of flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [Aligning items in a flex container](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Aligning_items)
- [Box alignment in grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
- [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment) module