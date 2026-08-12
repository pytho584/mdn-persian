---
title: <input type="email"> HTML attribute value
source: >-
  https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/email
translated_by: n8n + AI
---

# \<input type="email"> HTML attribute value

عنصرهای `<input>` از نوع **`email`** به کاربر امکان می‌دهند یک نشانی ایمیل را وارد کند و ویرایش کند؛ یا اگر ویژگی [`multiple`](../../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/multiple/) تعیین شده باشد، فهرستی از نشانی‌های ایمیل را وارد کند.

```html
<label for="email">Enter your example.com email:</label>

<input type="email" id="email" pattern=".+@example\.com" size="30" required />
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

مقدار ورودی به‌صورت خودکار اعتبارسنجی می‌شود تا مطمئن شود قبل از ارسال فرم، یا خالی است یا یک نشانی ایمیل با قالب درست (یا فهرستی از نشانی‌ها) باشد. شبه‌کلاس‌های [`:valid`](../../../../../../../../en-US/docs/Web/CSS/:valid/) و [`:invalid`](../../../../../../../../en-US/docs/Web/CSS/:invalid/) به‌صورت خودکار و در صورت لزوم اعمال می‌شوند تا نشان دهند مقدار فعلی فیلد یک نشانی ایمیل معتبر است یا نه.

### Value

ویژگی [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) عنصر `<input>` رشته‌ای را نگه می‌دارد که به‌صورت خودکار از نظر مطابقت با دستور زبان ایمیل اعتبارسنجی می‌شود. به‌طور مشخص، سه قالب مقدار وجود دارد که اعتبارسنجی را با موفقیت پاس می‌کنند:

1. رشتهٔ خالی (`""`) که نشان می‌دهد کاربر مقداری وارد نکرده یا مقدار حذف شده است.
2. یک نشانی ایمیل منفرد با قالب درست. این لزوماً به این معنا نیست که ایمیل وجود دارد، بلکه حداقل قالب آن درست است. یعنی `username@domain` یا `username@domain.tld`. البته قضیه به همین سادگی نیست؛ بخش [Validation](index.md#validation) را ببینید که یک [عبارت باقاعده (regular expression)](../../../../../../../../en-US/docs/Glossary/Regular_expression/) منطبق با الگوریتم اعتبارسنجی ایمیل ارائه می‌دهد.
3. فقط اگر ویژگی [`multiple`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#multiple) تعیین شده باشد، مقدار می‌تواند فهرستی از نشانی‌های ایمیل با قالب درست باشد که با کاما از هم جدا شده‌اند. هر فضای خالی ابتدا یا انتهای هر نشانی در فهرست حذف می‌شود.

بخش [Validation](index.md#validation) را برای جزئیات نحوهٔ اعتبارسنجی قالب نشانی‌های ایمیل ببینید.

### Additional attributes

علاوه بر [ویژگی‌های سراسری](../../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) و ویژگی‌هایی که روی همهٔ عناصر `<input>` بدون توجه به نوعشان عمل می‌کنند، ورودی‌های `email` از ویژگی‌های زیر پشتیبانی می‌کنند.

> \[!NOTE] ویژگی سراسری [`autocorrect`](../../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect/) را می‌توان به ورودی‌های ایمیل اضافه کرد، اما حالت ذخیره‌شده همیشه `off` است.

#### list

مقدار ویژگی `list` برابر با [`id`](../../../../../../../../en-US/docs/Web/API/Element/id/) یک عنصر `<datalist>` در همان سند است. `<datalist>` فهرستی از مقادیر ازپیش‌تعریف‌شده را برای پیشنهاد به کاربر در این ورودی فراهم می‌کند. هر مقداری در فهرست که با [`type`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#type) سازگار نباشد در گزینه‌های پیشنهادی قرار نمی‌گیرد. مقادیر ارائه‌شده پیشنهاد هستند، نه الزام؛ کاربران می‌توانند از این فهرست ازپیش‌تعریف‌شده انتخاب کنند یا مقدار دیگری وارد کنند.

#### maxlength

بیشترین طول رشته (بر حسب [UTF-16 code units](../../../../../../../../en-US/docs/Glossary/UTF-16/)) که کاربر می‌تواند در ورودی `email` وارد کند. این مقدار باید یک عدد صحیح ۰ یا بزرگ‌تر باشد. اگر `maxlength` مشخص نشده باشد یا مقدار نامعتبری داشته باشد، ورودی `email` حداکثر طول ندارد. این مقدار همچنین باید بزرگ‌تر یا مساوی مقدار `minlength` باشد.

اگر طول مقدار متنی فیلد بیشتر از `maxlength` (بر حسب \{{glossary("UTF-16", "واحد کد UTF-16")\}}) باشد، ورودی در [اعتبارسنجی محدودیت‌ها](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) رد می‌شود. اعتبارسنجی محدودیت‌ها فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند.

#### minlength

حداقل طول رشته (بر حسب \{{glossary("UTF-16", "واحد کد UTF-16")\}}) که کاربر می‌تواند در ورودی `email` وارد کند. این مقدار باید یک عدد صحیح نامنفی و کوچک‌تر یا مساوی مقدار مشخص‌شده در `maxlength` باشد. اگر `minlength` مشخص نشود یا مقدار نامعتبری داشته باشد، ورودی `email` حداقل طولی نخواهد داشت.

اگر طول متن واردشده در فیلد کمتر از `minlength` (بر حسب \{{glossary("UTF-16", "واحد کد UTF-16")\}}) باشد، ورودی در [اعتبارسنجی محدودیت‌ها](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) رد می‌شود. اعتبارسنجی محدودیت‌ها فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند.

#### multiple

یک ویژگی Boolean که در صورت وجود، نشان می‌دهد کاربر می‌تواند فهرستی از چندین آدرس ایمیل را با جداکننده کاما و به‌صورت اختیاری با فاصله وارد کند. برای مثال به [اجازه دادن به چند آدرس ایمیل](index.md#allowing_multiple_email_addresses) یا [HTML attribute: multiple](../../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/multiple/) برای جزئیات بیشتر مراجعه کنید.

> \[!NOTE] معمولاً اگر ویژگی [`required`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#required) را مشخص کنید، کاربر باید یک آدرس ایمیل معتبر وارد کند تا فیلد معتبر در نظر گرفته شود. اما اگر ویژگی `multiple` را اضافه کنید، فهرستی با صفر آدرس ایمیل (یک رشتهٔ خالی یا رشتۀ کاملاً شامل فاصله) یک مقدار معتبر محسوب می‌شود. به عبارت دیگر، وقتی `multiple` مشخص شده باشد، کاربر حتی نیازی به وارد کردن یک آدرس ایمیل ندارد، صرف‌نظر از مقدار `required`.

#### pattern

ویژگی `pattern`، زمانی که مشخص شود، یک عبارت باقاعده (regular expression) است که [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) ورودی باید با آن مطابقت داشته باشد تا مقدار از [اعتبارسنجی محدودیت‌ها](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) عبور کند. این عبارت باید یک عبارت باقاعدهٔ معتبر جاوااسکریپت باشد، مطابق نوع \{{jsxref("RegExp")\}} و مطابق مستندات [راهنمای عبارت‌های باقاعده](../../../../../../../../en-US/docs/Web/JavaScript/Guide/Regular_expressions/)؛ هنگام کامپایل عبارت باقاعده پرچم `'u'` مشخص می‌شود تا الگو به‌عنوان دنباله‌ای از کدپوینت‌های Unicode در نظر گرفته شود، نه به‌عنوان \{{Glossary("ASCII")\}}. نباید دور متن الگو از اسلش (forward slash) استفاده کنید.

اگر الگوی مشخص‌شده مشخص نباشد یا نامعتبر باشد، هیچ عبارت باقاعده‌ای اعمال نمی‌شود و این ویژگی کاملاً نادیده گرفته می‌شود.

> \[!NOTE] از ویژگی [`title`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#title) برای مشخص کردن متنی استفاده کنید که بیشتر مرورگرها آن را به‌عنوان tooltip نمایش می‌دهند تا نیازمندی‌های مطابقت با الگو را توضیح دهد. همچنین باید متن توضیحی دیگری در نزدیکی آن قرار دهید.

برای جزئیات و مثال به بخش [اعتبارسنجی الگو](index.md#pattern_validation) مراجعه کنید.

#### `placeholder`

ویژگی `placeholder` یک رشته است که یک راهنمای کوتاه به کاربر در مورد نوع اطلاعات مورد انتظار در فیلد ارائه می‌دهد. باید یک کلمه یا عبارت کوتاه باشد که نوع دادهٔ مورد انتظار را نشان می‌دهد، نه یک پیام توضیحی. متن _نباید_ شامل carriage return یا line feed باشد.

اگر محتوای کنترل یک جهت‌دار بودن (\{{Glossary("LTR")\}} یا \{{Glossary("RTL")\}}) دارد اما نیاز است placeholder را در جهت مخالف نمایش دهد، می‌توانید از کاراکترهای قالب‌بندی الگوریتم دوجهتی Unicode برای تغییر جهت‌دار بودن درون placeholder استفاده کنید؛ برای اطلاعات بیشتر به [How to use Unicode controls for bidi text](https://www.w3.org/International/questions/qa-bidi-unicode-controls) مراجعه کنید.

#### `readonly`

یک ویژگی (attribute) بولی است که اگر وجود داشته باشد، یعنی کاربر نمی‌تواند این فیلد را ویرایش کند. با این حال، مقدار آن (`value`) همچنان می‌تواند توسط کد جاوااسکریپت و با تنظیم مستقیم ویژگی `value` در `HTMLInputElement` تغییر کند.

> **نکته:** چون یک فیلد فقط‌خواندنی نمی‌تواند ارزشی داشته باشد، ویژگی `required` هیچ اثری روی ورودی‌هایی که ویژگی `readonly` هم روی آن‌ها تنظیم شده است ندارد.

#### `size`

ویژگی `size` یک مقدار عددی است که نشان می‌دهد فیلد ورودی چند کاراکتر عرض داشته باشد. مقدار باید عددی بزرگ‌تر از صفر باشد و مقدار پیش‌فرض آن ۲۰ است. از آنجا که عرض کاراکترها متفاوت است، این مقدار ممکن است دقیق نباشد و نباید به دقت آن تکیه کرد؛ نتیجه ممکن است باریک‌تر یا پهن‌تر از تعداد کاراکتر مشخص‌شده باشد، بسته به کاراکترها و فونت (تنظیمات \{{cssxref("font")\}}) در حال استفاده.

این ویژگی **محدودیتی** برای تعداد کاراکترهایی که کاربر می‌تواند در فیلد وارد کند تعیین نمی‌کند؛ فقط مشخص می‌کند که تقریباً چند کاراکتر در هر لحظه قابل مشاهده است. برای تعیین حداکثر طول داده ورودی، از ویژگی [`maxlength`](index.md#maxlength) استفاده کنید.

### استفاده از ورودی‌های ایمیل

آدرس‌های ایمیل از جمله پرکاربردترین داده‌های متنی هستند که در وب وارد می‌شوند؛ برای ورود به وب‌سایت‌ها، درخواست اطلاعات، تأیید سفارش، وب‌میل و غیره استفاده می‌شوند. به همین دلیل، نوع ورودی `email` می‌تواند کار شما را به‌عنوان توسعه‌دهنده وب بسیار ساده‌تر کند، زیرا در ساخت رابط کاربری و منطق مربوط به آدرس‌های ایمیل به شما کمک می‌کند. وقتی یک ورودی ایمیل با مقدار درست `type` یعنی `email` می‌سازید، اعتبارسنجی خودکار انجام می‌شود که متن واردشده حداقل از نظر شکل، یک آدرس ایمیل معتبر باشد. این کار می‌تواند از اشتباه تایپی کاربر یا وارد کردن آدرس نامعتبر جلوگیری کند.

با این حال، مهم است بدانید این برای اطمینان از اینکه متن واردشده یک آدرس ایمیل واقعاً موجود است، متعلق به کاربر سایت است یا به هر شکل دیگری قابل قبول است کافی نیست؛ فقط تضمین می‌کند که مقدار فیلد برای یک آدرس ایمیل به‌درستی قالب‌بندی شده است.

> **نکته:** همچنین بسیار مهم است به یاد داشته باشید که کاربر می‌تواند HTML شما را در پشت صحنه دستکاری کند، بنابراین سایت شما **نباید** برای هیچ هدف امنیتی به این اعتبارسنجی تکیه کند. شما **باید** آدرس ایمیل را در سمت سرور در هر تراکنشی که متن ارائه‌شده ممکن است پیامدهای امنیتی داشته باشد تأیید کنید.

#### یک ورودی ایمیل ساده

در حال حاضر، همه مرورگرهایی که این عنصر را پیاده‌سازی می‌کنند، آن را به‌صورت یک فیلد متنی استاندارد با قابلیت‌های اعتبارسنجی پایه پیاده‌سازی می‌کنند. با این حال، مشخصات به مرورگرها اجازه می‌دهد در این زمینه انعطاف داشته باشند. برای مثال، این عنصر می‌تواند با دفترچه آدرس داخلی دستگاه کاربر یکپارچه شود تا امکان انتخاب آدرس ایمیل از آن فهرست فراهم شود. در ساده‌ترین شکل، یک ورودی `email` را می‌توان این‌گونه پیاده‌سازی کرد:

```html
<input id="emailAddress" type="email" />
```

توجه کنید که وقتی خالی باشد یا یک آدرس ایمیل با قالب معتبر وارد شود، معتبر در نظر گرفته می‌شود، اما در غیر این صورت معتبر نیست. با افزودن ویژگی [`required`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#required)، فقط آدرس‌های ایمیلی که شکل معتبری دارند مجاز می‌شوند؛ دیگر وقتی فیلد خالی است معتبر در نظر گرفته نمی‌شود.

#### پذیرش چند آدرس ایمیل

با افزودن ویژگی بولی [`multiple`](../../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/multiple/)، ورودی می‌تواند چند آدرس ایمیل را بپذیرد.

```html
<input id="emailAddress" type="email" multiple />
```

وقتی ویژگی `multiple` استفاده میشود، ورودی زمانی معتبر است که یک آدرس ایمیل تکی وارد شده باشد، یا هر تعداد آدرس ایمیل که با کاما و بهصورت اختیاری با تعدادی کاراکتر فضای خالی (whitespace) از هم جدا شده باشند.

> \[!NOTE] وقتی `multiple` استفاده میشود، مقدار مجاز است خالی باشد.

چند مثال از رشته‌های معتبر هنگام استفاده از `multiple`:

* `""`
* `"me@example"`
* `"me@example.org"`
* `"me@example.org,you@example.org"`
* `"me@example.org, you@example.org"`
* `"me@example.org,you@example.org, us@example.org"`

چند مثال از رشته‌های نامعتبر:

* `","`
* `"me"`
* `"me@example.org you@example.org"`

#### Placeholder

گاهی اوقات مفید است که یک راهنمای درون‌متنی (in-context hint) ارائه کنیم تا مشخص شود دادهٔ ورودی باید چه شکلی باشد. این موضوع به‌ویژه وقتی اهمیت پیدا می‌کند که طراحی صفحه برچسب‌های توصیفی برای هر `input` نداشته باشد. اینجا جایی است که **placeholder**ها وارد عمل می‌شوند. placeholder مقداری است که با نمایش یک مثال از مقدار معتبر، شکل مورد انتظار `value` را نشان می‌دهد؛ این مثال در جعبهٔ ورودی نمایش داده می‌شود وقتی مقدار `value` خالی باشد. به محض اینکه داده وارد شود، placeholder ناپدید می‌شود؛ اگر جعبه خالی شود، دوباره ظاهر می‌شود.

در مثال زیر، یک input از نوع `email` با placeholder برابر با `sophie@example.com` داریم. توجه کنید که با تغییر محتوای جعبهٔ ورودی، placeholder ناپدید و دوباره ظاهر می‌شود.

```html
<input type="email" placeholder="sophie@example.com" />
```

#### کنترل اندازهٔ ورودی

شما می‌توانید علاوه بر طول فیزیکی جعبهٔ ورودی، حداقل و حداکثر طول مجاز برای متن ورودی را نیز کنترل کنید.

**اندازهٔ فیزیکی عنصر input**

اندازهٔ فیزیکی جعبهٔ ورودی را می‌توان با استفاده از ویژگی [`size`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#size) کنترل کرد. به کمک آن می‌توانید مشخص کنید جعبهٔ ورودی چند کاراکتر را در هر بار نمایش دهد. در این مثال، جعبهٔ ورودی `email` به عرض ۱۵ کاراکتر است:

```html
<input type="email" size="15" />
```

**طول مقدار عنصر**

مقدار `size` جدا از محدودیت طول خود آدرس ایمیل است؛ به این ترتیب می‌توانید فیلدها را در فضای کوچک جا دهید و همچنان اجازه دهید رشته‌های ایمیل طولانی‌تر وارد شوند. می‌توانید حداقل طول ورودی (بر حسب کاراکتر) را با ویژگی [`minlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#minlength) تعیین کنید؛ به همین ترتیب، از [`maxlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#maxlength) برای تعیین حداکثر طول آدرس ایمیل واردشده استفاده کنید.

مثال زیر یک جعبهٔ ورودی ایمیل به عرض ۳۲ کاراکتر می‌سازد که محتوای آن نباید کمتر از ۳ و بیشتر از ۶۴ کاراکتر باشد.

```html
<input type="email" size="32" minlength="3" maxlength="64" />
```

#### ارائهٔ گزینه‌های پیش‌فرض

**ارائهٔ یک مقدار پیش‌فرض با ویژگی value**

همیشه می‌توانید با تنظیم ویژگی [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value)، یک مقدار پیش‌فرض برای جعبهٔ ورودی `email` تعیین کنید:

```html
<input type="email" value="default@example.com" />
```

**ارائهٔ مقادیر پیشنهادی**

در ادامه، می‌توانید با مشخص کردن ویژگی [`list`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#list)، فهرستی از گزینه‌های پیش‌فرض ارائه دهید که کاربر بتواند از میان آن‌ها انتخاب کند. این کار کاربر را به آن گزینه‌ها محدود نمی‌کند، اما به او امکان می‌دهد آدرس‌های ایمیل پرکاربرد را سریع‌تر انتخاب کند. همچنین این ویژگی به [`autocomplete`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#autocomplete) هم کمک می‌کند. ویژگی `list` شناسهٔ یک `datalist` را مشخص می‌کند؛ این عنصر به نوبهٔ خود برای هر مقدار پیشنهادی، یک عنصر `option` دارد. `value` هر `option`، مقدار پیشنهادی متناظر برای جعبهٔ ورودی ایمیل است.

````markdown
```html
<input type="email" size="40" list="defaultEmails" />

<datalist id="defaultEmails">
  <option value="jbond007@mi6.defence.gov.uk"></option>
  <option value="jbourne@unknown.net"></option>
  <option value="nfury@shield.org"></option>
  <option value="tony@starkindustries.com"></option>
  <option value="hulk@grrrrrrrr.arg"></option>
</datalist>
````

با وجود عنصر `datalist` و `option`هایش، مرورگر مقادیر مشخص‌شده را به‌عنوان مقادیر بالقوه برای آدرس ایمیل پیشنهاد می‌دهد؛ این پیشنهادها معمولاً به‌صورت یک پاپ‌آپ یا منوی کشویی حاوی پیشنهادها نمایش داده می‌شوند. با اینکه تجربه کاربری دقیق ممکن است از مرورگری به مرورگر دیگر متفاوت باشد، معمولاً کلیک روی کادر ویرایش، منوی کشوییِ آدرس‌های ایمیل پیشنهادی را نشان می‌دهد. سپس، با تایپ کاربر، فهرست فیلتر می‌شود و فقط مقادیر منطبق نمایش داده می‌شوند. هر کاراکتر تایپ‌شده فهرست را محدودتر می‌کند تا زمانی که کاربر یک گزینه را انتخاب کند یا یک مقدار سفارشی تایپ کند.

### اعتبارسنجی

برای ورودی‌های `email` دو سطح اعتبارسنجی محتوا وجود دارد. اول، سطح استاندارد اعتبارسنجی که برای همه `input`ها ارائه می‌شود و به‌صورت خودکار تضمین می‌کند محتوا با الزامات یک آدرس ایمیل معتبر مطابقت دارد. اما این گزینه هم وجود دارد که فیلتر اضافی اضافه کنید تا اگر نیازهای تخصصی خودتان را دارید، برآورده شوند.

> \[!WARNING] اعتبارسنجی فرم HTML جایگزینی برای اسکریپت‌هایی نیست که تضمین می‌کنند داده واردشده قالب مناسبی دارد. خیلی راحت است که کسی تغییراتی در HTML ایجاد کند تا اعتبارسنجی را دور بزند یا آن را کاملاً حذف کند. همچنین امکان دارد کسی HTML شما را به‌کلی دور بزند و داده‌ها را مستقیماً به سرور شما ارسال کند. اگر کد سمت سرور شما داده دریافتی را اعتبارسنجی نکند، وقتی داده با قالب نادرست (یا داده‌ای که خیلی بزرگ است، نوع اشتباهی دارد، و غیره) وارد پایگاه‌داده شود، فاجعه رخ می‌دهد.

#### اعتبارسنجی پایه

مرورگرها به‌صورت خودکار اعتبارسنجی را ارائه می‌کنند تا مطمئن شوند فقط متنی که با قالب استاندارد آدرس‌های ایمیل اینترنتی مطابقت دارد، در کادر ورودی وارد شود. مرورگرها از الگوریتمی معادل عبارت باقاعده (regular expression) زیر استفاده می‌کنند:

```js
/^[\w.!#$%&'*+/=?^`{|}~-]+@[a-z\d](?:[a-z\d-]{0,61}[a-z\d])?(?:\.[a-z\d](?:[a-z\d-]{0,61}[a-z\d])?)*$/i;
```

برای آشنایی بیشتر با نحوه عملکرد اعتبارسنجی فرم و چگونگی استفاده از ویژگی‌های CSS یعنی `:valid` و `:invalid` برای استایل‌دهی به ورودی بر اساس معتبر بودن مقدار فعلی، به [Form data validation](../../../../../../../../en-US/docs/Learn_web_development/Extensions/Forms/Form_validation/) مراجعه کنید.

> \[!NOTE] مسائل شناخته‌شده‌ای در مشخصات مربوط به نام دامنه‌های بین‌المللی و اعتبارسنجی آدرس‌های ایمیل در HTML وجود دارد. برای جزئیات به [W3C bug 15489](https://www.w3.org/Bugs/Public/show_bug.cgi?id=15489) و [whatwg/html#4562](https://github.com/whatwg/html/issues/4562) مراجعه کنید.

#### اعتبارسنجی با الگو

اگر نیاز دارید آدرس ایمیل واردشده محدودتر از «هر رشته‌ای که شبیه آدرس ایمیل است» باشد، می‌توانید از ویژگی [`pattern`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#pattern) استفاده کنید تا یک عبارت باقاعده (regular expression) مشخص کنید که مقدار برای معتبر بودن باید با آن مطابقت داشته باشد. اگر ویژگی [`multiple`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#multiple) مشخص شده باشد، هر آیتم جداگانه در فهرست مقادیر جدا شده با کاما باید با عبارت باقاعده مطابقت کند.

به‌عنوان مثال، فرض کنید در حال ساختن صفحه‌ای برای کارمندان شرکت «Best Startup Ever, Inc.» هستید که به آنها امکان می‌دهد برای کمک با بخش IT تماس بگیرند. در فرم ساده‌شده ما، کاربر باید آدرس ایمیل و پیامی که مشکل مورد نیاز برای کمک را توصیف می‌کند وارد کند. ما می‌خواهیم مطمئن شویم که کاربر نه‌تنها یک آدرس ایمیل معتبر ارائه می‌دهد، بلکه به دلایل امنیتی، آدرس باید یک ایمیل شرکتی داخلی باشد.

````

از آنجایی که ورودی‌های نوع `email` هم اعتبارسنجی استاندارد آدرس ایمیل را انجام می‌دهند و هم [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) را بررسی می‌کنند، می‌توانید این قابلیت را به سادگی پیاده‌سازی کنید. ببینید چطور:

```css hidden
body {
  font: 16px sans-serif;
}

.emailBox {
  padding-bottom: 20px;
}

.messageBox {
  padding-bottom: 20px;
}

label {
  line-height: 22px;
}

label::after {
  content: ":";
}
````

```html
<form>
  <div class="emailBox">
    <label for="emailAddress">Your email address</label><br />
    <input
      id="emailAddress"
      type="email"
      size="64"
      maxlength="64"
      required
      placeholder="username@beststartupever.com"
      pattern=".+@beststartupever\.com"
      title="Please provide only a Best Startup Ever corporate email address" />
  </div>

  <div class="messageBox">
    <label for="message">Request</label><br />
    <textarea
      id="message"
      cols="80"
      rows="8"
      required
      placeholder="My shoes are too tight, and I have forgotten how to dance."></textarea>
  </div>
  <input type="submit" value="Send Request" />
</form>
```

\{{EmbedLiveSample("Pattern\_validation", 700, 300)\}}

فرم ما شامل یک `<input>` از نوع `email` برای آدرس ایمیل کاربر، یک `<textarea>` برای وارد کردن پیام، و یک `<input>` از نوع `"submit"` است که دکمه ارسال را می‌سازد. هر جعبه ورودی یک `<label>` مرتبط دارد تا کاربر بداند چه چیزی باید وارد کند.

حالا بیایید نگاهی دقیق‌تر به جعبه آدرس ایمیل بیندازیم. ویژگی‌های [`size`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#size) و [`maxlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#maxlength) آن هر دو روی ۶۴ تنظیم شده‌اند تا فضایی برای ۶۴ کاراکتر آدرس ایمیل نشان دهد و تعداد کاراکترهای وارد شده را به حداکثر ۶۴ محدود کند. ویژگی [`required`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#required) نیز مشخص شده است که وارد کردن یک آدرس ایمیل معتبر را الزامی می‌کند.

یک [`placeholder`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#placeholder) مناسب به صورت `username@beststartupever.com` قرار داده شده تا نشان دهد یک ورودی معتبر چه شکلی دارد. این رشته هم نشان می‌دهد که باید یک آدرس ایمیل وارد شود و هم پیشنهاد می‌کند که باید یک حساب کاربری شرکتی در beststartupever.com باشد. این مورد علاوه بر این است که استفاده از `type="email""` باعث می‌شود متن از نظر قالب ایمیل بررسی شود. اگر متن داخل جعبه ورودی یک آدرس ایمیل نباشد، پیام خطایی شبیه به این دریافت می‌کنید:

اگر فقط همین را می‌داشتیم، حداقل آدرس‌های ایمیل معتبر را اعتبارسنجی می‌کردیم. اما می‌خواهیم یک قدم جلوتر برویم: مطمئن شویم که آدرس ایمیل قطعاً به صورت `[username]@beststartupever.com` است. اینجاست که از [`pattern`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#pattern) استفاده می‌کنیم. `pattern` را روی `.+@beststartupever.com` تنظیم می‌کنیم. این عبارت منظم (regular expression) رشته‌ای را می‌خواهد که حداقل یک کاراکتر از هر نوعی داشته باشد، سپس یک `@` و بعد از آن دامنه `beststartupever.com`.

توجه کنید که این به هیچ عنوان فیلتر مناسبی برای آدرس‌های ایمیل معتبر نیست؛ مثلاً چیزهایی مثل `" @beststartupever.com"` (با فاصله ابتدایی) یا `"@@beststartupever.com"` را قبول می‌کند که هیچکدام معتبر نیستند. با این حال، مرورگر هم فیلتر استاندارد ایمیل را اجرا می‌کند و هم الگوی سفارشی ما را روی متن مشخص شده اعمال می‌کند. در نتیجه، اعتبارسنجی به این صورت می‌شود: «اول مطمئن شو این شبیه یک آدرس ایمیل معتبر است، و اگر هست، مطمئن شو که آدرس beststartupever.com هم هست.»

استفاده از `pattern` همراه با [`title`](../../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/title/) توصیه می‌شود. اگر این کار را می‌کنید، `title` **باید** الگوی مورد نظر را توصیف کند. یعنی باید توضیح دهد که داده‌ها باید چه قالبی داشته باشند، نه اطلاعات دیگر. دلیلش این است که ممکن است `title` به‌عنوان بخشی از پیام خطای اعتبارسنجی نمایش داده یا گفته شود. مثلاً مرورگر ممکن است پیام «متن وارد شده با الگوی مورد نیاز مطابقت ندارد» را به همراه `title` شما نمایش دهد. اگر `title` شما چیزی مثل «آدرس ایمیل» باشد، نتیجه پیامی می‌شود مانند «متن وارد شده با الگوی مورد نیاز مطابقت ندارد. آدرس ایمیل» که چندان خوب نیست.

به همین دلیل، ما رشته «لطفاً فقط یک آدرس ایمیل شرکتی Best Startup Ever ارائه دهید» را مشخص می‌کنیم. با این کار، پیام خطای کامل ممکن است چیزی شبیه «متن وارد شده با الگوی مورد نیاز مطابقت ندارد. لطفاً فقط یک آدرس ایمیل شرکتی Best Startup Ever ارائه دهید» باشد.

> \[!NOTE] اگر هنگام نوشتن regular expressionهای اعتبارسنجی خود به مشکل برخوردید و آن‌ها درست کار نکردند، کنسول مرورگر خود را بررسی کنید؛ ممکن است پیام‌های خطای مفیدی در آنجا وجود داشته باشد که به شما در حل مشکل کمک کند.

### مثال‌ها

در اینجا یک ورودی ایمیل با شناسه `emailAddress` داریم که حداکثر تا ۲۵۶ کاراکتر مجاز است. خود جعبهٔ ورودی از نظر فیزیکی ۶۴ کاراکتر عرض دارد و وقتی فیلد خالی است، متن `user@example.gov` را به‌عنوان placeholder نمایش می‌دهد. همچنین با استفاده از ویژگی [`multiple`](../../../../../../../../en-US/docs/Web/HTML/Reference/Attributes/multiple/)، جعبه طوری پیکربندی شده است که به کاربر اجازه می‌دهد صفر یا چند آدرس ایمیل را که با کاما از هم جدا شده‌اند وارد کند، همانطور که در [اجازه دادن به چند آدرس ایمیل](index.md#allowing_multiple_email_addresses) توضیح داده شده است. در آخر، ویژگی [`list`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#list) حاوی شناسه یک \{{HTMLElement("datalist")\}} است که \{{HTMLElement("option")\}}های آن مجموعه‌ای از مقادیر پیشنهادی را مشخص می‌کنند که کاربر می‌تواند از بین آن‌ها انتخاب کند.

به عنوان یک نکتهٔ اضافه، از عنصر \{{HTMLElement("label")\}} برای ایجاد یک برچسب برای جعبهٔ ورودی ایمیل استفاده شده است، با ویژگی [`for`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/label/#for) آن که به شناسه `emailAddress` عنصر \{{HTMLElement("input")\}} اشاره می‌کند. با پیوند دادن این دو عنصر به این روش، کلیک روی برچسب باعث دریافت focus توسط عنصر ورودی می‌شود.

```html
<label for="emailAddress">Email</label><br />
<input
  id="emailAddress"
  type="email"
  placeholder="user@example.gov"
  list="defaultEmails"
  size="64"
  maxlength="256"
  multiple />

<datalist id="defaultEmails">
  <option value="jbond007@mi6.defence.gov.uk"></option>
  <option value="jbourne@unknown.net"></option>
  <option value="nfury@shield.org"></option>
  <option value="tony@starkindustries.com"></option>
  <option value="hulk@grrrrrrrr.arg"></option>
</datalist>
```

### خلاصهٔ فنی

```markdown
<table class="properties">
  <tbody>
    <tr>
      <td><strong>مقدار</strong></td>
      <td>رشته‌ای که نشانی ایمیل را نشان می‌دهد، یا خالی</td>
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
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#multiple"><code>multiple</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#name"><code>name</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#pattern"><code>pattern</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#placeholder"><code>placeholder</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#readonly"><code>readonly</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#required"><code>required</code></a>,
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#size"><code>size</code></a>، و
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#type"><code>type</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های IDL</strong></td>
      <td><code>list</code> و <code>value</code></td>
    </tr>
    <tr>
      <td><strong>رابط DOM</strong></td>
      <td><code>HTMLInputElement</code></td>
    </tr>
    <tr>
      <td><strong>نقش ضمنی ARIA</strong></td>
      <td>
        بدون ویژگی <code>list</code>:
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role">textbox</a></code><br />
        با ویژگی <code>list</code>: <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role">combobox</a></code>
      </td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- [راهنمای فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)
- `<input>`
- [`<input type="tel">`](/en-US/docs/Web/HTML/Reference/Elements/input/tel)
- [`<input type="url">`](/en-US/docs/Web/HTML/Reference/Elements/input/url)
- ویژگی‌ها:
  - [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list)
  - [`minlength`](/en-US/docs/Web/HTML/Reference/Attributes/minlength)
  - [`maxlength`](/en-US/docs/Web/HTML/Reference/Attributes/maxlength)
  - [`multiple`](/en-US/docs/Web/HTML/Reference/Attributes/multiple)
  - [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern)
  - [`placeholder`](/en-US/docs/Web/HTML/Reference/Elements/input#placeholder)
  - [`readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly)
  - [`size`](/en-US/docs/Web/HTML/Reference/Attributes/size)
```
