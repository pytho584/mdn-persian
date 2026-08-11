---
title: "<input type=\"datetime-local\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/datetime-local"
translated_by: "n8n + AI"
---

elementهای `<input>` از نوع **`datetime-local`** کنترلهای ورودی میسازند که به کاربر اجازه میدهند بهراحتی هم تاریخ و هم زمان را وارد کند؛ شامل سال، ماه، روز و همچنین زمان بر حسب ساعت و دقیقه.

```html interactive-example
<label for="meeting-time">Choose a time for your appointment:</label>

<input
  type="datetime-local"
  id="meeting-time"
  name="meeting-time"
  value="2018-06-12T19:30"
  min="2018-06-07T00:00"
  max="2018-06-14T00:00" />
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

رابط کاربری این کنترل معمولاً از مرورگری به مرورگر دیگر متفاوت است. این کنترل برای نمایش _یک تاریخ و زمان محلی_ طراحی شده است، نه لزوماً _تاریخ و زمان محلی کاربر_. به عبارت دیگر، ورودی هر ترکیب معتبری از سال، ماه، روز، ساعت و دقیقه را میپذیرد — حتی اگر چنین ترکیبی در منطقه زمانی کاربر نامعتبر باشد (مثل آن یک ساعت در فاصله گذار به وقت تابستانی).

## مقدار

یک رشته (string) که مقدار تاریخ واردشده در ورودی را نشان میدهد. قالب مقدار تاریخ و زمان مورد استفاده این نوع ورودی در [رشتههای تاریخ و زمان محلی](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#local_date_and_time_strings) توضیح داده شده است.

میتوانید با قرار دادن یک تاریخ و زمان داخل attribute [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value)، مقدار پیشفرض ورودی را تنظیم کنید، مانند مثال زیر:

```html
<label for="party">Enter a date and time for your party booking:</label>
<input
  id="party"
  type="datetime-local"
  name="party-date"
  value="2017-06-01T08:30" />
```

یک نکته این است که قالب تاریخ و زمان نمایش دادهشده با `value` واقعی متفاوت است؛ تاریخ و زمان نمایش دادهشده بر اساس locale کاربر و همانطور که سیستمعامل او گزارش میدهد قالببندی میشود، در حالی که `value` تاریخ/زمان همیشه با قالب `YYYY-MM-DDTHH:mm` است. برای مثال، وقتی مقدار بالا به سرور ارسال شود، به این شکل خواهد بود: `party-date=2024-06-01T08:30`.

> [!NOTE]
> همچنین به خاطر داشته باشید که اگر چنین دادههایی از طریق HTTP [`GET`](/en-US/docs/Web/HTTP/Reference/Methods/GET) ارسال شوند، کاراکتر دو نقطه باید برای قرارگیری در پارامترهای URL escape شود، مثلاً `party-date=2024-06-01T08%3A30`. برای یکی از راههای انجام این کار، `encodeURI()` را ببینید.

همچنین میتوانید مقدار تاریخ را در JavaScript با استفاده از property `value` در `HTMLInputElement` بخوانید و تنظیم کنید، برای مثال:

```js
const dateControl = document.querySelector('input[type="datetime-local"]');
dateControl.value = "2017-06-01T08:30";
```

## ویژگیهای اضافی

علاوه بر attributeهای مشترک بین همه elementهای `<input>`، ورودیهای `datetime-local` attributeهای زیر را ارائه میدهند.

### max

آخرین تاریخ و زمانی که پذیرفته میشود. اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) واردشده در element دیرتر از این timestamp باشد، element در [اعتبارسنجی محدودیتها](/en-US/docs/Web/HTML/Guides/Constraint_validation) ناموفق میشود. اگر مقدار attribute `max` یک رشته معتبر نباشد که از قالب `YYYY-MM-DDTHH:mm` پیروی کند، element حداکثر مقداری نخواهد داشت.

این مقدار باید یک رشته تاریخ را مشخص کند که دیرتر یا برابر با رشتهای باشد که توسط attribute `min` تعیین شده است.

### min

قدیمی‌ترین تاریخ و زمانی که پذیرفته می‌شود؛ زمان‌هایی که زودتر از این باشند باعث می‌شوند عنصر در [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) شکست بخورد. اگر مقدار ویژگی `min` یک رشتهٔ معتبر با فرمت `YYYY-MM-DDTHH:mm` نباشد، عنصر حداقل مقدار نخواهد داشت.

این مقدار باید تاریخ و زمانی را مشخص کند که زودتر یا برابر با مقدار مشخص‌شده در ویژگی `max` باشد.

### step

ویژگی `step` عددی است که دانه‌بندی (granularity) موردنیاز برای مقدار را مشخص می‌کند، یا مقدار ویژهٔ `any` که در ادامه توضیح داده می‌شود. فقط مقادیری معتبر هستند که تعداد صحیحی قدم از مبدأ قدم داشته باشند. مبدأ قدم (step base) اگر مشخص شده باشد [`min`](#min) است، در غیر این صورت [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) و اگر هیچ‌کدام وجود نداشته باشد، `0` (مبدأ یونیکس، `1970-01-01T00:00`) خواهد بود.

برای ورودی‌های `datetime-local`، مقدار `step` بر حسب ثانیه داده می‌شود و به‌صورت تعداد میلی‌ثانیه‌ای برابر با ۱۰۰۰ برابر مقدار `step` در نظر گرفته می‌شود (مقدار عددی اصلی بر حسب میلی‌ثانیه است). مقدار پیش‌فرض ۶۰ است که یعنی ۱ دقیقه.

مقدار رشته‌ای `any` به این معناست که هیچ گامی اعمال نمی‌شود و هر مقداری مجاز است (به‌جز محدودیت‌های دیگر مانند [`min`](#min) و [`max`](#max)). در عمل، برای ورودی‌های `datetime-local` اثر آن همانند `60` است، زیرا رابط کاربری انتخابگر در این حالت فقط انتخاب دقیقه‌های کامل را امکان‌پذیر می‌کند.

> [!NOTE]
> هنگامی که دادهٔ واردشده توسط کاربر با پیکربندی گام مطابقت نداشته باشد، user agent ممکن است مقدار را به نزدیک‌ترین مقدار معتبر گرد کند و در صورت وجود دو گزینه به یک اندازه نزدیک، عدد مثبت را ترجیح دهد.

## استفاده از ورودی‌های datetime-local

ورودی‌های تاریخ/زمان برای توسعه‌دهنده راحت هستند؛ آن‌ها یک رابط کاربری ساده برای انتخاب تاریخ و زمان فراهم می‌کنند و قالب دادهٔ ارسالی به سرور را بدون توجه به locale کاربر نرمال‌سازی می‌کنند. با این حال، مهم است که کاربران خود را در نظر بگیرید. از کاربران نخواهید داده‌هایی را وارد کنند که برای کار کردن برنامهٔ شما لازم نیستند.

### کنترل اندازهٔ ورودی

`<input type="datetime-local">` از ویژگی‌های اندازه‌گذاری کنترل فرم مانند [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) پشتیبانی نمی‌کند. برای سفارشی‌سازی اندازهٔ این عناصر باید از [CSS](/en-US/docs/Web/CSS) استفاده کنید.

### تنظیم منطقه زمانی

یکی از چیزهایی که نوع ورودی `datetime-local` فراهم نمی‌کند، راهی برای تنظیم منطقه زمانی (time zone) و/یا locale کنترل تاریخ/زمان است. این امکان در نوع ورودی `datetime` وجود داشت، اما این نوع اکنون منسوخ شده و از مشخصات حذف شده است. دلایل اصلی این حذف، عدم پیاده‌سازی در مرورگرها و نگرانی‌های مربوط به رابط کاربری/تجربه کاربری بود. ساده‌تر است که فقط یک کنترل (یا چند کنترل) برای تنظیم تاریخ/زمان داشته باشید و سپس locale را در یک کنترل جداگانه مدیریت کنید.

برای مثال، اگر سیستمی می‌سازید که کاربر به احتمال زیاد از قبل وارد شده و localeاش از قبل تنظیم شده است، می‌توانید منطقه زمانی را در یک ورودی با نوع [`hidden`](/en-US/docs/Web/HTML/Reference/Elements/input/hidden) قرار دهید. برای مثال:

```html
<input type="hidden" id="timezone" name="timezone" value="-08:00" />
```

از طرف دیگر، اگر لازم بود به کاربر اجازه دهید منطقه زمانی را همراه با ورودی تاریخ/زمان وارد کند، می‌توانید از یک عنصر `select` استفاده کنید تا کاربر با انتخاب یک مکان خاص از میان مجموعه‌ای از مکان‌ها، منطقه زمانی درست را تنظیم کند:

```html
<select name="timezone" id="timezone">
  <option value="Pacific/Kwajalein">Eniwetok, Kwajalein</option>
  <option value="Pacific/Midway">Midway Island, Samoa</option>
  <option value="Pacific/Honolulu">Hawaii</option>
  <option value="Pacific/Marquesas">Taiohae</option>
  <!-- and so on -->
</select>
```

در هر دو حالت، مقادیر تاریخ/زمان و منطقه زمانی به‌صورت داده‌های جداگانه به سرور ارسال می‌شوند و سپس باید آن‌ها را به‌طور مناسب در پایگاه داده سمت سرور ذخیره کنید.

## اعتبارسنجی

پیش‌فرضاً، `<input type="datetime-local">` هیچ‌گونه اعتبارسنجی روی مقادیر واردشده اعمال نمی‌کند. پیاده‌سازی‌های رابط کاربری معمولاً اجازه نمی‌دهند چیزی غیر از تاریخ/ساعت وارد شود – که مفید است – اما کاربر ممکن است مقدار را خالی بگذارد و فرم را ارسال کند، یا تاریخ و/یا ساعت نامعتبری وارد کند (مثلاً ۳۲ آوریل).

می‌توانید از [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) برای محدود کردن تاریخ‌های قابل انتخاب استفاده کنید (به بخش [تنظیم حداکثر و حداقل تاریخ و زمان](#setting_maximum_and_minimum_dates_and_times) مراجعه کنید)، و از ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) برای اجباری کردن پر کردن تاریخ/ساعت بهره ببرید. در نتیجه، اگر تلاش کنید تاریخ خارج از محدوده یا فیلد خالی را ارسال کنید، مرورگر یک خطا نمایش می‌دهد.

بیایید یک مثال ببینیم؛ در اینجا مقادیر حداقل و حداکثر تاریخ/ساعت را تنظیم کرده‌ایم و فیلد را هم اجباری کرده‌ایم:

```html
<form>
  <div>
    <label for="party">
      Choose your preferred party date and time (required, June 1st 8.30am to
      June 30th 4.30pm):
    </label>
    <input
      id="party"
      type="datetime-local"
      name="party-date"
      min="2017-06-01T08:30"
      max="2017-06-30T16:30"
      required />
    <span class="validity"></span>
  </div>
  <div>
    <input type="submit" value="Book party!" />
  </div>
</form>
```

اگر فرم را با تاریخ ناقص (یا خارج از محدوده تعیین‌شده) ارسال کنید، مرورگر خطا نشان می‌دهد. می‌توانید همین حالا با مثال بالا کار کنید.

در اینجا CSS استفاده‌شده در مثال بالا آمده است. از ویژگی‌های CSS به نام `:valid` و `:invalid` برای استایل‌دهی به input بر اساس معتبر بودن مقدار فعلی استفاده کرده‌ایم. آیکون‌ها را روی یک `<span>` در کنار input قرار داده‌ایم.

```css
div {
  margin-bottom: 10px;
  display: flex;
  align-items: center;
}

label {
  display: inline-block;
  width: 300px;
}

input:invalid + span::after {
  content: "✖";
  padding-left: 5px;
}

input:valid + span::after {
  content: "✓";
  padding-left: 5px;
}
```

> [!WARNING]
> HTML form validation جایگزین اسکریپت‌هایی نیست که اطمینان حاصل کنند داده‌های واردشده در قالب صحیح هستند. تغییر دادن HTML برای دور زدن اعتبارسنجی یا حذف کامل آن، کار بسیار ساده‌ای است. همچنین کسی می‌تواند HTML شما را دور بزند و داده‌ها را مستقیماً به سرور شما ارسال کند. اگر کد سمت سرور شما داده‌های دریافتی را اعتبارسنجی نکند، ممکن است با ارسال داده‌هایی با فرمت نادرست (یا داده‌های خیلی بزرگ، از نوع اشتباه و غیره) مشکلاتی به وجود آید.

> [!NOTE]
> در یک input از نوع `datetime-local`، مقدار تاریخ همیشه به فرمت `YYYY-MM-DDTHH:mm` نرمال‌سازی می‌شود.

## مثال‌ها

### استفاده پایه از datetime-local

ساده‌ترین استفاده از `<input type="datetime-local">` شامل یک `<input>` پایه و یک عنصر `<label>` است، مانند زیر:

```html
<form>
  <label for="party">Enter a date and time for your party booking:</label>
  <input id="party" type="datetime-local" name="party-date" />
</form>
```

### تنظیم حداکثر و حداقل تاریخ و زمان

می‌توانید از ویژگی‌های [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) برای محدود کردن تاریخ/ساعت‌های قابل انتخاب توسط کاربر استفاده کنید. در مثال زیر، حداقل datetime را `2025-06-01T08:30` و حداکثر datetime را `2025-06-30T16:30` تنظیم کرده‌ایم:

```html
<form>
  <label for="party">Enter a date and time for your party booking:</label>
  <input
    id="party"
    type="datetime-local"
    name="party-date"
    min="2025-06-01T08:30"
    max="2025-06-30T16:30" />
</form>
```

تنها روزهای ژوئن ۲۰۲۵ قابل انتخاب هستند. بسته به مرورگر شما، زمان‌های خارج از محدوده مشخص شده ممکن است قابل انتخاب نباشند. در مرورگرهای دیگر، تاریخ‌ها و زمان‌های نامعتبر قابل انتخاب هستند اما با شبه‌کلاس‌های `:invalid` و `:out-of-range` مطابقت داشته و در [اعتبارسنجی](#validation) شکست می‌خورند.

در برخی مرورگرها (مثل Safari)، انتخاب‌گر تاریخ به نظر می‌رسد که هر تاریخی را مجاز می‌کند، اما مقدار پس از انتخاب به محدوده معتبر محدود می‌شود.

محدوده معتبر شامل تمام زمان‌های بین مقادیر `min` و `max` است؛ زمان روز فقط در اولین و آخرین تاریخ محدوده محدود می‌شود.

> [!NOTE]
> باید بتوانید از ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) برای تغییر تعداد روزهایی که每次 افزایش تاریخ پرش می‌کند استفاده کنید (مثلاً شاید فقط بخواهید شنبه‌ها قابل انتخاب باشند). اما در زمان نگارش این متن، این ویژگی در هیچ پیاده‌سازی به طور مؤثر کار نمی‌کند.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">مقدار</a></strong></td>
      <td>یک رشته که نمایانگر یک تاریخ و زمان (در منطقه زمانی محلی) است، یا خالی.</td>
    </tr>
    <tr>
      <td><strong>رویدادها</strong></td>
      <td>رویدادهای <code>change</code> و <code>input</code></td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های رایج پشتیبانی‌شده</strong></td>
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
      <td><code>HTMLInputElement</code></td>
    </tr>
    <tr>
      <td><strong>نقش ARIA ضمنی</strong></td>
      <td>نقش متناظری ندارد</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- عنصر عمومی `<input>` و رابط مورد استفاده برای دستکاری آن، `HTMLInputElement`
- [`<input type="date">`](/en-US/docs/Web/HTML/Reference/Elements/input/date) و [`<input type="time">`](/en-US/docs/Web/HTML/Reference/Elements/input/time)
- [قالب‌های تاریخ و زمان استفاده شده در HTML](/en-US/docs/Web/HTML/Guides/Date_and_time_formats)
- [آموزش انتخاب‌گر تاریخ و زمان](/en-US/docs/Learn_web_development/Extensions/Forms/HTML5_input_types#date_and_time_pickers)