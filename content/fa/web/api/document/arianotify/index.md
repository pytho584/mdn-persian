---
title: "Document: ariaNotify() method"
short-title: ariaNotify()
slug: Web/API/Document/ariaNotify
page-type: web-api-instance-method
browser-compat: api.Document.ariaNotify
---

{{ApiRef("DOM")}}

متد **`ariaNotify()`** در رابط {{domxref("Document")}} رشته‌ای متنی را برای اعلام شدن توسط یک {{glossary("screen reader")}} در صف قرار می‌دهد.

## Syntax

```js-nolint
ariaNotify(announcement)
ariaNotify(announcement, options)
```

### Parameters

- `announcement`
  - : رشته‌ای که متنی را که باید اعلام شود مشخص می‌کند.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها شامل ویژگی‌های زیر:
    - `priority`
      - : یک مقدار شمارشی که اولویت اعلان را مشخص می‌کند.
        مقادیر ممکن عبارتند از:
        - `normal`
          - : اعلان اولویت عادی دارد.
            پس از هر اعلانی که صفحه‌خوان در حال حاضر بیان می‌کند، خوانده خواهد شد.
            این مقدار پیش‌فرض است.
        - `high`
          - : اعلان اولویت بالایی دارد.
            بلافاصله خوانده می‌شود و هر اعلانی را که صفحه‌خوان در حال حاضر بیان می‌کند قطع می‌کند.

### Return value

هیچ مقداری ({{jsxref("undefined")}}).

## Description

متد **`ariaNotify()`** را می‌توان برای راه‌اندازی برنامه‌ریزی‌شدهٔ اعلان صفحه‌خوان استفاده کرد. این متد کارکردی مشابه [منطقه‌های زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) با چند مزیت فراهم می‌کند:

- منطقه‌های زنده فقط پس از تغییرات DOM می‌توانند اعلان کنند، در حالی که اعلان `ariaNotify()` را می‌توان در هر زمانی صادر کرد.
- اعلان‌های منطقهٔ زنده شامل خواندن محتوای به‌روزشدهٔ گره DOM تغییر یافته هستند، در حالی که محتوای اعلان `ariaNotify()` می‌تواند مستقل از محتوای DOM تعریف شود.

توسعه‌دهندگان اغلب برای دور زدن محدودیت‌های منطقه‌های زنده، از گره‌های DOM پنهانی که منطقهٔ زنده روی آن‌ها تنظیم شده استفاده می‌کنند و محتوای آن‌ها را با متن موردنظر برای اعلان به‌روزرسانی می‌کنند. این کار ناکارآمد و مستعد خطاست و `ariaNotify()` راهی برای جلوگیری از چنین مشکلاتی فراهم می‌کند.

برخی صفحه‌خوان‌ها چند اعلان `ariaNotify()` را به ترتیب می‌خوانند، اما این رفتار در همهٔ صفحه‌خوان‌ها و پلتفرم‌ها تضمین نمی‌شود. معمولاً فقط آخرین اعلان بیان می‌شود. ترکیب چند اعلان در یک اعلان، روش مطمئن‌تری است.

برای مثال، فراخوانی‌های زیر:

```js
document.ariaNotify("Hello there.");
document.ariaNotify("The time is now 8 o'clock.");
```

بهتر است به شکل زیر ترکیب شوند:

```js
document.ariaNotify("Hello there. The time is now 8 o'clock.");
```

اعلان‌های `ariaNotify()` به {{glossary("transient activation")}} نیاز ندارند؛ باید مراقب باشید کاربران صفحه‌خوان را با اعلان‌های زیاد بمباران نکنید، زیرا این کار می‌تواند تجربهٔ کاربری بدی ایجاد کند.

### Announcement priorities

یک اعلان `ariaNotify()` با `priority: high` قبل از یک اعلان `ariaNotify()` با `priority: normal` اعلام می‌شود.

اعلان‌های `ariaNotify()` تقریباً معادل اعلان‌های منطقهٔ زندهٔ ARIA هستند، به این صورت:

- `ariaNotify()` `priority: high`: `aria-live="assertive"`.
- `ariaNotify()` `priority: normal`: `aria-live="polite"`.

با این حال، اعلان‌های `aria-live` بر اعلان‌های `ariaNotify()` اولویت خواهند داشت.

### Language selection

صفحه‌خوان‌ها صدای مناسب برای خواندن اعلان‌های `ariaNotify()` را (از نظر لهجه، تلفظ و غیره) بر اساس زبان مشخص‌شده در ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) عنصر {{htmlelement("html")}} انتخاب می‌کنند؛ و اگر ویژگی `lang` تنظیم نشده باشد، از زبان پیش‌فرض عامل کاربر استفاده می‌شود.

### Permissions policy integration

استفاده از `ariaNotify()` در یک سند یا {{htmlelement("iframe")}} می‌تواند توسط یک [Permission Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) با نام {{httpheader("Permissions-Policy/aria-notify", "aria-notify")}} کنترل شود.

به‌طور مشخص، وقتی یک سیاست تعریف‌شده استفاده را مسدود کند، هر اعلانی که با `ariaNotify()` ساخته شود بی‌صدا رد می‌شود (ارسال نخواهد شد).

## Examples

### Basic `ariaNotify()` usage

این مثال شامل یک {{htmlelement("button")}} است که هنگام کلیک، اعلانی توسط صفحه‌خوان پخش می‌کند.

```html live-sample___basic-arianotify
<button>Press</button>
```

```css hidden live-sample___basic-arianotify
html,
body {
  height: 100%;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

```js live-sample___basic-arianotify
document.querySelector("button").addEventListener("click", () => {
  document.ariaNotify("Hi there, I'm Ed Winchester.");
});
```

#### Result

خروجی به صورت زیر است:

{{EmbedLiveSample("basic-arianotify", "100%", 60, , , , "aria-notify")}}

یک صفحه‌خوان را فعال کنید و دکمه را فشار دهید. باید بشنوید که صفحه‌خوان «Hi there, I'm Ed Winchester.» را می‌خواند.

### Accessible shopping list example

این مثال یک فهرست خرید است که به شما امکان افزودن و حذف اقلام را می‌دهد و هزینهٔ کل همهٔ اقلام را پیگیری می‌کند. وقتی آیتمی اضافه یا حذف می‌شود، صفحه‌خوان‌ها اعلانی را می‌خوانند که می‌گوید چه آیتمی اضافه/حذف شده و جمع کل به‌روزشده چقدر است.

#### HTML

اچ‌تی‌ام‌ال ما شامل یک {{htmlelement("form")}} با دو {{htmlelement("input")}} است — یک ورودی `text` برای وارد کردن نام آیتم و یک ورودی `number` برای وارد کردن قیمت. هر دو ورودی [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) هستند و ورودی `number` دارای مقدار [`step`](/en-US/docs/Web/HTML/Reference/Attributes/step) برابر با `0.01` است تا از وارد شدن مقادیر غیرقیمتی (مانند اعداد اعشاری بزرگ) جلوگیری شود.

در زیر فرم، یک [فهرست بدون ترتیب](/en-US/docs/Web/HTML/Reference/Elements/ul) برای نمایش آیتم‌های اضافه‌شده و یک عنصر {{htmlelement("p")}} برای نمایش هزینهٔ کل داریم.

```html live-sample___shopping-list
<h1><code>ariaNotify</code> demo: shopping list</h1>

<form>
  <div>
    <label for="item">Enter item name</label>
    <input type="text" name="item" id="item" required />
  </div>
  <div>
    <label for="price">Enter item price</label>
    <input type="number" name="price" id="price" step="0.01" required />
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>

<hr />

<ul></ul>

<p>Total: £0.00</p>
```

```css hidden live-sample___shopping-list
html {
  box-sizing: border-box;
  font: 1.2em / 1.5 system-ui;
}

body {
  width: 600px;
  margin: 0 auto;
}

form {
  padding: 0 50px;
}

div {
  display: flex;
  margin-bottom: 20px;
}

label {
  flex: 2;
}

input {
  flex: 4;
  padding: 5px;
}

form button {
  padding: 5px 10px;
  font-size: 1em;
  border-radius: 10px;
  border: 1px solid gray;
}

li {
  margin-bottom: 10px;
}

li button {
  font-size: 0.6rem;
  margin-left: 10px;
}
```

#### JavaScript

اسکریپت ما با چند تعریف ثابت شروع می‌شود که ارجاع‌هایی به `<form>`، دو عنصر `<input>` و عناصر `<ul>` و `<p>` را ذخیره می‌کنند. همچنین یک متغیر `total` برای ذخیرهٔ قیمت کل همهٔ آیتم‌ها داریم.

```js live-sample___shopping-list
const form = document.querySelector("form");
const item = document.querySelector("input[type='text']");
const price = document.querySelector("input[type='number']");
const priceList = document.querySelector("ul");
const totalOutput = document.querySelector("p");

let total = 0;
```

در بلوک کد بعدی، تابعی به نام `updateTotal()` تعریف می‌کنیم که فقط یک کار انجام می‌دهد: قیمت نمایش‌داده‌شده در عنصر `<p>` را به مقدار فعلی متغیر `total` به‌روزرسانی می‌کند:

```js live-sample___shopping-list
function updateTotal() {
  totalOutput.textContent = `Total: £${Number(total).toFixed(2)}`;
}
```

سپس تابعی به نام `addItemToList()` تعریف می‌کنیم. در بدنهٔ تابع ابتدا یک عنصر {{htmlelement("li")}} می‌سازیم تا آیتم تازه‌اضافه‌شده را ذخیره کند. نام و قیمت آیتم را در ویژگی‌های [`data-*`](/en-US/docs/Web/HTML/Reference/Global_attributes/data-*) روی عنصر ذخیره می‌کنیم و متن آن را برابر رشته‌ای شامل آیتم و قیمت قرار می‌دهیم. همچنین یک عنصر {{htmlelement("button")}} با متن «Remove &lt;item-name&gt;» می‌سازیم؛ سپس آیتم فهرست را به فهرست بدون ترتیب و دکمه را به آیتم فهرست اضافه می‌کنیم.

بخش دوم اصلی بدنهٔ تابع، تعریف یک شنوندهٔ رویداد `click` روی دکمه است. وقتی دکمه کلیک می‌شود، ابتدا ارجاعی به گرهٔ والد دکمه — یعنی آیتم فهرستی که داخل آن است — می‌گیریم. سپس عدد موجود در ویژگی `data-price` آیتم فهرست را از متغیر `total` کم می‌کنیم، تابع `updateTotal()` را برای به‌روزرسانی قیمت کل نمایش‌داده‌شده صدا می‌زنیم و سپس `ariaNotify()` را برای اعلام آیتم حذف‌شده و جمع کل جدید فراخوانی می‌کنیم. در نهایت، آیتم فهرست را از DOM حذف می‌کنیم.

```js live-sample___shopping-list
function addItemToList(item, price) {
  const listItem = document.createElement("li");
  listItem.setAttribute("data-item", item);
  listItem.setAttribute("data-price", price);
  listItem.textContent = `${item}: £${Number(price).toFixed(2)}`;
  const btn = document.createElement("button");
  btn.textContent = `Remove ${item}`;

  priceList.appendChild(listItem);
  listItem.appendChild(btn);

  btn.addEventListener("click", (e) => {
    const listItem = e.target.parentNode;
    total -= Number(listItem.getAttribute("data-price"));
    updateTotal();
    document.ariaNotify(
      `${listItem.getAttribute(
        "data-item",
      )} removed. Total is now £${total.toFixed(2)}.`,
      {
        priority: "high",
      },
    );
    listItem.remove();
  });
}
```

آخرین بلوک کد ما یک شنوندهٔ رویداد `submit` به `<form>` اضافه می‌کند. در داخل تابع کنترل‌کننده، ابتدا {{domxref("Event.preventDefault", "preventDefault()")}} را روی شیء رویداد صدا می‌زنیم تا از ارسال فرم جلوگیری شود. سپس `addItemToList()` را برای نمایش آیتم جدید و قیمتش در فهرست فراخوانی می‌کنیم، قیمت را به متغیر `total` اضافه می‌کنیم، `updateTotal()` را برای به‌روزرسانی جمع کل نمایش‌داده‌شده صدا می‌زنیم و سپس `ariaNotify()` را برای اعلام آیتم اضافه‌شده و جمع کل جدید فراخوانی می‌کنیم. در پایان، مقادیر فعلی فیلدهای ورودی را پاک می‌کنیم تا برای افزودن آیتم بعدی آماده شوند.

```js live-sample___shopping-list
form.addEventListener("submit", (e) => {
  e.preventDefault();

  addItemToList(item.value, price.value);
  total += Number(price.value);
  updateTotal();

  document.ariaNotify(
    `Item ${item.value}, price £${
      price.value
    }, added to list. Total is now £${total.toFixed(2)}.`,
    {
      priority: "high",
    },
  );

  item.value = "";
  price.value = "";
});
```

#### Result

خروجی به صورت زیر است:

{{EmbedLiveSample("shopping-list", "100%", 500, , , , "aria-notify")}}

یک صفحه‌خوان را فعال کنید و چند آیتم اضافه و حذف کنید. باید بشنوید که توسط صفحه‌خوان اعلام می‌شوند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Element.ariaNotify()")}}
- [ARIA live regions](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions)