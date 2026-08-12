---
title: <input type="month"> HTML attribute value
source: >-
  https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/month
translated_by: n8n + AI
---

# \<input type="month"> HTML attribute value

````markdown
عناصر `<input>` از نوع **`month`** فیلد ورودی می‌سازند که کاربر بتواند ماه و سال را به‌سادگی وارد کند. مقدار این فیلد رشته‌ای با قالب `YYYY-MM` است که `YYYY` سال چهاررقمی و `MM` شمارهٔ ماه است.

```html interactive-example
<label for="start">Start month:</label>

<input type="month" id="start" name="start" min="2018-03" value="2018-05" />
````

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

رابط کاربری این کنترل به‌طور کلی در مرورگرهای مختلف متفاوت است؛ در حال حاضر پشتیبانی از آن کامل نیست و فقط Chrome/Opera و Edge روی دسکتاپ — و بیشتر مرورگرهای مدرن موبایل — پیاده‌سازی قابل استفاده دارند.

در مرورگرهایی که ورودی `month` را پشتیبانی نمی‌کنند، کنترل به‌صورت خودکار به [`<input type="text">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/text/) تبدیل می‌شود؛ هرچند ممکن است برای اطمینان از قالب‌بندی صحیح متن ورودی، اعتبارسنجی خودکار انجام شود.

اگر از مرورگری استفاده می‌کنید که `month` را پشتیبانی نمی‌کند، تصویر زیر ظاهر این کنترل را در Chrome و Opera نشان می‌دهد. کلیک روی فلشِ رو به پایین در سمت راست، یک انتخاب‌گر تاریخ باز می‌کند که با آن می‌توانید ماه و سال را انتخاب کنید.

کنترل `month` در مایکروسافت اج به این شکل است:

### مقدار

رشته‌ای که مقدار ماه و سال واردشده را نشان می‌دهد، با قالب `YYYY-MM` (سال چهاررقمی یا بیشتر، سپس خط تیره (`-`) و بعد شمارهٔ ماه دو رقمی). قالب رشتهٔ ماه در این نوع ورودی در [رشته‌های ماه](../../../../../../../../en-US/docs/Web/HTML/Guides/Date_and_time_formats/#month_strings) توضیح داده شده است.

#### تنظیم مقدار پیش‌فرض

می‌توانید با قرار دادن ماه و سال در attribute [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) مقدار پیش‌فرضی برای کنترل تنظیم کنید، مانند مثال زیر:

```html
<label for="bday-month">What month were you born in?</label>
<input id="bday-month" type="month" name="bday-month" value="2001-06" />
```

نکته‌ای که باید به آن توجه کنید این است که قالب تاریخ نمایش‌داده‌شده با `value` واقعی فرق دارد؛ بیشتر user agentها ماه و سال را بر اساس locale سیستم‌عامل کاربر و به‌شکلی مناسب برای آن زبان نمایش می‌دهند، در حالی که `value` همیشه با قالب `yyyy-MM` فرمت می‌شود.

برای مثال، وقتی مقدار بالا به سرور ارسال شود، به شکل `bday-month=1978-06` خواهد بود.

#### تنظیم مقدار با JavaScript

همچنین می‌توانید مقدار تاریخ را در جاوااسکریپت با استفاده از property به نام `HTMLInputElement.value` بخوانید و تنظیم کنید، برای مثال:

```html
<label for="bday-month">What month were you born in?</label>
<input id="bday-month" type="month" name="bday-month" />
```

```js
const monthControl = document.querySelector('input[type="month"]');
monthControl.value = "2001-06";
```

### ویژگی‌های اضافی

علاوه بر attributeهای مشترک میان عناصر `<input>`، ورودی‌های `month` این attributeهای زیر را نیز ارائه می‌دهند.

#### list

````

مقادیر attribute `list`، `id` یک عنصر `<datalist>` است که در همان سند (document) قرار دارد.

عنصر `<datalist>` فهرستی از مقادیر از پیش‌تعریف‌شده را ارائه می‌دهد که به کاربر برای این ورودی پیشنهاد می‌شود.
هر مقداری که با [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) سازگار نباشد، در گزینه‌های پیشنهادی قرار نمی‌گیرد.
مقادیر ارائه‌شده فقط پیشنهاد هستند، نه الزام: کاربران می‌توانند از این فهرست از پیش‌تعریف‌شده انتخاب کنند یا مقدار متفاوتی وارد کنند.

### max

آخرین سال و ماه (به فرمت رشته‌ای که در بخش [Value](#value) توضیح داده شد) که قابل قبول است.
اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) وارد شده در عنصر از این مقدار بیشتر باشد، عنصر در [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) شکست می‌خورد.
اگر مقدار attribute `max` یک رشتهٔ معتبر در قالب `yyyy-MM` نباشد، عنصر هیچ مقدار بیشینه‌ای ندارد.

این مقدار باید یک جفت سال-ماه را مشخص کند که دیرتر یا برابر با مقداری باشد که توسط attribute `min` تعیین شده است.

### min

اولین سال و ماه قابل قبول، به همان قالب `yyyy-MM` که در بالا توضیح داده شد.
اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) عنصر کمتر از این مقدار باشد، عنصر در [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) شکست می‌خورد.
اگر مقداری برای `min` مشخص شود که یک رشتهٔ سال و ماه معتبر نباشد، ورودی هیچ مقدار کمینه‌ای ندارد.

این مقدار باید یک جفت سال-ماه باشد که زودتر یا برابر با مقداری است که توسط attribute `max` تعیین شده است.

### readonly

یک Boolean attribute که اگر وجود داشته باشد، به این معنی است که کاربر نمی‌تواند این فیلد را ویرایش کند.
با این حال، `value` آن همچنان می‌تواند توسط کد JavaScript که مستقیماً مقدار property {{domxref("HTMLInputElement.value")}} را تنظیم می‌کند، تغییر داده شود.

> [!NOTE]
> از آنجا که یک فیلد read-only نمی‌تواند مقدار داشته باشد، `required` هیچ تأثیری بر ورودی‌هایی که attribute `readonly` نیز دارند، ندارد.

### step

attribute `step` یک عدد است که دانه‌بندی (granularity) مقداری که باید رعایت شود را مشخص می‌کند، یا مقدار ویژهٔ `any` که در پایین توضیح داده شده است. فقط مقادیری معتبر هستند که تعداد صحیحی از step از step base فاصله داشته باشند. step base برابر [`min`](#min) است اگر مشخص شده باشد، در غیر این صورت [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) است، یا اگر هیچکدام ارائه نشده باشد، `0` (Unix epoch، `1970-01`) است.

برای ورودی‌های `month`، مقدار `step` بر حسب ماه داده می‌شود. مقدار پیش‌فرض `step` برابر ۱ است که نشان‌دهندهٔ ۱ ماه است.

مقدار رشته‌ای `any` به این معنی است که هیچ stepping ای اعمال نمی‌شود و هر مقداری مجاز است (به جز محدودیت‌های دیگر مانند [`min`](#min) و [`max`](#max)). در عمل، برای ورودی‌های `month` همان تأثیر `1` را دارد زیرا UI انتخاب‌گر فقط اجازهٔ انتخاب ماه‌های کامل را می‌دهد.

> [!NOTE]
> وقتی داده‌ای که کاربر وارد می‌کند با پیکربندی stepping مطابقت نداشته باشد، {{Glossary("user agent")}} ممکن است آن را به نزدیک‌ترین مقدار معتبر گرد کند و در صورت وجود دو گزینهٔ به یک اندازه نزدیک، مقادیر مثبت را ترجیح دهد.

## استفاده از ورودی‌های month

ورودی‌های مرتبط با تاریخ (از جمله `month`) در نگاه اول راحت به نظر می‌رسند؛ آنها یک UI آسان برای انتخاب تاریخ وعده می‌دهند و قالب داده‌ای که به سرور ارسال می‌شود را بدون توجه به locale کاربر استاندارد می‌کنند.
با این حال، مشکلاتی با `<input type="month">` وجود دارد زیرا در حال حاضر، بسیاری از مرورگرهای اصلی هنوز از آن پشتیبانی نمی‌کنند.

ما به کاربردهای اولیه و پیچیده‌تر `<input type="month">` نگاه می‌کنیم و سپس در بخش [مدیریت پشتیبانی مرورگر](#handling_browser_support) توصیه‌هایی برای کاهش مشکل پشتیبانی مرورگر ارائه می‌دهیم.

### کاربردهای اولیهٔ month

ساده‌ترین استفاده از `<input type="month">` شامل یک ترکیب اولیه از {{HTMLElement("input")}} و {{htmlelement("label")}} است، همانطور که در زیر می‌بینید:

```html
<form>
  <label for="bday-month">What month were you born in?</label>
  <input id="bday-month" type="month" name="bday-month" />
</form>
````

#### تنظیم حداکثر و حداقل تاریخ

می‌توانید با استفاده از attributeهای [`min`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#min) و [`max`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#max) بازهٔ تاریخ‌هایی را که کاربر می‌تواند انتخاب کند محدود کنید. در مثال زیر، حداقل ماه `1900-01` و حداکثر ماه `2013-12` را مشخص کرده‌ایم:

```html
<form>
  <label for="bday-month">What month were you born in?</label>
  <input
    id="bday-month"
    type="month"
    name="bday-month"
    min="1900-01"
    max="2013-12" />
</form>
```

نتیجه به این صورت است:

* فقط ماه‌های ژانویهٔ ۱۹۰۰ تا دسامبر ۲۰۱۳ قابل انتخاب هستند؛ ماه‌های خارج از این بازه در کنترل قابل اسکرول نیستند.
* بسته به مرورگری که استفاده می‌کنید، ماه‌های خارج از بازهٔ مشخص‌شده ممکن است در انتخابگر ماه قابل انتخاب نباشند (مثلاً در Edge)، یا نامعتبر باشند (به بخش [اعتبارسنجی](index.md#validation) نگاه کنید) اما همچنان در دسترس باشند (مثلاً در Chrome).

#### کنترل اندازهٔ ورودی

`<input type="month">` از attributeهای تنظیم اندازهٔ فرم مانند [`size`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#size) پشتیبانی نمی‌کند. برای اندازه‌دهی باید از [CSS](../../../../../../../../en-US/docs/Web/CSS/) استفاده کنید.

### اعتبارسنجی

به‌طور پیش‌فرض، `<input type="month">` هیچ اعتبارسنجی روی مقادیر واردشده اعمال نمی‌کند. پیاده‌سازی‌های UI معمولاً اجازه نمی‌دهند چیزی غیر از تاریخ وارد کنید — که مفید است — اما همچنان می‌توانید فرم را با ورودی `month` خالی ارسال کنید، یا یک تاریخ نامعتبر وارد کنید (مثلاً ۳۲ آوریل).

برای جلوگیری از این مشکل، می‌توانید از attributeهای [`min`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#min) و [`max`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#max) برای محدود کردن تاریخ‌های موجود استفاده کنید (به بخش [تنظیم حداکثر و حداقل تاریخ](index.md#setting_maximum_and_minimum_dates) مراجعه کنید)، و همچنین از attribute [`required`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#required) استفاده کنید تا پر کردن تاریخ اجباری شود.

در نتیجه، مرورگرهای پشتیبان، اگر بخواهید تاریخی خارج از بازهٔ تعیین‌شده یا یک فیلد تاریخ خالی را ارسال کنید، خطا نمایش می‌دهند.

بیایید مثالی را ببینیم؛ در اینجا حداقل و حداکثر تاریخ را تعیین کرده‌ایم و فیلد را هم اجباری کرده‌ایم:

```html
<form>
  <div>
    <label for="month">
      What month would you like to visit (June to Sept.)?
    </label>
    <input
      id="month"
      type="month"
      name="month"
      min="2022-06"
      max="2022-09"
      required />
    <span class="validity"></span>
  </div>
  <div>
    <input type="submit" value="Submit form" />
  </div>
</form>
```

اگر فرم را بدون مشخص کردن ماه و سال (یا با تاریخی خارج از بازهٔ تعیین‌شده) ارسال کنید، مرورگر خطا نمایش می‌دهد. می‌توانید همین حالا با مثال کار کنید.

برای کسانی که از مرورگر پشتیبان استفاده نمی‌کنند، این یک تصویر از صفحه است:

در اینجا CSS استفاده‌شده در مثال بالا آمده است. ما از شبه‌کلاس‌های `:valid` و `:invalid` برای استایل دادن ورودی بر اساس معتبر بودن یا نبودن مقدار فعلی استفاده می‌کنیم. باید آیکون‌ها را روی یک `<span>` کنار ورودی قرار می‌دادیم، نه روی خود ورودی، زیرا در Chrome محتوای تولیدشده داخل کنترل فرم قرار می‌گیرد و نمی‌توان آن را به‌طور مؤثر استایل داد یا نمایش داد.

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

> \[!WARNING] اعتبارسنجی فرم HTML جایگزینی برای اسکریپت‌هایی نیست که مطمئن می‌شوند داده‌های واردشده در قالب درست هستند. کسی به‌راحتی می‌تواند HTML را تغییر دهد و اعتبارسنجی را دور بزند یا کاملاً حذف کند. همچنین ممکن است کسی HTML شما را به‌طور کامل نادیده بگیرد و داده‌ها را مستقیم به سرور ارسال کند. اگر کد سمت سرور شما داده‌های دریافتی را اعتبارسنجی نکند، با ارسال داده‌های با قالب اشتباه (یا داده‌هایی که خیلی بزرگ هستند، نوع اشتباهی دارند و غیره) ممکن است فاجعه رخ دهد.

### مدیریت پشتیبانی مرورگر

همان‌طور که در بالا اشاره شد، مشکل اصلی استفاده از input های تاریخ در زمان نوشتن این مطلب این است که بسیاری از مرورگرهای اصلی هنوز همه آن‌ها را پیاده‌سازی نکرده‌اند؛ فقط Chrome/Opera و Edge روی دسکتاپ و بیشتر مرورگرهای مدرن روی موبایل از آن‌ها پشتیبانی می‌کنند. برای مثال، انتخابگر `month` در Chrome برای اندروید به این شکل است:

مرورگرهای غیرپشتیبان به‌صورت خودکار به یک input متنی برمی‌گردند؛ اما این موضوع هم از نظر یکپارچگی رابط کاربری (کنترل نمایش‌داده‌شده متفاوت خواهد بود) و هم از نظر مدیریت داده، مشکلاتی ایجاد می‌کند.

مشکل دوم از این دو جدی‌تر است. همان‌طور که قبلاً هم گفته شد، با یک input از نوع `month` مقدار واقعی همیشه به قالب `yyyy-mm` نرمال می‌شود. از طرف دیگر، یک input متنی در پیکربندی پیش‌فرض خود هیچ اطلاعی از قالب مورد انتظار تاریخ ندارد و این به دلیل روش‌های متعددی که مردم برای نوشتن تاریخ استفاده می‌کنند، یک مشکل است. برای مثال:

* `mmyyyy` (072022)
* `mm/yyyy` (07/2022)
* `mm-yyyy` (07-2022)
* `yyyy-mm` (2022-07)
* `Month yyyy` (July 2022)
* و غیره…

یکی از راه‌های حل این مشکل، قرار دادن attribute ی [`pattern`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#pattern) روی input از نوع `month` است. حتی اگر input از نوع `month` از این attribute استفاده نکند، وقتی مرورگر به رفتار با آن مثل input متنی برمی‌گردد، pattern اعمال خواهد شد. برای مثال، دموی زیر را در مرورگری که input از نوع `month` را پشتیبانی نمی‌کند مشاهده کنید:

```html
<form>
  <div>
    <label for="month">
      What month would you like to visit (June to Sept.)?
    </label>
    <input
      id="month"
      type="month"
      name="month"
      min="2022-06"
      max="2022-09"
      required
      pattern="[0-9]{4}-[0-9]{2}" />
    <span class="validity"></span>
  </div>
  <div>
    <input type="submit" value="Submit form" />
  </div>
</form>
```

اگر سعی کنید آن را ارسال کنید، می‌بینید که اگر ورودی با pattern «nnnn-nn» مطابقت نداشته باشد (که در آن n عددی از 0 تا 9 است)، مرورگر پیام خطا نمایش می‌دهد و input را نامعتبر علامت‌گذاری می‌کند. البته این کار مانع وارد کردن تاریخ‌های نامعتبر (مثل `0000-42`) یا تاریخ‌هایی با قالب نادرست که با pattern مطابقت دارند نمی‌شود.

همچنین این مشکل وجود دارد که کاربر لزوماً نمی‌داند کدام‌یک از قالب‌های تاریخ متعدد مورد انتظار است. بنابراین کار بیشتری پیش رو داریم.

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

بهترین راه برای کار با تاریخ در فرم‌ها به‌صورت سازگار با همه مرورگرها (تا زمانی که همه مرورگرهای اصلی مدتی از پشتیبانی این input ها گذشته باشد) این است که از کاربر بخواهید ماه و سال را در کنترل‌های جداگانه وارد کند — مثلاً با استفاده از عنصر `<select>` که رایج است و پیاده‌سازی آن را در پایین می‌بینید — یا از کتابخانه‌های جاوااسکریپت مثل افزونه [jQuery date picker](https://jqueryui.com/datepicker/) استفاده کنید.

### مثال‌ها

در این مثال، دو مجموعه از عناصر رابط کاربری می‌سازیم که هر کدام برای انتخاب ماه و سال توسط کاربر طراحی شده‌اند. اولی یک ورودی `month` بومی است و دومی یک جفت عنصر `select` که امکان انتخاب ماه و سال را به‌صورت مستقل فراهم می‌کنند؛ این کار برای سازگاری با مرورگرهایی است که هنوز از `<input type="month">` پشتیبانی نمی‌کنند.

#### HTML

فرمی که ماه و سال را درخواست می‌کند به این شکل است:

```html
<form>
  <div class="nativeDatePicker">
    <label for="month-visit">What month would you like to visit us?</label>
    <input type="month" id="month-visit" name="month-visit" />
    <span class="validity"></span>
  </div>
  <p class="fallbackLabel">What month would you like to visit us?</p>
  <div class="fallbackDatePicker">
    <div>
      <span>
        <label for="month">Month:</label>
        <select id="month" name="month">
          <option selected>January</option>
          <option>February</option>
          <option>March</option>
          <option>April</option>
          <option>May</option>
          <option>June</option>
          <option>July</option>
          <option>August</option>
          <option>September</option>
          <option>October</option>
          <option>November</option>
          <option>December</option>
        </select>
      </span>
      <span>
        <label for="year">Year:</label>
        <select id="year" name="year"></select>
      </span>
    </div>
  </div>
</form>
```

عنصر `div` با شناسه `nativeDatePicker` از نوع ورودی `month` برای درخواست ماه و سال استفاده می‌کند، در حالی که `div` با شناسه `fallbackDatePicker` به جای آن از یک جفت عنصر `select` استفاده می‌کند. اولی ماه و دومی سال را درخواست می‌کند.

عنصر `<select>` مربوط به انتخاب ماه به‌صورت سخت‌کدشده با نام ماه‌ها پر شده است، چون این نام‌ها تغییر نمی‌کنند (و بحث بومی‌سازی را کنار گذاشته‌ایم). فهرست مقادیر سال به‌صورت پویا بر اساس سال جاری تولید می‌شود (برای توضیحات دقیق درباره نحوه کار این توابع، به کامنت‌های کد زیر مراجعه کنید).

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

#### JavaScript

کد جاوااسکریپتی که انتخاب روش مناسب را مدیریت می‌کند و فهرست سال‌ها را برای عنصر `<select>` سالِ غیربومی می‌سازد، در ادامه آمده است.

بخش جذاب این مثال، کد تشخیص قابلیت (feature detection) است. برای تشخیص اینکه آیا مرورگر از `<input type="month">` پشتیبانی می‌کند، یک عنصر `input` جدید می‌سازیم، سعی می‌کنیم `type` آن را روی `month` تنظیم کنیم و بلافاصله بررسی می‌کنیم که نوع آن چه شده است. مرورگرهایی که از نوع `month` پشتیبانی نمی‌کنند، مقدار `text` برمی‌گردانند، چون ورودی در صورت عدم پشتیبانی به `text` برمی‌گردد. اگر `<input type="month">` پشتیبانی نشود، انتخابگر بومی را مخفی می‌کنیم و به جای آن رابط کاربری جایگزین را نشان می‌دهیم.

```js
// Get UI elements
const nativePicker = document.querySelector(".nativeDatePicker");
const fallbackPicker = document.querySelector(".fallbackDatePicker");
const fallbackLabel = document.querySelector(".fallbackLabel");

const yearSelect = document.querySelector("#year");
const monthSelect = document.querySelector("#month");

// Hide fallback initially
fallbackPicker.style.display = "none";
fallbackLabel.style.display = "none";

// Test whether a new date input falls back to a text input or not
const test = document.createElement("input");

try {
  test.type = "month";
} catch (e) {
  console.log(e.description);
}

// If it does, run the code inside the if () {} block
if (test.type === "text") {
  // Hide the native picker and show the fallback
  nativePicker.style.display = "none";
  fallbackPicker.style.display = "block";
  fallbackLabel.style.display = "block";
}
```

```markdown
// Populate the years dynamically
// (the months are always the same, therefore hardcoded)
populateYears();
}

function populateYears() {
  // Get the current year as a number
  const date = new Date();
  const year = date.getFullYear();

  // Make this year, and the 100 years before it available in the year <select>
  for (let i = 0; i <= 100; i++) {
    const option = document.createElement("option");
    option.textContent = year - i;
    yearSelect.appendChild(option);
  }
}
```

> \[!NOTE] به یاد داشته باشید که برخی سال‌ها ۵۳ هفته دارند (نگاه کنید به [Weeks per year](https://en.wikipedia.org/wiki/ISO_week_date#Weeks_per_year)).\
> هنگام توسعه برنامه‌های واقعی باید این نکته را در نظر بگیرید.

### خلاصه فنی

| [**Value (مقدار)**](index.md#value) | یک رشته (string) که نشان‌دهنده ماه و سال است، یا خالی.                                                                                                                                                                                                                                                                                                                         |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Events (رویدادها)**               | \{{domxref("HTMLElement/change\_event", "change")\}} و \{{domxref("Element/input\_event", "input")\}}                                                                                                                                                                                                                                                                          |
| **ویژگی‌های عمومی پشتیبانی‌شده**    | [`autocomplete`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#autocomplete)، [`list`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#list)، [`readonly`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#readonly)، [`step`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#step) |
| **ویژگی‌های IDL**                   | [`list`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#list)، [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value)، `valueAsDate`، `valueAsNumber`                                                                                                                                                                   |
| **DOM interface (رابط DOM)**        | \{{domxref("HTMLInputElement")\}}                                                                                                                                                                                                                                                                                                                                              |
| **نقش ARIA ضمنی**                   | [بدون نقش متناظر](https://w3c.github.io/html-aria/#dfn-no-corresponding-role)                                                                                                                                                                                                                                                                                                  |

### مشخصات

\{{Specifications\}}

### سازگاری با مرورگرها

\{{Compat\}}

### همچنین ببینید

* عنصر عمومی \{{HTMLElement("input")\}} و رابطی که برای کار با آن استفاده می‌شود: \{{domxref("HTMLInputElement")\}}
* [فرمت‌های تاریخ و زمان در HTML](../../../../../../../../en-US/docs/Web/HTML/Guides/Date_and_time_formats/)
* [آموزش انتخاب‌گر تاریخ و زمان](../../../../../../../../en-US/docs/Learn_web_development/Extensions/Forms/HTML5_input_types/#date_and_time_pickers)
* [`<input type="datetime-local">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/datetime-local/)، [`<input type="date">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/date/)، [`<input type="time">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/time/) و [`<input type="week">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/week/)

```
```
