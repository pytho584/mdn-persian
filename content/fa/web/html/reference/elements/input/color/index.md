---
title: "<input type=\"color\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/color"
translated_by: "n8n + AI"
---

# عنصر `<input type="color">`

عنصر‌های `<input>` از نوع **`color`** یک رابط کاربری در اختیار کاربر قرار می‌دهند که به او اجازه می‌دهد یک رنگ را مشخص کند؛ یا با استفاده از رابط انتخاب رنگ بصری، یا با وارد کردن رنگ در یک فیلد متنی با فرمت [مقدار رنگ CSS](/en-US/docs/Web/CSS/Reference/Values/color_value).

نمایش این عنصر ممکن است در مرورگرها و پلتفرم‌های مختلف تفاوت زیادی داشته باشد؛ می‌تواند یک ورودی متنی ساده باشد که به‌صورت خودکار اعتبارسنجی می‌کند تا مطمئن شود اطلاعات رنگ در قالب درست وارد شده است، یا یک انتخاب‌گر رنگ استاندارد پلتفرم، یا نوعی پنجره‌ی انتخاب رنگ سفارشی.

```html interactive-example
<p>Choose your colors:</p>

<div>
  <input type="color" id="foreground" name="foreground" value="#e66465" />
  <label for="foreground">Foreground color</label>
</div>

<div>
  <input
    type="color"
    id="background"
    name="background"
    value="oklab(50% 0.1 0.1 / 0.5)"
    colorspace="display-p3"
    alpha />
  <label for="background">Background color</label>
</div>
```

```css interactive-example
p,
label {
  font:
    1rem "Fira Sans",
    sans-serif;
}

input {
  margin: 0.4rem;
}
```

## مقدار

یک [مقدار رنگ CSS](/en-US/docs/Web/CSS/Reference/Values/color_value).

> [!NOTE]
> در گذشته، فقط رنگ‌های هگزادسیمال پایه (بدون کانال آلفا) مجاز بودند. اکنون هر فرمت رنگ CSS، از جمله رنگ‌های نام‌دار، نمادهای تابعی، و رنگ‌های هگزادسیمال با کانال آلفا قابل استفاده است. اگر `value` حذف شده باشد یا نامعتبر باشد، مقدار پیش‌فرض `#000000` (سیاه) خواهد بود.

## ویژگی‌های اضافی

علاوه بر [ویژگی سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) و [ویژگی‌های input](/en-US/docs/Web/HTML/Reference/Elements/input#attributes) که در همه‌ی عنصرهای `<input>` مشترک است، ورودی `color` از ویژگی‌های زیر نیز پشتیبانی می‌کند:

- `alpha` (آزمایشی)
  - : یک ویژگی [boolean](/en-US/docs/Glossary/Boolean/HTML) است؛ اگر وجود داشته باشد، نشان می‌دهد که کاربر نهایی می‌تواند مؤلفه‌ی آلفای رنگ را تغییر دهد و لازم نیست رنگ کاملاً غیرشفاف باشد.

- `colorspace` (آزمایشی)
  - : فضای رنگی (color space) رنگ را تعریف می‌کند و به رابط کاربری موردنظر برای ویجت انتخاب رنگ اشاره می‌کند. مقادیر قابل شمارش (enumerated) ممکن عبارت‌اند از:
    - `"limited-srgb"`: رنگ در فضای رنگی sRGB قرار دارد. این شامل مقادیر `rgb()`، `hsl()`، `hwb()` و `hex-color` می‌شود. مقدار رنگ به ۸ بیت برای هر مؤلفه‌ی `r`، `g` و `b` محدود می‌شود. این مقدار پیش‌فرض است.
    - `"display-p3"`: [فضای رنگی Display P3](/en-US/docs/Glossary/Color_space#display-p3)، به عنوان مثال `color(display-p3 1.84 -0.19 0.72 / 0.6)`

## استفاده از ورودی‌های color

ورودی‌های نوع `color` ساده هستند، چون تعداد ویژگی‌هایی که پشتیبانی می‌کنند محدود است.

### تنظیم یک رنگ پیش‌فرض

می‌توانید مثال بالا را برای تنظیم یک مقدار پیش‌فرض تغییر دهید، به طوری که انتخاب‌گر رنگ از قبل با رنگ پیش‌فرض پر شده باشد و انتخاب‌گر رنگ (در صورت وجود) نیز به همان رنگ پیش‌فرض اشاره کند.

```html
<input type="color" value="#ff0000" />
<input
  type="color"
  id="body"
  name="body"
  value="oklab(50% 0.1 0.1 / 0.5)"
  colorspace="display-p3"
  alpha />
```

اگر مقدار `value` را مشخص نکنید، یا مقدار نامعتبر باشد و مرورگر از آن پشتیبانی نکند، مقدار پیش‌فرض `#000000` خواهد بود که سیاهِ غیرشفاف است.

### پیگیری تغییر رنگ

مانند سایر انواع `<input>`، دو رویداد برای تشخیص تغییرات مقدار رنگ وجود دارد: `input` و `change`. رویداد `input` هر بار که رنگ تغییر می‌کند، روی المنت `<input>` رخ می‌دهد. رویداد `change` وقتی رخ می‌دهد که کاربر انتخابگر رنگ را ببندد. در هر دو حالت، می‌توانید مقدار جدید المنت را با نگاه‌کردن به [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) تعیین کنید.

در ادامه نمونه‌ای را می‌بینید که تغییرات مقدار رنگ را در طول زمان دنبال می‌کند:

```js
colorPicker.addEventListener("input", updateFirst);
colorPicker.addEventListener("change", watchColorPicker);

function watchColorPicker(event) {
  document.querySelectorAll("p").forEach((p) => {
    p.style.color = event.target.value;
  });
}
```

### انتخاب مقدار

وقتی مرورگر از رابط انتخابگر رنگ پشتیبانی نمی‌کند، پیاده‌سازی inputهای رنگ به صورت جعبه متنی خواهد بود که محتوا را به طور خودکار اعتبارسنجی می‌کند تا مطمئن شود مقدار در قالب درست است. در این حالت می‌توانید از متد `select()` برای انتخاب متن موجود در فیلد ویرایش استفاده کنید.

اگر مرورگر به جای آن از انتخابگر رنگ استفاده کند، `select()` هیچ کاری انجام نمی‌دهد. باید از این رفتار آگاه باشید تا کد شما در هر دو حالت پاسخ مناسب بدهد.

```js
colorPicker.select();
```

## اعتبارسنجی

مقدار یک input از نوع رنگ نامعتبر در نظر گرفته می‌شود اگر عامل کاربر (user agent) نتواند ورودی کاربر را به نماد هگزادسیمال هفت‌کاراکتری با حروف کوچک تبدیل کند. در این صورت، شبه‌کلاس `:invalid` روی المنت اعمال می‌شود.

## مثال

بیایید مثالی بسازیم که با دنبال‌کردن رویدادهای `change` و `input`، کار بیشتری با input رنگ انجام دهد؛ رنگ جدید را گرفته و آن را روی تمام المنت‌های `<p>` در سند اعمال کند.

### HTML

بخش HTML کاملاً ساده است — چند پاراگراف توضیحی به همراه یک `<input>` از نوع `color` با شناسه `color-picker` که از آن برای تغییر رنگ متن پاراگراف‌ها استفاده می‌کنیم.

```html
<p>
  An example demonstrating the use of the
  <code>&lt;input type="color"&gt;</code> control.
</p>

<label for="color-picker">Color:</label>
<input type="color" value="#ff0000" id="color-picker" />

<p>
  Watch the paragraph colors change when you adjust the color picker. As you
  make changes in the color picker, the first paragraph's color changes, as a
  preview (this uses the <code>input</code> event). When you close the color
  picker, the <code>change</code> event fires, and we detect that to change
  every paragraph to the selected color.
</p>
```

### JavaScript

#### مقداردهی اولیه

کد زیر input رنگ را مقداردهی اولیه می‌کند:

```js
const defaultColor = "#0000ff";
const colorPicker = document.querySelector("#color-picker");
colorPicker.value = defaultColor;
colorPicker.addEventListener("input", updateFirst);
colorPicker.addEventListener("change", updateAll);
colorPicker.select();
```

کد بالا ارجاعی از المنت `<input>` رنگ را در متغیری به نام `colorPicker` ذخیره می‌کند، سپس مقدار input رنگ را به مقدار `defaultColor` تنظیم می‌کند. سپس رویداد `input` را به صدا زدن تابع `updateFirst()` و رویداد `change` را به صدا زدن تابع `updateAll()` متصل می‌کند. این توابع را در ادامه خواهید دید.

در نهایت، متد `select()` را صدا می‌زنیم تا محتوای متنی input رنگ انتخاب شود، اگر کنترل به صورت فیلد متنی پیاده‌سازی شده باشد (اگر رابط انتخابگر رنگ ارائه شده باشد، این کار اثری ندارد).

#### واکنش به تغییرات رنگ

ما دو تابع برای مدیریت تغییر رنگ داریم. تابع `updateFirst()` با رویداد `input` فراخوانی می‌شود. این تابع رنگ اولین عنصر پاراگراف در سند را با مقدار جدید ورودی رنگ هماهنگ می‌کند. از آنجایی که رویداد `input` با هر بار تغییر مقدار (مثلاً افزایش روشنایی رنگ) فعال می‌شود، هنگام استفاده از انتخاب‌گر رنگ بارها اجرا خواهد شد.

```js
function updateFirst(event) {
  const p = document.querySelector("p");
  if (p) {
    p.style.color = event.target.value;
  }
}
```

وقتی انتخاب‌گر رنگ بسته شود (یعنی مقدار دیگر تغییر نخواهد کرد مگر اینکه کاربر دوباره آن را باز کند)، یک رویداد `change` به عنصر فرستاده می‌شود. ما این رویداد را با تابع `updateAll()` مدیریت می‌کنیم و با استفاده از [`Event.target.value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) رنگ نهایی انتخاب‌شده را می‌گیریم:

```js
function updateAll(event) {
  document.querySelectorAll("p").forEach((p) => {
    p.style.color = event.target.value;
  });
}
```

این کار رنگ تمام بلوک‌های {{HTMLElement("p")}} را طوری تنظیم می‌کند که ویژگی {{cssxref("color")}} آن‌ها با مقدار جاری ورودی رنگ (که با {{domxref("Event.target", "event.target")}} به آن اشاره می‌کنیم) مطابقت داشته باشد.

### نتیجه

نتیجه نهایی به این شکل است:

{{EmbedLiveSample("Example", 700, 200)}}

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">مقدار (Value)</a></strong></td>
      <td>
        هر مقدار CSS {{cssxref("&lt;color&gt;")}} در هر نمادگذاری
      </td>
    </tr>
    <tr>
      <td><strong>رویدادها (Events)</strong></td>
      <td>
        {{domxref("HTMLElement/change_event", "change")}} و
        {{domxref("Element/input_event", "input")}}
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های عمومی پشتیبانی‌شده</strong></td>
      <td>
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete"><code>autocomplete</code></a> و
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#list"><code>list</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های IDL</strong></td>
      <td>
        <a href="/en-US/docs/Web/API/HTMLInputElement/alpha"><code>alpha</code></a>،
        <a href="/en-US/docs/Web/API/HTMLInputElement/colorSpace"><code>colorSpace</code></a>،
        <a href="/en-US/docs/Web/API/HTMLInputElement/list"><code>list</code></a> و
        <a href="/en-US/docs/Web/API/HTMLInputElement/value"><code>value</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>رابط DOM</strong></td>
      <td><p>{{domxref("HTMLInputElement")}}</p></td>
    </tr>
    <tr>
      <td><strong>نقش ARIA ضمنی</strong></td>
      <td><a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظر ندارد</a></td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref('HTMLInputElement.alpha')}}
- {{domxref('HTMLInputElement.colorspace')}}