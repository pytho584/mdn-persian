---
title: "<input type=\"number\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/number"
translated_by: "n8n + AI"
---

عناصر `<input>` از نوع **`number`** برای وارد کردن عدد توسط کاربر استفاده می‌شوند. این عناصر به‌صورت built-in اعتبارسنجی دارند و ورودی‌های غیرعددی را رد می‌کنند.

مرورگر می‌تواند دکمه‌های افزایش/کاهش (stepper arrows) را نمایش دهد تا کاربر با موس یا لمس انگشت مقدار را تغییر دهد.

```html interactive-example
<label for="tentacles">تعداد شاخک‌ها (۱۰ تا ۱۰۰):</label>

<input type="number" id="tentacles" name="tentacles" min="10" max="100" />
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

در مرورگرهایی که از input نوع `number` پشتیبانی نمی‌کنند، این input به نوع `text` برگشت می‌خورد.

## مقدار (Value)

یک عدد که مقدار وارد شده در input را نشان می‌دهد. می‌توانید یک مقدار پیش‌فرض با قرار دادن عدد در attribute `value` تنظیم کنید:

```html
<input id="number" type="number" value="42" />
```

## ویژگی‌های اضافی (Additional attributes)

علاوه بر ویژگی‌های مشترک همه انواع `<input>`، inputهای نوع `number` از این ویژگی‌ها نیز پشتیبانی می‌کنند.

### `list`

مقدار attribute `list`، `id` یک عنصر `<datalist>` در همان سند است. `<datalist>` لیستی از مقادیر از پیش‌تعریف‌شده را برای پیشنهاد به کاربر فراهم می‌کند. هر مقداری در لیست که با نوع `type` سازگار نباشد، در گزینه‌های پیشنهادی نمایش داده نمی‌شود. مقادیر ارائه‌شده فقط پیشنهاد هستند، نه الزام: کاربر می‌تواند از این لیست انتخاب کند یا مقدار دیگری وارد کند.

### `max`

حداکثر مقدار قابل قبول برای این input. اگر مقدار `value` واردشده از این بیشتر باشد، عنصر در [constraint validation](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Constraint_validation) مردود می‌شود. اگر مقدار `max` یک عدد معتبر نباشد، عنصر حداکثر مقداری ندارد.

این مقدار باید بزرگ‌تر یا مساوی مقدار `min` باشد.

### `min`

حداقل مقدار قابل قبول برای این input. اگر مقدار `value` عنصر از این کمتر باشد، عنصر در [constraint validation](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Constraint_validation) مردود می‌شود. اگر مقدار `min` یک عدد معتبر نباشد، input حداقل مقداری ندارد.

این مقدار باید کوچک‌تر یا مساوی مقدار `max` باشد.

### `placeholder`

attribute `placeholder` یک رشته است که یک راهنمای مختصر به کاربر می‌دهد تا بفهمد چه نوع اطلاعاتی در فیلد مورد انتظار است. باید یک کلمه یا عبارت کوتاه باشد که نوع داده‌ی مورد انتظار را نشان دهد، نه یک پیام توضیحی. متن _نباید_ شامل carriage return یا line feed باشد.

اگر محتوای کنترل یک جهت‌دهی دارد ({{Glossary("LTR")}} یا {{Glossary("RTL")}}) اما نیاز است placeholder در جهت مخالف نمایش داده شود، می‌توانید از کاراکترهای قالب‌بندی الگوریتم دوجهتی Unicode برای تغییر جهت درون placeholder استفاده کنید. برای اطلاعات بیشتر به [How to use Unicode controls for bidi text](https://www.w3.org/International/questions/qa-bidi-unicode-controls) مراجعه کنید.

> [!NOTE]
> تا حد امکان از استفاده از attribute با نام `placeholder` خودداری کنید. این attribute از نظر معنایی به اندازه روش‌های دیگر برای توضیح فرم مفید نیست و می‌تواند مشکلات فنی غیرمنتظره‌ای در محتوای شما ایجاد کند. برای اطلاعات بیشتر به [برچسب‌های `<input>`](/en-US/docs/Web/HTML/Reference/Elements/input#labels) مراجعه کنید.

### `readonly`

یک attribute از نوع Boolean است که اگر وجود داشته باشد، یعنی کاربر نمی‌تواند این فیلد را ویرایش کند. با این حال، مقدار `value` آن همچنان می‌تواند توسط کد جاوااسکریپت و با تنظیم مستقیم property مربوط به `value` در `HTMLInputElement` تغییر کند.

> [!NOTE]
> چون یک فیلد read-only نمی‌تواند مقدار داشته باشد، `required` هیچ تأثیری روی inputهایی که attribute با نام `readonly` نیز در آن‌ها مشخص شده است ندارد.

### `step`

attribute با نام `step` عددی است که دانه‌بندی (granularity) موردنیاز برای مقدار را مشخص می‌کند، یا مقدار خاص `any` که در ادامه توضیح داده شده است. فقط مقادیری معتبر هستند که مضربی کامل از `step` نسبت به مبنا (base) باشند. مبنای `step` برابر است با [`min`](#min) اگر مشخص شده باشد، در غیر این صورت [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value)، و اگر هیچ‌کدام مشخص نشده باشند، `0`.

مقدار پیش‌فرض `step` برای inputهای نوع `number` برابر `1` است و بنابراین فقط اعداد صحیح قابل وارد کردن هستند—_مگر اینکه_ مبنای `step` عدد صحیح نباشد.

مقدار رشته‌ای `any` به این معنی است که هیچ `step` خاصی اعمال نمی‌شود و هر مقدار (با رعایت سایر محدودیت‌ها مانند [`min`](#min) و [`max`](#max)) مجاز است.

> [!NOTE]
> وقتی دادهٔ واردشده توسط کاربر با تنظیمات `step` هماهنگ نباشد، ممکن است user agent مقدار را به نزدیک‌ترین مقدار معتبر گرد کند و در صورت وجود دو گزینهٔ به همان اندازه نزدیک، عدد مثبت را ترجیح دهد.

## استفاده از input های عددی

نوع `number` فقط باید برای اعداد پلکانی (incremental) استفاده شود، مخصوصاً وقتی که دکمه‌های افزایش/کاهش (spinbutton) برای تجربه کاربری مفید هستند. نوع `number` برای مقادیری که اتفاقاً فقط از ارقام تشکیل شده‌اند اما به معنای دقیق عدد نیستند، مناسب نیست؛ مانند کد پستی در بسیاری از کشورها یا شماره کارت اعتباری. برای ورودی‌های غیرعددی، از یک نوع input دیگر استفاده کنید، مانند [`<input type="tel">`](/en-US/docs/Web/HTML/Reference/Elements/input/tel) یا نوع دیگری از `<input>` با attribute مربوط به [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode):

```html
<input type="text" inputmode="numeric" pattern="\d*" />
```

المان‌های `<input type="number">` می‌توانند کار شما را هنگام ساختن رابط کاربری و منطق ورود اعداد به یک فرم ساده‌تر کنند. وقتی یک input عددی با مقدار درست `type`، یعنی `number` می‌سازید، به‌صورت خودکار اعتبارسنجی می‌شود که متن واردشده عدد است و معمولاً یک جفت دکمه بالا و پایین برای افزایش و کاهش مقدار دریافت می‌کنید.

> [!WARNING]
> منطقاً نباید بتوانید کاراکتری غیر از عدد در یک input عددی وارد کنید. برخی مرورگرها کاراکترهای نامعتبر را مجاز می‌دانند و برخی نه؛ به [باگ ۱۳۹۸۵۲۸ فایرفاکس](https://bugzil.la/1398528) مراجعه کنید.

> [!NOTE]
> کاربر می‌تواند پشت صحنه HTML شما را تغییر دهد، بنابراین سایت شما برای اهداف امنیتی _نباید_ به اعتبارسنجی سمت کلاینت متکی باشد. در سمت سرور، هر تراکنشی که مقدار ارائه‌شده در آن می‌تواند هر نوع پیامد امنیتی داشته باشد، _باید_ بررسی کنید.

مرورگرهای موبایل همچنین با نمایش یک صفحه‌کلید ویژه که برای وارد کردن اعداد مناسب‌تر است، تجربه کاربری را بهبود می‌بخشند.

### یک input عددی پایه

در ساده‌ترین شکل، یک input عددی می‌تواند به این صورت پیاده‌سازی شود:

```html
<label for="ticketNum">Number of tickets you would like to buy:</label>
<input id="ticketNum" type="number" name="ticketNum" value="0" />
```

یک input عددی زمانی معتبر در نظر گرفته می‌شود که خالی باشد یا یک عدد واحد وارد شده باشد؛ در غیر این صورت نامعتبر است. اگر attribute مربوط به [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) استفاده شود، input خالی دیگر معتبر در نظر گرفته نمی‌شود.

> [!NOTE]
> هر عددی مقدار قابل قبولی است، به شرطی که یک [عدد اعشاری معتبر](https://html.spec.whatwg.org/multipage/infrastructure.html#valid-floating-point-number) باشد (یعنی [NaN](/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) یا [Infinity](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Infinity) نباشد).

### Placeholder ها

گاهی اوقات مفید است که یک راهنمای درون متنی درباره شکل داده ورودی به کاربر ارائه شود. این موضوع به‌خصوص زمانی اهمیت دارد که طراحی صفحه، برچسب توصیفی برای هر `<input>` نداشته باشد. اینجا جایی است که **Placeholder** وارد می‌شود. Placeholder مقداری است که معمولاً برای ارائه راهنمایی درباره قالبی که مقدار (`value`) ورودی باید داشته باشد استفاده می‌شود. وقتی `value` عنصر برابر `""` باشد، داخل کادر ویرایش نمایش داده می‌شود. به محض وارد شدن داده در کادر، placeholder ناپدید می‌شود؛ اگر کادر خالی شود، دوباره ظاهر می‌شود.

```html
<input type="number" placeholder="Multiple of 10" />
```

### کنترل اندازه گام

به‌طور پیش‌فرض، دکمه‌های بالا و پایین که برای افزایش و کاهش عدد استفاده می‌شوند، مقدار را یک واحد تغییر می‌دهند. می‌توانید این رفتار را با استفاده از ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) تغییر دهید. این ویژگی عددی را به عنوان مقدار می‌پذیرد که اندازه گام را مشخص می‌کند. مثال بالا دارای placeholder است که می‌گوید مقدار باید مضربی از ۱۰ باشد، پس منطقی است که مقدار `step` را برابر `10` قرار دهیم:

```html
<input type="number" placeholder="multiple of 10" step="10" />
```

در این مثال، خواهید دید که فلش‌های بالا و پایین مقدار را هر بار ۱۰ واحد کم و زیاد می‌کنند، نه ۱ واحد. همچنان می‌توانید عددی را که مضربی از ۱۰ نیست به‌صورت دستی وارد کنید، اما این مقدار نامعتبر در نظر گرفته می‌شود.

### تعیین مقادیر حداقل و حداکثر

می‌توانید از ویژگی‌های [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) برای تعیین حداقل و حداکثر مقدار مجاز فیلد استفاده کنید. برای مثال، بیایید به مثال خود حداقل `0` و حداکثر `100` بدهیم:

```html
<input type="number" placeholder="multiple of 10" step="10" min="0" max="100" />
```

در این نسخه به‌روزرسانی‌شده، دکمه‌های گام بالا و پایین اجازه نمی‌دهند از ۰ پایین‌تر یا از ۱۰۰ بالاتر بروید. همچنان می‌توانید عددی خارج از این محدوده را به‌صورت دستی وارد کنید، اما نامعتبر خواهد بود.

### اجازه دادن به مقادیر اعشاری

یکی از مشکلات ورودی‌های عددی این است که اندازه گام پیش‌فرض آنها ۱ است. اگر بخواهید عددی اعشاری وارد کنید که عدد صحیح نیست (مثل «۱.۱»)، نامعتبر در نظر گرفته می‌شود. توجه کنید مقادیری مثل «۱.۰» معتبر هستند، چون از نظر عددی معادل اعداد صحیح‌اند. اگر می‌خواهید مقادیر اعشاری وارد کنید، باید این را در مقدار `step` منعکس کنید (مثلاً `step="0.01"` تا دو رقم اعشار مجاز شود). یک مثال ساده:

```html
<input type="number" placeholder="1.0" step="0.01" min="0" max="10" />
```

می‌بینید که این مثال هر مقدار بین `0.0` و `10.0` را با دو رقم اعشار مجاز می‌کند. برای مثال، «۹.۵۲» معتبر است، اما «۹.۵۲۱» معتبر نیست.

اگر می‌خواهید مقادیر اعشاری دلخواه را مجاز کنید، می‌توانید مقدار `step` را برابر `"any"` قرار دهید.

### کنترل اندازه ورودی

عناصر `<input>` از نوع `number` از ویژگی‌های اندازه‌گیری فرم مانند [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) پشتیبانی نمی‌کنند. برای تغییر اندازه این کنترلها باید از [CSS](/en-US/docs/Web/CSS) استفاده کنید.

برای مثال، اگر بخواهید عرض input فقط به اندازه‌ای باشد که یک عدد سه‌رقمی وارد شود، می‌توانید HTML را تغییر دهید و یک [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) به آن اضافه کنید و placeholder را کوتاه‌تر کنید، چون فیلد برای متنی که تا حالا استفاده می‌کردیم خیلی窄 می‌شود:

```html
<input
  type="number"
  placeholder="x10"
  step="10"
  min="0"
  max="100"
  id="number" />
```

سپس با CSS عرض المنت را با استفاده از selector `#number` محدود می‌کنیم:

```css
#number {
  width: 3em;
}
```

### ارائه مقادیر پیشنهادی

می‌توانید با استفاده از ویژگی [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list) یک لیست از گزینه‌های پیش‌فرض ارائه دهید که کاربر بتواند از بین آن‌ها انتخاب کند. مقدار این ویژگی باید [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یک {{HTMLElement("datalist")}} باشد. داخل آن دیتالیست هم به ازای هر مقدار پیشنهادی یک {{HTMLElement("option")}} قرار می‌دهید. مقدار `value` هر `option`، مقدار پیشنهادی متناظر برای جعبه ورودی عدد است.

```html
<input id="ticketNum" type="number" name="ticketNum" list="defaultNumbers" />
<span class="validity"></span>

<datalist id="defaultNumbers">
  <option value="10045678"></option>
  <option value="103421"></option>
  <option value="11111111"></option>
  <option value="12345678"></option>
  <option value="12999922"></option>
</datalist>
```

## اعتبارسنجی

قبلاً به تعدادی از ویژگی‌های اعتبارسنجی ورودی‌های `number` اشاره کردیم؛ بیایید مرورشان کنیم:

- المنت‌های `<input type="number">` به‌طور خودکار هر ورودی‌ای که عدد نباشد (یا خالی باشد، مگر `required` مشخص شده باشد) را نامعتبر اعلام می‌کنند.
- با استفاده از ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) می‌توانید ورودی خالی را هم نامعتبر کنید. (یعنی فیلد _باید_ پر شود.)
- با ویژگی [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) می‌توانید مقادیر معتبر را به گام‌های مشخصی محدود کنید (مثلاً مضرب‌های ۱۰).
- با ویژگی‌های [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) می‌توانید مقادیر معتبر را به یک بازه محدود کنید.

مثال زیر همه این ویژگی‌ها را نشان می‌دهد، و همچنین از CSS برای نمایش آیکون‌های معتبر و نامعتبر بر اساس مقدار `input` استفاده می‌کند:

```html
<form>
  <div>
    <label for="balloons">Number of balloons to order (multiples of 10):</label>
    <input
      id="balloons"
      type="number"
      name="balloons"
      step="10"
      min="0"
      max="100"
      required />
    <span class="validity"></span>
  </div>
  <div>
    <input type="submit" />
  </div>
</form>
```

سعی کنید فرم را با مقادیر نامعتبر مختلف ارسال کنید — مثلاً بدون مقدار، مقداری زیر ۰ یا بالای ۱۰۰، مقداری که مضرب ۱۰ نباشد، یا یک مقدار غیرعددی — و ببینید پیام‌های خطایی که مرورگر نشان می‌دهد چقدر متفاوت هستند.

CSS اعمال‌شده برای این مثال به صورت زیر است:

```css
div {
  margin-bottom: 10px;
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

در اینجا از pseudo-classهای {{cssxref(":invalid")}} و {{cssxref(":valid")}} استفاده می‌کنیم تا یک آیکون مناسب (نامعتبر یا معتبر) را به‌عنوان محتوای تولیدشده روی {{htmlelement("span")}} مجاور قرار دهیم و به‌صورت بصری وضعیت اعتبار را نشان دهیم.

این آیکون را روی یک `<span>` جداگانه قرار داده‌ایم تا انعطاف‌پذیری بیشتری داشته باشد. بعضی مرورگرها محتوای تولیدشده را روی برخی انواع ورودی‌های فرم به‌خوبی نمایش نمی‌دهند. (برای مثال، بخش مربوط به اعتبارسنجی [`<input type="date">`](/en-US/docs/Web/HTML/Reference/Elements/input/date#validation) را ببینید.)

> [!WARNING]
> اعتبارسنجی فرم در HTML جایگزینی برای اسکریپت‌های سمت سرور نیست که اطمینان می‌دهند داده‌های واردشده در قالب صحیح هستند!
>
> خیلی راحت کسی می‌تواند HTML را دستکاری کند تا اعتبارسنجی را دور بزند یا کاملاً حذف کند. همچنین ممکن است کسی HTML شما را نادیده بگیرد و داده‌ها را مستقیماً به سرور ارسال کند.
>
> اگر کد سمت سرور نتواند داده‌های دریافتی را اعتبارسنجی کند، ارسال داده‌های با فرمت نامناسب (یا داده‌های خیلی بزرگ، از نوع اشتباه و غیره) می‌تواند فاجعه ایجاد کند.

### اعتبارسنجی الگو

عنصرهای `<input type="number">` از به‌کارگیری attribute [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) برای مطابقت مقادیر واردشده با یک الگوی regex مشخص پشتیبانی نمی‌کنند.

دلیل این است که inputهای عددی فقط وقتی معتبر هستند که عدد داشته باشند، و می‌توانید با attributeهای [`min`](/en-US/docs/Web/HTML/Reference/Elements/input#min) و [`max`](/en-US/docs/Web/HTML/Reference/Elements/input#max) کمینه و بیشینهٔ تعداد ارقام معتبر را محدود کنید (همانطور که در بالا توضیح داده شد).

## دسترس‌پذیری

نقش ضمنی [role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) برای عنصر `<input type="number">` برابر است با [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role). اگر spinbutton برای کنترل فرم شما ویژگی مهمی نیست، بهتر است از `type="number"` استفاده نکنید. در عوض، از [`inputmode="numeric"`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode) به‌همراه attribute [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern) استفاده کنید که کاراکترها را به اعداد و کاراکترهای مرتبط محدود می‌کند. با `<input type="number">`، این خطر وجود دارد که کاربر هنگام انجام کار دیگری، به‌طور تصادفی عددی را افزایش دهد. علاوه بر این، اگر کاربران بخواهند چیزی غیر از عدد وارد کنند، هیچ بازخورد صریحی دربارهٔ اشتباه خود دریافت نمی‌کنند.

همچنین استفاده از attribute [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) را در نظر بگیرید تا کاربران فرم‌ها را سریع‌تر و با خطای کمتری تکمیل کنند. برای مثال، برای فعال‌کردن تکمیل خودکار در فیلد کدپستی، مقدار `autocomplete="postal-code"` را تنظیم کنید.

## مثال‌ها

ما قبلاً گفتیم که به‌طور پیش‌فرض مقدار افزایش (increment) برابر `1` است و می‌توانید با attribute [`step`](/en-US/docs/Web/HTML/Reference/Elements/input#step) ورودی اعشاری را مجاز کنید. بیایید دقیق‌تر به آن نگاه کنیم.

در مثال زیر، فرمی برای واردکردن قد کاربر داریم. این فرم به‌طور پیش‌فرض قد را بر حسب متر می‌پذیرد، اما می‌توانید با کلیک روی دکمهٔ مربوطه، فرم را به‌گونه‌ای تغییر دهید که قد را بر حسب فوت و اینچ بپذیرد. ورودیِ قد بر حسب متر، اعشار را تا دو رقم قبول می‌کند.

HTML به این صورت است:

```html
<form>
  <div class="metersInputGroup">
    <label for="meters">Enter your height — meters:</label>
    <input
      id="meters"
      type="number"
      name="meters"
      step="0.01"
      min="0"
      placeholder="e.g. 1.78"
      required />
    <span class="validity"></span>
  </div>
  <div class="feetInputGroup">
    <span>Enter your height — </span>
    <label for="feet">feet:</label>
    <input id="feet" type="number" name="feet" min="0" step="1" />
    <span class="validity"></span>
    <label for="inches">inches:</label>
    <input id="inches" type="number" name="inches" min="0" max="11" step="1" />
    <span class="validity"></span>
  </div>
  <div>
    <input
      type="button"
      class="meters"
      value="Enter height in feet and inches" />
  </div>
  <div>
    <input type="submit" value="Submit form" />
  </div>
</form>
```

می‌بینید که از بسیاری از attributeهایی که قبلاً در این مقاله بررسی کردیم استفاده می‌کنیم. از آنجا که می‌خواهیم مقدار متر را با سانتی‌متر بپذیریم، مقدار `step` را روی `0.01` تنظیم کرده‌ایم، بنابراین مقادیری مانند _1.78_ نامعتبر دیده نمی‌شوند. همچنین برای آن input، یک placeholder تعیین کرده‌ایم.

ما ابتدا ورودی‌های feet و inches را با استفاده از `style="display: none;"` مخفی کرده‌ایم تا متر به‌عنوان نوع ورودی پیش‌فرض باشد.

حالا سراغ CSS برویم. این استایل‌دهی بسیار شبیه به استایل اعتبارسنجی (validation) که قبلاً دیدیم است؛ نکته‌ی خاصی ندارد.

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

و در نهایت، کد جاوااسکریپت:

```js
const metersInputGroup = document.querySelector(".metersInputGroup");
const feetInputGroup = document.querySelector(".feetInputGroup");
const metersInput = document.querySelector("#meters");
const feetInput = document.querySelector("#feet");
const inchesInput = document.querySelector("#inches");
const switchBtn = document.querySelector('input[type="button"]');

feetInputGroup.style.display = "none"; // Hide feet/inches inputs initially

switchBtn.addEventListener("click", () => {
  if (switchBtn.getAttribute("class") === "meters") {
    switchBtn.setAttribute("class", "feet");
    switchBtn.value = "Enter height in meters";

    metersInputGroup.style.display = "none";
    feetInputGroup.style.display = "block";

    feetInput.setAttribute("required", "");
    inchesInput.setAttribute("required", "");
    metersInput.removeAttribute("required");

    metersInput.value = "";
  } else {
    switchBtn.setAttribute("class", "meters");
    switchBtn.value = "Enter height in feet and inches";

    metersInputGroup.style.display = "block";
    feetInputGroup.style.display = "none";

    feetInput.removeAttribute("required");
    inchesInput.removeAttribute("required");
    metersInput.setAttribute("required", "");

    feetInput.value = "";
    inchesInput.value = "";
  }
});
```

پس از تعریف چند متغیر، یک event listener به `button` اضافه می‌شود تا مکانیزم جابه‌جایی را کنترل کند. این کار شامل تغییر `class` دکمه و عنصر `<label>` و به‌روزرسانی مقادیر نمایشی دو مجموعه ورودی هنگام فشردن دکمه است.

(توجه کنید که ما در اینجا بین متر و feet/inches تبدیل رفت‌وبرگشت انجام نمی‌دهیم؛ کاری که یک وب‌اپلیکیشن واقعی احتمالاً انجام می‌دهد.)

> [!NOTE]
> وقتی کاربر دکمه را کلیک می‌کند، attributeهای `required` از ورودی‌هایی که مخفی می‌کنیم حذف می‌شوند و attributeهای `value` خالی می‌شوند. این کار باعث می‌شود اگر هر دو مجموعه ورودی پر نشده‌اند، فرم بتواند ارسال شود. همچنین تضمین می‌کند که فرم داده‌ای را که کاربر قصد ارسال آن را نداشته، ارسال نکند.
>
> اگر این کار را انجام ندهید، برای ارسال فرم باید هم feet/inches **و هم** متر را پر کنید!

## خلاصه فنی

| ویژگی | توضیح |
| --- | --- |
| **مقدار** | یک `Number` که نمایانگر یک عدد است، یا خالی |
| **رویدادها** | `change` و `input` |
| **ویژگی‌های رایج پشتیبانی‌شده** | [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete)، [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list)، [`placeholder`](/en-US/docs/Web/HTML/Reference/Elements/input#placeholder)، [`readonly`](/en-US/docs/Web/HTML/Reference/Elements/input#readonly) |
| **ویژگی‌های IDL** | [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list)، [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value)، `valueAsNumber` |
| **رابط DOM** | `HTMLInputElement` |
| **نقش ARIA ضمنی** | [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role) |

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- [راهنمای فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)
- [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input)
- [`<input type="tel">`](/en-US/docs/Web/HTML/Reference/Elements/input/tel)