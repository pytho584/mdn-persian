---
title: "<input type=\"url\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/url"
translated_by: "n8n + AI"
---

المان‌های `<input>` با تایپ **`url`** برای ورود و ویرایش URL (آدرس اینترنتی) توسط کاربر استفاده می‌شوند.

```html interactive-example
<form>
  <label for="url">Enter an https:// URL:</label>
  <input
    type="url"
    name="url"
    id="url"
    placeholder="https://example.com"
    pattern="https://.*"
    size="30"
    required />
</form>
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

مقدار این ورودی پیش از ارسال فرم به صورت خودکار اعتبارسنجی می‌شود تا مطمئن شویم که فیلد یا خالی است و یا یک URL با ساختار صحیح در آن وارد شده است. کلاس‌های کاذب (pseudo-classes) در CSS مانند `:valid` و `:invalid` به طور خودکار اعمال می‌شوند تا معتبر بودن یا نبودن مقدار ورودی را به شکل بصری به کاربر نشان دهند.

## مقدار (Value)

اتریبیوت `value` در المان `<input>` حاوی رشته‌ای (string) است که به طور خودکار با ساختار استاندارد URL اعتبارسنجی می‌شود. به طور دقیق‌تر، دو فرمت زیر می‌توانند از این اعتبارسنجی عبور کنند:

۱. یک رشته خالی ("") که نشان می‌دهد کاربر مقداری وارد نکرده یا مقدار قبلی را پاک کرده است.
۲. یک URL مطلق (absolute URL) با ساختار صحیح. این لزوماً به این معنی نیست که آدرس اینترنتی مورد نظر وجود خارجی دارد، بلکه فقط فرمت نگارش آن درست است. برای مثال، عبارتی مانند `urlscheme://rest-of-url` معتبر شناخته می‌شود، حتی اگر `urlscheme` وارد شده واقعی نباشد.

برای اطلاعات بیشتر درباره نحوه سنجش صحت آدرس‌ها، بخش [Validation](#validation) را ببینید.

## اتریبیوت‌های اضافی

علاوه بر اتریبیوت‌های عمومی ([global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)) و اتریبیوت‌های مشترک در تمام ورودی‌های `<input>`، ورودی‌های نوع `url` از اتریبیوت‌های زیر نیز پشتیبانی می‌کنند:

> [!NOTE]
> اتریبیوت عمومی `autocorrect` را می‌توان به ورودی‌های `url` اضافه کرد، اما مقدار ذخیره‌شده برای آن همیشه روی `off` قرار می‌گیرد.

### list

مقدار اتریبیوت `list` برابر با `id` یک المان `<datalist>` در همان سند (document) است. المان `<datalist>` لیستی از مقادیر از‌پیش‌تعریف‌شده را به کاربر پیشنهاد می‌دهد. مقادیری که در این لیست با تایپ `url` سازگار نباشند، نمایش داده نخواهند شد. این مقادیر صرفاً پیشنهاد هستند و کاربر مجبور به انتخاب آن‌ها نیست؛ او می‌تواند از لیست انتخاب کند یا یک آدرس کاملاً متفاوت بنویسد.

### maxlength

حداکثر طول رشته (بر اساس واحدهای کد UTF-16) که کاربر می‌تواند در ورودی `url` وارد کند. این مقدار باید یک عدد صحیح بزرگ‌تر یا مساوی `0` باشد. اگر هیچ مقدار یا مقدار نامعتبری برای `maxlength` مشخص نشود، محدودیت حداکثری وجود نخواهد داشت. این مقدار باید بزرگ‌تر یا مساوی مقدار `minlength` باشد.

در صورتی که طول متن وارد شده بیشتر از `maxlength` باشد، فرم در اعتبارسنجی محدودیت‌ها ([constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)) رد خواهد شد. این اعتبارسنجی فقط زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند.

### minlength

حداقل طول رشته (بر اساس واحدهای کد UTF-16) که کاربر می‌تواند در ورودی `url` وارد کند. این مقدار باید یک عدد صحیح غیرمنفی و کوچک‌تر یا مساوی مقدار `maxlength` باشد. اگر هیچ مقدار یا مقدار نامعتبری برای `minlength` مشخص نشود، محدودیت حداقلی وجود نخواهد داشت.

اگر طول متن وارد شده در فیلد کمتر از مقدار `minlength` (بر اساس واحدهای کد {{glossary("UTF-16", "UTF-16")}}) باشد، این ورودی در [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) (اعتبارسنجی محدودیت‌ها) رد خواهد شد. این اعتبارسنجی تنها زمانی اعمال می‌شود که مقدار توسط کاربر تغییر کند.

### pattern

اتریبیوت `pattern` یک عبارت منظم (Regular Expression) است که مقدار [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) ورودی باید با آن مطابقت داشته باشد تا از سد [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) عبور کند. این عبارت باید یک عبارت منظم معتبر در جاوااسکریپت باشد (همان‌طور که در شیء {{jsxref("RegExp")}} استفاده می‌شود و در [راهنمای عبارات منظم](/en-US/docs/Web/JavaScript/Guide/Regular_expressions) توضیح داده شده است). هنگام کامپایل این عبارت منظم، فلگ `'u'` اعمال می‌شود تا الگو به جای {{Glossary("ASCII")}}، به عنوان توالی‌ای از Unicode code pointها در نظر گرفته شود. نیازی به نوشتن اسلش (forward slash یا همان `/`) در ابتدا و انتهای الگو نیست.

اگر این اتریبیوت مشخص نشود یا مقدار آن نامعتبر باشد، هیچ عبارت منظمی اعمال نخواهد شد و این ویژگی کاملاً نادیده گرفته می‌شود.

> [!NOTE]
> از اتریبیوت [`title`](/en-US/docs/Web/HTML/Reference/Elements/input#title) برای نوشتن متنی استفاده کنید که بیشتر مرورگرها آن را به عنوان tooltip (توضیح کوتاهی که با نگه داشتن موس روی فیلد ظاهر می‌شود) نمایش می‌دهند تا به کاربر بگویند برای مطابقت با الگو چه شرایطی لازم است. همچنین بهتر است توضیحات تکمیلی را در نزدیکی فیلد قرار دهید.

برای جزئیات بیشتر و دیدن نمونه کد، بخش [Pattern validation](#pattern_validation) را ببینید.

### placeholder

اتریبیوت `placeholder` رشته‌ای است که راهنمایی کوتاهی درباره نوع اطلاعات مورد انتظار در فیلد به کاربر ارائه می‌دهد. این مقدار باید یک کلمه یا عبارت کوتاه باشد که نمونه‌ای از داده مورد انتظار را نشان دهد، نه یک پیام توضیحی طولانی. این متن نباید حاوی شکستگی خط (line feed یا carriage return) باشد.

اگر جهت متن کنترل شما (راست‌به‌چپ یا چپ‌به‌راست) مشخص است، اما می‌خواهید `placeholder` را در جهت مخالف نشان دهید، می‌توانید از کاراکترهای قالب‌بندی الگوریتم دوطرفه یونیکد (Unicode bidirectional algorithm) برای تغییر جهت متن درون placeholder استفاده کنید. برای اطلاعات بیشتر، [How to use Unicode controls for bidi text](https://www.w3.org/International/questions/qa-bidi-unicode-controls) را مطالعه کنید.

> [!NOTE]
> تا حد امکان از اتریبیوت `placeholder` استفاده نکنید. این اتریبیوت از نظر معنایی (semantic) به اندازه روش‌های دیگر توضیح فرم‌ها مفید نیست و می‌تواند مشکلات فنی پیش‌بینی‌نشده‌ای در محتوای شما ایجاد کند. برای اطلاعات بیشتر، بخش [`<input>` labels](/en-US/docs/Web/HTML/Reference/Elements/input#labels) را ببینید.

### readonly

اتریبیوت بولین (Boolean) [`readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly) در صورت وجود، مشخص می‌کند که کاربر نمی‌تواند مقدار این فیلد را ویرایش کند. با این حال، مقدار `value` آن همچنان می‌تواند از طریق کدهای جاوااسکریپت و با تغییر مستقیم پراپرتی `value` در {{domxref("HTMLInputElement")}} تغییر کند.

> [!NOTE]
> از آنجایی که کاربر نمی‌تواند مقدار یک فیلد فقط‌خواندنی (read-only) را تغییر دهد، اتریبیوت [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) روی فیلدهایی که اتریبیوت `readonly` دارند هیچ تأثیری نخواهد داشت.

### size

اتریبیوت `size` یک مقدار عددی است که عرض فیلد ورودی را بر حسب تعداد کاراکتر مشخص می‌کند. این مقدار باید عددی بزرگتر از صفر باشد و مقدار پیش‌فرض آن ۲۰ است. از آنجا که عرض کاراکترهای مختلف با هم تفاوت دارد، این عرض ممکن است کاملاً دقیق نباشد و نباید صددرصد روی آن حساب کنید؛ بسته به نوع کاراکترها و فونت استفاده شده (تنظیمات {{cssxref("font")}})، ورودی نهایی ممکن است کمی باریک‌تر یا پهن‌تر از تعداد کاراکتر مشخص‌شده باشد.

این اتریبیوت محدودیتی برای تعداد کاراکترهای قابل ورود توسط کاربر ایجاد *نمی‌کند*؛ بلکه فقط مشخص می‌کند که تقریباً چه تعداد کاراکتر به طور هم‌زمان در کادر فیلد دیده شوند. برای تعیین حداکثر تعداد کاراکترهای مجاز ورودی، از اتریبیوت [`maxlength`](#maxlength) استفاده کنید.

### spellcheck

ویژگی جهانی [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) برای فعال یا غیرفعال کردن قابلیت بررسی املایی (spell-checking) روی یک element استفاده می‌شود. این attribute را می‌توان روی هر محتوای قابل ویرایشی اعمال کرد، اما در اینجا ویژگی‌های خاص استفاده از آن روی elementهای `<input>` را بررسی می‌کنیم. مقادیر مجاز برای `spellcheck` عبارتند از:

- `false`
  - : غیرفعال کردن بررسی املایی برای این element.
- `true`
  - : فعال کردن بررسی املایی برای این element.
- "" (رشته خالی) یا بدون مقدار
  - : استفاده از رفتار پیش‌فرض مرورگر برای بررسی املایی. این رفتار ممکن است بر اساس تنظیمات `spellcheck` در element والد (parent) یا عوامل دیگر تعیین شود.

بررسی املایی در یک فیلد input زمانی فعال می‌شود که ویژگی `readonly` روی آن تنظیم نشده باشد و فیلد غیرفعال (disabled) نباشد.

توجه داشته باشید که مقدار برگشتی از خواندن ویژگی `spellcheck` ممکن است وضعیت واقعی بررسی املایی را نشان ندهد؛ چرا که تنظیمات و ترجیحات مرورگر (user agent) کاربر می‌تواند این مقدار را نادیده بگیرد (override کند).

## استفاده از inputهای URL

وقتی یک input برای دریافت آدرس اینترنتی با `type="url"` می‌سازید، مرورگر به طور خودکار فرمت متن وارد شده را اعتبار‌سنجی (validate) می‌کند تا مطمئن شود ساختار یک URL معتبر را دارد. این ویژگی کمک می‌کند جلوی اشتباهات تایپی کاربر در نوشتن آدرس وب‌سایت گرفته شود.

البته به این نکته مهم توجه داشته باشید که این بررسی فقط صحت ساختار ظاهری URL را تایید می‌کند؛ یعنی تضمین نمی‌کند که این آدرس واقعاً وجود دارد، متعلق به خود کاربر است یا از نظر امنیتی مشکلی ندارد.

> [!NOTE]
> از آنجا که کاربران می‌توانند کدهای HTML صفحه را در مرورگر خود تغییر دهند، هرگز نباید برای اهداف امنیتی به این اعتبار‌سنجی سمت فرانت‌اند اتکا کنید. **ضروری است** که برای هرگونه تراکنش حساس، صحت و اعتبار URL را حتماً در سمت سرور (server-side) نیز بررسی کنید.

### یک نمونه ساده از input با نوع URL

این element مانند یک فیلد متنی استاندارد پیاده‌سازی می‌شود، اما قابلیت‌های پایه برای اعتبار‌سنجی دارد. ساده‌ترین شکل پیاده‌سازی آن به این صورت است:

```html
<input id="myURL" name="myURL" type="url" />
```

دقت کنید که این فیلد در حالت خالی و همچنین زمانی که یک آدرس URL با ساختار صحیح وارد شده باشد، معتبر (valid) شناخته می‌شود؛ در غیر این صورت نامعتبر است. با اضافه کردن attribute با نام [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required)، فیلد دیگر نمی‌تواند خالی بماند و حتماً باید یک URL با فرمت صحیح در آن نوشته شود.

اتفاق پیچیده‌ای در پس‌زمینه رخ نمی‌دهد. با ارسال (submit) این فرم، داده‌ها به این شکل به سرور فرستاده می‌شوند: `myURL=http%3A%2F%2Fwww.example.com`. همان‌طور که می‌بینید، کاراکترهای خاص به طور خودکار انکود (escape) شده‌اند.

### استفاده از Placeholder

گاهی اوقات بهتر است راهنمای کوچکی درون فیلد قرار دهید تا کاربر متوجه ساختار داده ورودی شود. این موضوع به ویژه زمانی اهمیت دارد که طراحی صفحه شامل Labelهای توصیفی برای هر `<input>` نباشد. در این مواقع **placeholder** به کار می‌آید. placeholder متنی است که ساختار صحیح داده ورودی را با یک مثال نشان می‌دهد و تا زمانی که فیلد خالی است، داخل آن نمایش داده می‌شود. به محض اینکه کاربر شروع به تایپ کند، این متن ناپدید می‌شود و در صورت پاک کردن مجدد متن، دوباره نشان داده خواهد شد.

در نمونه زیر، یک input از نوع `url` به همراه placeholder با مقدار `http://www.example.com` تعریف شده است:

```html
<input
  id="myURL"
  name="myURL"
  type="url"
  placeholder="http://www.example.com" />
```

### کنترل اندازه input

شما می‌توانید هم طول ظاهری فیلد ورودی در صفحه و هم حداقل و حداکثر تعداد کاراکترهای مجاز برای متن ورودی را کنترل کنید.

#### اندازه ظاهری element ورودی

با استفاده از attribute (ویژگی) [`size`](/en-US/docs/Web/HTML/Reference/Elements/input#size) می‌توانید اندازه ظاهری فیلد ورودی (input box) را کنترل کنید. این ویژگی مشخص می‌کند که چند کاراکتر به طور هم‌زمان در فیلد نمایش داده شوند. برای مثال، در کد زیر عرض فیلد ورودی `url` برابر با ۳۰ کاراکتر تنظیم شده است:

```html
<input id="myURL" name="myURL" type="url" size="30" />
```

#### محدودیت طول مقدار ورودی

ویژگی `size` ارتباطی با محدودیت طول خود URL واردشده ندارد. برای تعیین حداقل تعداد کاراکتر مجاز برای URL ورودی، می‌توانید از attribute [`minlength`](/en-US/docs/Web/HTML/Reference/Elements/input#minlength) و برای تعیین حداکثر تعداد کاراکتر از [`maxlength`](/en-US/docs/Web/HTML/Reference/Elements/input#maxlength) استفاده کنید. اگر `maxLength` بزرگ‌تر از `size` باشد، محتوای فیلد هنگام تایپ اسکرول می‌شود تا مکان‌نما یا بخش انتخاب‌شده همیشه دیده شود.

در مثال زیر، یک فیلد ورودی URL با عرض ظاهری ۳۰ کاراکتر ایجاد شده است که مقدار ورودی آن باید حداقل ۱۰ و حداکثر ۸۰ کاراکتر باشد.

```html
<input
  id="myURL"
  name="myURL"
  type="url"
  size="30"
  minlength="10"
  maxlength="80" />
```

> [!NOTE]
> این ویژگی‌ها روی اعتبارسنجی (validation) نیز تأثیر می‌گذارند. اگر طول مقدار واردشده کمتر از حداقل یا بیشتر از حداکثر تعیین‌شده باشد، ورودی نامعتبر (invalid) شناخته می‌شود. علاوه بر این، بیشتر مرورگرها اجازه نمی‌دهند کاربر متنی طولانی‌تر از مقدار `maxlength` را تایپ کند.

### تعیین گزینه‌های پیش‌فرض

#### تعیین یک مقدار پیش‌فرض واحد با ویژگی value

مانند تمام فیلدهای ورودی دیگر، برای فیلد `url` هم می‌توانید با استفاده از attribute [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) یک مقدار پیش‌فرض تعیین کنید:

```html
<input id="myURL" name="myURL" type="url" value="http://www.example.com" />
```

#### ارائه گزینه‌های پیشنهادی

یک گام فراتر اینکه می‌توانید با استفاده از attribute [`list`](/en-US/docs/Web/HTML/Reference/Elements/input#list) لیستی از گزینه‌های پیش‌فرض را به کاربر پیشنهاد دهید. این کار کاربر را به انتخاب این گزینه‌ها محدود نمی‌کند، بلکه به او اجازه می‌دهد تا آدرس‌های متداول را سریع‌تر انتخاب کند. این ویژگی به عملکرد [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete) نیز کمک می‌کند. ویژگی `list` شناسه (ID) یک عنصر {{HTMLElement("datalist")}} را دریافت می‌کند. این عنصر نیز شامل چندین عنصر {{HTMLElement("option")}} است که هر کدام یکی از مقادیر پیشنهادی را در خود دارند. ویژگی `value` در هر `option` مقدار پیشنهادی برای فیلد URL را مشخص می‌کند.

```html
<input id="myURL" name="myURL" type="url" list="defaultURLs" />

<datalist id="defaultURLs">
  <option value="https://developer.mozilla.org/"></option>
  <option value="http://www.google.com/"></option>
  <option value="http://www.microsoft.com/"></option>
  <option value="https://www.mozilla.org/"></option>
  <option value="http://w3.org/"></option>
</datalist>
```

با تعریف عنصر {{HTMLElement("datalist")}} و گزینه‌های درون آن ({{HTMLElement("option")}})، browser مقادیر مشخص‌شده را به عنوان گزینه‌های پیشنهادی به کاربر نمایش می‌دهد؛ این پیشنهادها معمولاً به صورت یک منوی کشویی (drop-down) یا پاپ‌آپ ظاهر می‌شوند. اگرچه نحوه نمایش در مرورگرهای مختلف ممکن است کمی متفاوت باشد، اما معمولاً با کلیک روی فیلد ورودی، لیست پیشنهادی باز می‌شود. با شروع تایپ توسط کاربر، این لیست فیلتر شده و فقط مقادیر همخوانی‌دار نمایش داده می‌شوند. هر کاراکتری که تایپ می‌شود، گزینه‌ها را محدودتر می‌کند تا زمانی که کاربر یکی را انتخاب کند یا آدرس اختصاصی خود را بنویسد.

#### استفاده از برچسب (label) برای گزینه‌های پیشنهادی

می‌توانید با افزودن attribute [`label`](/en-US/docs/Web/HTML/Reference/Elements/option#label) به تگ‌های `<option>`، برای هر گزینه یک برچسب متنی تعریف کنید. برخی مرورگرها ممکن است فقط این برچسب‌ها را نشان دهند و برخی دیگر هم برچسب و هم آدرس URL را در کنار هم نمایش دهند.

```html
<input id="myURL" name="myURL" type="url" list="defaultURLs" />

<datalist id="defaultURLs">
  <option value="https://developer.mozilla.org/" label="MDN Web Docs"></option>
  <option value="http://www.google.com/" label="Google"></option>
  <option value="http://www.microsoft.com/" label="Microsoft"></option>
  <option value="https://www.mozilla.org/" label="Mozilla"></option>
  <option value="http://w3.org/" label="W3C"></option>
</datalist>
```

## Validation

اعتبارسنجی (Validation) مقادیر ورودی در `url` در دو سطح انجام می‌شود. سطح اول، همان اعتبارسنجی استاندارد تمام عناصر `<input>` است که به طور خودکار بررسی می‌کند آیا مقدار وارد شده یک URL معتبر است یا خیر. علاوه بر این، می‌توانید فیلترهای دلخواه خود را هم اضافه کنید تا ورودی‌ها دقیقاً مطابق با نیازهای اختصاصی پروژه شما باشند.

> [!WARNING]
> اعتبارسنجی فرم‌ها در سمت HTML هرگز جایگزین مناسبی برای کدهای اعتبارسنجی سمت سرور نیست. دور زدن یا حذف کامل کدهای HTML برای کاربران کار بسیار ساده‌ای است. همچنین کاربران می‌توانند فرآیند HTML را کاملاً نادیده گرفته و داده‌ها را مستقیماً به سرور ارسال کنند. اگر سرور داده‌های دریافتی را اعتبارسنجی نکند، ورود داده‌های نامعتبر، بسیار حجیم یا با فرمت اشتباه به دیتابیس می‌تواند مشکلات جدی ایجاد کند.

### اعتبارسنجی پایه

مرورگرهایی که از نوع ورودی `url` پشتیبانی می‌کنند، به صورت خودکار بررسی می‌کنند که متن وارد شده در کادر ورودی حتماً ساختار استاندارد یک URL را داشته باشد.

ساختار (Syntax) یک URL جزئیات و پیچیدگی‌های زیادی دارد که توسط استاندارد [URL Living Standard](https://url.spec.whatwg.org/) از گروه WHATWG تعریف شده است. اگر می‌خواهید با این ساختار بیشتر آشنا شوید، می‌توانید مقاله [URL چیست؟](/en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL) را مطالعه کنید.

### اجباری کردن وارد کردن URL

همان‌طور که پیش‌تر اشاره شد، برای اجباری کردن پر کردن فیلد URL قبل از ارسال فرم (به طوری که کاربر نتواند آن را خالی بگذارد)، کافی است ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) را به عنصر `input` اضافه کنید.

### اعتبارسنجی با الگو (Pattern)

اگر می‌خواهید ورودی را به مواردی فراتر از یک URL ساده و کلی محدود کنید، می‌توانید از ویژگی [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) استفاده کنید. با این ویژگی می‌توانید یک عبارت باقاعده (Regular Expression) تعریف کنید که مقدار ورودی حتماً باید با آن مطابقت داشته باشد.

## Examples

### اعتبارسنجی URL

در این مثال، با استفاده از ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) پر کردن فیلد را اجباری می‌کنیم. همچنین با کمک ویژگی [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) شرایطی تعیین می‌کنیم که آدرس وارد شده حتماً متعلق به دامنه `mozilla.org` باشد.

#### HTML

در این ورودی `url`، ویژگی `pattern` را روی مقدار `".*\.mozilla\.org.*"` تنظیم کرده‌ایم. این عبارت باقاعده رشته‌ای را تایید می‌کند که شامل هر تعدادی کاراکتر در ابتدا، سپس عبارت ".mozilla.org" و بعد از آن مجدداً هر تعدادی کاراکتر باشد. از آنجایی که مرورگر هم فیلتر استاندارد URL و هم الگوی اختصاصی ما را روی متن اعمال می‌کند، خروجی نهایی این خواهد بود: "ورودی باید یک URL معتبر باشد و در عین حال شامل عبارت `.mozilla.org` نیز باشد."

توجه داشته باشید که الگوهای دقیق‌تری مانند `https://developer\.mozilla\.org.*` امنیت و دقت بالاتری دارند، اما استفاده از آن‌ها در این سناریو، ویژگی `type="url"` را عملاً بی‌استفاده (Redundant) می‌کند.

ویژگی [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title) نیز راهنمایی درباره الگو (Pattern) را در اختیار کاربران فناوری‌های کمکی (مانند صفحه‌خوان‌ها) قرار می‌دهد.

```html live-sample___url-validation
<form>
  <label for="myURL">
    Enter a url from this site:
    <input
      id="myURL"
      name="myURL"
      type="url"
      required
      pattern=".*\.mozilla\.org.*"
      title="URL should include mozilla.org" />
    <span class="validity"></span>
  </label>
  <button>Submit</button>
</form>
```

#### CSS

با استفاده از CSS می‌توان راهنماهای بصری ایجاد کرد تا کاربر متوجه معتبر ({{cssxref(":valid")}}) یا نامعتبر ({{cssxref(":invalid")}}) بودن محتوا شود. این کار با افزودن ویژگی {{cssxref("content")}} مناسب انجام می‌شود و همچنین شامل یک [متن جایگزین (alternative text)](/en-US/docs/Web/CSS/Reference/Properties/content#alternative_text_string_counter_attr) برای کاربران ابزارهای کمکی (accessibility) است.

```css live-sample___url-validation
input:focus:invalid {
  outline: 2px solid red;
}

input:focus:valid {
  outline: 2px solid green;
}

input + span {
  padding: 0 0.3rem;
}

input:invalid + span::after {
  content: "✖" / "Content is not valid";
  color: red;
}

input:valid + span::after {
  content: "✓" / "Content is valid";
  color: green;
}
```

#### نتیجه

آدرس (URL) این صفحه را کپی کرده و در فیلد ورودی قرار دهید؛ در این حالت یک outline و تیک سبز رنگ مشاهده خواهید کرد. اگر آدرس دیگری را وارد کنید که شامل **mozilla.org** نباشد یا ساختار URL آن نامعتبر باشد، یک outline و علامت ضربدر قرمز رنگ نمایش داده می‌شود.

برای مشاهده نمونه‌های دیگر، بخش‌های [اعتبارسنجی الگو (Pattern validation)](#pattern_validation) و [استفاده از ورودی‌های URL (Using URL inputs)](#using_url_inputs) را بررسی کنید.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <td><strong><a href="#value">مقدار (Value)</a></strong></td>
      <td>یک رشته متنی (string) معرف یک URL، یا خالی</td>
    </tr>
    <tr>
      <td><strong>رویدادها (Events)</strong></td>
      <td>
        {{domxref("HTMLElement/change_event", "change")}} و
        {{domxref("Element/input_event", "input")}}
      </td>
    </tr>
    <tr>
      <td><strong>اتریبیوت‌های مشترک پشتیبانی‌شده</strong></td>
      <td>
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#autocomplete"><code>autocomplete</code></a>،
        <a href="/en-US/docs/Web/HTML/Reference/Elements/input#list"><code>list</code></a>،
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
      <td><strong>اتریبیوت‌های IDL</strong></td>
      <td>
        <code>list</code>، <code>value</code>، <code>selectionEnd</code>،
        <code>selectionDirection</code>
      </td>
    </tr>
    <tr>
      <td><strong>اینترفیس DOM</strong></td>
      <td><p>{{domxref("HTMLInputElement")}}</p></td>
    </tr>
    <tr>
      <td><strong>نقش ضمنی ARIA (Implicit ARIA Role)</strong></td>
      <td>
        بدون اتریبیوت <code>list</code>:
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role">textbox</a></code><br />
        با اتریبیوت <code>list</code>: <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role">combobox</a></code>
      </td>
    </tr>
  </tbody>
</table>

## مشخصات فنی

## سازگاری با مرورگرها

## همچنین ببینید

- [راهنمای فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)
- {{HTMLElement("input")}}
- [`<input type="tel">`](/en-US/docs/Web/HTML/Reference/Elements/input/tel)
- [`<input type="email">`](/en-US/docs/Web/HTML/Reference/Elements/input/email)