---
title: "<input type=\"time\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/time"
translated_by: "n8n + AI"
---

عناصر `<input>` از نوع **`time`** (زمان) فیلدهای ورودی ایجاد می‌کنند که کاربر می‌تواند به راحتی یک ساعت (ساعت و دقیقه و به‌صورت اختیاری ثانیه) را وارد کند.

ظاهر رابط کاربری این کنترل به مرورگر و سیستم‌عامل بستگی دارد، اما عملکرد آن در همه‌جا یکسان است. مقدار (value) همیشه به صورت ۲۴ ساعته با فرمت `HH:mm` یا `HH:mm:ss` و با صفرهای ابتدایی ذخیره می‌شود، صرف‌نظر از فرمت ورودی رابط کاربری.

```html interactive-example
<label for="appointment">Choose a time for your meeting:</label>

<input
  type="time"
  id="appointment"
  name="appointment"
  min="09:00"
  max="18:00"
  required />

<small>Office hours are 9am to 6pm</small>
```

```css interactive-example
label {
  display: block;
  font:
    1rem "Fira Sans",
    sans-serif;
}

input,
label {
  margin: 0.4rem 0;
}
```

## ویژگی‌های اضافه (Additional attributes)

علاوه بر ویژگی‌های مشترک بین تمام عناصر `<input>`، ورودی‌های `time` ویژگی‌های زیر را نیز دارند.

> [!NOTE]
> برخلاف بسیاری از انواع داده، مقادیر زمان یک **دامنهٔ دوره‌ای (periodic domain)** دارند؛ یعنی مقادیر به بالاترین مقدار ممکن می‌رسند و سپس دوباره به ابتدا برمی‌گردند. برای مثال، اگر `min` را `14:00` و `max` را `2:00` تعیین کنید، بازهٔ زمانی مجاز از ساعت ۲ بعد از ظهر شروع شده، از نیمه‌شب عبور می‌کند و تا ساعت ۲ بامداد روز بعد ادامه می‌یابد. در بخش [عبور min و max از نیمه‌شب](#making_min_and_max_cross_midnight) بیشتر توضیح داده شده است.

### `list`

مقدار ویژگی `list`، `id` یک عنصر `<datalist>` در همان سند است. این `<datalist>` لیستی از مقادیر ازپیش‌تعریف‌شده را برای پیشنهاد به کاربر فراهم می‌کند. هر مقداری که با [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) همخوانی نداشته باشد در گزینه‌های پیشنهادی نمایش داده نمی‌شود. مقادیر ارائه‌شده فقط پیشنهاد هستند، نه الزام؛ کاربر می‌تواند از این لیست انتخاب کند یا مقدار دیگری وارد کند.

### `max`

یک رشته (string) که آخرین زمان قابل قبول را مشخص می‌کند. این رشته باید با [فرمت مقدار زمان](#time_value_format) که در بالا توضیح داده شد مطابقت داشته باشد. اگر رشته مشخص‌شده یک زمان معتبر نباشد، حداکثر مقداری تنظیم نخواهد شد.

### `min`

یک رشته که اولین زمان قابل قبول را مشخص می‌کند و با [فرمت مقدار زمان](#time_value_format) که پیش‌تر توضیح داده شد ارائه می‌شود. اگر مقدار مشخص‌شده یک رشتهٔ زمانی معتبر نباشد، حداقل مقداری تنظیم نخواهد شد.

### `readonly`

یک ویژگی Boolean که اگر وجود داشته باشد، کاربر نمی‌تواند این فیلد را ویرایش کند. اما همچنان می‌توان مقدار `value` آن را مستقیماً از طریق JavaScript با تنظیم خاصیت `value` روی `HTMLInputElement` تغییر داد.

> [!NOTE]
> از آنجایی که یک فیلد فقط‌خواندنی (read-only) نمی‌تواند مقدار داشته باشد، ویژگی `required` روی ورودی‌هایی که `readonly` نیز دارند اثری ندارد.

### `step`

ویژگی `step` یک عدد است که دانه‌بندی (granularity) مجاز برای مقدار را مشخص می‌کند. همچنین می‌تواند مقدار ویژه `any` باشد که در ادامه توضیح داده می‌شود. فقط مقادیری معتبر هستند که مضرب صحیحی از `step` نسبت به پایهٔ step (step base) باشند. پایهٔ step به ترتیب اولویت برابر است با `min` (اگر مشخص شده باشد)، در غیر این صورت `value`، و اگر هیچ‌کدام مشخص نشده باشند، `0` (`00:00:00`).

برای ورودی‌های `time`، مقدار `step` بر حسب ثانیه داده می‌شود و به عنوان یک عدد میلی‌ثانیه‌ای برابر با ۱۰۰۰ برابر مقدار `step` در نظر گرفته می‌شود (مقدار عددی زیربنایی بر حسب میلی‌ثانیه است). مقدار پیش‌فرض `60` است که به معنی ۱ دقیقه می‌باشد.

مقدار رشته‌ای `any` به این معناست که هیچ گام‌گذاری (stepping) در نظر گرفته نشده و هر مقداری مجاز است (به جز محدودیت‌های دیگر مانند [`min`](#min) و [`max`](#max)). در عمل، این مقدار برای ورودی‌های `time` همان اثر `60` را دارد زیرا رابط کاربری انتخاب‌گر (picker UI) در این حالت فقط امکان انتخاب دقیقه‌های کامل را می‌دهد.

> **نکته:**  
> وقتی داده‌های وارد شده توسط کاربر با پیکربندی گام‌گذاری مطابقت نداشته باشد، user agent ممکن است به نزدیک‌ترین مقدار معتبر گرد کند و در صورت وجود دو گزینه به یک اندازه نزدیک، عدد بزرگ‌تر را ترجیح دهد.

## اعتبارسنجی

به‌طور پیش‌فرض، `<input type="time">` هیچ اعتبارسنجی (validation) روی مقادیر وارد شده اعمال نمی‌کند، جز اینکه رابط کاربری user agent معمولاً به شما اجازه نمی‌دهد چیزی غیر از یک مقدار زمان وارد کنید. این مفید است، اما نمی‌توانید کاملاً به این موضوع تکیه کنید که مقدار یک رشته زمان معتبر باشد، زیرا ممکن است یک رشته خالی (`""`) باشد که مجاز است. برای مثال‌هایی از اعتبارسنجی محدودیت (constraint validation) با استفاده از ویژگی‌های `min`، `max`، `step` و `required`، به بخش [تنظیم حداکثر و حداقل زمان](#setting_maximum_and_minimum_times) مراجعه کنید.

## مثال‌ها

### استفاده‌های پایه از time

ساده‌ترین استفاده از `<input type="time">` شامل یک ترکیب پایه `<input>` و {{htmlelement("label")}} است، مانند زیر:

```html
<form>
  <label for="appointment-time">Choose an appointment time: </label>
  <input id="appointment-time" type="time" name="appointment-time" />
</form>
```

### ایجاد یک رابط انتخاب‌گر زمان

در این مثال، یک عنصر رابط برای انتخاب زمان با استفاده از انتخاب‌گر بومی ساخته شده با `<input type="time">` ایجاد می‌کنیم:

```html
<form>
  <label for="appointment-time">
    Choose an appointment time (opening hours 12:00 to 18:00):
  </label>
  <input
    id="appointment-time"
    type="time"
    name="appointment-time"
    min="12:00"
    max="18:00"
    required />
  <span class="validity"></span>
</form>
```

```css
input[type="time"] {
  width: 100px;
}

input + span {
  padding-right: 30px;
}

input:invalid + span::after {
  position: absolute;
  content: "✖";
  padding-left: 5px;
}

input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
}
```

### کنترل اندازه ورودی

`<input type="time">` از ویژگی‌های اندازه‌دهی فرم مانند [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) پشتیبانی نمی‌کند، زیرا زمان‌ها همیشه تقریباً به یک تعداد کاراکتر هستند. برای نیازهای اندازه‌دهی باید از [CSS](/en-US/docs/Web/CSS) استفاده کنید.

### تنظیم ویژگی value

می‌توانید یک مقدار پیش‌فرض برای ورودی با قرار دادن یک زمان معتبر در ویژگی [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) هنگام ایجاد عنصر `<input>` تعیین کنید، مانند زیر:

```html
<label for="appointment-time">Choose an appointment time: </label>
<input
  id="appointment-time"
  type="time"
  name="appointment-time"
  value="13:30" />
```

### تنظیم مقدار با استفاده از JavaScript

همچنین می‌توانید مقدار زمان را در JavaScript با استفاده از ویژگی `value` {{domxref("HTMLInputElement")}} دریافت و تنظیم کنید، برای مثال:

```js
const timeControl = document.querySelector('input[type="time"]');
timeControl.value = "15:30";
```

### فرمت مقدار زمان

`value` ورودی `time` همیشه در قالب ۲۴ ساعته با صفرهای پیش‌فرض است: `HH:mm`، صرف‌نظر از قالب ورودی که احتمالاً بر اساس locale کاربر (یا user agent) انتخاب می‌شود. اگر زمان شامل ثانیه باشد (به [استفاده از ویژگی step](#using_the_step_attribute) مراجعه کنید)، قالب همیشه `HH:mm:ss` است. می‌توانید درباره فرمت مقدار زمان استفاده شده توسط این نوع ورودی در [رشته‌های زمان](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#time_strings) بیشتر بیاموزید.

در این مثال، می‌توانید مقدار ورودی زمان را با وارد کردن یک زمان و مشاهده تغییر آن پس از آن ببینید.

### نگاهی به HTML

ابتدا ساختار HTML را بررسی می‌کنیم. یک برچسب (`<label>`) و یک ورودی (`<input>`) تعریف کرده‌ایم و یک عنصر `<p>` که شامل یک `<span>` است برای نمایش مقدار ورودی `time`:

```html
<form>
  <label for="startTime">زمان شروع: </label>
  <input type="time" id="startTime" />
  <p>
    مقدار ورودی <code>time</code>:
    <code>"<span id="value">تعریف نشده</span>"</code>.
  </p>
</form>
```

### کد JavaScript

کد JavaScript به ورودی زمان گوش می‌دهد تا رویداد `input` را تشخیص دهد. این رویداد هر بار که محتوای عنصر ورودی تغییر کند، فعال می‌شود. در این لحظه، محتوای `<span>` با مقدار جدید ورودی جایگزین می‌شود.

```js
const startTime = document.getElementById("startTime");
const valueSpan = document.getElementById("value");

startTime.addEventListener("input", () => {
  valueSpan.innerText = startTime.value;
});
```

هنگامی که یک فرم شامل ورودی `time` ارسال می‌شود، مقدار آن قبل از قرار گرفتن در داده‌های فرم کدگذاری می‌شود. داده‌های فرم برای یک ورودی زمان همیشه به شکل `name=HH%3Amm` یا در صورت وجود ثانیه `name=HH%3Amm%3Ass` خواهد بود (برای اطلاعات بیشتر به بخش [استفاده از ویژگی step](#using-the-step-attribute) مراجعه کنید).

### استفاده از ویژگی `step`

با استفاده از ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) می‌توانید مقدار پرش زمانی را هنگام افزایش یا کاهش زمان تغییر دهید (مثلاً طوری که با کلیک روی فلش‌های کوچک، زمان هر بار ۱۰ دقیقه جلو یا عقب برود).

این ویژگی یک عدد صحیح می‌گیرد که تعداد ثانیه‌های افزایش را مشخص می‌کند؛ مقدار پیش‌فرض ۶۰ ثانیه است. با این مقدار پیش‌فرض، بیشتر رابط‌های کاربری مرورگرها ساعت و دقیقه را نشان می‌دهند، اما ثانیه را نمایش نمی‌دهند. اگر ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) را با هر عددی به جز مضرب ۶۰ تنظیم کنید، ثانیه‌ها به رابط کاربری اضافه می‌شوند (البته اگر `min` یا `max` قبلاً ثانیه‌ها را نمایش نداده باشند).

```html
<form>
  <label for="appointment-time">زمان قرار ملاقات را انتخاب کنید: </label>
  <input id="appointment-time" type="time" name="appointment-time" step="2" />
</form>
```

برای مشخص کردن گام بر اساس دقیقه یا ساعت، تعداد دقیقه یا ساعت را بر حسب ثانیه بنویسید؛ مثلاً ۱۲۰ برای ۲ دقیقه، یا ۷۲۰۰ برای ۲ ساعت.

### تنظیم حداقل و حداکثر زمان

با استفاده از ویژگی‌های [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) می‌توانید زمان‌های مجاز را محدود کنید. در مثال زیر حداقل زمان را `12:00` و حداکثر را `18:00` قرار داده‌ایم:

```html
<form>
  <label for="appointment-time">
    زمان قرار ملاقات را انتخاب کنید (ساعت کاری ۱۲:۰۰ تا ۱۸:۰۰):
  </label>
  <input
    id="appointment-time"
    type="time"
    name="appointment-time"
    min="12:00"
    max="18:00" />
  <span class="validity"></span>
</form>
```

### CSS مربوط به مثال بالا

در CSS زیر از شبه‌کلاس‌های `:valid` و `:invalid` برای استایل‌دهی به ورودی بر اساس معتبر بودن مقدار استفاده کرده‌ایم. یک آیکون به عنوان محتوای تولید شده (generated content) روی `<span>` کنار ورودی اضافه می‌کنیم.

```css
div {
  margin-bottom: 10px;
  position: relative;
}

input[type="number"] {
  width: 100px;
}

input + span {
  padding-right: 30px;
}

input:invalid + span::after {
  position: absolute;
  content: "✖";
  padding-left: 5px;
}

input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
}
```

نتیجه این است که:

- فقط زمان‌های بین ۱۲:۰۰ و ۱۸:۰۰ معتبر محسوب می‌شوند؛ زمان‌های خارج از این بازه نامعتبر هستند.

#### عبور `min` و `max` از نیمه‌شب

(در اینجا متن اصلی درباره عبور از نیمه‌شب ادامه دارد که ظاهراً در ورودی شما کامل نیست. اگر نیاز به تکمیل دارید، لطفاً بخش باقی‌مانده را ارائه دهید.)

با تنظیم یک attribute به نام [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) که بزرگ‌تر از attribute مربوط به [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) باشد، محدودهٔ زمانی معتبر از نیمه‌شب عبور کرده و یک بازهٔ زمانی قابل قبول ایجاد می‌کند. این قابلیت در هیچ نوع `input` دیگری پشتیبانی نمی‌شود.

```js
const input = document.createElement("input");
input.type = "time";
input.min = "23:00";
input.max = "01:00";
input.value = "23:59";

if (input.validity.valid && input.type === "time") {
  // <input type=time> reversed range supported
} else {
  // <input type=time> reversed range unsupported
}
```

### الزامی کردن زمان

علاوه بر این، می‌توانید از attribute ای به نام [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) استفاده کنید تا پر کردن فیلد زمان اجباری شود. اگر بخواهید زمانی خارج از محدودهٔ تعیین‌شده یا فیلد خالی را ارسال کنید، مرورگر خطا نمایش می‌دهد.

بیایید یک مثال ببینیم؛ در اینجا حداقل و حداکثر زمان را تعیین کرده‌ایم و فیلد را نیز اجباری کرده‌ایم:

```html
<form>
  <div>
    <label for="appointment-time">
      Choose an appointment time (opening hours 12:00 to 18:00):
    </label>
    <input
      id="appointment-time"
      type="time"
      name="appointment-time"
      min="12:00"
      max="18:00"
      required />
    <span class="validity"></span>
  </div>
  <div>
    <input type="submit" value="Submit form" />
  </div>
</form>
```

اگر فرم را با زمانی ناقص (یا زمانی خارج از محدودهٔ تعیین‌شده) ارسال کنید، مرورگر خطا نمایش می‌دهد. حالا می‌توانید با مثال بالا کار کنید.

> [!WARNING]
> اعتبارسنجی HTML به هیچ وجه جایگزینی برای اسکریپت‌هایی نیست که مطمئن می‌شوند داده واردشده در قالب درست است. خیلی راحت می‌توان HTML را تغییر داد تا اعتبارسنجی دور زده شود یا کاملاً حذف شود. همچنین ممکن است کسی HTML شما را به کلی نادیده بگیرد و داده‌ها را مستقیماً به سرور ارسال کند. اگر کد سمت سرور شما نتواند داده دریافتی را اعتبارسنجی کند، ممکن است فاجعه رخ دهد؛ مثلاً داده‌ای با قالب نادرست، یا داده‌ای که بیش از حد بزرگ است، یا نوع اشتباه دارد، و مواردی از این دست ارسال شود.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="/en-US/docs/Web/HTML/Reference/Elements/input#value">مقدار</a></strong></td>
      <td>یک string نشان‌دهنده زمان، یا خالی.</td>
    </tr>
    <tr>
      <td><strong>رویدادها</strong></td>
      <td>
        <code>change</code> و <code>input</code>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های مشترک پشتیبانی‌شده</strong></td>
      <td>
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete"><code>autocomplete</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#list"><code>list</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#readonly"><code>readonly</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#step"><code>step</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های IDL</strong></td>
      <td>
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#list"><code>list</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#value"><code>value</code></a>,
        <code>valueAsDate</code>,
        <code>valueAsNumber</code>
      </td>
    </tr>
    <tr>
      <td><strong>رابط DOM</strong></td>
      <td><p><code>HTMLInputElement</code></p></td>
    </tr>
    <tr>
      <td><strong>نقش ARIA ضمنی</strong></td>
      <td><a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">no corresponding role</a></td>
    </tr>
  </tbody>
</table>

- [`<input type="date">`](/en-US/docs/Web/HTML/Reference/Elements/input/date)
- [`<input type="datetime-local">`](/en-US/docs/Web/HTML/Reference/Elements/input/datetime-local)
- [`<input type="week">`](/en-US/docs/Web/HTML/Reference/Elements/input/week)
- [`<input type="month">`](/en-US/docs/Web/HTML/Reference/Elements/input/month)
- المان (element) عمومی [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input) و اینترفیس [`HTMLInputElement`](/en-US/docs/Web/API/HTMLInputElement) برای کار با آن
- [قالب‌های تاریخ و زمان در HTML](/en-US/docs/Web/HTML/Guides/Date_and_time_formats)
- [آموزش Date and Time picker](/en-US/docs/Learn_web_development/Extensions/Forms/HTML5_input_types#date_and_time_pickers)