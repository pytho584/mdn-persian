---
title: <input type="search"> HTML attribute value
source: >-
  https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/search
translated_by: n8n + AI
---

# \<input type="search"> HTML attribute value

عناصر `<input type="search">` فیلدهای متنی هستند که کاربر برای وارد کردن عبارت جستجو از آن‌ها استفاده می‌کند. این فیلدها از نظر عملکردی با inputهای نوع `text` تفاوتی ندارند، اما ممکن است مرورگر (user agent) آن‌ها را به شکلی متفاوت نمایش دهد.

```html
<label for="site-search">Search the site:</label>
<input type="search" id="site-search" name="q" />

<button>Search</button>
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

### مقدار (Value)

ویژگی [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) یک رشته (string) را نگه می‌دارد که مقدار وارد شده در فیلد جستجو را نشان می‌دهد. در جاوااسکریپت می‌توانید از طریق [`HTMLInputElement.value`](../../../../../../../../en-US/docs/Web/API/HTMLInputElement/value/) به این مقدار دسترسی داشته باشید.

```js
searchTerms = mySearch.value;
```

اگر محدودیت اعتبارسنجی خاصی برای این input در نظر گرفته نشده باشد (برای جزئیات بیشتر به بخش [اعتبارسنجی](index.md#validation) مراجعه کنید)، مقدار می‌تواند هر رشته‌ای (حتی رشته خالی `""`) باشد.

### ویژگی‌های اضافی (Additional attributes)

علاوه بر [ویژگی‌های سراسری (global attributes)](../../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) و ویژگی‌هایی که روی همه عناصر \{{HTMLElement("input")\}} صرف‌نظر از نوع آن‌ها اعمال می‌شود، فیلدهای جستجو از ویژگی‌های زیر نیز پشتیبانی می‌کنند.

#### list

مقدار ویژگی `list`، `id` یک عنصر \{{HTMLElement("datalist")\}} در همان سند است. این \{{HTMLElement("datalist")\}} فهرستی از مقادیر از پیش‌تعریف‌شده را برای پیشنهاد به کاربر در این input فراهم می‌کند. هر مقداری در این فهرست که با [`type`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#type) سازگار نباشد، در گزینه‌های پیشنهادی نمایش داده نمی‌شود. مقادیر ارائه‌شده صرفاً پیشنهاد هستند، نه الزام؛ کاربر می‌تواند از این فهرست انتخاب کند یا مقدار دیگری وارد کند.

#### maxlength

حداکثر طول رشته (بر حسب \{{glossary("UTF-16", "واحد کد UTF-16")\}}) که کاربر می‌تواند در فیلد جستجو وارد کند. این مقدار باید یک عدد صحیح 0 یا بیشتر باشد. اگر `maxlength` مشخص نشود یا مقدار نامعتبری داشته باشد، فیلد جستجوی حداکثر طول نخواهد داشت. این مقدار همچنین باید بزرگ‌تر یا مساوی مقدار `minlength` باشد.

اگر طول متن وارد شده در فیلد از `maxlength` \{{glossary("UTF-16", "واحد کد UTF-16")\}} بیشتر باشد، input در [اعتبارسنجی محدودیت‌ها (constraint validation)](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) با خطا مواجه می‌شود. اعتبارسنجی فقط زمانی اعمال می‌شود که کاربر مقدار را تغییر دهد.

#### minlength

حداقل طول رشته (بر حسب \{{glossary("UTF-16", "واحد کد UTF-16")\}}) که کاربر می‌تواند در فیلد جستجو وارد کند. این مقدار باید یک عدد صحیح غیرمنفی و کوچک‌تر یا مساوی مقدار `maxlength` باشد. اگر `minlength` مشخص نشود یا مقدار نامعتبری داشته باشد، فیلد جستجوی حداقل طول نخواهد داشت.

اگر طول متن وارد شده در فیلد از `minlength` \{{glossary("UTF-16", "واحد کد UTF-16")\}} کمتر باشد، فیلد جستجو در [اعتبارسنجی محدودیت‌ها](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) با خطا مواجه می‌شود. اعتبارسنجی فقط زمانی اعمال می‌شود که کاربر مقدار را تغییر دهد.

#### pattern

ویژگی `pattern`، در صورت مشخص شدن، یک عبارت منظم است که مقدار [`value`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#value) ورودی باید با آن مطابقت داشته باشد تا از [اعتبارسنجی محدودیت‌ها](../../../../../../../../en-US/docs/Web/HTML/Guides/Constraint_validation/) عبور کند. این عبارت باید یک عبارت منظم معتبر جاوااسکریپت باشد، همانطور که توسط نوع \{{jsxref("RegExp")\}} استفاده می‌شود و در [راهنمای عبارت‌های منظم](../../../../../../../../en-US/docs/Web/JavaScript/Guide/Regular_expressions/) مستند شده است. هنگام کامپایل عبارت منظم، پرچم `'u'` اضافه می‌شود تا الگو به‌عنوان دنباله‌ای از کدپوینت‌های Unicode در نظر گرفته شود، نه به‌عنوان \{{Glossary("ASCII")\}}. در متن الگو نباید از اسلش‌های جلو استفاده شود.

اگر الگوی مشخص‌شده تعریف نشده یا نامعتبر باشد، هیچ عبارت منظمی اعمال نمی‌شود و این ویژگی کاملاً نادیده گرفته می‌شود.

> **نکته:** از ویژگی [`title`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#title) برای مشخص کردن متنی استفاده کنید که مرورگرها معمولاً به‌عنوان tooltip نمایش می‌دهند تا توضیح دهد شرایط مطابقت با الگو چیست. همچنین باید متن توضیحی دیگری در نزدیکی آن بیاورید.

برای جزئیات و یک مثال، بخش [مشخص کردن یک الگو](index.md#specifying_a_pattern) را ببینید.

#### placeholder

ویژگی `placeholder` یک رشته است که یک راهنمای کوتاه به کاربر می‌دهد تا بفهمد چه نوع اطلاعاتی در فیلد مورد انتظار است. این باید یک کلمه یا عبارت کوتاه باشد که نوع دادهٔ مورد انتظار را نشان دهد، نه یک پیام توضیحی. متن نباید شامل carriage return یا line feed باشد.

اگر محتوای کنترل یک جهت‌گیری دارد (\{{Glossary("LTR")\}} یا \{{Glossary("RTL")\}}) اما باید placeholder را در جهت مخالف نمایش دهد، می‌توانید از کاراکترهای قالب‌بندی الگوریتم دوطرفهٔ Unicode برای نادیده گرفتن جهت‌گیری درون placeholder استفاده کنید. برای اطلاعات بیشتر به [چگونگی استفاده از کنترل‌های Unicode برای متن دوطرفه](https://www.w3.org/International/questions/qa-bidi-unicode-controls) مراجعه کنید.

> **نکته:** اگر می‌توانید، از استفاده از ویژگی `placeholder` خودداری کنید. این ویژگی به اندازهٔ روش‌های دیگر برای توضیح فرم از نظر معنایی مفید نیست و می‌تواند مشکلات فنی غیرمنتظره‌ای در محتوای شما ایجاد کند. برای اطلاعات بیشتر به [`<input>` labels](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#labels) مراجعه کنید.

#### readonly

یک ویژگی Boolean که در صورت وجود، به این معنی است که کاربر نمی‌تواند این فیلد را ویرایش کند. با این حال، مقدار `value` آن همچنان می‌تواند توسط کد جاوااسکریپت از طریق تنظیم مستقیم property `value` در \{{domxref("HTMLInputElement")\}} تغییر یابد.

> **نکته:** از آنجا که یک فیلد read‑only نمی‌تواند مقدار داشته باشد، `required` روی ورودی‌هایی که ویژگی `readonly` نیز دارند تأثیری ندارد.

#### size

ویژگی `size` یک مقدار عددی است که نشان می‌دهد فیلد ورودی چند کاراکتر عرض داشته باشد. مقدار باید عددی بزرگتر از صفر باشد و مقدار پیش‌فرض ۲۰ است. از آنجایی که پهنای کاراکترها متفاوت است، این مقدار ممکن است دقیق نباشد و نباید به آن برای دقت اعتماد کرد؛ ورودی حاصل ممکن است باریک‌تر یا عریض‌تر از تعداد کاراکتر مشخص‌شده باشد، بسته به کاراکترها و فونت (تنظیمات \{{cssxref("font")\}} در حال استفاده).

این ویژگی **محدودیتی** برای تعداد کاراکترهایی که کاربر می‌تواند در فیلد وارد کند تعیین نمی‌کند. فقط تقریباً مشخص می‌کند که در یک زمان چند کاراکتر قابل مشاهده است. برای تعیین یک حد بالایی برای طول دادهٔ ورودی، از ویژگی [`maxlength`](index.md#maxlength) استفاده کنید.

#### spellcheck

[`spellcheck`](../../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck/) یک ویژگی سراسری است که برای نشان دادن فعال یا غیرفعال بودن غلط‌یابی املایی برای یک عنصر استفاده می‌شود. می‌توان آن را روی هر محتوای قابل ویرایش استفاده کرد، اما در اینجا جزئیات مربوط به استفاده از `spellcheck` روی عناصر \{{HTMLElement("input")\}} را بررسی می‌کنیم. مقادیر مجاز برای `spellcheck` عبارتند از:

* `false`
  * : غلط‌یابی املایی را برای این عنصر غیرفعال کنید.
* `true`
  * : غلط‌یابی املایی را برای این عنصر فعال کنید.
* "" (رشتهٔ خالی) یا بدون مقدار
  * : از رفتار پیش‌فرض عنصر برای غلط‌یابی املایی پیروی کنید. این ممکن است بر اساس تنظیمات `spellcheck` والد یا عوامل دیگر باشد.

یک فیلد ورودی می‌تواند قابلیت بررسی املا داشته باشد، اگر ویژگی [`readonly`](index.md#readonly) روی آن تنظیم نشده باشد و غیرفعال (disabled) نباشد.

مقداری که با خواندن `spellcheck` به دست می‌آید ممکن است وضعیت واقعی بررسی املا در آن کنترل را منعکس نکند، اگر تنظیمات دلخواه \{{Glossary("user agent", "user agent")\}} بر این تنظیم غلبه کند.

### ویژگی‌های غیراستاندارد

ویژگی‌های غیراستاندارد زیر برای فیلدهای ورودی جستجو در دسترس هستند. تا جای ممکن از استفاده از آن‌ها خودداری کنید.

#### incremental

ویژصیت بولین `incremental` یک افزونهٔ WebKit و Blink است (بنابراین توسط Safari، Opera، Chrome و ... پشتیبانی می‌شود). اگر وجود داشته باشد، به \{{Glossary("user agent")\}} می‌گوید که ورودی را به‌عنوان یک جستجوی زنده پردازش کند. وقتی کاربر مقدار فیلد را ویرایش می‌کند، user agent رویدادهای \{{domxref("HTMLInputElement/search\_event", "search")\}} را به شیء \{{domxref("HTMLInputElement")\}} که نمایندهٔ جعبه جستجو است می‌فرستد. این به کد شما اجازه می‌دهد نتایج جستجو را در زمان واقعی و هم‌زمان با ویرایش جستجو توسط کاربر به‌روز کند.

اگر `incremental` مشخص نشده باشد، رویداد \{{domxref("HTMLInputElement/search\_event", "search")\}} فقط زمانی ارسال می‌شود که کاربر به‌طور صریح جستجویی را آغاز کند (مثلاً با فشار دادن کلید <kbd>Enter</kbd> یا <kbd>Return</kbd> در حین ویرایش فیلد).

رویداد `search` محدود به نرخ (rate-limited) است به‌طوری که بیشتر از یک بازهٔ زمانی تعریف‌شده توسط پیاده‌سازی ارسال نشود.

#### results

ویژگی `results` – که فقط توسط Safari پشتیبانی می‌شود – یک مقدار عددی است که به شما امکان می‌دهد حداکثر تعداد ورودی‌هایی را که در منوی کشویی ارائه‌شده توسط خود عنصر \{{HTMLElement("input")\}} برای جستجوهای قبلی نمایش داده می‌شود، بازنویسی کنید.

مقدار باید یک عدد اعشاری غیرمنفی باشد. اگر ارائه نشود یا مقدار نامعتبری داده شود، از حداکثر تعداد پیش‌فرض مرورگر استفاده می‌شود.

### استفاده از ورودی‌های جستجو

عناصر `<input>` از نوع `search` بسیار شبیه به عناصر نوع `text` هستند، با این تفاوت که به‌طور خاص برای مدیریت عبارت‌های جستجو در نظر گرفته شده‌اند. آن‌ها اساساً از نظر رفتار معادل هستند، اما user agentها ممکن است به‌طور پیش‌فرض آن‌ها را متفاوت استایل کنند (و البته سایت‌ها می‌توانند از stylesheetها برای اعمال استایل‌های سفارشی به آن‌ها استفاده کنند).

#### مثال پایه

```html
<form>
  <div>
    <input type="search" id="mySearch" name="q" />
    <button>Search</button>
  </div>
</form>
```

این طور نمایش داده می‌شود:

\{{EmbedLiveSample("Basic\_example", 600, 40)\}}

`q` رایج‌ترین `name`ای است که به ورودی‌های جستجو داده می‌شود، اگرچه الزامی نیست. هنگام ارسال، جفت نام/مقداری که به سرور ارسال می‌شود به صورت `q=searchTerm` خواهد بود.

> \[!NOTE] باید حتماً یک [`name`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#name) برای ورودی خود تنظیم کنید، در غیر این صورت چیزی ارسال نخواهد شد.

#### تفاوت‌های بین انواع search و text

تفاوت‌های اصلی و پایه‌ای در نحوه مدیریت آن‌ها توسط مرورگرهاست. اولین نکته این است که برخی مرورگرها یک آیکون ضربدر نشان می‌دهند که می‌توان روی آن کلیک کرد تا عبارت جستجو فوراً حذف شود. در Chrome این عمل با فشردن کلید Escape نیز فعال می‌شود. تصویر زیر از Chrome است:

علاوه بر این، مرورگرهای مدرن معمولاً عبارت‌های جستجوی قبلی را در دامنه‌های مختلف ذخیره می‌کنند، که سپس به‌عنوان گزینه‌های تکمیل خودکار در جستجوهای بعدی در ورودی‌های جستجوی آن دامنه ظاهر می‌شوند. این به کاربرانی کمک می‌کند که معمولاً جستجوهای مشابهی را انجام می‌دهند. این تصویر از Firefox است:

در اینجا، بیایید به برخی تکنیک‌های مفید که می‌توانید در فرم‌های جستجوی خود اعمال کنید نگاه کنیم.

#### تنظیم placeholderها

می‌توانید درون فیلد جستجو یک placeholder (متن راهنما) قرار دهید تا کاربر متوجه شود چه کاری باید انجام دهد. این کار با استفاده از attribute [`placeholder`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#placeholder) انجام می‌شود. مثال زیر را ببینید:

```html
<form>
  <div>
    <input
      type="search"
      id="mySearch"
      name="q"
      placeholder="Search the site…" />
    <button>Search</button>
  </div>
</form>
```

در مرورگر، این placeholder به صورت زیر نمایش داده می‌شود:

#### برچسب‌ها و دسترسی‌پذیری در فرم جستجو

یکی از مشکلات فرم‌های جستجو، دسترسی‌پذیری (accessibility) آنهاست. یک الگوی طراحی رایج این است که برای فیلد جستجو برچسب (label) جداگانه‌ای قرار ندهند (هرچند ممکن است یک آیکون ذره‌بین یا مشابه آن وجود داشته باشد)، زیرا معمولاً مکان قرارگیری فیلد جستجو برای کاربران بینا مقصود آن را مشخص می‌کند ([این مثال یک الگوی رایج را نشان می‌دهد](https://mdn.github.io/learning-area/accessibility/aria/website-aria-roles/)).

اما این می‌تواند برای کاربران screen reader (صفحه‌خوان) گیج‌کننده باشد، زیرا هیچ نشانهٔ کلامی از کاربرد فیلد جستجو دریافت نمی‌کنند. راهی برای جلوگیری از این مشکل بدون تأثیر بر طراحی بصری، استفاده از [landmark elements (عناصر نقاط عطف)](../../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/landmark_role/) است.

* کل بخش جستجو را درون یک عنصر \{{HTMLElement("search")\}} قرار دهید. این عنصر یک منطقهٔ landmark (نقطه عطف) ایجاد می‌کند که فناوری‌های کمکی می‌توانند آن را اعلام کرده و کاربر به سرعت به آن پیمایش کند. اگر `<input>` شما از قبل درون یک `<form>` است، می‌توانید به جای آن به عنصر `<form>` یک [`role="search"`](../../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role/) اضافه کنید که آن را نیز به یک landmark جستجو تبدیل می‌کند. عنصر `<search>` از معناشناسی (semantics) بومی HTML استفاده می‌کند، در حالی که `role="search"` پشتیبانی بیشتری دارد و اگر از قبل یک wrapper `<form>` دارید، تایپ آن کوتاه‌تر است.
* اگر این کافی نبود، می‌توانید از attribute [`aria-label`](../../../../../../../../en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label/) روی خود \{{HTMLElement("input")\}} استفاده کنید. این attribute یک برچسب متنی توصیفی است که screen reader آن را می‌خواند؛ به عنوان معادل غیربصری `<label>` عمل می‌کند.

بیایید یک مثال را بررسی کنیم:

```html
<search>
  <form>
    <div>
      <input
        type="search"
        id="mySearch"
        name="q"
        placeholder="Search the site…"
        aria-label="Search through site content" />
      <button>Search</button>
    </div>
  </form>
</search>
```

نمایش این کد در مرورگر تفاوتی با مثال قبلی ندارد، اما کاربران screen reader اطلاعات بسیار بیشتری در دسترس دارند.

> \[!NOTE]\
> برای اطلاعات بیشتر دربارهٔ این ویژگی‌های دسترسی‌پذیری، به بخش [Signposts/Landmarks](../../../../../../../../en-US/docs/Learn_web_development/Core/Accessibility/WAI-ARIA_basics/#signpostslandmarks) مراجعه کنید.

#### اندازهٔ فیزیکی عنصر input

اندازهٔ فیزیکی جعبهٔ ورودی را می‌توان با attribute [`size`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#size) کنترل کرد. با استفاده از آن می‌توانید تعداد کاراکترهایی را که جعبه در یک لحظه نمایش می‌دهد مشخص کنید. برای مثال، در اینجا جعبهٔ جستجو ۳۰ کاراکتر عرض دارد:

```html
<form>
  <div>
    <input
      type="search"
      id="mySearch"
      name="q"
      placeholder="Search the site…"
      size="30" />
    <button>Search</button>
  </div>
</form>
```

نتیجه یک جعبهٔ ورودی عریض‌تر است:

### اعتبارسنجی (Validation)

عناصر `<input>` از نوع `search` همان ویژگی‌های اعتبارسنجی مشابه ورودی‌های معمولی `text` را دارند. اما معمولاً نیازی به استفاده از این ویژگی‌ها برای جعبه‌های جستجو نیست. در بسیاری موارد کاربران باید بتوانند هر چیزی را جستجو کنند، اما مواردی مانند جستجو در داده‌هایی با فرمت مشخص قابل بررسی است.

> \[!NOTE] اعتبارسنجی فرم در HTML جایگزینی برای اسکریپت‌هایی _نیست_ که تضمین می‌کنند داده‌های واردشده در قالب درست هستند. خیلی راحت می‌توان HTML را طوری تغییر داد که اعتبارسنجی را دور بزند یا کاملاً حذف کند. همچنین ممکن است شخصی اصلاً از HTML شما عبور کند و داده‌ها را مستقیماً به سرور شما ارسال کند. اگر کد سمت سرور شما داده‌های دریافتی را اعتبارسنجی نکند، وقتی داده‌هایی با فرمت نامناسب (یا داده‌هایی که بیش از حد بزرگ هستند، نوع اشتباهی دارند و غیره) وارد پایگاه‌داده شما شوند، ممکن است فاجعه رخ دهد.

#### نکته‌ای درباره استایل‌دهی

pseudo-classهای مفیدی برای استایل‌دهی به elementهای فرم معتبر/نامعتبر در دسترس است: `:valid` و `:invalid`. در این بخش از CSS زیر استفاده می‌کنیم که یک تیک (چک‌مارک) کنار inputهای دارای مقدار معتبر و یک ضربدر کنار inputهای دارای مقدار نامعتبر قرار می‌دهد.

```css
input:invalid ~ span::after {
  content: "✖";
  padding-left: 5px;
  position: absolute;
}

input:valid ~ span::after {
  content: "✓";
  padding-left: 5px;
  position: absolute;
}
```

این روش همچنین نیاز دارد که یک element `<span>` بعد از element فرم قرار بگیرد که نقش نگهدارنده آیکون‌ها را داشته باشد. این لازم بود چون بعضی input typeها در بعضی browserها آیکون‌هایی را که بلافاصله بعد از آن‌ها قرار می‌گیرند به خوبی نمایش نمی‌دهند.

#### الزامی کردن input

برای الزامی کردن مقدار ورودی قبل از اجازه ارسال فرم، می‌توانید به‌عنوان راهی ساده از attribute [`required`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#required) استفاده کنید:

```html
<form>
  <div>
    <input
      type="search"
      id="mySearch"
      name="q"
      placeholder="Search the site…"
      required />
    <button>Search</button>
    <span class="validity"></span>
  </div>
</form>
```

```css
input {
  margin-right: 10px;
}

input:invalid ~ span::after {
  content: "✖";
  padding-left: 5px;
  position: absolute;
}

input:valid ~ span::after {
  content: "✓";
  padding-left: 5px;
  position: absolute;
}
```

نتیجه به این صورت است:

علاوه بر این، اگر فرم را بدون وارد کردن عبارت جستجو ارسال کنید، browser پیامی نشان می‌دهد. مثال زیر از Firefox است:

پیام‌های متفاوتی هنگام ارسال فرم با انواع مختلف داده‌های نامعتبر داخل inputها نمایش داده می‌شود؛ مثال‌های زیر را ببینید.

#### طول مقدار input

با استفاده از attribute [`minlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#minlength) می‌توانید حداقل طول (بر حسب کاراکتر) مقدار واردشده را تعیین کنید؛ به همین ترتیب، از [`maxlength`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#maxlength) برای تعیین حداکثر طول مقدار واردشده استفاده کنید.

مثال زیر لازم دارد مقدار واردشده بین ۴ تا ۸ کاراکتر باشد.

```html
<form>
  <div>
    <label for="mySearch">Search for user</label>
    <input
      type="search"
      id="mySearch"
      name="q"
      placeholder="User IDs are 4–8 characters in length"
      required
      size="30"
      minlength="4"
      maxlength="8" />
    <button>Search</button>
    <span class="validity"></span>
  </div>
</form>
```

```css
input {
  margin-right: 10px;
}

input:invalid ~ span::after {
  content: "✖";
  padding-left: 5px;
  position: absolute;
}

input:valid ~ span::after {
  content: "✓";
  padding-left: 5px;
  position: absolute;
}
```

نتیجه به این صورت است:

اگر فرم را با کمتر از ۴ کاراکتر ارسال کنید، پیام خطای مناسبی دریافت می‌کنید (که بین browserها متفاوت است). اگر بخواهید بیش از ۸ کاراکتر وارد کنید، browser به شما اجازه نمی‌دهد.

#### تعیین pattern

می‌توانید از attribute [`pattern`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/#pattern) استفاده کنید تا یک regular expression مشخص کنید که مقدار ورودی باید از آن پیروی کند تا معتبر در نظر گرفته شود (برای آشنایی سریع به [Validating against a regular expression](../../../../../../../../en-US/docs/Learn_web_development/Extensions/Forms/Form_validation/#validating_against_a_regular_expression) مراجعه کنید).

بیایید یک مثال ببینیم. فرض کنید می‌خواهیم یک فرم جستجوی شناسه محصول ارائه دهیم، و همه شناسه‌ها کدهای دو حرفی به دنبال چهار عدد هستند. مثال زیر این کار را پوشش می‌دهد:

```html
<form>
  <div>
    <label for="mySearch">Search for product by ID:</label>
    <input
      type="search"
      id="mySearch"
      name="q"
      placeholder="two letters followed by four numbers"
      required
      size="30"
      pattern="[A-z]{2}[0-9]{4}" />
    <button>Search</button>
    <span class="validity"></span>
  </div>
</form>
```

```css
input {
  margin-right: 10px;
}

input:invalid ~ span::after {
  content: "✖";
  padding-left: 5px;
  position: absolute;
}

input:valid ~ span::after {
  content: "✓";
  padding-left: 5px;
  position: absolute;
}
```

نمایش آن به این صورت است:

(نمونه زنده حذف شد)

### مثال‌ها

یک مثال خوب از فرم جستجو در بستر واقعی را می‌توانید در نمونه [website-aria-roles](https://github.com/mdn/learning-area/tree/main/accessibility/aria/website-aria-roles) ببینید ([مشاهده نسخه زنده](https://mdn.github.io/learning-area/accessibility/aria/website-aria-roles/)).

### خلاصه فنی

| ویژگی                            | توضیحات                                                                                                                  |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **مقدار (Value)**                | یک رشته که مقدار موجود در فیلد جستجو را نشان می‌دهد.                                                                     |
| **رویدادها (Events)**            | `change` و `input`                                                                                                       |
| **ویژگی‌های مشترک پشتیبانی‌شده** | `autocomplete`, `list`, `maxlength`, `minlength`, `pattern`, `placeholder`, `required`, `size`                           |
| **ویژگی‌های IDL**                | `value`                                                                                                                  |
| **رابط DOM**                     | `HTMLInputElement`                                                                                                       |
| **نقش ARIA ضمنی**                | <p>بدون attribute <code>list</code>: <code>searchbox</code><br>با attribute <code>list</code>: <code>combobox</code></p> |

### مشخصات

(بخش Specifications حذف شد)

### سازگاری با مرورگرها

(بخش Browser compatibility حذف شد)

### جستارهای وابسته

* [فرم‌های HTML](../../../../../../../../en-US/docs/Learn_web_development/Extensions/Forms/)
* عنصر `<input>` و رابط `HTMLInputElement` که بر اساس آن ساخته شده است
* [`<input type="text">`](../../../../../../../../en-US/docs/Web/HTML/Reference/Elements/input/text/)
