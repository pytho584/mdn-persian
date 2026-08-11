---
title: "popover HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/popover"
translated_by: "n8n + AI"
---

ویژگی سراسری `popover` برای مشخص کردن یک عنصر بهعنوان عنصر popover استفاده میشود.

## مقدار

ویژگی `popover` میتواند یکی از مقادیر زیر را بگیرد:

- `"auto"`
  - : popoverهای [`auto`](/en-US/docs/Web/API/Popover_API/Using#auto_state_and_light_dismiss) قابلیت «بسته شدن سبک» (light dismiss) دارند؛ یعنی میتوانید با کلیک در بیرون از popover یا فشردن کلید <kbd>Esc</kbd> آن را مخفی کنید. نمایش یک popover از نوع `auto` معمولاً باعث بسته شدن دیگر popoverهای `auto` که از قبل نمایش داده شدهاند میشود، مگر اینکه تو در تو (nested) باشند.

    > [!NOTE]
    > تنظیم مقدار خالی برای `popover` — یعنی `popover` یا `popover=""` — معادل تنظیم `popover="auto"` است.

- `"hint"`
  - : popoverهای [`hint`](/en-US/docs/Web/API/Popover_API/Using#using_hint_popover_state) هنگام نمایش، popoverهای `auto` را نمیبندند، اما popoverهای hint دیگری را که در [پشته hint](/en-US/docs/Web/API/Popover_API/Using#popover_openclose_interaction_rules) اجداد آنها محسوب نمیشوند، میبندند. این popoverها قابلیت بسته شدن سبک دارند و به درخواست بسته شدن پاسخ میدهند.

- `"manual"`
  - : popoverهای [`manual`](/en-US/docs/Web/API/Popover_API/Using#using_manual_popover_state) نمیتوانند بهصورت سبک بسته شوند و بهطور خودکار بسته نمیشوند. این popoverها باید بهصورت صریح و با استفاده از دکمههای نمایش/مخفی کردن/تغییر وضعیت declarative یا با JavaScript نمایش داده و مخفی شوند. چند popover مستقل از نوع `manual` میتوانند همزمان نمایش داده شوند.

## توضیحات

عناصر popover تا زمانی که توسط یک عنصر فراخوان/کنترل (مثل `<button>` یا `<input type="button">` با ویژگی [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget)) یا فراخوانی {{domxref("HTMLElement.showPopover()")}} باز نشوند، با `display: none` مخفی میمانند.

وقتی popover باز است، در بالای همه عناصر دیگر در لایه بالایی (top layer) قرار میگیرد و تحت تأثیر استایل [`position`](/en-US/docs/Web/CSS/position) یا [`overflow`](/en-US/docs/Web/CSS/overflow) عناصر والد قرار نمیگیرد.

popoverهایی که حالت [`auto`](/en-US/docs/Web/API/Popover_API/Using#auto_state_and_light_dismiss) دارند را میتوان با کنترلهای مرتبط (که با ویژگی [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) مشخص میشوند) نمایش داد و مخفی کرد، و همچنین میتوان آنها را با کلیک در بیرون از ناحیه popover، باز کردن popover دیگر، یا استفاده از مکانیزمهای مخصوص مرورگر مانند کلید <kbd>Esc</kbd> بهصورت سبک بست.

بهطور کلی فقط یک popover از نوع `auto` میتواند همزمان روی صفحه نمایش داده شود؛ اگر وقتی یک popover نمایش داده شده است، popover دیگری نمایش دهید، popover اول مخفی میشود. استثنا در مورد popoverهای auto تو در تو است. برای جزئیات بیشتر به [Nested popovers](/en-US/docs/Web/API/Popover_API/Using#nested_popovers) مراجعه کنید.

این popoverها را میتوان با JavaScript نیز کنترل کرد؛ مثلاً متد {{domxref("HTMLElement.togglePopover()")}} برای تغییر وضعیت نمایش و مخفی شدن استفاده میشود.

در مقابل، popoverهای [`manual`](/en-US/docs/Web/API/Popover_API/Using#using_manual_popover_state) باید بهصورت دستی نمایش داده و مخفی شوند. آنها هنگام نمایش، popoverهای دیگر را بهطور خودکار نمیبندند و قابلیت بسته شدن سبک را ندارند. این ویژگی برای مواردی مفید است که میخواهید چند popover را همزمان نمایش دهید.

popoverهای [`hint`](/en-US/docs/Web/API/Popover_API/Using#using_hint_popover_state) هنگام نمایش، popoverهای `auto` را نمیبندند، اما popoverهای hint دیگری را که در پشته hint اجداد آنها نیستند میبندند. این popoverها قابلیت بسته شدن سبک دارند و به درخواست بسته شدن پاسخ میدهند.

معمولاً popoverهای `hint` در واکنش به رویدادهای جاوااسکریپتی غیر از کلیک نمایش داده و پنهان می‌شوند؛ مانند [`mouseover`](/en-US/docs/Web/API/Element/mouseover_event)/[`mouseout`](/en-US/docs/Web/API/Element/mouseout_event) و [`focus`](/en-US/docs/Web/API/Element/focus_event)/[`blur`](/en-US/docs/Web/API/Element/blur_event). کلیک کردن روی یک دکمه برای باز کردن یک popover از نوع `hint` باعث می‌شود یک popover باز از نوع `auto` به‌صورت light-dismiss بسته شود (یعنی با کلیک بیرون از آن، بسته شود).

برای اطلاعات دقیق دربارهٔ نحوهٔ استفاده، به صفحهٔ اصلی «Popover API» مراجعه کنید.

## مثال‌ها

### تبدیل یک عنصر به popover

کد زیر یک دکمه را نمایش می‌دهد که هنگام فعال‌شدن، یک عنصر popover را باز می‌کند. این رفتار را می‌توان تنها با HTML پیاده‌سازی کرد.

```html
<button popovertarget="my-popover">Open Popover</button>

<div popover id="my-popover">Greetings, one and all!</div>
```

### popoverهای تودرتو

در این مثال، یک دکمه یک popover را باز می‌کند که شامل popoverهای تودرتوی بیشتری است. این popoverهای تودرتو را می‌توان بدون بستن popover منوی اصلی باز کرد.

#### HTML

در بخش اول HTML، یک `<button>` می‌سازیم که popover اصلی را باز می‌کند؛ همان منویی که چند گزینه دارد.

```html
<header>
  <button popovertarget="menu">Open Menu</button>
</header>
<main>
  <!--  Page content goes here  -->
</main>
```

در بخش دوم HTML، منوی popover را می‌سازیم که با دکمهٔ ساخته‌شده در بلوک کد قبلی باز می‌شود. این منوی popover شامل یک فهرست نامرتب از آیتم‌های منو است و هر آیتم یک دکمهٔ اطلاعات دارد که یک popover تودرتو را باز می‌کند. منوی popover از `popover="auto"` استفاده می‌کند؛ یعنی وقتی popoverهای تودرتو باز می‌شوند، این منو بسته نخواهد شد.

```html
<!-- menu popover -->
<div id="menu" popover="auto">
  <ul>
    <li>
      <a href="#">New thing</a><button popovertarget="new-info">ⓘ</button>
    </li>
    <li>
      <a href="#">Open thing</a><button popovertarget="open-info">ⓘ</button>
    </li>
    <li>
      <a href="#">Save thing</a><button popovertarget="save-info">ⓘ</button>
    </li>
    <li>
      <a href="#">Close thing</a><button popovertarget="close-info">ⓘ</button>
    </li>
  </ul>
</div>
```

در بخش پایانی HTML، popoverهای اطلاعات را برای هر آیتم منو می‌سازیم. هر popover دارای `popover="hint"` است؛ یعنی popover منوی اصلی را نمی‌بندد، اما popoverهای اطلاعات دیگری را که باز هستند می‌بندد.

```html
<!-- info popovers -->
<div id="new-info" class="info-popover" popover="hint">
  This is some information about <strong>creating a new</strong> thing.
</div>
<div id="open-info" class="info-popover" popover="hint">
  This is some information about <strong>opening an existing</strong> thing.
</div>
<div id="save-info" class="info-popover" popover="hint">
  This is some information about <strong>saving the current</strong> thing.
</div>
<div id="close-info" class="info-popover" popover="hint">
  This is some information about <strong>closing the current</strong> thing.
</div>
```

#### CSS

```css hidden
header {
  display: flex;
  justify-content: center;
}
header button {
  margin: 0.4rem auto;
}
```

ما از [anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) برای قرار دادن منوی popover در زیر `<button>` و از [grid](/en-US/docs/Web/CSS/Guides/Grid_layout) برای چیدمان آیتم‌های منو و دکمه‌های اطلاعات استفاده کرده‌ایم.

```css
#menu {
  margin: 0;
  margin-top: 0.4rem;
  inset: auto;
  position-area: bottom;
}
#menu ul {
  display: grid;
  grid-template-columns: max-content 1fr;
  gap: 0.4rem;
  padding: 0.4rem;
}
#menu li {
  grid-column: span 2;
  display: grid;
  grid: inherit;
  grid-template-columns: subgrid;
  gap: 1.4rem;
}
li [popovertarget] {
  cursor: pointer;
  font-size: 1.2rem;
}
li button {
  border: none;
  padding: 0;
  background-color: inherit;
}
```

در اینجا نیز از anchor positioning استفاده کرده‌ایم تا popoverهای اطلاعات در سمت راست دکمه‌های اطلاعات متناظرشان ظاهر شوند.

```css
div.info-popover {
  margin: 2rem;
  inset: auto;
  max-width: 300px;
  position-area: right;
}
```

#### نتیجه

روی دکمه _Open Menu_ کلیک کنید، سپس روی آیکون‌های اطلاعات (ⓘ) کنار گزینه‌های منو بزنید تا popoverهای اطلاعات باز شوند.

> [!NOTE]
> برای مشاهدهٔ مجموعهٔ کامل مثال‌های popover از MDN، به [صفحهٔ اصلی مثال‌های Popover API](https://mdn.github.io/dom-examples/popover-api/) مراجعه کنید.

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- Popover API
- [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) HTML attribute
- [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) HTML attribute
- `::backdrop` CSS pseudo-element
- `:popover-open` CSS pseudo-class