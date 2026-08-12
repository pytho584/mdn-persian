---
title: <input type="tel"> HTML attribute value
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/tel
translated_by: n8n + AI
---

# \<input type="tel"> HTML attribute value

element‌های `<input>` از نوع `tel` برای وارد کردن و ویرایش شماره تلفن توسط کاربر استفاده می‌شوند. برخلاف [`<input type="email">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/email/) و [`<input type="url">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/url/)، مقدار این ورودی قبل از ارسال فرم به‌طور خودکار برای قالب خاصی اعتبارسنجی نمی‌شود، چون قالب‌های شماره تلفن در سراسر جهان بسیار متنوع هستند.

```html
<label for="phone">
  Enter your phone number:<br />
  <small>Format: 123-456-7890</small>
</label>

<input
  type="tel"
  id="phone"
  name="phone"
  pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
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

با اینکه ورودی‌های نوع `tel` از نظر عملکردی با ورودی‌های متنی استاندارد یکسان‌اند، کاربردهای مفیدی دارند؛ مهم‌ترین آن‌ها این است که مرورگرهای موبایل — به‌ویژه تلفن‌های هوشمند — ممکن است یک صفحه‌کلید سفارشی بهینه‌شده برای وارد کردن شماره تلفن نمایش دهند. استفاده از یک نوع ورودی خاص برای شماره تلفن، افزودن اعتبارسنجی و مدیریت سفارشی شماره‌ها را نیز راحت‌تر می‌کند.

> **نکته:** مرورگرهایی که از نوع `tel` پشتیبانی نمی‌کنند، به یک ورودی متنی استاندارد ([`text`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/text/)) برمی‌گردند.

### مقدار

attribute [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) در element `<input>` حاوی رشته‌ای است که یا یک شماره تلفن را نشان می‌دهد یا یک رشته خالی (`""`) است.

### ویژگی‌های اضافی

علاوه بر [attributeهای سراسری](../../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) و attributeهایی که روی همه elementهای `<input>` بدون توجه به نوعشان کار می‌کنند، ورودی‌های شماره تلفن از attributeهای زیر پشتیبانی می‌کنند.

#### list

مقدار attribute «list» برابر با [`id`](../../../../../../../../en-US/docs/Web/API/Element/id/) یک element `<datalist>` در همان سند است. `<datalist>` فهرستی از مقادیر از پیش تعریف‌شده برای پیشنهاد به کاربر فراهم می‌کند. هر مقداری در این فهرست که با [`type`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#type) سازگار نباشد، در گزینه‌های پیشنهادی قرار نمی‌گیرد. مقادیر ارائه‌شده فقط پیشنهاد هستند، نه الزام؛ کاربر می‌تواند از این فهرست انتخاب کند یا مقدار دیگری وارد کند.

#### maxlength

حداکثر طول رشته (بر حسب [واحدهای UTF-16](../../../../../../../../en-US/docs/Glossary/UTF-16/)) که کاربر می‌تواند در فیلد شماره تلفن وارد کند. این مقدار باید یک عدد صحیح ۰ یا بزرگ‌تر باشد. اگر `maxlength` مشخص نشده باشد یا مقدار نامعتبری تعیین شود، فیلد شماره تلفن حداکثر طول ندارد. این مقدار همچنین باید بزرگ‌تر یا مساوی مقدار `minlength` باشد.

اگر طول متن واردشده در فیلد بیشتر از `maxlength` (بر حسب [واحدهای UTF-16](../../../../../../../../en-US/docs/Glossary/UTF-16/)) باشد، ورودی در [اعتبارسنجی محدودیت‌ها](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) ناموفق خواهد بود. اعتبارسنجی محدودیت‌ها فقط زمانی اعمال می‌شود که کاربر مقدار را تغییر دهد.

#### minlength

حداقل طول رشته (بر حسب [واحدهای UTF-16](../../../../../../../../en-US/docs/Glossary/UTF-16/)) که کاربر می‌تواند در فیلد شماره تلفن وارد کند. این مقدار باید یک عدد صحیح غیرمنفی و کوچک‌تر یا مساوی مقدار `maxlength` باشد. اگر `minlength` مشخص نشده باشد یا مقدار نامعتبری تعیین شود، ورودی شماره تلفن حداقل طول ندارد.

اگر طول متن واردشده در فیلد کمتر از `minlength` واحد کد UTF-16 باشد، فیلد شماره تلفن در [اعتبارسنجی محدودیت‌ها](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) ناموفق خواهد بود. اعتبارسنجی محدودیت‌ها فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند.

#### pattern

ویژگی `pattern`، وقتی مشخص شده باشد، یک عبارت منظم است که [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) ورودی باید با آن مطابقت داشته باشد تا مقدار از [اعتبارسنجی محدودیت‌ها](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) عبور کند. این عبارت باید یک عبارت منظم معتبر جاوااسکریپت باشد؛ همان‌طور که در نوع `RegExp` استفاده می‌شود و در [راهنمای عبارت‌های منظم](../../../../../../../../en-US/docs/Web/JavaScript/Guide/Regular_expressions/) مستند شده است. هنگام کامپایل عبارت منظم، پرچم `'u'` تنظیم می‌شود تا الگو به‌عنوان دنباله‌ای از نقطه‌های کد یونیکد در نظر گرفته شود، نه به‌صورت ASCII. دور متن الگو نباید اسلش جلو قرار دهید.

اگر الگوی مشخص‌شده وجود نداشته باشد یا نامعتبر باشد، هیچ عبارت منظمی اعمال نمی‌شود و این ویژگی کاملاً نادیده گرفته می‌شود.

> \[!NOTE] از ویژگی [`title`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#title) برای مشخص‌کردن متنی استفاده کنید که بیشتر مرورگرها آن را به‌صورت tooltip نمایش می‌دهند تا الزامات مطابقت با الگو را توضیح دهد. همچنین بهتر است متن توضیحی دیگری در نزدیکی فیلد قرار دهید.

برای جزئیات و مثال، به بخش [اعتبارسنجی الگو](index.md#pattern_validation) در ادامه مراجعه کنید.

#### placeholder

ویژگی `placeholder` رشته‌ای است که راهنمای کوتاهی به کاربر می‌دهد درباره اینکه چه نوع اطلاعاتی در فیلد انتظار می‌رود. این مقدار باید یک کلمه یا عبارت کوتاه باشد که نوع دادهٔ مورد انتظار را نشان دهد، نه یک پیام توضیحی. متن _نباید_ شامل بازگشت به ابتدای خط (carriage return) یا تغذیه خط (line feed) باشد.

اگر محتوای کنترل یک جهت‌گیری خاص (LTR یا RTL) دارد اما لازم است placeholder در جهت مخالف نمایش داده شود، می‌توانید از کاراکترهای قالب‌بندی الگوریتم دوجهتهٔ یونیکد برای تغییر جهت‌گیری درون placeholder استفاده کنید. برای اطلاعات بیشتر، [نحوهٔ استفاده از کنترل‌های یونیکد برای متن دوجهته](https://www.w3.org/International/questions/qa-bidi-unicode-controls) را ببینید.

> \[!NOTE] در صورت امکان از استفاده از ویژگی `placeholder` خودداری کنید. این ویژگی از نظر معنایی به اندازهٔ روش‌های دیگر برای توضیح فرم شما مفید نیست و می‌تواند مشکلات فنی غیرمنتظره‌ای در محتوای شما ایجاد کند. برای اطلاعات بیشتر به [برچسب‌های `<input>`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#labels) مراجعه کنید.

#### readonly

یک ویژگی Boolean است که اگر حضور داشته باشد، یعنی کاربر نمی‌تواند این فیلد را ویرایش کند. با این حال، مقدار (`value`) آن همچنان می‌تواند توسط کد جاوااسکریپت و با تنظیم مستقیم ویژگی `value` در `HTMLInputElement` تغییر کند.

> \[!NOTE] از آنجا که یک فیلد فقط‌خواندنی نمی‌تواند مقداری داشته باشد، `required` روی inputهایی که ویژگی `readonly` نیز مشخص شده است هیچ تأثیری ندارد.

#### size

ویژگی `size` یک مقدار عددی است که نشان می‌دهد فیلد ورودی چند کاراکتر عرض داشته باشد. مقدار باید عددی بزرگ‌تر از صفر باشد و مقدار پیش‌فرض آن 20 است. از آنجا که عرض کاراکترها متفاوت است، این مقدار ممکن است دقیق نباشد و نباید به آن به‌عنوان مقدار دقیق اعتماد کرد؛ فیلد حاصل ممکن است باریک‌تر یا عریض‌تر از تعداد کاراکترهای مشخص‌شده باشد، بسته به کاراکترها و فونت (تنظیمات `font`) در حال استفاده.

این ویژگی _حداکثر_ تعداد کاراکتری که کاربر می‌تواند در فیلد وارد کند را تعیین نمی‌کند. فقط تقریباً مشخص می‌کند که چند کاراکتر در هر لحظه قابل مشاهده است. برای تعیین سقف بالای طول دادهٔ ورودی، از ویژگی [`maxlength`](index.md#maxlength) استفاده کنید.

شماره تلفن یکی از رایج‌ترین انواع داده‌هایی است که در وب جمع‌آوری می‌شود. مثلاً وقتی سایت ثبت‌نام یا فروشگاهی می‌سازید، تقریباً مطمئناً باید از کاربر شماره تلفن بخواهید — چه برای کارهای تجاری و چه برای تماس اضطراری. با این‌که ورود شماره تلفن خیلی عادی است، متأسفانه هیچ راه‌حل «یک‌اندازه برای همه» برای اعتبارسنجی شماره تلفن عملی نیست.

خوشبختانه می‌توانید نیازهای سایت خودتان را در نظر بگیرید و سطح مناسبی از اعتبارسنجی را خودتان پیاده کنید. جزئیات را در بخش [Validation](index.md#validation) ببینید.

#### صفحه‌کلیدهای سفارشی

یکی از مزیت‌های اصلی `<input type="tel">` این است که باعث می‌شود مرورگرهای موبایل یک صفحه‌کلید مخصوص برای وارد کردن شماره تلفن نمایش دهند. مثلاً در ادامه، صفحه‌کلید چند دستگاه را می‌بینید.

| Firefox for Android | WebKit iOS (Safari/Chrome/Firefox) |
| ------------------- | ---------------------------------- |
|                     |                                    |

#### یک ورودی tel ساده

در ساده‌ترین شکل، یک ورودی tel را می‌توان این‌طور پیاده کرد:

```html
<label for="telNo">Phone number:</label>
<input id="telNo" name="telNo" type="tel" />
```

هیچ اتفاق عجیبی اینجا نمی‌افتد. وقتی فرم به سرور ارسال شود، دادهٔ ورودی بالا مثلاً به شکل `telNo=+12125553151` ارسال می‌شود.

#### Placeholderها

گاهی اوقات مفید است که در داخل همان زمینه، راهنمایی بدهید که دادهٔ ورودی باید چه شکلی باشد. این موضوع وقتی اهمیت بیشتری پیدا می‌کند که طراحی صفحه برای هر `<input>` برچسب توصیفی نداشته باشد. اینجا جایی است که **placeholder**ها وارد کار می‌شوند. placeholder مقدار نمونه‌ای است که نشان می‌دهد `value` باید چه فرمی داشته باشد؛ یک مقدار معتبر را نمایش می‌دهد و وقتی مقدار `value` عنصر برابر `""` باشد، داخل جعبهٔ ویرایش دیده می‌شود. به محض اینکه کاربر داده‌ای وارد کند، placeholder ناپدید می‌شود و اگر جعبه خالی شود، دوباره ظاهر می‌شود.

در اینجا یک ورودی `tel` با placeholder با مقدار `123-4567-8901` داریم. توجه کنید که با دستکاری محتوای فیلد، placeholder ناپدید و دوباره ظاهر می‌شود.

```html
<input id="telNo" name="telNo" type="tel" placeholder="123-4567-8901" />
```

#### کنترل اندازهٔ ورودی

می‌توانید هم طول فیزیکی جعبهٔ ورودی و هم حداقل و حداکثر طول متن ورودی را کنترل کنید.

**اندازهٔ فیزیکی عنصر input**

اندازهٔ فیزیکی جعبهٔ ورودی را می‌توان با استفاده از attribute [`size`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#size) کنترل کرد. با این attribute می‌توانید تعیین کنید جعبهٔ ورودی در هر لحظه چند کاراکتر را نشان دهد. مثلاً در این مثال، جعبهٔ ویرایش `tel` به عرض ۲۰ کاراکتر است:

```html
<input id="telNo" name="telNo" type="tel" size="20" />
```

**طول مقدار عنصر**

ویژگی `size` با محدودیت طول شمارهٔ تلفن ورودی جدا است. با استفاده از attribute [`minlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#minlength) می‌توانید حداقل طول مجاز (بر حسب کاراکتر) را برای شماره تلفن واردشده مشخص کنید؛ به همین ترتیب، از [`maxlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#maxlength) برای تعیین حداکثر طول شمارهٔ تلفن ورودی استفاده کنید.

مثال زیر یک جعبهٔ ورودی شماره تلفن با عرض ۲۰ کاراکتر می‌سازد که محتوای آن نباید کمتر از ۹ کاراکتر و بیشتر از ۱۴ کاراکتر باشد.

```html
<input
  id="telNo"
  name="telNo"
  type="tel"
  size="20"
  minlength="9"
  maxlength="14" />
```

> \[!NOTE] ویژگی‌های بالا بر [اعتبارسنجی](index.md#validation) تأثیر می‌گذارند — در مثال بالا، اگر طول مقدار کمتر از ۹ کاراکتر یا بیشتر از ۱۴ باشد، ورودی‌ها نامعتبر در نظر گرفته می‌شوند. اکثر مرورگرها حتی اجازه نمی‌دهند مقداری بیشتر از حداکثر طول وارد کنید.

#### ارائه گزینه‌های پیش‌فرض

**ارائه یک مقدار پیش‌فرض با استفاده از ویژگی value**

مثل همیشه، می‌توانید با تنظیم ویژگی [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) یک مقدار پیش‌فرض برای جعبه ورودی `tel` تعیین کنید:

```html
<input id="telNo" name="telNo" type="tel" value="333-4444-4444" />
```

**ارائه مقادیر پیشنهادی**

برای گام فراتر، می‌توانید فهرستی از مقادیر پیش‌فرض شماره تلفن ارائه دهید که کاربر از میان آن‌ها انتخاب کند. برای این کار، از ویژگی [`list`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#list) استفاده کنید. این کار کاربر را به آن گزینه‌ها محدود نمی‌کند، اما به او امکان می‌دهد شماره‌های تلفن پرکاربرد را سریع‌تر انتخاب کند. همچنین این ویژگی به [`autocomplete`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#autocomplete) هم راهنمایی می‌دهد. ویژگی `list` شناسه عنصر `<datalist>` را مشخص می‌کند که به نوبه خود برای هر مقدار پیشنهادی، یک عنصر `<option>` دارد؛ `value` هر `option`، مقدار پیشنهادی متناظر برای جعبه ورودی شماره تلفن است.

```html
<label for="telNo">Phone number: </label>
<input id="telNo" name="telNo" type="tel" list="defaultTels" />

<datalist id="defaultTels">
  <option value="111-1111-1111"></option>
  <option value="122-2222-2222"></option>
  <option value="333-3333-3333"></option>
  <option value="344-4444-4444"></option>
</datalist>
```

با قرار دادن عنصر `<datalist>` و `<option>`های آن، مرورگر مقادیر مشخص‌شده را به‌عنوان مقادیر احتمالی شماره تلفن پیشنهاد می‌دهد؛ معمولاً این پیشنهادها به صورت یک پاپ‌آپ یا منوی کشویی نمایش داده می‌شوند. اگرچه تجربه کاربری دقیق ممکن است از مرورگری به مرورگر دیگر متفاوت باشد، معمولاً کلیک در جعبه ویرایش، یک منوی کشویی از شماره تلفن‌های پیشنهادی نمایش می‌دهد. سپس وقتی کاربر تایپ می‌کند، فهرست طوری تنظیم می‌شود که فقط مقادیر مطابقِ فیلترشده نمایش داده شود. هر کاراکتر تایپ‌شده فهرست را محدودتر می‌کند تا کاربر یک انتخاب کند یا مقدار سفارشی تایپ کند.

در اینجا یک اسکرین‌شات از شکل احتمالی آن می‌بینید:

### اعتبارسنجی

همانطور که قبلاً هم اشاره کردیم، ارائه یک راه‌حل اعتبارسنجی سمت کلاینت که برای همه شماره تلفن‌ها یکسان و مناسب باشد، نسبتاً دشوار است. پس چه می‌توانیم بکنیم؟ بیایید چند گزینه را بررسی کنیم.

> \[!WARNING] اعتبارسنجی HTML جایگزینی برای اسکریپت‌های سمت سرور که قبل از ورود داده به پایگاه داده، از قالب صحیح آن اطمینان حاصل می‌کنند _نیست_. خیلی راحت می‌شود HTML را طوری تغییر داد که اعتبارسنجی را دور بزند یا آن را کاملاً حذف کند. همچنین ممکن است کسی HTML شما را به طور کامل دور بزند و داده را مستقیماً به سرور ارسال کند. اگر کد سمت سرور شما داده دریافت‌شده را اعتبارسنجی نکند، در صورت ورود داده‌های با قالب اشتباه (یا داده‌ای که خیلی بزرگ است، نوع اشتباهی دارد و موارد مشابه) به پایگاه داده، فاجعه رخ می‌دهد.

#### اجباری کردن شماره تلفن

می‌توانید با استفاده از ویژگی [`required`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#required) کاری کنید که ورودی خالی نامعتبر باشد و به سرور ارسال نشود. برای مثال، از این HTML استفاده می‌کنیم:

```html
<form>
  <div>
    <label for="telNo">Enter a telephone number (required): </label>
    <input id="telNo" name="telNo" type="tel" required />
    <span class="validity"></span>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

#### اعتبارسنجی با الگو (Pattern validation)

اگر می‌خواهید اعداد واردشده را بیشتر محدود کنید تا با یک الگوی خاص مطابقت داشته باشند، می‌توانید از [`pattern`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#pattern) استفاده کنید. این ویژگی یک \{{Glossary("regular expression")\}} (عبارت منظّم) را به عنوان مقدار می‌پذیرد که مقدار واردشده باید با آن مطابقت کند.

در این مثال از همان CSS قبلی استفاده می‌کنیم، اما HTML را به شکل زیر تغییر داده‌ایم:

```html
<form>
  <div>
    <label for="telNo">
      Enter a telephone number (in the form xxx-xxx-xxxx):
    </label>
    <input
      id="telNo"
      name="telNo"
      type="tel"
      required
      pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}" />
    <span class="validity"></span>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
```

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
  color: darkred;
}

input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
  color: #009000;
}
```

توجه کنید که مقدار واردشده تا زمانی که با الگوی `xxx-xxx-xxxx` مطابقت نداشته باشد، نامعتبر گزارش می‌شود؛ مثلاً `41-323-421` پذیرفته نمی‌شود. `800-MDN-ROCKS` هم پذیرفته نمی‌شود. اما `865-555-6502` پذیرفته می‌شود. این الگوی خاص فقط برای برخی منطقه‌های جغرافیایی (locales) مناسب است — در یک برنامه واقعی احتمالاً باید الگو را بر اساس locale کاربر تغییر دهید.

### مثال‌ها

در این مثال، یک عنصر \{{htmlelement("select")\}} داریم که به کاربر اجازه می‌دهد کشور خود را انتخاب کند، و مجموعه‌ای از `<input type="tel">` برای وارد کردن هر بخش از شماره تلفن. هیچ دلیلی ندارد که نتوانید چندین `tel` input داشته باشید.

هر input دارای ویژگی [`placeholder`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#placeholder) است تا به کاربران بینا راهنمایی کند چه چیزی وارد کنند، ویژگی [`pattern`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#pattern) برای اعمال تعداد کاراکترهای مشخص در بخش مورد نظر، و ویژگی [`aria-label`](../../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label/) که برای کاربران screen reader (صفحه‌خوان) توضیحی را می‌خواند.

````markdown
# مثال: انتخاب کشور و وارد کردن شماره تلفن

در این مثال یک فرم HTML نشان داده شده است که کاربر ابتدا کشور خود را از یک فهرست انتخابی (`<select>`) انتخاب می‌کند و سپس شماره تلفن را در سه فیلد جداگانه وارد می‌کند. با تغییر کشور، ویژگی‌های `pattern`، `placeholder` و `aria-label` این فیلدها به‌صورت پویا تغییر می‌کنند تا با قالب شماره تلفن آن کشور یا منطقه هماهنگ شوند.

## HTML

```html
<form>
  <div>
    <label for="country">Choose your country:</label>
    <select id="country" name="country">
      <option>UK</option>
      <option selected>US</option>
      <option>Germany</option>
    </select>
  </div>
  <div>
    <p>Enter your telephone number:</p>
    <span class="areaDiv">
      <input
        id="areaNo"
        name="areaNo"
        type="tel"
        required
        placeholder="Area code"
        pattern="[0-9]{3}"
        aria-label="Area code" />
      <span class="validity"></span>
    </span>
    <span class="number1Div">
      <input
        id="number1"
        name="number1"
        type="tel"
        required
        placeholder="First part"
        pattern="[0-9]{3}"
        aria-label="First part of number" />
      <span class="validity"></span>
    </span>
    <span class="number2Div">
      <input
        id="number2"
        name="number2"
        type="tel"
        required
        placeholder="Second part"
        pattern="[0-9]{4}"
        aria-label="Second part of number" />
      <span class="validity"></span>
    </span>
  </div>
  <div>
    <button>Submit</button>
  </div>
</form>
````

### JavaScript

جاوااسکریپت این مثال شامل یک event handler به نام `onchange` است که هنگام تغییر مقدار `<select>`، ویژگی‌های `pattern`، `placeholder` و `aria-label` عناصر `<input>` را متناسب با قالب شماره تلفن آن کشور یا منطقه به‌روزرسانی می‌کند.

```js
const selectElem = document.querySelector("select");
const inputElems = document.querySelectorAll("input");

selectElem.onchange = () => {
  for (const e of inputElems) {
    e.value = "";
  }

  if (selectElem.value === "US") {
    inputElems[2].parentNode.style.display = "inline";

    inputElems[0].placeholder = "Area code";
    inputElems[0].pattern = "[0-9]{3}";

    inputElems[1].placeholder = "First part";
    inputElems[1].pattern = "[0-9]{3}";
    inputElems[1].setAttribute("aria-label", "First part of number");

    inputElems[2].placeholder = "Second part";
    inputElems[2].pattern = "[0-9]{4}";
    inputElems[2].setAttribute("aria-label", "Second part of number");
  } else if (selectElem.value === "UK") {
    inputElems[2].parentNode.style.display = "none";

    inputElems[0].placeholder = "Area code";
    inputElems[0].pattern = "[0-9]{3,6}";

    inputElems[1].placeholder = "Local number";
    inputElems[1].pattern = "[0-9]{4,8}";
    inputElems[1].setAttribute("aria-label", "Local number");
  } else if (selectElem.value === "Germany") {
    inputElems[2].parentNode.style.display = "inline";

    inputElems[0].placeholder = "Area code";
    inputElems[0].pattern = "[0-9]{3,5}";

    inputElems[1].placeholder = "First part";
    inputElems[1].pattern = "[0-9]{2,4}";
    inputElems[1].setAttribute("aria-label", "First part of number");

    inputElems[2].placeholder = "Second part";
    inputElems[2].pattern = "[0-9]{4}";
    inputElems[2].setAttribute("aria-label", "Second part of number");
  }
};
```

### توضیح

این ایده‌ی جالبی است و یک راه‌حل بالقوه برای مسئله‌ی کار با شماره‌تلفن‌های بین‌المللی ارائه می‌کند. البته برای پوشش دادن همه‌ی کشورها باید مثال را گسترش دهید؛ این کار به تلاش زیادی نیاز دارد و باز هم هیچ تضمینی وجود ندارد که کاربران شماره را به‌درستی وارد کنند. شاید این سؤال پیش بیاید که آیا انجام این همه کار در سمت کلاینت (client-side) ارزش دارد، وقتی می‌توانید به کاربر اجازه دهید شماره را در هر قالبی که خواست وارد کند و بعد آن را در سمت سرور (server-side) اعتبارسنجی و پاکسازی کنید. انتخاب نهایی با خود شماست.

### CSS

استایل‌های استفاده‌شده در این مثال به صورت زیر است:

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
  color: darkred;
}
```

```css
input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
  color: #009000;
}
```

### خلاصه فنی

| **مقدار**                          | یک string که شماره تلفن را نشان می‌دهد، یا خالی.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **رویدادها**                       | change و input                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **attributeهای رایج پشتیبانی‌شده** | [`autocomplete`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#autocomplete)، [`list`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#list)، [`maxlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#maxlength)، [`minlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#minlength)، [`pattern`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#pattern)، [`placeholder`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#placeholder)، [`readonly`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#readonly) و [`size`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#size) |
| **IDL attributeها**                | `list`، `selectionStart`، `selectionEnd`، `selectionDirection` و `value`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **رابط DOM**                       | `HTMLInputElement`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **نقش ضمنی ARIA**                  | <p>بدون attribute <code>list</code>: <a href="../../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role/"><code>textbox</code></a><br>با attribute <code>list</code>: <a href="../../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role/"><code>combobox</code></a></p>                                                                                                                                                                                                                                                                                                                                                                                                                                             |

### مشخصات

### سازگاری مرورگر

### همچنین ببینید

* [راهنمای فرم‌های HTML](../../../../../../../../en-US/docs/Learn_web_development/Extensions/Forms/)
* [`<input>`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/)
  * [`<input type="text">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/text/)
  * [`<input type="email">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/email/)
