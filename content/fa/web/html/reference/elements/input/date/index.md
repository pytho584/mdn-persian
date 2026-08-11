---
title: "<input type=\"date\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/date"
translated_by: "n8n + AI"
---

عناصر `<input>` با **`type="date"`** یک فیلد ورودی می‌سازند که کاربر می‌تواند یک تاریخ را وارد کند. ظاهر این فیلد انتخاب تاریخ (date picker) بسته به مرورگر و سیستم‌عامل متفاوت است. مقدار نهایی به فرمت `yyyy-mm-dd` نرمال می‌شود.

مقدار حاصل شامل سال، ماه و روز است، اما _نه_ زمان. نوع‌های ورودی `<input type="time">` و `<input type="datetime-local">` از ورودی زمان و تاریخ+زمان پشتیبانی می‌کنند.

```html
<label for="start">تاریخ شروع:</label>

<input
  type="date"
  id="start"
  name="trip-start"
  value="2018-07-22"
  min="2018-01-01"
  max="2018-12-31" />
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

## مقدار (Value)

یک رشته که تاریخ وارد شده در input را نشان می‌دهد. تاریخ بر اساس [فرمت رشته‌های تاریخ](/en-US/docs/Web/HTML/Guides/Date_and_time_formats#date_strings) قالب‌بندی می‌شود.

می‌توانید یک مقدار پیش‌فرض برای input با استفاده از یک تاریخ درون attribute [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) تنظیم کنید، مثل:

```html
<input type="date" value="2017-06-01" />
```

> **نکته:** فرمت تاریخ نمایش‌داده‌شده با `value` واقعی متفاوت است — تاریخ نمایشی _بر اساس locale مرورگر کاربر_ قالب‌بندی می‌شود، اما `value` تجزیه‌شده همیشه به فرمت `yyyy-mm-dd` است.

می‌توانید مقدار تاریخ را در JavaScript با استفاده از propertyهای `value` و `valueAsNumber` از {{domxref("HTMLInputElement")}} بخوانید و تنظیم کنید. مثلاً:

```js
const dateControl = document.querySelector('input[type="date"]');
dateControl.value = "2017-06-01";
console.log(dateControl.value); // چاپ می‌کند "2017-06-01"
console.log(dateControl.valueAsNumber); // چاپ می‌کند 1496275200000، یک timestamp جاوااسکریپت (ms)
```

این کد اولین عنصر `<input>` را که `type` آن `date` است پیدا می‌کند و مقدار آن را به `2017-06-01` (اول ژوئن ۲۰۱۷) تنظیم می‌کند. سپس آن مقدار را دوباره به صورت رشته و عدد می‌خواند.

## attributeهای اضافی

علاوه بر [attributeهای سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) و [attributeهای input](/en-US/docs/Web/HTML/Reference/Elements/input#attributes) که برای همه عناصر `<input>` مشترک است، input از نوع `date` از attributeهای زیر پشتیبانی می‌کند:

### `max`

آخرین تاریخی که پذیرفته می‌شود. اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) وارد شده در عنصر بعد از این تاریخ باشد، عنصر در [اعتبارسنجی محدودیت‌ها (constraint validation)](/en-US/docs/Web/HTML/Guides/Constraint_validation) رد می‌شود. اگر مقدار attribute `max` یک رشته تاریخ معتبر به فرمت `yyyy-mm-dd` نباشد، عنصر هیچ حداکثر تاریخی ندارد.

اگر هر دو attribute `max` و `min` تنظیم شده باشند، این مقدار باید یک رشته تاریخ **بعد از یا برابر با** مقدار موجود در `min` باشد.

### `min`

اولین تاریخی که پذیرفته می‌شود. اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) وارد شده در عنصر قبل از این تاریخ باشد، عنصر در [اعتبارسنجی محدودیت‌ها (constraint validation)](/en-US/docs/Web/HTML/Guides/Constraint_validation) رد می‌شود. اگر مقدار attribute `min` یک رشته تاریخ معتبر به فرمت `yyyy-mm-dd` نباشد، عنصر هیچ حداقل تاریخی ندارد.

اگر هر دو attribute `max` و `min` تنظیم شده باشند، این مقدار باید یک رشته تاریخ **قبل از یا برابر با** مقدار موجود در `max` باشد.

### `step`

ویژگی `step` عددی است که میزان دانه‌بندی (granularity) مقدار مجاز را مشخص می‌کند، یا مقدار ویژهٔ `any` که در ادامه توضیح داده شده است. تنها مقادیری معتبرند که تعداد صحیحی گام از پایهٔ گام (step base) فاصله داشته باشند. پایهٔ گام همان [`min`](#min) در صورت مشخص شدن، در غیر این صورت [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) و اگر هیچ‌کدام داده نشده باشد، `0` (مبدأ یونیکس، `1970-01-01`) است.

برای ورودی‌های `date`، مقدار `step` بر حسب روز داده می‌شود و به صورت تعداد میلی‌ثانیه‌ای برابر با ۸۶٬۴۰۰٬۰۰۰ برابر مقدار `step` در نظر گرفته می‌شود (مقدار عددی اصلی بر حسب میلی‌ثانیه است). مقدار پیش‌فرض ۱ است که یعنی ۱ روز.

مقدار رشته‌ای `any` به این معنی است که هیچ گام‌بندی‌ای اعمال نمی‌شود و هر مقداری مجاز است (به‌جز محدودیت‌های دیگر مانند [`min`](#min) و [`max`](#max)). در عمل، برای ورودی‌های `date` همان اثر `1` را دارد، زیرا رابط کاربری انتخابگر فقط انتخاب روزهای کامل را امکان‌پذیر می‌کند.

> [!NOTE]
> وقتی داده‌ای که کاربر وارد می‌کند با پیکربندی گام‌بندی مطابقت ندارد، عامل کاربر (user agent) ممکن است مقدار را به نزدیک‌ترین مقدار معتبر گرد کند و اگر دو گزینه به یک اندازه نزدیک باشند، عدد مثبت را ترجیح می‌دهد.

## استفاده از ورودی‌های date

ورودی‌های date رابط ساده‌ای برای انتخاب تاریخ فراهم می‌کنند و قالب داده‌ای که به سرور ارسال می‌شود را مستقل از locale کاربر نرمال‌سازی می‌کنند.

در این بخش، ابتدا کاربردهای پایه و سپس کاربردهای پیچیده‌تر `<input type="date">` را بررسی می‌کنیم.

### کاربردهای پایهٔ date

ساده‌ترین کاربرد `<input type="date">` شامل یک `<input>` به‌همراه عنصر `<label>` است، همان‌طور که در زیر می‌بینید:

```html
<form action="https://example.com">
  <label>
    Enter your birthday:
    <input type="date" name="bday" />
  </label>

  <p><button>Submit</button></p>
</form>
```

این HTML تاریخ واردشده را با کلید `bday` به `https://example.com` ارسال می‌کند و در نتیجه URLای مانند `https://example.com/?bday=1955-06-08` ساخته می‌شود.

### تنظیم حداکثر و حداقل تاریخ

می‌توانید از ویژگی‌های [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) برای محدود کردن تاریخ‌های قابل انتخاب توسط کاربر استفاده کنید. در مثال زیر، حداقل تاریخ `2017-04-01` و حداکثر تاریخ `2017-04-30` را تعیین کرده‌ایم:

```html
<form>
  <label>
    Choose your preferred party date:
    <input type="date" name="party" min="2017-04-01" max="2017-04-30" />
  </label>
</form>
```

نتیجه این است که فقط روزهای آوریل ۲۰۱۷ قابل انتخاب هستند؛ بخش ماه و سال جعبهٔ متن غیرقابل ویرایش می‌شود و تاریخ‌های خارج از آوریل ۲۰۱۷ را نمی‌توان در ویجت انتخابگر انتخاب کرد.

می‌توانید از ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) برای تغییر تعداد روزهایی که هر بار هنگام افزایش تاریخ پرش می‌شود استفاده کنید (مثلاً برای اینکه فقط شنبه‌ها قابل انتخاب باشند).

### کنترل اندازهٔ ورودی

`<input type="date">` از ویژگی‌های اندازه‌گیری فرم مانند [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) پشتیبانی نمی‌کند. برای اندازه‌دهی آن از [CSS](/en-US/docs/Web/CSS) استفاده کنید.

## اعتبارسنجی

به‌طور پیش‌فرض، `<input type="date">` مقدار واردشده را فراتر از قالب آن بررسی نمی‌کند. رابط‌های کاربری معمولاً اجازه نمی‌دهند چیزی غیر از تاریخ وارد کنید — که این خود مفید است.

اگر از [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) برای محدود کردن تاریخ‌های موجود استفاده کنید (به [تنظیم حداکثر و حداقل تاریخ](#setting_maximum_and_minimum_dates) مراجعه کنید)، کنترل فرم تاریخ‌های نامعتبر را غیرفعال می‌کند و اگر بخواهید تاریخی خارج از محدوده ارسال کنید، خطا نشان می‌دهد.

همچنین می‌توانید از ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) استفاده کنید تا پر کردن تاریخ اجباری شود — اگر بخواهید فیلد تاریخ را خالی ارسال کنید، خطایی نمایش داده می‌شود.

بیایید نمونه‌ای از حداقل و حداکثر تاریخ را ببینیم و همچنین یک فیلد را الزامی کنیم:

```html
<form>
  <label>
    Choose your preferred party date (required, April 1st to 20th):
    <input
      type="date"
      name="party"
      min="2017-04-01"
      max="2017-04-20"
      required />
    <span class="validity"></span>
  </label>

  <p>
    <button>Submit</button>
  </p>
</form>
```

اگر فرم را با تاریخ ناقص (یا تاریخی خارج از محدوده تعیین‌شده) ارسال کنید، مرورگر یک خطا نشان می‌دهد. می‌توانید همین حالا با مثال کار کنید.

در اینجا CSS استفاده‌شده در مثال بالا آورده شده است. ما از pseudo-elements `:valid` و `:invalid` برای اضافه‌کردن یک آیکون در کنار input استفاده می‌کنیم تا بر اساس معتبربودن مقدار فعلی، وضعیت را نشان دهد. مجبور شدیم آیکون را روی یک `<span>` در کنار input قرار دهیم، نه خود input، زیرا دست‌کم در Chrome محتوای تولیدی input داخل کنترل فرم قرار می‌گیرد و نمی‌توان آن را به‌درستی استایل داد یا نشان داد.

```css
label {
  display: flex;
  align-items: center;
}

span::after {
  padding-left: 5px;
}

input:invalid + span::after {
  content: "✖";
}

input:valid + span::after {
  content: "✓";
}
```

> [!WARNING]
> اعتبارسنجی سمت کلاینت (client-side form validation) _جایگزین_ اعتبارسنجی روی سرور نیست. به‌راحتی می‌توان HTML را تغییر داد، یا به‌کلی از HTML عبور کرد و داده را مستقیماً به سرور ارسال کرد. اگر سرور داده‌های دریافتی را اعتبارسنجی نکند، ممکن است فاجعه رخ دهد: داده‌هایی با قالب نامناسب، بیش از حد بزرگ، نوع اشتباه و غیره.

## مثال‌ها (Examples)

در این مثال، یک انتخاب‌گر تاریخ با استفاده از `<input type="date">` بومی ایجاد می‌کنیم.

### HTML

کد HTML به این شکل است:

```html
<form>
  <div class="nativeDatePicker">
    <label for="bday">تاریخ تولد خود را وارد کنید:</label>
    <input type="date" id="bday" name="bday" />
    <span class="validity"></span>
  </div>
</form>
```

### CSS

کد CSS به این شکل است:

```css
input:invalid + span::after {
  content: " ✖";
}

input:valid + span::after {
  content: " ✓";
}
```

### نتایج

## خلاصه فنی (Technical summary)

| عنوان | مقدار |
|-------|-------|
| **مقدار (Value)** | یک رشته (string) که تاریخ را در قالب YYYY-MM-DD نشان می‌دهد، یا خالی |
| **رویدادها (Events)** | `change` و `input` |
| **ویژگی‌های مشترک پشتیبانی‌شده** | `autocomplete`، `list`، `readonly`، `step` |
| **ویژگی‌های IDL** | `value`، `valueAsDate`، `valueAsNumber` |
| **DOM interface** | `HTMLInputElement` |
| **نقش ARIA ضمنی** | هیچ نقش متناظری ندارد |

## مشخصات (Specifications)

## سازگاری با مرورگرها (Browser compatibility)

## همچنین ببینید (See also)```

- المان عمومی `<input>` و اینترفیس مورد استفاده برای کار با آن، `HTMLInputElement`
- [آموزش انتخابگر تاریخ و زمان](/en-US/docs/Learn_web_development/Extensions/Forms/HTML5_input_types#date_and_time_pickers)
- [فرمت‌های تاریخ و زمان در HTML](/en-US/docs/Web/HTML/Guides/Date_and_time_formats)