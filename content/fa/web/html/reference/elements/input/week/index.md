---
title: <input type="week"> HTML attribute value
source: >-
  https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/week
translated_by: n8n + AI
---

# \<input type="week"> HTML attribute value

**عنصر `<input>` از نوع `week`** فیلدهای ورودی ایجاد می‌کند که ورود سال و شماره هفته (بر اساس استاندارد ISO 8601) را آسان می‌سازد – یعنی هفته ۱ تا ۵۲ یا ۵۳.

```html
<label for="camp-week">Choose a week in May or June:</label>

<input
  type="week"
  name="week"
  id="camp-week"
  min="2018-W18"
  max="2018-W26"
  required />
```

```css
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

ظاهر این کنترل در مرورگرهای مختلف متفاوت است. در حال حاضر پشتیبانی بین مرورگرها محدود است و تنها Chrome/Opera و Microsoft Edge از آن پشتیبانی می‌کنند. در مرورگرهای پشتیبان‌نشده، این کنترل به صورت خودکار به `<input type="text">` کاهش می‌یابد.

### مقدار (value)

یک رشته که مقدار هفته/سال وارد شده را نمایش می‌دهد. قالب مقدار تاریخ و زمان این نوع input در [رشته‌های هفته](../../../../../../../../en-US/docs/Web/HTML/Guides/Date_and_time_formats/#week_strings) توضیح داده شده است.

می‌توانید یک مقدار پیش‌فرض برای input با قرار دادن مقداری در attribute [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) تعیین کنید، مثلاً:

```html
<label for="week">What week would you like to start?</label>
<input id="week" type="week" name="week" value="2017-W01" />
```

نکته مهم: قالبی که نمایش داده می‌شود ممکن است با `value` واقعی متفاوت باشد. `value` همیشه به صورت `yyyy-Www` قالب‌بندی می‌شود. مثلاً مرورگر ممکن است مقدار بالا را به صورت `Week 01, 2017` نمایش دهد، اما مقدار ارسالی به سرور همیشه `week=2017-W01` خواهد بود.

همچنین می‌توانید مقدار را در JavaScript با استفاده از property \{{domxref("HTMLInputElement.value", "value")\}} عنصر input بخوانید یا تنظیم کنید:

```js
const weekControl = document.querySelector('input[type="week"]');
weekControl.value = "2017-W45";
```

### ویژگی‌های اضافی

علاوه بر ویژگی‌های مشترک عنصر \{{HTMLElement("input")\}}، ورودی‌های week ویژگی‌های زیر را دارند.

#### max

آخرین (از نظر زمانی) سال و شماره هفته، به رشته‌ای که در بخش [مقدار](index.md#value) توضیح داده شد. اگر [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) وارد شده از این مقدار بیشتر باشد، عنصر در [اعتبارسنجی محدودیت](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) شکست می‌خورد. اگر مقدار `max` یک رشته هفته معتبر نباشد، عنصر حداکثر مقداری نخواهد داشت.

این مقدار باید بزرگ‌تر یا مساوی سال و هفته تعیین‌شده در ویژگی `min` باشد.

#### min

اولین سال و هفته‌ای که پذیرفته می‌شود. اگر [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) عنصر کمتر از این مقدار باشد، عنصر در [اعتبارسنجی محدودیت](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) ناموفق خواهد بود. اگر برای `min` مقداری تعیین شود که رشته‌ی هفته‌ی معتبری نباشد، ورودی هیچ حداقل مقداری نخواهد داشت.

این مقدار باید کمتر یا مساوی مقدار ویژگی `max` باشد.

#### readonly

یک ویژگی Boolean که اگر وجود داشته باشد، به این معنی است که کاربر نمی‌تواند این فیلد را ویرایش کند. با این حال، مقدار `value` آن همچنان می‌تواند توسط کد جاوااسکریپت با تنظیم مستقیم ویژگی `value` در `HTMLInputElement` تغییر کند.

> \[!NOTE] از آنجا که یک فیلد read-only نمی‌تواند مقداری داشته باشد، `required` هیچ اثری بر ورودی‌هایی که ویژگی `readonly` نیز دارند ندارد.

#### step

ویژگی `step` عددی است که میزان دانه‌بندی (granularity) مقداری که باید رعایت شود را مشخص می‌کند. همچنین می‌تواند مقدار ویژه‌ی `any` باشد که در ادامه توضیح داده شده است. فقط مقادیری معتبر هستند که مضربی صحیح از step نسبت به پایه‌ی step باشند. پایه‌ی step برابر است با [`min`](index.md#min) اگر مشخص شده باشد، در غیر این صورت [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value)، و اگر هیچ‌کدام مشخص نشده باشد، ‎−259,200,000 (آغاز هفته‌ی `1970-W01`).

برای ورودی‌های `week`، مقدار `step` به هفته داده می‌شود و به عنوان تعداد میلی‌ثانیه برابر با ۶۰۴,۸۰۰,۰۰۰ بار مقدار `step` در نظر گرفته می‌شود (مقدار عددی اصلی بر حسب میلی‌ثانیه است). مقدار پیش‌فرض ۱ است که نشان‌دهنده‌ی یک هفته است.

مقدار رشته‌ای `any` به این معنی است که هیچ گام (step) اجباری نیست و هر مقداری مجاز است (به جز سایر محدودیت‌ها مثل [`min`](index.md#min) و [`max`](index.md#max)). در عمل، برای ورودی‌های `week` همان اثر `1` را دارد، زیرا رابط کاربری انتخابگر فقط انتخاب هفته‌های کامل را اجازه می‌دهد.

> \[!NOTE] وقتی داده‌ی واردشده توسط کاربر با پیکربندی گام مطابقت نداشته باشد، عامل کاربر (user agent) ممکن است مقدار را به نزدیک‌ترین مقدار معتبر گرد کند و در صورت وجود دو گزینه‌ی به یک اندازه نزدیک، اعداد مثبت را ترجیح دهد.

### استفاده از ورودی‌های week

ورودی‌های week در نگاه اول راحت به نظر می‌رسند، زیرا رابط کاربری ساده‌ای برای انتخاب هفته فراهم می‌کنند و فرمت داده‌ای را که به سرور ارسال می‌شود، بدون توجه به مرورگر یا locale کاربر، نرمال می‌کنند. با این حال، مشکلاتی با `<input type="week">` وجود دارد زیرا پشتیبانی مرورگرها در همه‌ی مرورگرها تضمین‌شده نیست.

ما به کاربردهای پایه و پیچیده‌تر `<input type="week">` خواهیم پرداخت و سپس پیشنهادهایی برای کاهش مشکل پشتیبانی مرورگر ارائه خواهیم داد (به [مدیریت پشتیبانی مرورگر](index.md#handling_browser_support) مراجعه کنید).

#### کاربردهای پایه‌ی week

ساده‌ترین استفاده از `<input type="week">` شامل یک `<input>` ساده به همراه یک عنصر `<label>` است، همان‌طور که در زیر می‌بینید:

```html
<form>
  <label for="week">What week would you like to start?</label>
  <input id="week" type="week" name="week" />
</form>
```

#### کنترل اندازه‌ی ورودی

`<input type="week">` از ویژگی‌های اندازه‌دهی فرم مانند [`size`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#size) پشتیبانی نمی‌کند. برای تنظیم اندازه باید از [CSS](../../../../../../../../en-US/docs/Web/CSS/) استفاده کنید.

#### استفاده از ویژگی step

شما باید بتوانید از ویژگی [`step`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#step) برای تغییر تعداد هفته‌هایی که هنگام افزایش یا کاهش پرش می‌شود استفاده کنید، با این حال به نظر نمی‌رسد که این ویژگی در مرورگرهای پشتیبانی‌کننده اثری داشته باشد.

### اعتبارسنجی

به طور پیش‌فرض، `<input type="week">` هیچ اعتبارسنجی روی مقادیر واردشده اعمال نمی‌کند. پیاده‌سازی‌های رابط کاربری معمولاً اجازه نمی‌دهند چیزی غیر از یک هفته/سال معتبر مشخص کنید که مفید است، اما همچنان امکان ارسال فرم با فیلد خالی وجود دارد. همچنین ممکن است بخواهید محدوده‌ی هفته‌های قابل انتخاب را محدود کنید.

#### تنظیم حداکثر و حداقل هفته‌ها

برای محدود کردن هفته‌های معتبری که کاربر می‌تواند انتخاب کند، می‌توانید از attributeهای [`min`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#min) و [`max`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#max) استفاده کنید. در مثال زیر، مقدار کمینه `Week 01, 2017` و بیشینه `Week 52, 2017` را تنظیم کرده‌ایم:

```html
<form>
  <label for="week">What week would you like to start?</label>
  <input id="week" type="week" name="week" min="2017-W01" max="2017-W52" />
  <span class="validity"></span>
</form>
```

CSS استفاده‌شده در مثال بالا به این صورت است. در اینجا از شبه‌کلاس‌های `:valid` و `:invalid` برای استایل‌دهی به input بر اساس معتبر بودن مقدار فعلی استفاده می‌کنیم. مجبور شدیم آیکون‌ها را روی یک `<span>` در کنار input قرار دهیم، نه روی خود input؛ چون در Chrome محتوای تولیدشده داخل form control قرار می‌گیرد و نمی‌توان آن را به‌طور مؤثر استایل داد یا نمایش داد.

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

نتیجه این است که فقط هفته‌های بین W01 تا W52 در سال 2017 معتبر دیده می‌شوند و در مرورگرهای پشتیبانی‌کننده قابل انتخاب هستند.

#### الزامی کردن مقدار هفته

علاوه بر این، می‌توانید از attribute «required» برای الزامی کردن پر کردن هفته استفاده کنید. در نتیجه، مرورگرهای پشتیبانی‌کننده اگر بخواهید یک فیلد هفتهٔ خالی را ارسال کنید، خطا نمایش می‌دهند.

بیایید به یک مثال نگاه کنیم؛ در اینجا حداقل و حداکثر هفته را تنظیم کرده‌ایم و فیلد را هم الزامی کرده‌ایم:

```html
<form>
  <div>
    <label for="week">What week would you like to start?</label>
    <input
      id="week"
      type="week"
      name="week"
      min="2017-W01"
      max="2017-W52"
      required />
    <span class="validity"></span>
  </div>
  <div>
    <input type="submit" value="Submit form" />
  </div>
</form>
```

اگر فرم را بدون مقدار ارسال کنید، مرورگر خطا نمایش می‌دهد. الان می‌توانید با مثال بازی کنید.

در اینجا یک اسکرین‌شات برای کسانی است که از مرورگر پشتیبانی‌کننده استفاده نمی‌کنند:

> \[!WARNING] اعتبارسنجی فرم HTML جایگزینی برای اسکریپت‌هایی که تضمین می‌کنند دادهٔ واردشده قالب مناسبی دارد، _نیست_. خیلی راحت می‌شود HTML را تغییر داد تا validation دور زده شود یا کاملاً حذف شود. همچنین ممکن است کسی HTML شما را دور بزند و داده را مستقیماً به سرور شما ارسال کند. اگر کد سمت سرور شما نتواند داده‌ای را که دریافت می‌کند اعتبارسنجی کند، ارسال دادهٔ با قالب نامناسب (یا داده‌ای که خیلی بزرگ است، نوع اشتباهی دارد و غیره) می‌تواند فاجعه به بار آورد.

### مدیریت پشتیبانی مرورگرها

همانطور که در بالا اشاره شد، مشکل اصلی استفاده از inputهای week در حال حاضر پشتیبانی مرورگر است: Safari و Firefox در دسکتاپ از آن پشتیبانی نمی‌کنند و نسخه‌های قدیمی IE هم پشتیبانی نمی‌کنند.

پلتفرم‌های موبایل مثل Android و iOS از چنین inputهایی به خوبی استفاده می‌کنند؛ این پلتفرم‌ها کنترل‌های UI تخصصی ارائه می‌دهند که انتخاب مقدار را در محیط لمسی بسیار آسان می‌کند. برای مثال، انتخاب‌گر هفته (`week` picker) در Chrome برای Android به این شکل است:

مرورگرهایی که از این نوع ورودی پشتیبانی نمی‌کنند، به‌صورت خودکار به یک ورودی متنی معمولی برمی‌گردند؛ اما این موضوع هم از نظر سازگاری رابط کاربری (کنترل نمایش‌داده‌شده متفاوت خواهد بود) و هم از نظر پردازش داده، مشکلاتی ایجاد می‌کند.

مشکل دوم جدی‌تر است. همان‌طور که قبلاً اشاره شد، با یک ورودی `week` مقدار واقعی همیشه به قالب `yyyy-Www` نرمال‌سازی می‌شود. وقتی مرورگر به یک ورودی متنی ساده برمی‌گردد، هیچ راهنمایی برای قالب‌بندی صحیح ورودی وجود ندارد و قطعاً این قالب به‌طور شهودی قابل حدس نیست. روش‌های مختلفی برای نوشتن مقادیر هفته وجود دارد؛ مثلاً:

* `Week 1 2017`
* `Jan 2-8 2017`
* `2017-W01`
* و غیره.

بهترین راه برای کار با هفته/سال در فرم‌ها، در حال حاضر و با پشتیبانی همهٔ مرورگرها، این است که کاربر هفته و سال را در کنترل‌های جداگانه وارد کند (مثلاً با عنصر `<select>` که رایج است؛ مثال زیر را ببینید)، یا از کتابخانه‌های جاوااسکریپت مانند [jQuery date picker](https://jqueryui.com/datepicker/) استفاده کنید.

### مثال‌ها

در این مثال، دو مجموعه از عناصر رابط کاربری برای انتخاب هفته ایجاد می‌کنیم: یک انتخابگر بومی با استفاده از `<input type="week">`، و یک مجموعه از دو عنصر `<select>` برای انتخاب هفته/سال در مرورگرهای قدیمی‌تر که از نوع ورودی `week` پشتیبانی نمی‌کنند.

```html
<form>
  <div class="nativeWeekPicker">
    <label for="week">What week would you like to start?</label>
    <input
      id="week"
      type="week"
      name="week"
      min="2017-W01"
      max="2018-W52"
      required />
    <span class="validity"></span>
  </div>
  <p class="fallbackLabel">What week would you like to start?</p>
  <div class="fallbackWeekPicker">
    <div>
      <span>
        <label for="week">Week:</label>
        <select id="fallbackWeek" name="week"></select>
      </span>
      <span>
        <label for="year">Year:</label>
        <select id="year" name="year">
          <option value="2017" selected>2017</option>
          <option value="2018">2018</option>
        </select>
      </span>
    </div>
  </div>
</form>
```

مقادیر هفته به‌صورت پویا توسط کد جاوااسکریپت زیر تولید می‌شوند.

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

بخش دیگری از کد که ممکن است برایتان جالب باشد، کد تشخیص ویژگی (feature detection) است. برای اینکه بفهمیم مرورگر از `<input type="week">` پشتیبانی می‌کند یا نه، یک عنصر جدید `<input>` می‌سازیم، سعی می‌کنیم `type` آن را روی `week` تنظیم کنیم و بلافاصله بررسی می‌کنیم که `type` در نهایت چه مقدار دارد. مرورگرهای غیرپشتیبان مقدار `text` برمی‌گردانند، چون نوع `week` به `text` باز می‌گردد. اگر `<input type="week">` پشتیبانی نشود، انتخابگر بومی را مخفی می‌کنیم و به‌جای آن رابط کاربری جایگزین (عناصر `<select>`) را نشان می‌دهیم.

```js
// Get UI elements
const nativePicker = document.querySelector(".nativeWeekPicker");
const fallbackPicker = document.querySelector(".fallbackWeekPicker");
const fallbackLabel = document.querySelector(".fallbackLabel");

const yearSelect = document.querySelector("#year");
const weekSelect = document.querySelector("#fallbackWeek");

// Hide fallback initially
fallbackPicker.style.display = "none";
fallbackLabel.style.display = "none";

// Test whether a new date input falls back to a text input or not
const test = document.createElement("input");

try {
  test.type = "week";
} catch (e) {
  console.log(e.description);
}
```

اگر شرط درست باشد، کد داخل بلوک `if` اجرا می‌شود:

```js
if (test.type === "text") {
  // Hide the native picker and show the fallback
  nativePicker.style.display = "none";
  fallbackPicker.style.display = "block";
  fallbackLabel.style.display = "block";

  // populate the weeks dynamically
  populateWeeks();
}

function populateWeeks() {
  // Populate the week select with 52 weeks
  for (let i = 1; i <= 52; i++) {
    const option = document.createElement("option");
    option.textContent = i < 10 ? `0${i}` : i;
    weekSelect.appendChild(option);
  }
}
```

> \[!NOTE] به یاد داشته باشید که بعضی سال‌ها ۵۳ هفته دارند (به [Weeks per year](https://en.wikipedia.org/wiki/ISO_week_date#Weeks_per_year) مراجعه کنید). در برنامه‌های واقعی حتماً این نکته را در نظر بگیرید.

### خلاصه فنی

| **مقدار (Value)**                | یک رشته (string) که یک هفته و سال را مشخص می‌کند، یا خالی                                                                                                                                                                                                                                                                                                                      |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **رویدادها (Events)**            | `change` و `input`                                                                                                                                                                                                                                                                                                                                                             |
| **ویژگی‌های عمومی پشتیبانی‌شده** | [`autocomplete`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#autocomplete)، [`list`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#list)، [`readonly`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#readonly)، [`step`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#step) |
| **ویژگی‌های IDL**                | [`list`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#list)، [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value)، `valueAsDate`، `valueAsNumber`                                                                                                                                                                   |
| **DOM interface**                | `HTMLInputElement`                                                                                                                                                                                                                                                                                                                                                             |
| **نقش ARIA ضمنی**                | [نقش متناظر ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role)                                                                                                                                                                                                                                                                                                 |

### مشخصات

### سازگاری با مرورگرها

### همچنین ببینید

* [المان عمومی `<input>`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/) و [interface مربوط به آن، `HTMLInputElement`](../../../../../../../../en-US/docs/Web/API/HTMLInputElement/)
* [فرمت‌های تاریخ و زمان استفاده شده در HTML](../../../../../../../../en-US/docs/Web/HTML/Guides/Date_and_time_formats/)
* [`<input type="datetime-local">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/datetime-local/)، [`<input type="date">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/date/)، [`<input type="time">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/time/) و [`<input type="month">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/month/)
