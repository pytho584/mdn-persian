---
title: "popover HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/popover"
translated_by: "n8n + AI"
---

# ویژگی سراسری `popover`

ویژگی سراسری (global attribute) **`popover`** برای مشخص کردن یک عنصر به‌عنوان عنصر پاپاور استفاده می‌شود.

## مقدار

ویژگی `popover` می‌تواند یکی از مقادیر زیر را بگیرد:

- `"auto"`
  - : پاپاورهای «`auto`» را می‌توان با «light dismiss» بست؛ یعنی با کلیک بیرون از پاپاور یا فشردن کلید <kbd>Esc</kbd> می‌شود آن را مخفی کرد. نمایش یک پاپاور `auto` معمولاً باعث می‌شود پاپاورهای `auto` دیگری که در حال نمایش هستند بسته شوند، مگر اینکه تو در تو (nested) باشند.

    > توجه: تنظیم مقدار خالی برای `popover` — یعنی `popover` یا `popover=""` — معادل `popover="auto"` است.

- `"hint"`
  - : پاپاورهای [`hint`](/en-US/docs/Web/API/Popover_API/Using#using_hint_popover_state) هنگام نمایش، پاپاورهای `auto` را نمی‌بندند؛ اما سایر پاپاورهای `hint` را که در [پشته hint (hint stack)](/en-US/docs/Web/API/Popover_API/Using#popover_openclose_interaction_rules) جد (ancestor) آن‌ها نیستند می‌بندند. این پاپاورها را می‌توان با light dismiss بست و به درخواست‌های بستن پاسخ می‌دهند.

- `"manual"`
  - : پاپاورهای [`manual`](/en-US/docs/Web/API/Popover_API/Using#using_manual_popover_state) را نمی‌توان با «light dismiss» بست و به‌صورت خودکار بسته نمی‌شوند. برای نمایش و بستن این پاپاورها باید به‌صورت صریح از دکمه‌های نمایش/پنهان/تغییر وضعیت (declarative show/hide/toggle) یا JavaScript استفاده کرد. چند پاپاور مستقل `manual` می‌توانند همزمان نمایش داده شوند.

## توضیحات

عناصر پاپاور تا وقتی که توسط یک عنصر کنترل‌کننده (مثلاً یک `<button>` یا `<input type="button">` با ویژگی `popovertarget`) یا با فراخوانی `HTMLElement.showPopover()` باز نشده‌اند، با `display: none` مخفی می‌مانند.

وقتی باز باشند، عناصر پاپاور بالای همه عناصر دیگر در لایه بالایی (top layer) قرار می‌گیرند و از استایل `position` یا `overflow` عناصر والد تأثیر نمی‌پذیرند.

پاپاورهایی که حالت [`auto`](/en-US/docs/Web/API/Popover_API/Using#auto_state_and_light_dismiss) دارند را می‌توان با کنترل‌های مرتبط (که با ویژگی `popovertarget` مشخص می‌شوند) نمایش داد یا مخفی کرد. همچنین می‌توان این پاپاورها را با کلیک بیرون از ناحیه پاپاور، باز کردن پاپاور دیگر، یا استفاده از مکانیزم‌های مخصوص مرورگر مثل کلید <kbd>Esc</kbd> بست (light dismiss).

معمولاً فقط یک پاپاور `auto` می‌تواند در هر لحظه روی صفحه نمایش داده شود؛ یعنی اگر هنگام نمایش یک پاپاور، پاپاور دیگری را نمایش دهید، پاپاور اول مخفی می‌شود. تنها استثنا وقتی است که پاپاورهای `auto` تو در تو داشته باشیم. برای جزئیات بیشتر به [پاپاورهای تو در تو](/en-US/docs/Web/API/Popover_API/Using#nested_popovers) مراجعه کنید.

این پاپاورها را می‌توان با JavaScript هم کنترل کرد؛ مثلاً متد `HTMLElement.togglePopover()` برای تغییر وضعیت نمایش و مخفی بودن پاپاور استفاده می‌شود.

در مقابل، پاپاورهای `manual` باید به‌صورت دستی نمایش داده و مخفی شوند. این پاپاورها هنگام نمایش، پاپاورهای دیگر را به‌طور خودکار نمی‌بندند و نمی‌توان آن‌ها را با light dismiss مخفی کرد. بنابراین می‌توان چند پاپاور `manual` را همزمان نمایش داد.

پاپاورهای `hint` هنگام نمایش، پاپاورهای `auto` را نمی‌بندند؛ اما پاپاورهای `hint` دیگری را که در پشته hint جد آن‌ها نیستند، می‌بندند. این پاپاورها را می‌توان light dismiss کرد و به درخواست‌های بستن پاسخ می‌دهند.

معمولاً popover های `hint` در پاسخ به رویدادهای غیرکلیکی جاوااسکریپت مثل [`mouseover`](/en-US/docs/Web/API/Element/mouseover_event)/[`mouseout`](/en-US/docs/Web/API/Element/mouseout_event) و [`focus`](/en-US/docs/Web/API/Element/focus_event)/[`blur`](/en-US/docs/Web/API/Element/blur_event) نمایش داده و پنهان می‌شوند. اگر با کلیک روی دکمه‌ای یک popover از نوع `hint` باز شود، یک popover باز از نوع `auto` به‌صورت light-dismiss بسته می‌شود.

برای اطلاعات بیشتر درباره نحوه استفاده، به صفحه اصلی «Popover API» مراجعه کنید.

## Examples

### ساخت یک عنصر به عنوان popover

کد زیر یک دکمه رندر می‌کند که با فعال شدن، یک عنصر popover را باز می‌کند. این رفتار را می‌توان فقط با HTML پیاده‌سازی کرد.

```html
<button popovertarget="my-popover">Open Popover</button>

<div popover id="my-popover">Greetings, one and all!</div>
```

### popover های تودرتو

در این مثال، یک دکمه یک popover باز می‌کند که شامل popover های تودرتوی دیگری است. این popover ها را می‌توان بدون بستن popover منوی اصلی باز کرد.

#### HTML

در بخش اول HTML، یک {{htmlElement("button")}} می‌سازیم که popover اصلی را باز می‌کند؛ این popover یک منو با چند گزینه است.

```html
<header>
  <button popovertarget="menu">Open Menu</button>
</header>
<main>
  <!--  Page content goes here  -->
</main>
```

در بخش دوم HTML، منوی popover را می‌سازیم که با دکمه بالا باز می‌شود. این منو شامل یک لیست نامرتب از آیتم‌هاست و هر آیتم یک دکمه اطلاعات دارد که یک popover تودرتو را باز می‌کند. منوی اصلی از `popover="auto"` استفاده می‌کند، یعنی با باز شدن popover های تودرتو بسته نخواهد شد.

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

در بخش آخر HTML، popover های اطلاعات مربوط به هر آیتم منو را می‌سازیم. هر کدام از `popover="hint"` استفاده می‌کنند؛ یعنی منوی اصلی را نمی‌بندند، اما سایر popover های اطلاعاتی باز را می‌بندند.

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

برای قرار دادن منوی popover زیر دکمه `<button>` از [anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning) و برای چیدمان آیتم‌های منو و دکمه‌های اطلاعات از [grid](/en-US/docs/Web/CSS/Guides/Grid_layout) استفاده کرده‌ایم.

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

در این‌جا نیز از anchor positioning استفاده کرده‌ایم تا popover های اطلاعات در سمت راست دکمه‌های مربوطه ظاهر شوند.

```markdown
```css
div.info-popover {
  margin: 2rem;
  inset: auto;
  max-width: 300px;
  position-area: right;
}
```

#### نتیجه

برای باز کردن پاپ‌اورها، دکمهٔ _Open Menu_ را کلیک کنید و سپس روی آیکون‌های اطلاعات (ⓘ) کنار گزینه‌های منو بزنید.

> [!NOTE]
> برای دسترسی به مجموعهٔ کامل مثال‌های MDN مربوط به Popover API، به [صفحهٔ نمونه‌های Popover API](https://mdn.github.io/dom-examples/popover-api/) مراجعه کنید.

## همچنین ببینید

- [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget) ویژگی HTML
- [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) ویژگی HTML
```