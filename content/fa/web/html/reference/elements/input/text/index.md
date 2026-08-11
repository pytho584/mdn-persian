---
title: "<input type=\"text\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/text"
translated_by: "n8n + AI"
---

عناصر `<input>` از نوع **`text`**، فیلدهای متنی تک‌خطی ساده ایجاد می‌کنند.

```html interactive-example
<label for="name">Name (4 to 8 characters):</label>

<input
  type="text"
  id="name"
  name="name"
  required
  minlength="4"
  maxlength="8"
  size="10" />
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

## Value

ویژگی [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) یک رشته است که مقدار فعلی متن وارد‌شده در فیلد متنی را نگه می‌دارد. می‌توانید این مقدار را با استفاده از خاصیت `value` در `HTMLInputElement` (در JavaScript) دریافت کنید.

```js
let theText = myTextInput.value;
```

اگر هیچ محدودیتی برای اعتبارسنجی ورودی وجود نداشته باشد (برای جزئیات بیشتر به بخش [Validation](#validation) مراجعه کنید)، مقدار می‌تواند یک رشتهٔ خالی (`""`) باشد.

## ویژگی‌های اضافی

علاوه بر [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) و ویژگی‌هایی که روی همهٔ عناصر {{HTMLElement("input")}} بدون توجه به نوع آن‌ها اعمال می‌شوند، ورودی‌های `text` از ویژگی‌های زیر نیز پشتیبانی می‌کنند.

### `list`

مقدار ویژگی `list`، `id` یک عنصر {{HTMLElement("datalist")}} است که در همان سند قرار دارد. {{HTMLElement("datalist")}} فهرستی از مقادیر از پیش‌تعریف‌شده را برای پیشنهاد به کاربر در این ورودی فراهم می‌کند. هر مقداری در فهرست که با [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) سازگار نباشد، در گزینه‌های پیشنهادی گنجانده نمی‌شود. مقادیر ارائه‌شده فقط پیشنهاد هستند، نه الزام؛ کاربران می‌توانند از این فهرست از پیش‌تعریف‌شده انتخاب کنند یا مقدار متفاوتی وارد کنند.

### `maxlength`

حداکثر طول رشته (بر حسب واحدهای کد UTF-16) که کاربر می‌تواند در ورودی `text` وارد کند. این مقدار باید یک عدد صحیح ۰ یا بیشتر باشد. اگر `maxlength` مشخص نشود یا مقدار نامعتبری داشته باشد، ورودی `text` حداکثر طول نخواهد داشت. این مقدار همچنین باید بزرگتر یا مساوی مقدار `minlength` باشد.

اگر طول مقدار متنی فیلد بیشتر از `maxlength` واحد کد UTF-16 باشد، ورودی در [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) شکست می‌خورد. اعتبارسنجی محدودیت‌ها فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند.

### `minlength`

حداقل طول رشته (بر حسب واحدهای کد UTF-16) که کاربر می‌تواند در ورودی `text` وارد کند. این مقدار باید یک عدد صحیح غیرمنفی و کوچکتر یا مساوی مقدار `maxlength` باشد. اگر `minlength` مشخص نشود یا مقدار نامعتبری داشته باشد، ورودی `text` حداقل طول نخواهد داشت.

اگر طول متن واردشده در فیلد کمتر از `minlength` واحد کد UTF-16 باشد، ورودی در [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) شکست می‌خورد. اعتبارسنجی محدودیت‌ها فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند.

### `pattern`

ویژگی `pattern`، اگر مشخص شده باشد، یک عبارت منظم (regular expression) است که `value` ورودی باید با آن مطابقت داشته باشد تا بتواند [اعتبارسنجی محدودیت (constraint validation)](/en-US/docs/Web/HTML/Guides/Constraint_validation) را پشت سر بگذارد. این عبارت باید یک عبارت منظم معتبر جاوااسکریپت باشد، مانند آنچه در نوع {{jsxref("RegExp")}} استفاده می‌شود و در [راهنمای عبارات منظم](/en-US/docs/Web/JavaScript/Guide/Regular_expressions) مستند شده است. هنگام کامپایل عبارت منظم، پرچم `'u'` اضافه می‌شود تا الگو به‌عنوان دنباله‌ای از نقاط کد یونیکد (Unicode code points) در نظر گرفته شود، نه به‌عنوان {{Glossary("ASCII")}}. در اطراف متن الگو نباید اسلش (forward slash) نوشته شود.

اگر الگوی مشخص شده تعریف نشده یا نامعتبر باشد، هیچ عبارت منظمی اعمال نمی‌شود و این ویژگی به‌کلی نادیده گرفته می‌شود.

> [!NOTE]
> از ویژگی [`title`](/en-US/docs/Web/HTML/Reference/Elements/input#title) برای مشخص کردن متنی استفاده کنید که بیشتر مرورگرها آن را به‌عنوان راهنمای ابزار (tooltip) نمایش می‌دهند تا توضیح دهد که برای مطابقت با الگو چه شرایطی لازم است. همچنین باید متن توضیحی دیگری هم در نزدیکی آن قرار دهید.

برای جزئیات بیشتر و یک مثال به [مشخص کردن یک الگو (Specifying a pattern)](#specifying_a_pattern) مراجعه کنید.

### `placeholder`

ویژگی `placeholder` یک رشته (string) است که یک راهنمای کوتاه به کاربر می‌دهد و نشان می‌دهد چه نوع اطلاعاتی در فیلد انتظار می‌رود. این رشته باید یک کلمه یا عبارت کوتاه باشد که نوع داده‌ی مورد انتظار را نشان دهد، نه یک پیام توضیحی. متن _نباید_ شامل بازگشت به ابتدای خط (carriage return) یا خط جدید (line feed) باشد.

اگر محتوای کنترل یک جهت‌دهی (directionality) دارد (مثلاً {{Glossary("LTR")}} یا {{Glossary("RTL")}}) اما نیاز است placeholder را در جهت مخالف نمایش دهد، می‌توانید از نویسه‌های قالب‌بندی الگوریتم دوجهته (Unicode bidirectional algorithm formatting characters) برای تغییر جهت درون placeholder استفاده کنید. برای اطلاعات بیشتر به [How to use Unicode controls for bidi text](https://www.w3.org/International/questions/qa-bidi-unicode-controls) مراجعه کنید.

> [!NOTE]
> در صورت امکان از استفاده از ویژگی `placeholder` خودداری کنید. این ویژگی به اندازه‌ی روش‌های دیگر برای توضیح فرم شما از نظر معنایی (semantically) مفید نیست و می‌تواند مشکلات فنی غیرمنتظره‌ای در محتوایتان ایجاد کند. برای اطلاعات بیشتر به [ملاحظات دسترسی‌پذیری `<input>`](/en-US/docs/Web/HTML/Reference/Elements/input#accessibility) مراجعه کنید.

### `readonly`

یک ویژگی بولی (Boolean) که اگر وجود داشته باشد، به این معنی است که کاربر نمی‌تواند این فیلد را ویرایش کند. با این حال، مقدار `value` آن همچنان می‌تواند توسط کد جاوااسکریپت و با تنظیم مستقیم ویژگی `value` در {{domxref("HTMLInputElement")}} تغییر داده شود.

> [!NOTE]
> از آنجایی که یک فیلد فقط‌خواندنی (read-only) نمی‌تواند مقدار داشته باشد، ویژگی `required` روی ورودی‌هایی که ویژگی `readonly` نیز دارند هیچ تأثیری ندارد.

### `size`

ویژگی `size` یک مقدار عددی است که نشان می‌دهد فیلد ورودی چند کاراکتر عرض داشته باشد. مقدار باید عددی بزرگتر از صفر باشد و مقدار پیش‌فرض ۲۰ است. از آنجایی که عرض کاراکترها متفاوت است، ممکن است این مقدار دقیق نباشد و نباید به آن اعتماد کرد؛ ورودی حاصل ممکن است باریک‌تر یا پهن‌تر از تعداد کاراکتر مشخص‌شده باشد، بسته به کاراکترها و تنظیمات فونت ({{cssxref("font")}}).

این ویژگی _محدودیتی_ برای تعداد کاراکترهایی که کاربر می‌تواند وارد کند ایجاد نمی‌کند. فقط تقریباً مشخص می‌کند که چند کاراکتر در یک زمان قابل مشاهده هستند. برای تعیین یک محدودیت بالای طول داده‌های ورودی، از ویژگی [`maxlength`](#maxlength) استفاده کنید.

### `spellcheck`

ویژگی سراسری [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) برای مشخص کردن اینکه آیا غلط‌یابی املایی (spell-checking) برای یک عنصر فعال شود یا خیر استفاده می‌شود. این ویژگی می‌تواند روی هر محتوای قابل ویرایش استفاده شود، اما در اینجا نکات خاص مربوط به استفاده از `spellcheck` روی عناصر {{HTMLElement("input")}} را بررسی می‌کنیم. مقادیر مجاز برای `spellcheck` عبارتند از:

- `false`
  - : غلط‌یابی املایی را برای این عنصر غیرفعال می‌کند.
- `true`
  - : غلط‌یابی املایی را برای این عنصر فعال می‌کند.
- `""` (رشته خالی) یا بدون مقدار
  - : از رفتار پیش‌فرض عنصر برای غلط‌یابی املایی پیروی می‌کند. این ممکن است بر اساس تنظیمات `spellcheck` والد یا عوامل دیگر باشد.

یک فیلد ورودی می‌تواند غلط‌یابی خودکار (spell-checking) داشته باشد، اگر attribute `readonly` روی آن تنظیم نشده باشد و غیرفعال (disabled) نباشد.

مقداری که با خواندن `spellcheck` برگردانده می‌شود ممکن است منعکس‌کنندهٔ وضعیت واقعی غلط‌یابی درون کنترل نباشد، اگر تنظیمات برگزیدهٔ user agent این تنظیم را override کند.

## استفاده از ورودی‌های متنی

المان‌های `<input>` از نوع `text` ورودی‌های تک‌خطی و ساده می‌سازند. هرجا که کاربر باید یک مقدار تک‌خطی وارد کند و نوع ورودی خاص‌تری برای آن مقدار وجود ندارد (مثلاً اگر [تاریخ](/en-US/docs/Web/HTML/Reference/Elements/input/datetime-local)، [URL](/en-US/docs/Web/HTML/Reference/Elements/input/url)، [ایمیل](/en-US/docs/Web/HTML/Reference/Elements/input/email)، یا [عبارت جستجو](/en-US/docs/Web/HTML/Reference/Elements/input/search) باشد، گزینه‌های بهتری دارید)، باید از آن‌ها استفاده کنید.

### مثال پایه

```html
<form>
  <div>
    <label for="uname">یک نام کاربری انتخاب کنید: </label>
    <input type="text" id="uname" name="name" />
  </div>
  <div>
    <button>ارسال</button>
  </div>
</form>
```

این به صورت زیر نمایش داده می‌شود:

وقتی فرم ارسال شود، جفت name/value داده‌ای که به سرور فرستاده می‌شود `name=Chris` خواهد بود (اگر کاربر قبل از ارسال مقدار "Chris" را وارد کرده باشد). حتماً باید attribute `name` را روی المان `<input>` قرار دهید، در غیر این صورت مقدار فیلد متنی در داده‌های ارسالی لحاظ نمی‌شود.

### تنظیم placeholder

می‌توانید یک placeholder مفید درون ورودی متنی خود قرار دهید که با استفاده از attribute `placeholder` راهنمایی برای ورود داده ارائه دهد. به مثال زیر نگاه کنید:

```html
<form>
  <div>
    <label for="uname">یک نام کاربری انتخاب کنید: </label>
    <input
      type="text"
      id="uname"
      name="name"
      placeholder="حروف کوچک، همه یک کلمه" />
  </div>
  <div>
    <button>ارسال</button>
  </div>
</form>
```

نحوهٔ نمایش placeholder در زیر قابل مشاهده است:

placeholder معمولاً با رنگی روشن‌تر از رنگ foreground المان نمایش داده می‌شود و به محض اینکه کاربر شروع به تایپ متن در فیلد کند (یا هرگاه فیلد با تنظیم attribute `value` به صورت برنامه‌نویسی مقدار داشته باشد) به طور خودکار ناپدید می‌شود.

### اندازه فیزیکی المان ورودی

اندازه فیزیکی جعبه ورودی را می‌توان با استفاده از attribute `size` کنترل کرد. با این کار می‌توانید تعداد کاراکترهایی را که ورودی متنی می‌تواند در یک زمان نمایش دهد، مشخص کنید. این attribute بر عرض المان تأثیر می‌گذارد و به شما امکان می‌دهد عرض را به جای پیکسل بر حسب تعداد کاراکتر تعیین کنید. برای مثال، در اینجا ورودی ۳۰ کاراکتر عرض دارد:

```html
<form>
  <div>
    <label for="uname">یک نام کاربری انتخاب کنید: </label>
    <input
      type="text"
      id="uname"
      name="name"
      placeholder="حروف کوچک، همه یک کلمه"
      size="30" />
  </div>
  <div>
    <button>ارسال</button>
  </div>
</form>
```

## اعتبارسنجی

المان‌های `<input>` از نوع `text` هیچ اعتبارسنجی خودکاری روی آن‌ها اعمال نمی‌شود (چون یک ورودی متنی پایه باید قادر به پذیرش هر رشته دلخواهی باشد)، اما چند گزینه اعتبارسنجی سمت کاربر (client-side) در دسترس است که در ادامه به آن‌ها می‌پردازیم.

> [!NOTE]
> اعتبارسنجی فرم HTML جایگزینی برای اسکریپت‌های سمت سرور نیست که مطمئن می‌شوند دادهٔ واردشده قالب درستی دارد. خیلی راحت می‌توان HTML را تغییر داد تا اعتبارسنجی دور زده شود یا کلاً حذف شود. همچنین امکان دارد کسی HTML شما را دور بزند و داده‌ها را مستقیماً به سرور ارسال کند. اگر کد سمت سرور دادهٔ دریافتی را اعتبارسنجی نکند، ورود داده‌های با قالب اشتباه (یا داده‌ای که بیش از حد بزرگ است، نوع اشتباهی دارد و غیره) می‌تواند فاجعه ایجاد کند.

### نکته‌ای درباره استایل‌دهی

شبه‌کلاس‌های مفیدی برای استایل‌دهی به المان‌های فرم وجود دارند که به کاربر کمک می‌کنند ببیند مقادیرشان معتبر است یا نه. این شبه‌کلاس‌ها عبارت‌اند از `:valid` و `:invalid`. در این بخش، از CSS زیر استفاده می‌کنیم که یک علامت تیک (✓) کنار ورودی‌های معتبر و یک ضربدر (X) کنار ورودی‌های نامعتبر قرار می‌دهد.

```css
div {
  margin-bottom: 10px;
  position: relative;
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

این تکنیک همچنین به یک المان `<span>` بعد از المان فرم نیاز دارد که به عنوان نگهدارندهٔ آیکن‌ها عمل کند. این کار لازم است، چون بعضی از نوع‌های input در بعضی مرورگرها آیکن‌هایی را که مستقیماً بعد از خودشان قرار می‌گیرند خوب نمایش نمی‌دهند.

### الزامی کردن ورودی

می‌توانید از ویژگی `required` به عنوان راهی ساده استفاده کنید تا قبل از اجازهٔ ارسال فرم، وارد کردن مقدار الزامی شود:

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input type="text" id="uname" name="name" required />
    <span class="validity"></span>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

```css hidden
div {
  margin-bottom: 10px;
  position: relative;
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

نتیجه به این شکل نمایش داده می‌شود:

اگر فرم را بدون وارد کردن نام کاربری ارسال کنید، مرورگر یک پیام خطا نشان می‌دهد.

### طول مقدار ورودی

با استفاده از ویژگی `minlength` می‌توانید حداقل طول (به تعداد کاراکتر) مقدار واردشده را مشخص کنید؛ به همین ترتیب، از `maxlength` برای تعیین حداکثر طول مقدار واردشده، بر حسب کاراکتر، استفاده کنید.

مثال زیر ایجاب می‌کند مقدار واردشده بین ۴ تا ۸ کاراکتر باشد.

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input
      type="text"
      id="uname"
      name="name"
      required
      size="10"
      placeholder="Username"
      minlength="4"
      maxlength="8" />
    <span class="validity"></span>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

```css hidden
div {
  margin-bottom: 10px;
  position: relative;
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

نتیجه به این شکل نمایش داده می‌شود:

اگر فرم را با کمتر از ۴ کاراکتر ارسال کنید، پیام خطای مناسبی دریافت می‌کنید (که در مرورگرهای مختلف متفاوت است). اگر بخواهید بیش از ۸ کاراکتر وارد کنید، مرورگر اجازه نمی‌دهد.

> [!NOTE]
> اگر `minlength` را مشخص کنید اما `required` را مشخص نکنید، ورودی معتبر در نظر گرفته می‌شود؛ زیرا کاربر ملزم به وارد کردن مقدار نیست.

### مشخص کردن pattern

میتوانید از attribute [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) برای تعیین یک عبارت باقاعده (regular expression) استفاده کنید که مقدار واردشده باید با آن مطابقت داشته باشد تا معتبر در نظر گرفته شود (برای آشنایی سریع با استفاده از عبارتهای باقاعده در اعتبارسنجی ورودیها، [اعتبارسنجی با عبارت باقاعده](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation#validating_against_a_regular_expression) را ببینید).

مثال زیر مقدار را به ۴ تا ۸ نویسه (character) محدود میکند و الزام میکند که فقط شامل حروف کوچک (lowercase) باشد.

```html
<form>
  <div>
    <label for="uname">Choose a username: </label>
    <input
      type="text"
      id="uname"
      name="name"
      required
      size="45"
      pattern="[a-z]{4,8}" />
    <span class="validity"></span>
    <p>Usernames must be lowercase and 4-8 characters in length.</p>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

```css hidden
div {
  margin-bottom: 10px;
  position: relative;
}

p {
  font-size: 80%;
  color: #999999;
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

این مثال به این شکل رندر میشود:

## مثالها

نمونه‌های خوبی از inputهای متنی در بستر واقعی را می‌توانید در مقالات [اولین فرم HTML شما](/en-US/docs/Learn_web_development/Extensions/Forms/Your_first_form) و [چگونه یک فرم HTML را ساختاربندی کنیم](/en-US/docs/Learn_web_development/Extensions/Forms/How_to_structure_a_web_form) ببینید.

## خلاصه‌ٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">مقدار</a></strong></td>
      <td>رشته‌ای (string) که متن موجود در فیلد متنی را نمایش می‌دهد.</td>
    </tr>
    <tr>
      <td><strong>رویدادها</strong></td>
      <td><code>change</code> و <code>input</code></td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های رایج پشتیبانی‌شده</strong></td>
      <td>
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete"><code>autocomplete</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#list"><code>list</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#maxlength"><code>maxlength</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#minlength"><code>minlength</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#pattern"><code>pattern</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#placeholder"><code>placeholder</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#readonly"><code>readonly</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#required"><code>required</code></a> و
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#size"><code>size</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های IDL</strong></td>
      <td><a href="/en-US/docs/Web/HTML/Reference/Elements/input#list"><code>list</code></a>, <code>value</code></td>
    </tr>
    <tr>
      <td><strong>رابط DOM</strong></td>
      <td><code>HTMLInputElement</code></td>
    </tr>
    <tr>
      <td><strong>نقش ARIA ضمنی</strong></td>
      <td>
        هنگامی که attribute <code>list</code> وجود نداشته باشد:
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role">textbox</a></code><br />
        هنگامی که attribute <code>list</code> وجود داشته باشد: <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role">combobox</a></code>
      </td>
    </tr>
  </tbody>
</table>

## See also

- [فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)
- عنصر `input` و اینترفیس `HTMLInputElement` که بر پایهٔ آن ساخته شده است.
- [`<input type="search">`](/en-US/docs/Web/HTML/Reference/Elements/input/search)
- عنصر `textarea`: ورودی متن چندخطی