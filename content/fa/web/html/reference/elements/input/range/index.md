---
title: "<input type=\"range\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/range"
translated_by: "n8n + AI"
---

عنصرهای `<input>` از نوع **`range`** به کاربر اجازه میدهند یک مقدار عددی مشخص کند که نباید از یک مقدار معین کمتر و از مقدار معین دیگری بیشتر باشد. با این حال، مقدار دقیق اهمیت چندانی ندارد. این کنترل معمولاً به‌صورت لغزنده (slider) یا چرخاننده (dial) نمایش داده می‌شود، نه به‌صورت جعبه ورود متن مثل نوع ورودی `number`.

چون این نوع ویجت دقیق نیست، فقط باید زمانی استفاده شود که مقدار دقیق کنترل مهم نیست.

```html interactive-example
<p>Audio settings:</p>

<div>
  <input type="range" id="volume" name="volume" min="0" max="11" />
  <label for="volume">Volume</label>
</div>

<div>
  <input
    type="range"
    id="cowbell"
    name="cowbell"
    min="0"
    max="100"
    value="90"
    step="10" />
  <label for="cowbell">Cowbell</label>
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

اگر مرورگر کاربر از نوع `range` پشتیبانی نکند، آن را به‌عنوان یک ورودی `text` در نظر می‌گیرد.

## مقدار

مقدار یک `<input type="range">` با استفاده از attribute «[`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value)» تنظیم می‌شود که یک رشته شامل عدد انتخاب‌شده را می‌پذیرد. این مقدار هرگز رشته خالی (`""`) نیست. مقدار پیش‌فرض، نقطه وسط بین حداقل و حداکثر مشخص‌شده است — مگر اینکه حداکثر واقعاً از حداقل کمتر باشد، که در این صورت مقدار پیش‌فرض برابر با مقدار attribute «`min`» می‌شود. الگوریتم تعیین مقدار پیش‌فرض به این صورت است:

```js
defaultValue =
  rangeElem.max < rangeElem.min
    ? rangeElem.min
    : rangeElem.min + (rangeElem.max - rangeElem.min) / 2;
```

اگر تلاش شود مقدار کمتر از حداقل تنظیم شود، همان حداقل به‌عنوان مقدار در نظر گرفته می‌شود. به همین ترتیب، اگر مقدار بیشتر از حداکثر تنظیم شود، نتیجه به حداکثر محدود می‌شود.

### اعتبارسنجی

هیچ اعتبارسنجی مبتنی بر pattern در دسترس نیست؛ با این حال، انواع زیر از اعتبارسنجی خودکار انجام می‌شود:

- اگر مقدار «[`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value)» به چیزی تنظیم شود که نتوان آن را به یک عدد اعشاری معتبر تبدیل کرد، اعتبارسنجی ناموفق است؛ زیرا ورودی با مشکل bad input مواجه است.
- مقدار از «[`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min)» کمتر نخواهد بود. مقدار پیش‌فرض ۰ است.
- مقدار از «[`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max)» بیشتر نخواهد بود. مقدار پیش‌فرض ۱۰۰ است.
- مقدار مضربی از «[`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step)» خواهد بود. مقدار پیش‌فرض ۱ است.

## attributeهای اضافی

علاوه بر attributeهای مشترک بین همهٔ عنصرهای `<input>`، ورودی‌های range attributeهای زیر را نیز ارائه می‌دهند.

> [!NOTE]
> این attributeهای ورودی برای input range اعمال نمی‌شوند: `accept`, `alt`, `checked`, `dirname`, `formaction`, `formenctype`, `formmethod`, `formnovalidate`, `formtarget`, `height`, `maxlength`, `minlength`, `multiple`, `pattern`, `placeholder`, `readonly`, `required`, `size` و `src`. اگر هرکدام از این attributeها گنجانده شوند، نادیده گرفته می‌شوند.

### list

مقدار ویژگی `list` برابر با `id` یک عنصر {{HTMLElement("datalist")}} است که در همان سند قرار دارد. این عنصر لیستی از مقادیر از پیش‌تعریف‌شده را برای پیشنهاد به کاربر فراهم می‌کند. هر مقداری در این لیست که با [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) ورودی همخوانی نداشته باشد، در گزینه‌های پیشنهادی نمایش داده نمی‌شود. مقادیر ارائه‌شده فقط پیشنهاد هستند، نه الزام؛ کاربر می‌تواند از این لیست انتخاب کند یا مقدار متفاوتی وارد کند.

برای مشاهدهٔ نمونه‌ای از نحوهٔ نمایش گزینه‌ها در یک محدوده (range) در مرورگرهای پشتیبانی‌کننده، بخش [اضافه‌کردن علامت‌های تیک](#adding_tick_marks) را ببینید.

### max

بزرگ‌ترین مقدار مجاز در محدوده. اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) واردشده از این مقدار بیشتر باشد، عنصر در [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) رد می‌شود. اگر مقدار ویژگی [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max) یک عدد نباشد، عنصر حداکثر مقدار نخواهد داشت.

این مقدار باید بزرگ‌تر یا مساوی مقدار ویژگی [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) باشد. به ویژگی HTML [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max) مراجعه کنید.

### min

کوچک‌ترین مقدار مجاز در محدوده. اگر [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) عنصر از این مقدار کمتر باشد، عنصر در [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) رد می‌شود. اگر مقداری برای `min` مشخص شود که عدد معتبری نباشد، ورودی حداقل مقدار نخواهد داشت.

این مقدار باید کوچک‌تر یا مساوی مقدار ویژگی [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max) باشد. به ویژگی HTML [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min) مراجعه کنید.

> **توجه:** اگر مقادیر `min` و `max` برابر باشند یا مقدار `max` از `min` کمتر باشد، کاربر نمی‌تواند با محدوده تعامل کند.

### step

ویژگی `step` عددی است که دقت (granularity) مقدار مجاز را مشخص می‌کند، یا می‌تواند مقدار خاص `any` باشد که در ادامه توضیح داده می‌شود. تنها مقادیری معتبر هستند که تعداد کامل مراحل از پایهٔ گام (step base) فاصله داشته باشند. پایهٔ گام به‌ترتیب: اگر `min` مشخص شده باشد، همان `min` است؛ در غیر این صورت اگر `value` مشخص شده باشد، `value` است؛ و اگر هیچ‌کدام مشخص نباشند، `0` در نظر گرفته می‌شود.

مقدار پیش‌فرض گام برای ورودی‌های `step` برابر `1` است و فقط ورود اعداد صحیح را مجاز می‌کند—مگر اینکه پایهٔ گام یک عدد صحیح نباشد.

مقدار رشته‌ای `any` به این معناست که هیچ گام‌بندی ضمنی‌ای وجود ندارد و هر مقداری (با رعایت سایر محدودیت‌ها مانند [`min`](#min) و [`max`](#max)) مجاز است. برای مثال نحوهٔ کار این ویژگی در مرورگرهای پشتیبانی‌کننده، بخش [تنظیم step به مقدار `any`](#setting_step_to_any) را ببینید.

> **توجه:** وقتی مقدار واردشده توسط کاربر با پیکربندی گام مطابقت نداشته باشد، عامل کاربر (user agent) ممکن است مقدار را به نزدیک‌ترین مقدار معتبر گرد کند و در صورت برابری فاصله، عدد را به سمت بالا گرد می‌کند.

## ویژگی‌های غیراستاندارد

### orient

مشابه ویژگی غیراستاندارد CSS `-moz-orient` که روی عناصر {{htmlelement('progress')}} و {{htmlelement('meter')}} تأثیر می‌گذارد، ویژگی `orient` جهت نمایش اسلایدر محدوده را مشخص می‌کند. مقادیر شامل `horizontal` (افقی) و `vertical` (عمودی) است.

## مثال‌ها

نوع `number` به کاربر اجازه می‌دهد عددی را با محدودیت‌های دلخواه بین حداقل و حداکثر وارد کند، اما نیاز دارد که کاربر مقدار مشخصی را تایپ کند. در مقابل، نوع ورودی `range` به شما امکان می‌دهد در شرایطی که کاربر ممکن است به مقدار عددی دقیق اهمیت ندهد یا حتی آن را نداند، از او یک مقدار بخواهید.

چند نمونه از موقعیت‌های رایج استفاده از ورودی‌های محدوده:

- کنترل‌های صوتی مثل بلندی صدا، میزان تعادل (balance) یا فیلترها.
- کنترل‌های تنظیم رنگ مانند کانال‌های رنگی، شفافیت، روشنایی و موارد مشابه.
- کنترل‌های تنظیم بازی مثل دشواری، فاصله دید، اندازه دنیا و غیره.
- طول رمز عبوری که یک مدیر رمز (password manager) تولید می‌کند.

به‌عنوان یک قانون کلی، اگر کاربر بیشتر به درصد فاصله بین حداقل و حداکثر مقدار علاقه‌مند است تا خود عدد واقعی، input از نوع range گزینه بسیار مناسبی است. مثلاً برای کنترل بلندی صدای یک سیستم صوتی خانگی، کاربران معمولاً فکر می‌کنند «صدا را روی نصف حداکثر بگذار» به جای «صدا را روی ۰.۵ بگذار».

### تعیین حداقل و حداکثر

به‌صورت پیش‌فرض، حداقل مقدار ۰ و حداکثر ۱۰۰ است. اگر این مقادیر موردنظر شما نیست، می‌توانید به سادگی با تغییر مقادیر attributeهای [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) مرزهای دیگری تعیین کنید. این مقادیر می‌توانند هر عدد اعشاری باشند.

برای مثال، برای گرفتن عددی بین ۱۰- و ۱۰ از کاربر، می‌توانید از کد زیر استفاده کنید:

```html
<input type="range" min="-10" max="10" />
```

### تنظیم دانه‌بندی مقدار

به‌صورت پیش‌فرض، دانه‌بندی (granularity) برابر ۱ است؛ یعنی مقدار همیشه یک عدد صحیح است. برای کنترل دانه‌بندی می‌توانید attribute مربوط به [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) را تغییر دهید. مثلاً اگر به مقداری نیاز دارید که بین ۵ و ۱۰ نصفه باشد، باید مقدار `step` را روی ۰.۵ تنظیم کنید:

#### تنظیم attribute ی step

```html
<input type="range" min="5" max="10" step="0.5" />
```

#### تنظیم step روی `any`

اگر می‌خواهید هر مقداری را پذیرا باشید، بدون توجه به اینکه مقدار چند رقم اعشار داشته باشد، می‌توانید برای attribute ی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) مقدار `any` را مشخص کنید:

##### HTML

```html
<input id="pi_input" type="range" min="0" max="3.14" step="any" />
<p>Value: <output id="value"></output></p>
```

##### JavaScript

```js
const value = document.querySelector("#value");
const input = document.querySelector("#pi_input");
value.textContent = input.value;
input.addEventListener("input", (event) => {
  value.textContent = event.target.value;
});
```

این مثال به کاربر اجازه می‌دهد هر عددی بین ۰ و π را بدون هیچ محدودیتی در بخش اعشار انتخاب کند. از JavaScript برای نمایش تغییر مقدار هنگام تعامل کاربر با range استفاده شده است.

### افزودن تیک‌ها

برای افزودن تیک‌ها به کنترل range، attribute ی `list` را وارد کنید و مقدار آن را برابر `id` یک عنصر {{HTMLElement("datalist")}} قرار دهید. این عنصر مجموعه‌ای از تیک‌ها را روی کنترل مشخص می‌کند. هر نقطه با یک عنصر {{HTMLElement("option")}} نمایش داده می‌شود که attribute ی [`value`](/en-US/docs/Web/HTML/Reference/Elements/option#value) آن برابر با مقداری است که باید در آن نقطه تیک رسم شود.

#### HTML

```html
<label for="temp">Choose a comfortable temperature:</label><br />
<input type="range" id="temp" name="temp" list="markers" />

<datalist id="markers">
  <option value="0"></option>
  <option value="25"></option>
  <option value="50"></option>
  <option value="75"></option>
  <option value="100"></option>
</datalist>
```

#### نتیجه

### استفاده از یک datalist برای چند کنترل range

برای جلوگیری از تکرار کد، می‌توانید از همان {{HTMLElement("datalist")}} برای چند عنصر `<input type="range">` و سایر انواع {{HTMLElement("input")}} استفاده کنید.

> [!NOTE]
> اگر در مثال زیر بخواهید [برچسب‌ها را هم نمایش دهید](#adding_labels)، برای هر input از نوع range باید یک `datalist` جداگانه داشته باشید.

#### HTML

```html
<p>
  <label for="temp1">Temperature for room 1:</label>
  <input type="range" id="temp1" name="temp1" list="values" />
</p>
<p>
  <label for="temp2">Temperature for room 2:</label>
  <input type="range" id="temp2" name="temp2" list="values" />
</p>

<p>
  <label for="temp3">Temperature for room 3:</label>
  <input type="range" id="temp3" name="temp3" list="values" />
</p>

<datalist id="values">
  <option value="0" label="0"></option>
  <option value="25" label="25"></option>
  <option value="50" label="50"></option>
  <option value="75" label="75"></option>
  <option value="100" label="100"></option>
</datalist>
```

#### نتیجه

### افزودن برچسب‌ها

می‌توانید با دادن ویژگی `label` به عناصر `<option>`، علامت‌های روی نوار را برچسب‌گذاری کنید. اما محتوای این برچسب‌ها به‌صورت پیش‌فرض نمایش داده نمی‌شود. با CSS می‌توانید برچسب‌ها را نمایش دهید و آن‌ها را در موقعیت درست قرار دهید. در ادامه یک روش برای این کار نشان داده شده است.

#### HTML

```html
<label for="tempB">Choose a comfortable temperature:</label><br />
<input type="range" id="tempB" name="temp" list="values" />

<datalist id="values">
  <option value="0" label="very cold!"></option>
  <option value="25" label="cool"></option>
  <option value="50" label="medium"></option>
  <option value="75" label="getting warm!"></option>
  <option value="100" label="hot!"></option>
</datalist>
```

#### CSS

```css
datalist {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  writing-mode: vertical-lr;
  width: 200px;
}

option {
  padding: 0;
}

input[type="range"] {
  width: 200px;
  margin: 0;
}
```

#### نتیجه

### ایجاد کنترل‌های range عمودی

به‌طور پیش‌فرض، مرورگرها ورودی‌های range را به‌صورت لغزنده‌هایی رندر می‌کنند که دستگیرهٔ آن‌ها به چپ و راست حرکت می‌کند.

برای ایجاد یک range عمودی که در آن دستگیره بالا و پایین می‌رود، ویژگی `writing-mode` را با مقدار `vertical-rl` یا `vertical-lr` تنظیم کنید:

```html hidden
<input type="range" min="0" max="10" value="8" />
```

```css
input[type="range"] {
  writing-mode: vertical-lr;
}
```

این کار باعث می‌شود لغزندهٔ range به‌صورت عمودی رندر شود:

#### نتیجه

همچنین می‌توانید ویژگی CSS `appearance` را به مقدار غیراستاندارد `slider-vertical` تنظیم کنید تا از نسخه‌های قدیمی‌تر Chrome و Safari پشتیبانی کنید؛ و ویژگی غیراستاندارد `orient="vertical"` را اضافه کنید تا از نسخه‌های قدیمی‌تر Firefox پشتیبانی شود.

برای مثال‌ها، به [Creating vertical form controls](/en-US/docs/Web/CSS/Guides/Writing_modes/Vertical_controls) مراجعه کنید.

## خلاصه فنی
```

```markdown
| ویژگی | توضیح |
| --- | --- |
| مقدار (Value) | یک رشته که نمایش رشته‌ای مقدار عددی انتخاب‌شده است؛ برای دریافت مقدار به‌صورت عدد از [`valueAsNumber`](/en-US/docs/Web/API/HTMLInputElement/valueAsNumber) استفاده کنید. |
| رویدادها (Events) | رویدادهای [`change`](/en-US/docs/Web/API/HTMLElement/change_event) و [`input`](/en-US/docs/Web/API/Element/input_event) |
| ویژگی‌های عمومی پشتیبانی‌شده (Supported common attributes) | ویژگی‌های [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete)، [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list)، [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max)، [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) |
| ویژگی‌های IDL (IDL attributes) | ویژگی‌های [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list)، [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) و `valueAsNumber` |
| رابط DOM (DOM interface) | رابط [`HTMLInputElement`](/en-US/docs/Web/API/HTMLInputElement) |
| نقش ضمنی ARIA (Implicit ARIA Role) | نقش [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role) |

## همچنین ببینید

- [فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)
- [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input) و رابط [`HTMLInputElement`](/en-US/docs/Web/API/HTMLInputElement) که بر اساس آن ساخته شده است.
- [`<input type="number">`](/en-US/docs/Web/HTML/Reference/Elements/input/number)
- [`validityState.rangeOverflow`](/en-US/docs/Web/API/ValidityState/rangeOverflow) و [`validityState.rangeUnderflow`](/en-US/docs/Web/API/ValidityState/rangeUnderflow)
- [کنترل چندین پارامتر با ConstantSourceNode](/en-US/docs/Web/API/Web_Audio_API/Controlling_multiple_parameters_with_ConstantSourceNode)
- [ایجاد کنترل‌های فرم عمودی](/en-US/docs/Web/CSS/Guides/Writing_modes/Vertical_controls)
- [استایل‌دهی به عنصر range](https://css-tricks.com/sliding-nightmare-understanding-range-input/)
```