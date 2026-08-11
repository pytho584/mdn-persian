---
title: "<select> HTML select element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/select"
translated_by: "n8n + AI"
---

# عنصر `<select>` در HTML

عنصر **`<select>`** در HTML یک کنترل (control) برای نمایش یک منوی گزینه‌ها است.

```html interactive-example
<label for="pet-select">Choose a pet:</label>

<select name="pets" id="pet-select">
  <option value="">--Please choose an option--</option>
  <option value="dog">Dog</option>
  <option value="cat">Cat</option>
  <option value="hamster">Hamster</option>
  <option value="parrot">Parrot</option>
  <option value="spider">Spider</option>
  <option value="goldfish">Goldfish</option>
</select>
```

```css interactive-example
label {
  font-family: sans-serif;
  font-size: 1rem;
  padding-right: 10px;
}

select {
  font-size: 0.9rem;
  padding: 2px 5px;
}
```

مثال بالا کاربرد معمولی `<select>` را نشان می‌دهد. به این عنصر یک `id` داده شده تا بتوان آن را با یک `<label>` برای دسترسی‌پذیری (accessibility) مرتبط کرد. همچنین یک `name` دارد که نام داده‌ای ارسالی به سرور را مشخص می‌کند. هر گزینه‌ی منو با یک عنصر `<option>` که درون `<select>` قرار گرفته تعریف می‌شود.

هر عنصر `<option>` باید یک ویژگی `value` داشته باشد که مقدار داده‌ای برای ارسال به سرور هنگام انتخاب آن گزینه را مشخص می‌کند. اگر ویژگی `value` وجود نداشته باشد، مقدار پیش‌فرض برابر متن داخل عنصر خواهد بود. می‌توانید یک ویژگی `selected` روی یک `<option>` قرار دهید تا آن گزینه به‌طور پیش‌فرض هنگام بارگذاری صفحه انتخاب شود. اگر `selected` مشخص نشود، اولین `<option>` به‌طور پیش‌فرض انتخاب می‌شود.

یک عنصر `<select>` در JavaScript با شیء `HTMLSelectElement` نمایش داده می‌شود. این شیء یک ویژگی `value` دارد که مقدار گزینه‌ی انتخاب‌شده را نگه می‌دارد.

عنصر `<select>` دارای ویژگی‌های منحصربه‌فردی برای کنترل است، مانند `multiple` برای تعیین اینکه چند گزینه قابل انتخاب باشند، و `size` برای مشخص کردن تعداد گزینه‌های نمایش‌داده‌شده در یک زمان. همچنین بیشتر ویژگی‌های عمومی ورودی فرم مانند `required`، `disabled`، `autofocus` و غیره را می‌پذیرد.

می‌توانید عناصر `<option>` را درون `<optgroup>` قرار دهید تا گروه‌های جداگانه‌ای از گزینه‌ها داخل منوی کشویی ایجاد کنید. همچنین می‌توانید از عناصر `<hr>` برای ایجاد جداکننده‌های بصری بین گزینه‌ها استفاده کنید.

برای مثال‌های بیشتر، به [The native form widgets: Drop-down content](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Other_form_controls#drop-down_controls) مراجعه کنید.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
  - : رشته‌ای که به ویژگی تکمیل خودکار (autocomplete) عامل کاربر (user agent) اشاره می‌دهد. برای فهرست کامل مقادیر و جزئیات نحوه استفاده از autocomplete، به [ویژگی autocomplete در HTML](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete) مراجعه کنید.
- `autofocus`
  - : این ویژگی Boolean به شما امکان می‌دهد مشخص کنید که یک کنترل فرم هنگام بارگذاری صفحه، فوکس ورودی (input focus) داشته باشد. فقط یک عنصر فرم در یک سند می‌تواند ویژگی `autofocus` داشته باشد.
- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
  - : این ویژگی Boolean نشان می‌دهد که کاربر نمی‌تواند با کنترل تعامل داشته باشد. اگر این ویژگی مشخص نشده باشد، کنترل تنظیمات خود را از عنصر والد (مثلاً {{htmlelement("fieldset")}}) به ارث می‌برد؛ اگر عنصر والد با ویژگی `disabled` تنظیم نشده باشد، کنترل فعال است.
- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)
  - : عنصر {{HTMLElement("form")}}ای که `<select>` به آن متصل می‌شود (_مالک فرم_). مقدار این ویژگی باید [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یک `<form>` در همان سند باشد. (اگر این ویژگی تنظیم نشده باشد، `<select>` به عنصر `<form>` ancestor خود متصل می‌شود، در صورت وجود.)

    این ویژگی به شما امکان می‌دهد عناصر `<select>` را به `<form>`هایی در هر جای سند متصل کنید، نه فقط داخل یک `<form>`. همچنین می‌تواند یک عنصر `<form>` ancestor را نادیده بگیرد.

- [`multiple`](/en-US/docs/Web/HTML/Reference/Attributes/multiple)
  - : این ویژگی Boolean نشان می‌دهد که چندین گزینه می‌توانند در لیست انتخاب شوند. اگر مشخص نشده باشد، فقط یک گزینه در هر بار می‌تواند انتخاب شود. وقتی `multiple` مشخص شده است، بیشتر مرورگرها به جای یک drop-down تک‌خطی، یک جعبه لیست پیمایش‌شونده (scrolling list box) نمایش می‌دهند. گزینه‌های انتخاب‌شده با استفاده از قرارداد آرایه‌ای {{domxref("URLSearchParams")}} ارسال می‌شوند، یعنی `name=value1&name=value2`.
- `name`
  - : این ویژگی برای مشخص کردن نام کنترل استفاده می‌شود.
- [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required)
  - : یک ویژگی Boolean که نشان می‌دهد باید یک گزینه با مقدار رشته‌ای غیرخالی انتخاب شود.
- [`size`](/en-US/docs/Web/HTML/Reference/Attributes/size)
  - : اگر کنترل به صورت جعبه لیست پیمایش‌شونده نمایش داده شود (مثلاً وقتی `multiple` مشخص شده است)، این ویژگی تعداد ردیف‌هایی را که باید در یک زمان قابل مشاهده باشند، مشخص می‌کند. مرورگرها ملزم به نمایش یک عنصر select به صورت جعبه لیست پیمایش‌شونده نیستند. مقدار پیش‌فرض `0` است.

    > [!NOTE]
    > طبق مشخصات HTML، مقدار پیش‌فرض برای `size` باید `1` باشد؛ اما در عمل، این موضوع باعث شکستن برخی وب‌سایت‌ها شده است و هیچ مرورگر دیگری در حال حاضر این کار را انجام نمی‌دهد، بنابراین Mozilla تصمیم گرفته است که در حال حاضر در Firefox مقدار `0` را بازگرداند.

## نکات استفاده

### گزینه‌های داخل عناصر wrapper

عنصر `<select>` لیست گزینه‌های خود را از تمام فرزندان `<option>` می‌سازد، نه فقط فرزندان مستقیم. این بدان معناست که گزینه‌ها می‌توانند در عناصر دیگر مانند {{HTMLElement("div")}} پیچیده شوند و همچنان به عنوان گزینه‌های قابل انتخاب در drop-down ظاهر شوند و در ارسال فرم گنجانده شوند. عناصر wrapper برای استایل‌دهی در [عناصر select قابل شخصی‌سازی](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select) مفید هستند، اما تأثیری بر رفتار select ندارند: آنها گروه‌ها، برچسب‌ها یا جداکننده‌ها ایجاد نمی‌کنند. برای گروه‌بندی گزینه‌ها زیر یک عنوان، از {{HTMLElement("optgroup")}} استفاده کنید؛ یک {{HTMLElement("option")}} اگر گروه ancestor باشد، بخشی از `<optgroup>` محسوب می‌شود، بنابراین عناصر wrapper نیز می‌توانند در داخل یک گروه بدون شکستن ارتباط استفاده شوند.

> [!NOTE]
> مرورگرهایی که رفتار تجزیه‌ی مدرن دارند، همه‌ی عناصر نوشته‌شده درون `<select>` را در DOM حفظ می‌کنند — از جمله عناصر wrapper، `<button>` و `<selectedcontent>`.
> مرورگرهای قدیمی‌تر هنگام تجزیه، عناصر غیرمجاز را حذف می‌کنند و فقط ساختار `<option>`، `<optgroup>` و `<hr>` را باقی می‌گذارند.
> در نتیجه، استایل‌دهی، مارک‌آپ یا اسکریپتی که به عناصر حذف‌شده وابسته است، در مرورگرهای قدیمی کار نخواهد کرد.

### انتخاب چند گزینه

در رایانه‌ی رومیزی، چندین روش برای انتخاب چند گزینه در یک عنصر `<select>` با ویژگی `multiple` وجود دارد:

کاربران ماوس می‌توانند کلیدهای <kbd>Ctrl</kbd>، <kbd>Command</kbd> یا <kbd>Shift</kbd> را نگه دارند (بسته به سیستم‌عامل شما) و سپس روی چند گزینه کلیک کنند تا آن‌ها را انتخاب یا از انتخاب خارج کنند.

> [!WARNING]
> سازوکار انتخاب چند آیتم غیرهمجوار با صفحه‌کلید که در ادامه توضیح داده شده، در حال حاضر فقط در Firefox کار می‌کند.
>
> در macOS، میانبرهای <kbd>Ctrl</kbd> + <kbd>Up</kbd> و <kbd>Ctrl</kbd> + <kbd>Down</kbd> با میانبرهای پیش‌فرض سیستم‌عامل برای _Mission Control_ و _Application windows_ تداخل دارند؛ بنابراین باید این میانبرها را غیرفعال کنید تا کار کند.

کاربران صفحه‌کلید می‌توانند چند آیتم همجوار را به این روش انتخاب کنند:

- تمرکز روی عنصر `<select>` (مثلاً با استفاده از <kbd>Tab</kbd>).
- انتخاب یک آیتم در بالای یا پایین محدوده‌ای که می‌خواهند انتخاب کنند، با استفاده از کلیدهای مکان‌نمای <kbd>Up</kbd> و <kbd>Down</kbd> برای رفتن به بالا و پایین گزینه‌ها.
- نگه‌داشتن کلید <kbd>Shift</kbd> و سپس استفاده از کلیدهای مکان‌نمای <kbd>Up</kbd> و <kbd>Down</kbd> برای افزایش یا کاهش محدوده‌ی آیتم‌های انتخاب‌شده.

کاربران صفحه‌کلید می‌توانند چند آیتم غیرهمجوار را به این روش انتخاب کنند:

- تمرکز روی عنصر `<select>` (مثلاً با استفاده از <kbd>Tab</kbd>).
- نگه‌داشتن کلید <kbd>Ctrl</kbd> و سپس استفاده از کلیدهای مکان‌نمای <kbd>Up</kbd> و <kbd>Down</kbd> برای تغییر گزینه‌ی «focused» در سلکت، یعنی همان‌که اگر بخواهید انتخاب می‌شود. گزینه‌ی «focused» با یک خط‌چین دور آن هایلایت می‌شود، دقیقاً مثل یک لینک فوکوس‌شده با صفحه‌کلید.
- فشار دادن <kbd>Space</kbd> برای انتخاب یا لغو انتخاب گزینه‌های «focused».

## استایل‌دهی با CSS

عنصر `<select>` از نظر تاریخی با CSS به‌سختی قابل استایل‌دهی مؤثر بوده است. راهنماهای زیر شامل اطلاعاتی درباره‌ی قابلیت‌هایی هستند که استایل‌دهی کاملاً سفارشی‌پذیر برای عناصر select فراهم می‌کنند:

- [Customizable select elements](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select)
- [Customizable select listboxes](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select_listboxes)

### استایل‌دهی قدیمی (legacy) select

در مرورگرهایی که از قابلیت‌های مدرن سفارشی‌سازی پشتیبانی نمی‌کنند (یا در پایگاه‌های کد legacy که نمی‌توان از آن‌ها استفاده کرد)، شما به دستکاری [box model](/en-US/docs/Learn_web_development/Core/Styling_basics/Box_model)، [فونت نمایشی](/en-US/docs/Web/CSS/Guides/Fonts) و موارد مشابه محدود هستید. همچنین می‌توانید از ویژگی `appearance` برای حذف `appearance` پیش‌فرض سیستم استفاده کنید.

با این حال، دستیابی به نتیجه‌ای یکسان در مرورگرهای مختلف با عناصر سنتی `<select>` دشوار است. اگر می‌خواهید کنترل کامل داشته باشید، بهتر است از کتابخانه‌ای استفاده کنید که امکانات خوبی برای استایل‌دهی ویجت‌های فرم فراهم می‌کند، یا سعی کنید منوی کشویی خودتان را با عناصر غیرمعنایی، JavaScript و [WAI-ARIA](/en-US/docs/Learn_web_development/Core/Accessibility/WAI-ARIA_basics) برای ارائه‌ی معناسازی بسازید.

می‌توانید از شبه‌کلاس `:open` برای استایل‌دهی به عناصر `<select>` در حالت باز استفاده کنید، یعنی وقتی لیست گزینه‌های کشویی نمایش داده می‌شود. این مورد برای عناصر `<select>` چندخطی (آن‌هایی که ویژگی [`multiple`](/en-US/docs/Web/HTML/Reference/Attributes/multiple) تنظیم شده) صدق نمی‌کند — آن‌ها معمولاً به‌صورت یک جعبه‌ی لیست اسکرول‌شونده رندر می‌شوند تا منوی کشویی، بنابراین حالت باز ندارند.

برای اطلاعات بیشتر درباره‌ی استایل‌دهی قدیمی `<select>`، نگاه کنید به:

- [Styling HTML forms](/en-US/docs/Learn_web_development/Extensions/Forms/Styling_web_forms)
- [Advanced styling for HTML forms](/en-US/docs/Learn_web_development/Extensions/Forms/Advanced_form_styling)
- property `field-sizing` نحوهٔ اندازه‌گیری عناصر `<select>` را نسبت به گزینه‌های داخلشان کنترل می‌کند.

## دسترس‌پذیری

`<hr>` داخل یک `<select>` باید صرفاً تزئینی در نظر گرفته شود، زیرا این عناصر در حال حاضر در درخت دسترس‌پذیری (accessibility tree) نمایش داده نمی‌شوند و بنابراین در دسترس فناوری‌های کمکی (assistive technologies) قرار نمی‌گیرند.

## مثال‌ها

### select پایه

مثال زیر یک منوی کشویی با سه مقدار ایجاد می‌کند. گزینهٔ دوم شامل attribute با نام `selected` است و همین باعث می‌شود آن گزینه به‌طور پیش‌فرض انتخاب شده باشد.

```html
<select name="choice">
  <option value="first">First Value</option>
  <option value="second" selected>Second Value</option>
  <option value="third">Third Value</option>
</select>
```

#### نتیجه

### select با گروه‌بندی گزینه‌ها

مثال زیر یک منوی کشویی با گروه‌بندی ایجاد می‌کند که با استفاده از `<optgroup>` و `<hr>` درک محتوای منو را برای کاربر آسان‌تر می‌کند.

```html
<label for="hr-select">Your favorite food</label> <br />

<select name="foods" id="hr-select">
  <option value="">Choose a food</option>
  <hr />
  <optgroup label="Fruit">
    <option value="apple">Apples</option>
    <option value="banana">Bananas</option>
    <option value="cherry">Cherries</option>
    <option value="damson">Damsons</option>
  </optgroup>
  <hr />
  <optgroup label="Vegetables">
    <option value="artichoke">Artichokes</option>
    <option value="broccoli">Broccoli</option>
    <option value="cabbage">Cabbages</option>
  </optgroup>
  <hr />
  <optgroup label="Meat">
    <option value="beef">Beef</option>
    <option value="chicken">Chicken</option>
    <option value="pork">Pork</option>
  </optgroup>
  <hr />
  <optgroup label="Fish">
    <option value="cod">Cod</option>
    <option value="haddock">Haddock</option>
    <option value="salmon">Salmon</option>
    <option value="turbot">Turbot</option>
  </optgroup>
</select>
```

#### نتیجه

### select پیشرفته با چند ویژگی

مثال زیر پیچیده‌تر است و ویژگی‌های بیشتری را که می‌توانید روی عنصر `<select>` استفاده کنید نشان می‌دهد:

- attribute با نام `multiple` امکان انتخاب بیش از یک گزینه را فراهم می‌کند.
- attribute با نام `size` برابر `4` قرار داده شده است؛ یعنی ۴ خط در هر بار نمایش داده می‌شود. کاربران می‌توانند برای دیدن همهٔ گزینه‌ها اسکرول کنند.
- دو عنصر `<optgroup>` اضافه شده است که دو گروه‌بندی بصری ایجاد می‌کنند؛ معمولاً نام گروه به‌صورت پررنگ و گزینه‌های تو در تو با تورفتگی نمایش داده می‌شوند.
- attribute با نام `disabled` روی گزینهٔ «Hamster» قرار داده شده است و آن گزینه را غیرقابل‌انتخاب می‌کند.

```html
<label>
  Please choose one or more pets:
  <select name="pets" multiple size="4">
    <optgroup label="4-legged pets">
      <option value="dog">Dog</option>
      <option value="cat">Cat</option>
      <option value="hamster" disabled>Hamster</option>
    </optgroup>
    <optgroup label="Flying pets">
      <option value="parrot">Parrot</option>
      <option value="macaw">Macaw</option>
      <option value="albatross">Albatross</option>
    </optgroup>
  </select>
</label>
```

#### نتیجه

## خلاصه فنی

| ویژگی | مقدار |
|-------|-------|
| دسته‌بندی محتوا | [محتوای جریانی](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [محتوای عبارتی](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، [محتوای تعاملی](/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content)، [فهرست‌شده](/en-US/docs/Web/HTML/Guides/Content_categories#listed)، [قابل برچسب‌گذاری](/en-US/docs/Web/HTML/Guides/Content_categories#labelable)، [قابل بازنشانی](/en-US/docs/Web/HTML/Guides/Content_categories#resettable)، [قابل ارسال](/en-US/docs/Web/HTML/Guides/Content_categories#submittable) و یک [عنصر مرتبط با فرم](/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content) |
| محتوای مجاز | <ul><li>عناصر <code>&lt;option&gt;</code>، <code>&lt;optgroup&gt;</code> یا <code>&lt;hr&gt;</code>، و در صورت جعبه کشویی (drop down box)، اختیاری با یک عنصر <code>&lt;button&gt;</code> که حاوی یک عنصر <code>&lt;selectedcontent&gt;</code> تودرتو باشد.</li><li>عناصر <code>&lt;div&gt;</code>، <code>&lt;script&gt;</code>، <code>&lt;template&gt;</code> و <code>&lt;noscript&gt;</code>.</li></ul> |
| حذف تگ | هیچکدام؛ هر دو تگ شروع و پایان اجباری هستند. |
| والدین مجاز | هر عنصری که [محتوای عبارتی](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را می‌پذیرد. |
| نقش ARIA ضمنی | <code>combobox</code> اگر ویژگی <code>multiple</code> **نداشته باشد** و ویژگی <code>size</code> بزرگتر از 1 **نداشته باشد**، در غیر این صورت <code>listbox</code>. |
| نقش‌های ARIA مجاز | <code>menu</code> اگر ویژگی <code>multiple</code> **نداشته باشد** و ویژگی <code>size</code> بزرگتر از 1 **نداشته باشد**، در غیر این صورت <code>combobox</code> مجاز است اما توصیه نمی‌شود. |
| رابط DOM | <code>HTMLSelectElement</code> |

## Specifications

## Browser compatibility

## همچنین ببینید

- عنصر `<option>`
- عنصر `<optgroup>`
- [عناصر select قابل سفارشی‌سازی](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select)
- رویدادهای `change` و `input` که توسط `<select>` شلیک می‌شوند.