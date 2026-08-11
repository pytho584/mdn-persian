---
title: "<input type=\"password\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/password"
translated_by: "n8n + AI"
---

عناصر `<input>` از نوع **`password`** راهی امن برای وارد کردن رمز عبور توسط کاربر فراهم می‌کنند.

این عنصر به صورت یک کنترل ویرایش متن تک‌خطی نمایش داده می‌شود که در آن متن به‌گونه‌ای پوشانده می‌شود که قابل خواندن نباشد. معمولاً هر کاراکتر با نمادی مثل ستاره ("\*") یا نقطه ("•") جایگزین می‌شود. این نماد بسته به {{Glossary("user agent")}} و سیستم عامل متفاوت خواهد بود.

{{InteractiveExample("HTML Demo: &lt;input type=&quot;password&quot;&gt;", "tabbed-standard")}}

```html interactive-example
<div>
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" />
</div>

<div>
  <label for="pass">Password (8 characters minimum):</label>
  <input type="password" id="pass" name="password" minlength="8" required />
</div>

<input type="submit" value="Sign in" />
```

```css interactive-example
label {
  display: block;
}

input[type="submit"],
label {
  margin-top: 1rem;
}
```

رفتار دقیق فرآیند ورود رمز عبور ممکن است در مرورگرهای مختلف متفاوت باشد. برخی مرورگرها کاراکتر تایپ‌شده را برای لحظه‌ای قبل از پوشاندن آن نمایش می‌دهند، در حالی که برخی دیگر به کاربر اجازه می‌دهند نمایش متن ساده را روشن یا خاموش کند. هر دو روش به کاربر کمک می‌کنند تا مطمئن شود رمز عبور مورد نظر را وارد کرده است، که این کار به‌ویژه در دستگاه‌های همراه دشوار است.

> [!NOTE]
> هر فرمی که شامل اطلاعات حساس مانند رمز عبور است (مانند فرم‌های ورود) باید از طریق HTTPS ارائه شود. بسیاری از مرورگرها اکنون مکانیزم‌هایی برای هشدار در مورد فرم‌های ورود ناامن پیاده‌سازی کرده‌اند.

## مقدار (Value)

مقدار [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) یک رشته است که محتوای فعلی کنترل ویرایش متن مورد استفاده برای وارد کردن رمز عبور را نشان می‌دهد. اگر کاربر هنوز چیزی وارد نکرده باشد، این مقدار یک رشته خالی (`""`) است. اگر ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) مشخص شده باشد، جعبه ویرایش رمز عبور باید مقداری غیر از رشته خالی داشته باشد تا معتبر در نظر گرفته شود.

اگر ویژگی [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) مشخص شده باشد، محتوای یک کنترل `password` تنها زمانی معتبر در نظر گرفته می‌شود که مقدار تأیید اعتبار را پاس کند؛ برای اطلاعات بیشتر به بخش [اعتبارسنجی](#validation) مراجعه کنید.

> [!NOTE]
> کاراکترهای خط جدید (U+000A) و بازگشت به اول خط (U+000D) در مقدار `password` مجاز نیستند. هنگام تنظیم مقدار یک کنترل رمز عبور، این کاراکترها از مقدار حذف می‌شوند.

## ویژگی‌های اضافی

علاوه بر [ویژگی‌های global](/en-US/docs/Web/HTML/Reference/Global_attributes) و ویژگی‌هایی که روی همه عناصر {{HTMLElement("input")}} بدون توجه به نوعشان اعمال می‌شوند، فیلدهای ورودی رمز عبور از ویژگی‌های زیر پشتیبانی می‌کنند.

> [!NOTE]
> ویژگی global [`autocorrect`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect) می‌تواند به ورودی‌های رمز عبور اضافه شود، اما حالت ذخیره‌شده همیشه `off` است.

### maxlength

حداکثر طول رشته (بر حسب {{glossary("UTF-16", "واحد کد UTF-16")}}) که کاربر می‌تواند در فیلد رمز عبور وارد کند. این مقدار باید یک عدد صحیح ۰ یا بیشتر باشد. اگر `maxlength` مشخص نشود یا یک مقدار نامعتبر مشخص شود، فیلد رمز عبور حداکثر طول ندارد. این مقدار همچنین باید بزرگتر یا مساوی با مقدار `minlength` باشد.

اگر طول متن وارد شده در فیلد بیش از `maxlength` {{glossary("UTF-16", "واحد کد UTF-16")}} باشد، ورودی در [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) ناموفق خواهد بود. اعتبارسنجی محدودیت‌ها فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند.

### minlength

حداقل طول رشته (بر حسب واحدهای کد UTF-16) که کاربر می‌تواند در فیلد رمز عبور وارد کند. این مقدار باید یک عدد صحیح نامنفی و کوچک‌تر یا مساوی مقدار مشخص‌شده توسط `maxlength` باشد. اگر `minlength` مشخص نشده باشد یا مقدار نامعتبری داشته باشد، ورودی رمز عبور حداقل طول نخواهد داشت.

اگر طول متن واردشده در فیلد کمتر از `minlength` واحد کد UTF-16 باشد، ورودی در [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) ناموفق خواهد بود. اعتبارسنجی محدودیت فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کرده باشد.

### pattern

ویژگی `pattern`، وقتی مشخص شود، یک عبارت باقاعده است که [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) ورودی باید برای قبولی در [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) با آن مطابقت داشته باشد. این عبارت باید یک عبارت باقاعده معتبر جاوااسکریپت باشد، همان‌طور که توسط نوع `RegExp` استفاده می‌شود و در [راهنمای عبارت‌های باقاعده](/en-US/docs/Web/JavaScript/Guide/Regular_expressions) مستند شده است. هنگام کامپایل عبارت باقاعده، پرچم `'u'` مشخص می‌شود تا الگو به‌عنوان دنباله‌ای از نقاط کد Unicode در نظر گرفته شود، نه به‌صورت ASCII. هیچ اسلش (/) نباید دور متن الگو قرار بگیرد.

اگر الگوی مشخص‌شده تعیین نشده باشد یا نامعتبر باشد، هیچ عبارت باقاعده‌ای اعمال نمی‌شود و این ویژگی کاملاً نادیده گرفته می‌شود.

> [!NOTE]
> از ویژگی [`title`](/en-US/docs/Web/HTML/Reference/Elements/input#title) برای مشخص کردن متنی استفاده کنید که بیشتر مرورگرها آن را به‌صورت tooltip نمایش می‌دهند تا توضیح دهد الزامات مطابقت با الگو چیست. همچنین باید متن توضیحی دیگری در نزدیکی آن قرار دهید.

استفاده از `pattern` برای ورودی‌های رمز عبور به‌شدت توصیه می‌شود تا اطمینان حاصل شود که رمزهای عبور معتبر با طیف گسترده‌ای از کلاس‌های کاراکتری انتخاب و توسط کاربران استفاده می‌شوند. با استفاده از `pattern` می‌توانید قوانین حروف بزرگ و کوچک را اجباری کنید، استفاده از تعدادی رقم و/یا کاراکترهای نقطه‌گذاری را الزامی کنید و غیره. برای جزئیات و مثال، به بخش [Validation](#validation) مراجعه کنید.

### placeholder

ویژگی `placeholder` رشته‌ای است که راهنمای کوتاهی به کاربر می‌دهد درباره اینکه چه نوع اطلاعاتی در فیلد انتظار می‌رود. باید یک کلمه یا عبارت کوتاه باشد که نوع دادهٔ مورد انتظار را نشان دهد، نه یک پیام توضیحی. متن _نباید_ شامل نویسه‌های بازگشت به ابتدای سطر (carriage return) یا خط جدید (line feed) باشد.

اگر محتوای کنترل یک جهت (LTR یا RTL) داشته باشد اما لازم باشد placeholder در جهت مخالف نمایش داده شود، می‌توانید از نویسه‌های قالب‌بندی الگوریتم دوجهتهٔ Unicode برای لغو جهت درون placeholder استفاده کنید. برای اطلاعات بیشتر، [How to use Unicode controls for bidi text](https://www.w3.org/International/questions/qa-bidi-unicode-controls) را ببینید.

> [!NOTE]
> تا حد امکان از استفاده از ویژگی `placeholder` خودداری کنید. این ویژگی از نظر معنایی به اندازهٔ روش‌های دیگر برای توضیح فرم مفید نیست و می‌تواند مشکلات فنی غیرمنتظره‌ای در محتوای شما ایجاد کند. برای اطلاعات بیشتر، برچسب‌های [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input#labels) را ببینید.

### readonly

یک ویژگی Boolean است که اگر وجود داشته باشد، به این معنی است که این فیلد نمی‌تواند توسط کاربر ویرایش شود. با این حال، `value` آن همچنان می‌تواند از طریق کد جاوااسکریپتی که مستقیماً مقدار ویژگی [`HTMLInputElement.value`](/en-US/docs/Web/API/HTMLInputElement/value) را تنظیم می‌کند، تغییر کند.

> [!NOTE]
> از آنجا که یک فیلد read-only نمی‌تواند مقدار داشته باشد، `required` روی ورودی‌هایی که ویژگی `readonly` نیز برایشان مشخص شده است هیچ اثری ندارد.

### size

attribute `size` یک مقدار عددی است که مشخص می‌کند فیلد input تقریباً چند کاراکتر عرض داشته باشد. این مقدار باید عددی بزرگ‌تر از صفر باشد و مقدار پیش‌فرض آن ۲۰ است. چون عرض کاراکترها متفاوت است، این مقدار ممکن است دقیق باشد یا نباشد و نباید به دقیق بودن آن تکیه کرد؛ input نهایی بسته به کاراکترها و تنظیمات `font` ممکن است از تعداد کاراکتر مشخص‌شده باریک‌تر یا پهن‌تر باشد.

این کار _هیچ_ محدودیتی روی تعداد کاراکترهایی که کاربر می‌تواند در فیلد وارد کند ایجاد نمی‌کند. این attribute فقط مشخص می‌کند تقریباً چند کاراکتر در هر لحظه قابل مشاهده است. برای تنظیم سقف طول داده ورودی، از attribute [`maxlength`](#maxlength) استفاده کنید.

## استفاده از ورودی‌های رمز عبور

فیلدهای ورودی رمز عبور معمولاً دقیقاً مثل سایر فیلدهای متنی کار می‌کنند؛ تفاوت اصلی این است که محتوا پنهان می‌شود تا افراد نزدیک کاربر نتوانند رمز عبور را بخوانند.

### یک ورودی رمز عبور ساده

در اینجا ساده‌ترین input رمز عبور را می‌بینیم که یک برچسب با استفاده از element `<label>` برای آن ساخته شده است.

```html
<label for="userPassword">Password: </label>
<input id="userPassword" type="password" />
```

### اجازه دادن به autocomplete

برای اینکه مدیر رمز عبور (password manager) کاربر بتواند رمز عبور را به‌صورت خودکار وارد کند، attribute [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete) را مشخص کنید. برای رمز عبور، معمولاً باید یکی از مقادیر زیر باشد:

- `on`
  - : به browser یا مدیر رمز عبور اجازه بده فیلد رمز عبور را به‌صورت خودکار پر کند. این مقدار به اندازه `current-password` یا `new-password` اطلاعات مفیدی در اختیار آن‌ها قرار نمی‌دهد.
- `off`
  - : به browser یا مدیر رمز عبور اجازه نده فیلد رمز عبور را به‌صورت خودکار پر کند. توجه داشته باشید که برخی نرم‌افزارها این مقدار را نادیده می‌گیرند، چون معمولاً به توانایی کاربران برای رعایت شیوه‌های امن رمز عبور آسیب می‌زند.
- `current-password`
  - : به browser یا مدیر رمز عبور اجازه بده رمز عبور فعلی سایت را وارد کند. این مقدار اطلاعات بیشتری از `on` دارد؛ چون به browser یا مدیر رمز عبور اجازه می‌دهد رمز عبور شناخته‌شده و فعلی سایت را در فیلد وارد کند، اما رمز جدیدی پیشنهاد نمی‌دهد.
- `new-password`
  - : به browser یا مدیر رمز عبور اجازه بده رمز عبور جدیدی برای سایت وارد کند. این مقدار در فرم‌های «تغییر رمز عبور» و «کاربر جدید» روی فیلدی که از کاربر رمز عبور جدید می‌خواهد استفاده می‌شود. رمز جدید ممکن است بسته به مدیر رمز عبور به روش‌های مختلفی تولید شود؛ مثلاً رمز پیشنهادی جدیدی را پر کند یا رابطی برای ساخت رمز جدید به کاربر نشان دهد.

```html
<label for="userPassword">Password:</label>
<input id="userPassword" type="password" autocomplete="current-password" />
```

### الزامی کردن رمز عبور

برای اینکه به browser کاربر بگویید قبل از ارسال فرم، فیلد رمز عبور باید مقدار معتبری داشته باشد، attribute بولین [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) را مشخص کنید.

```html
<label for="userPassword">Password: </label>
<input id="userPassword" type="password" required />
<input type="submit" value="Submit" />
```

### مشخص کردن input mode

اگر قوانین پیشنهادی (یا اجباری) رمز عبور شما به یک رابط ورودی متنی جایگزین نسبت به صفحه‌کلید استاندارد نیاز دارد، می‌توانید از attribute [`inputmode`](/en-US/docs/Web/HTML/Reference/Elements/input#inputmode) برای درخواست یک حالت خاص استفاده کنید. واضح‌ترین مورد استفاده، وقتی است که رمز عبور باید عددی باشد (مثل PIN). مثلاً دستگاه‌های موبایل با صفحه‌کلید مجازی ممکن است به‌جای صفحه‌کلید کامل، به چیدمان صفحه‌کلید عددی تغییر حالت دهند تا وارد کردن رمز آسان‌تر شود. اگر PIN یک‌بارمصرف است، attribute [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete) را روی `off` یا `one-time-code` قرار دهید تا به browser یا مدیر رمز عبور پیشنهاد شود که آن را ذخیره نکند.

```html
<label for="pin">PIN: </label>
<input id="pin" type="password" inputmode="numeric" />

### تعیین محدودیت‌های طول

طبق معمول، می‌توانید از ویژگی‌های [`minlength`](/en-US/docs/Web/HTML/Reference/Elements/input#minlength) و [`maxlength`](/en-US/docs/Web/HTML/Reference/Elements/input#maxlength) برای تعیین حداقل و حداکثر طول مجاز رمز عبور استفاده کنید. این مثال، نمونهٔ قبلی را گسترش می‌دهد و مشخص می‌کند که PIN کاربر باید حداقل ۴ و حداکثر ۸ رقم باشد. ویژگی [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) نیز برای اطمینان از این‌که فیلد ورود رمز عبور به اندازهٔ ۸ کاراکتر عرض داشته باشد استفاده شده است.

```html
<label for="pin">PIN:</label>
<input
  id="pin"
  type="password"
  inputmode="numeric"
  minlength="4"
  maxlength="8"
  size="8" />
```

### انتخاب متن

درست مثل سایر کنترل‌های ورود متنی، می‌توانید از متد `select()` برای انتخاب تمام متن موجود در فیلد رمز عبور استفاده کنید.

#### HTML

```html
<label for="userPassword">Password: </label>
<input id="userPassword" type="password" size="12" />
<button id="selectAll">Select All</button>
```

#### JavaScript

```js
document.getElementById("selectAll").onclick = () => {
  document.getElementById("userPassword").select();
};
```

#### نتیجه

همچنین می‌توانید از `selectionStart` و `selectionEnd` (از طریق `HTMLInputElement`) برای دریافت (یا تنظیم) بازه‌ای از کاراکترها که در حال حاضر در فیلد انتخاب شده‌اند استفاده کنید، و از `selectionDirection` برای فهمیدن اینکه انتخاب در چه جهتی انجام شده است (یا بسته به پلتفرم شما در چه جهتی گسترش خواهد یافت؛ برای توضیح بیشتر به مستندات آن مراجعه کنید). با این حال، چون متن رمز عبور پنهان است، کاربرد این ویژگی‌ها تا حدی محدود است.

### اعتبارسنجی

اگر اپلیکیشن شما محدودیت‌هایی روی مجموعه کاراکترها یا هر الزام دیگری برای محتوای واقعی رمز عبور واردشده دارد، می‌توانید از ویژگی [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) برای تعریف یک عبارت باقاعده استفاده کنید تا به‌طور خودکار اطمینان حاصل شود که رمزهای عبور این الزامات را برآورده می‌کنند.

در این مثال، فقط مقادیری معتبرند که از حداقل چهار و حداکثر هشت رقم هگزادسیمال تشکیل شده باشند.

```html
<label for="hexId">Hex ID: </label>
<input
  id="hexId"
  type="password"
  pattern="[0-9a-fA-F]{4,8}"
  title="Enter an ID consisting of 4-8 hexadecimal digits"
  autocomplete="new-password" />
```

### مثال‌ها

#### درخواست شماره تأمین اجتماعی (SSN)

این مثال فقط ورودی‌ای را می‌پذیرد که با قالب [شماره تأمین اجتماعی معتبر ایالات متحده](https://en.wikipedia.org/wiki/Social_Security_number#Structure) مطابقت داشته باشد. این شماره‌ها که برای اهداف مالیاتی و شناسایی در آمریکا استفاده می‌شوند، به شکل «123-45-6789» هستند. قوانین مختلفی نیز برای مقادیر مجاز در هر گروه وجود دارد.

#### HTML

```html
<label for="ssn">SSN:</label>
<input
  type="password"
  id="ssn"
  inputmode="numeric"
  minlength="9"
  maxlength="12"
  pattern="(?!000)([0-6]\d{2}|7([0-6]\d|7[012]))([ -])?(?!00)\d\d\3(?!0000)\d{4}"
  required
  autocomplete="off" />
<br />
<label for="ssn">Value:</label>
<span id="current"></span>
```

این کد از یک `pattern` استفاده می‌کند که مقدار واردشده را به رشته‌هایی محدود می‌کند که نشان‌دهنده شماره‌های تأمین اجتماعی قانونی هستند. واضح است که این regexp تضمین نمی‌کند شماره SSN معتبر باشد (چون به پایگاه‌داده سازمان تأمین اجتماعی دسترسی نداریم)، اما مطمئن می‌کند که شماره می‌تواند معتبر باشد؛ به‌طور کلی از مقادیری که نمی‌توانند معتبر باشند جلوگیری می‌کند. علاوه بر این، به سه گروه ارقام اجازه می‌دهد با فاصله، خط تیره («-») یا بدون جداکننده از هم جدا شوند.

ویژگی [`inputmode`](/en-US/docs/Web/HTML/Reference/Elements/input#inputmode) روی `numeric` تنظیم شده تا دستگاه‌های دارای کیبورد مجازی را تشویق کند به حالت صفحه‌کلید عددی بروند و ورود اطلاعات آسان‌تر شود. ویژگی‌های [`minlength`](/en-US/docs/Web/HTML/Reference/Elements/input#minlength) و [`maxlength`](/en-US/docs/Web/HTML/Reference/Elements/input#maxlength) به ترتیب روی ۹ و ۱۲ کاراکتر تنظیم شده‌اند تا مقدار ورودی حداقل ۹ و حداکثر ۱۲ کاراکتر باشد (مقدار اول بدون جداکننده بین گروه‌های رقمی و مقدار دوم با جداکننده). ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) برای مشخص کردن این که این فیلد حتماً باید مقدار داشته باشد استفاده شده است. در نهایت [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete) روی `off` تنظیم شده تا password manager و قابلیت‌های بازیابی نشست (session restore) سعی در تنظیم مقدار آن نکنند، چون اینجا خبری از رمز عبور نیست.

#### JavaScript

کد JavaScript مقدار SSN وارد شده را روی صفحه نمایش می‌دهد تا بتوانید آن را ببینید. این کار هدف فیلد password را نقض می‌کند اما برای آزمایش `pattern` مفید است.

```js
const ssn = document.getElementById("ssn");
const current = document.getElementById("current");

ssn.oninput = (event) => {
  current.textContent = ssn.value;
};
```

#### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">مقدار (Value)</a></strong></td>
      <td>یک رشته که نشان‌دهنده رمز عبور است، یا خالی</td>
    </tr>
    <tr>
      <td><strong>رویدادها (Events)</strong></td>
      <td>
        {{domxref("HTMLElement/change_event", "change")}} و
        {{domxref("Element/input_event", "input")}}
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های عمومی پشتیبانی‌شده (Supported Common Attributes)</strong></td>
      <td>
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete"><code>autocomplete</code></a>،
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#inputmode"><code>inputmode</code></a>،
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#maxlength"><code>maxlength</code></a>،
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#minlength"><code>minlength</code></a>،
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#pattern"><code>pattern</code></a>،
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#placeholder"><code>placeholder</code></a>،
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#readonly"><code>readonly</code></a>،
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#required"><code>required</code></a> و
         <a href="/en-US/docs/Web/HTML/Reference/Elements/input#size"><code>size</code></a>
      </td>
    </tr>
    <tr>
      <td><strong>ویژگی‌های IDL</strong></td>
      <td>
        <code>selectionStart</code>، <code>selectionEnd</code>،
        <code>selectionDirection</code> و <code>value</code>
      </td>
    </tr>
    <tr>
      <td><strong>رابط DOM</strong></td>
      <td><p>{{domxref("HTMLInputElement")}}</p></td>
    </tr>
    <tr>
      <td><strong>نقش ARIA ضمنی</strong></td>
      <td><a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">بدون نقش متناظر</a></td>
    </tr>
  </tbody>
</table>