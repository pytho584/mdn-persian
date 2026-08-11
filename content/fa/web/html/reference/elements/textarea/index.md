---
title: "<textarea> HTML textarea element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/textarea"
translated_by: "n8n + AI"
---

عنصر **`<textarea>`** یک کنترل ویرایش متن ساده (plain-text) چندخطی در HTML است. این عنصر وقتی به کار می‌آید که می‌خواهید کاربر بتواند مقدار قابل توجهی متن آزاد وارد کند؛ مثلاً نظر در یک فرم بازخورد یا دیدگاه.

```html
<label for="story">داستانت را برایمان تعریف کن:</label>

<textarea id="story" name="story" rows="5" cols="33">
شب تاریک و طوفانی بود...
</textarea>
```

```css
label,
textarea {
  font-size: 0.8rem;
  letter-spacing: 1px;
}

textarea {
  padding: 10px;
  max-width: 100%;
  line-height: 1.5;
  border-radius: 5px;
  border: 1px solid #cccccc;
  box-shadow: 1px 1px 1px #999999;
}

label {
  display: block;
  margin-bottom: 10px;
}
```

مثال بالا چند ویژگی `<textarea>` را نشان می‌دهد:

- یک `id` که به `<textarea>` اجازه می‌دهد با یک عنصر {{htmlelement("label")}} مرتبط شود (برای دسترسی‌پذیری).
- یک `name` که نام داده‌ای را مشخص می‌کند که هنگام ارسال فرم به سرور ارسال می‌شود.
- ویژگی‌های `rows` و `cols` برای تعیین اندازه دقیق `<textarea>`. تنظیم این دو برای یکپارچگی ظاهر خوب است، چون پیش‌فرض مرورگرها متفاوت است.
- عنصر `<textarea>` محتوای خود را در HTML و JavaScript به صورت متفاوت مشخص می‌کند:
  - در HTML، محتوای اولیه `<textarea>` بین تگ باز و بسته قرار می‌گیرد، نه به عنوان یک attribute به نام `value`.
  - در JavaScript، عنصر `<textarea>` یک property به نام [`value`](/en-US/docs/Web/API/HTMLTextAreaElement/value) دارد که برای خواندن یا تنظیم محتوای فعلی به کار می‌رود، و [`defaultValue`](/en-US/docs/Web/API/HTMLTextAreaElement/defaultValue) برای دریافت و تنظیم مقدار اولیه (معادل دسترسی به محتوای متنی عنصر HTML).

`<textarea>` همچنین چندین attribute مشترک با `<input>`های فرم را می‌پذیرد، مانند `autocapitalize`، `autocomplete`، `autofocus`، `disabled`، `placeholder`، `readonly` و `required`.

## ویژگی‌ها (Attributes)

این عنصر از [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) نیز پشتیبانی می‌کند.

- [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize)
  - : کنترل می‌کند که آیا متن ورودی به صورت خودکار با حرف بزرگ شروع شود یا نه، و اگر بله، به چه صورت.

- [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
  - : کنترل می‌کند که آیا مرورگر می‌تواند متن وارد شده را به صورت خودکار کامل کند. مقادیر ممکن عبارتند از:
    - `off`: کاربر باید هر بار به صورت دستی مقدار را وارد کند، یا خود سند روش تکمیل خودکار دیگری ارائه می‌دهد. مرورگر به صورت خودکار ورودی را تکمیل نمی‌کند.
    - `on`: مرورگر می‌تواند مقدار را بر اساس مقادیری که کاربر در دفعات قبل وارد کرده است، به صورت خودکار کامل کند.
    - [`<token-list>`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete#token_list_tokens): مجموعه‌ای مرتب از توکن‌های جزئیات تکمیل خودکار که با فاصله از هم جدا شده‌اند. می‌تواند به صورت اختیاری با یک توکن بخش‌بندی، یک توکن گروه‌بندی صورتحساب یا حمل‌ونقل، و/یا یک توکن که نوع گیرنده را مشخص می‌کند، همراه شود.

    عناصر `<textarea>` که attribute `autocomplete` را مشخص نمی‌کنند، وضعیت `on` یا `off` را از مالک فرم خود (form owner) به ارث می‌برند. مالک فرم یا عنصر {{HTMLElement("form")}}ای است که این `<textarea>` درون آن قرار دارد، یا عنصر فرمی که `id` آن در attribute `form` عنصر `<textarea>` ذکر شده است. برای اطلاعات بیشتر، به attribute [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/form#autocomplete) در {{HTMLElement("form")}} مراجعه کنید.

- [`autocorrect`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocorrect)
  - : کنترل می‌کند که آیا تصحیح خودکار املا و پردازش متن هنگام ویرایش این `textarea` فعال باشد یا نه. مقادیر مجاز عبارتند از:
    - `on`
      - : فعال‌سازی تصحیح خودکار املا و جایگزینی متن.
    - `off`
      - : غیرفعال‌سازی تصحیح خودکار املا و جایگزینی متن.

- [`autofocus`](/en-US/docs/Web/HTML/Reference/Global_attributes/autofocus)
  - : این ویژگی Boolean به شما اجازه می‌دهد مشخص کنید که یک کنترل فرم هنگام بارگذاری صفحه، فوکوس ورودی داشته باشد. فقط یک عنصر مرتبط با فرم در یک سند می‌تواند این ویژگی را داشته باشد.

- `cols`
  - : عرض قابل مشاهدهٔ کنترل متن، بر حسب عرض میانگین کاراکترها. اگر مشخص شود، باید یک عدد صحیح مثبت باشد. اگر مشخص نشود، مقدار پیش‌فرض `20` است.

- [`dirname`](/en-US/docs/Web/HTML/Reference/Attributes/dirname)
  - : این ویژگی برای نشان دادن جهت متن محتویات عنصر استفاده می‌شود. برای اطلاعات بیشتر، به [ویژگی `dirname`](/en-US/docs/Web/HTML/Reference/Attributes/dirname) مراجعه کنید.

- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
  - : این ویژگی Boolean نشان می‌دهد که کاربر نمی‌تواند با کنترل تعامل کند. اگر این ویژگی مشخص نشود، کنترل تنظیمات خود را از عنصر والد به ارث می‌برد، به عنوان مثال `<fieldset>`؛ اگر هنگام تنظیم ویژگی `disabled` عنصر پدری وجود نداشته باشد، کنترل فعال است.

- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)
  - : عنصر فرمی که عنصر `<textarea>` با آن مرتبط است (به اصطلاح «مالک فرم» - form owner). مقدار ویژگی باید `id` یک عنصر فرم در همان سند باشد. اگر این ویژگی مشخص نشود، عنصر `<textarea>` باید از نوادگان یک عنصر فرم باشد. این ویژگی به شما امکان می‌دهد عناصر `<textarea>` را در هر جای سند قرار دهید، نه فقط به عنوان نوادگان عناصر فرم.

- [`maxlength`](/en-US/docs/Web/HTML/Reference/Attributes/maxlength)
  - : حداکثر طول رشته (اندازه‌گیری شده بر اساس واحدهای کد UTF-16) که کاربر می‌تواند وارد کند. اگر این مقدار مشخص نشود، کاربر می‌تواند تعداد نامحدودی کاراکتر وارد کند.

- [`minlength`](/en-US/docs/Web/HTML/Reference/Attributes/minlength)
  - : حداقل طول رشته (اندازه‌گیری شده بر اساس واحدهای کد UTF-16) که کاربر باید وارد کند.

- `name`
  - : نام کنترل.

- [`placeholder`](/en-US/docs/Web/HTML/Reference/Attributes/placeholder)
  - : راهنمایی برای کاربر دربارهٔ آنچه می‌توان در کنترل وارد کرد. بازگشت‌های کرج (Carriage returns) یا خط‌های جدید (line-feeds) در متن placeholder هنگام نمایش راهنما باید به عنوان شکست خط در نظر گرفته شوند.

    > [!NOTE]
    > Placeholderها فقط باید برای نشان دادن نمونه‌ای از نوع داده‌ای که باید در فرم وارد شود استفاده شوند؛ آن‌ها جایگزینی برای عنصر مناسب `<label>` متصل به ورودی نیستند. برای توضیح کامل به [برچسب‌های `<input>`](/en-US/docs/Web/HTML/Reference/Elements/input#labels) مراجعه کنید.

- [`readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly)
  - : این attribute از نوع Boolean است و مشخص می‌کند که کاربر نمی‌تواند مقدار کنترل را تغییر دهد. برخلاف attribute `disabled`، `readonly` از کلیک یا انتخاب در کنترل جلوگیری نمی‌کند. مقدار یک کنترل read-only همچنان همراه فرم ارسال می‌شود.
- [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required)
  - : این attribute مشخص می‌کند که کاربر باید قبل از ارسال فرم یک مقدار وارد کند.
- `rows`
  - : تعداد خطوط متنی قابل مشاهده برای کنترل. اگر مشخص شود، باید یک عدد صحیح مثبت باشد. اگر مشخص نشود، مقدار پیش‌فرض ۲ است.
- [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck)
  - : مشخص می‌کند که آیا `<textarea>` توسط مرورگر/سیستم‌عامل زیرین مورد بررسی املایی قرار می‌گیرد. مقدار می‌تواند:
    - `true`: نشان می‌دهد که عنصر نیاز به بررسی املا و دستور زبان دارد.
    - `default`: نشان می‌دهد که عنصر باید بر اساس رفتار پیش‌فرض عمل کند، که احتمالاً بر اساس مقدار `spellcheck` عنصر والد است.
    - `false`: نشان می‌دهد که عنصر نباید بررسی املایی شود.
- `wrap`
  - : نحوه شکستن (wrap) مقدار کنترل را برای ارسال فرم مشخص می‌کند. مقادیر ممکن:
    - `hard`: مرورگر به‌طور خودکار خطوط جدید (CR+LF) درج می‌کند تا هر خط از عرض کنترل بلندتر نباشد. برای این کار باید attribute [`cols`](#cols) مشخص شود.
    - `soft`: مرورگر تضمین می‌کند که تمام خطوط جدید در مقدار وارد شده به صورت جفت `CR+LF` باشند، اما خطوط جدید اضافی به مقدار اضافه نمی‌شود.
    - `off` (غیراستاندارد): مانند `soft` است، اما ظاهر را به `white-space: pre` تغییر می‌دهد، بنابراین بخش‌های خطی که از `cols` بیشتر هستند شکسته نمی‌شوند و `<textarea>` به صورت افقی اسکرول می‌شود.

    اگر این attribute مشخص نشود، مقدار پیش‌فرض `soft` است.

## استایل‌دهی با CSS

`<textarea>` یک عنصر جایگزین‌شده (replaced element) است — ابعاد ذاتی دارد، مانند یک تصویر شطرنجی. به‌طور پیش‌فرض، مقدار {{cssxref("display")}} آن `inline-block` است. در مقایسه با سایر عناصر فرم، استایل‌دهی آن نسبتاً آسان است، زیرا box model، فونت‌ها، طرح رنگ و غیره با CSS معمولی به راحتی قابل تغییر هستند.

[استایل‌دهی به فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms/Styling_web_forms) نکات مفیدی در مورد استایل‌دهی `<textarea>`ها ارائه می‌دهد.

### ناهماهنگی خط پایه (baseline)

مشخصات HTML تعریف نمی‌کند که خط پایه (baseline) یک `<textarea>` کجا قرار دارد، بنابراین مرورگرهای مختلف آن را در موقعیت‌های متفاوتی تنظیم می‌کنند. در Gecko، خط پایه `<textarea>` روی خط پایه اولین خط textarea قرار می‌گیرد، در مرورگر دیگری ممکن است روی پایین جعبه `<textarea>` تنظیم شود. از {{cssxref("vertical-align", "vertical-align: baseline")}} روی آن استفاده نکنید؛ رفتار غیرقابل پیش‌بینی است.

### کنترل تغییر اندازه textarea

در بیشتر مرورگرها، `<textarea>`ها قابل تغییر اندازه هستند — یک دستگیره کشیدن (drag handle) در گوشه سمت راست پایین مشاهده می‌کنید که می‌توان از آن برای تغییر اندازه عنصر در صفحه استفاده کرد. این رفتار توسط ویژگی CSS {{ cssxref("resize") }} کنترل می‌شود — تغییر اندازه به‌طور پیش‌فرض فعال است، اما می‌توانید با استفاده از مقدار `none` برای `resize` آن را به‌طور صریح غیرفعال کنید:

```css
textarea {
  resize: none;
}
```

### استایل‌دهی به مقادیر معتبر و نامعتبر

مقادیر معتبر و نامعتبر یک عنصر `<textarea>` (برای مثال، مقادیر داخل و خارج از محدوده تعیین‌شده توسط `minlength`، `maxlength` یا `required`) می‌توانند با استفاده از شبه‌کلاس‌های {{cssxref(":valid")}} و {{cssxref(":invalid")}} برجسته شوند. به عنوان مثال، برای دادن حاشیه متفاوت به textarea بر اساس معتبر یا نامعتبر بودن آن:

```css
textarea:invalid {
  border: 2px dashed red;
}

textarea:valid {
  border: 2px solid lime;
}
```

## مثال‌ها

### مثال پایه

مثال زیر یک textarea با تعداد مشخصی ردیف و ستون، مقداری محتوای پیش‌فرض و استایل‌های CSS نشان می‌دهد که از تغییر اندازه عنصر به بیش از ۵۰۰px عرض و ۱۳۰px ارتفاع جلوگیری می‌کند:

```markdown
```html
<textarea name="textarea" rows="5" cols="15">Write something here</textarea>
```

```css
textarea {
  max-height: 130px;
  max-width: 500px;
}
```

#### نتیجه

### مثال با استفاده از `minlength` و `maxlength`

در این مثال تعداد کاراکترها حداقل ۱۰ و حداکثر ۲۰ است. امتحان کنید.

```html
<textarea name="textarea" rows="5" cols="30" minlength="10" maxlength="20">
Write something here…
</textarea>
```

```css
textarea {
  max-height: 130px;
  max-width: 500px;
}
```

#### نتیجه

توجه کنید که `minlength` مانع حذف کاراکتر توسط کاربر نمیشود، حتی اگر این حذف باعث شود تعداد کاراکتر از حداقل کمتر شود؛ اما در این صورت مقدار واردشده در `<textarea>` نامعتبر خواهد بود. همچنین توجه کنید که حتی اگر مقدار `minlength` تنظیم شده باشد (مثلاً ۳)، یک `<textarea>` خالی همچنان معتبر در نظر گرفته میشود، مگر اینکه ویژگی `required` نیز تنظیم شده باشد.

### مثال با استفاده از `placeholder`

در این مثال یک placeholder تنظیم شده است. توجه کنید که با شروع تایپ در کادر، placeholder ناپدید میشود.

```html
<textarea
  name="textarea"
  rows="5"
  cols="30"
  placeholder="Comment text."></textarea>
```

```css
textarea {
  max-height: 130px;
  max-width: 500px;
}
```

#### نتیجه

> [!NOTE]
> Placeholderها باید فقط برای نمایش نمونهای از نوع دادهای استفاده شوند که قرار است در فرم وارد شود؛ آنها _جایگزین_ یک عنصر `<label>` مناسب که به ورودی متصل شده نیستند. برای توضیح کامل به [`<input>` labels](/en-US/docs/Web/HTML/Reference/Elements/input#labels) مراجعه کنید.

### ناحیه‌های متنی غیرفعال و readonly

این مثال دو `<textarea>` را نشان می‌دهد — یکی [`readonly`](/en-US/docs/Web/HTML/Reference/Attributes/readonly) و دیگری [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled). محتوای هیچ‌کدام قابل ویرایش نیست، اما عنصر `readonly` قابلفوکوس است و مقدار آن در فرم‌ها ارسال می‌شود. مقدار عنصر `disabled` ارسال نمی‌شود و قابلفوکوس نیست.

```html
<textarea name="textarea" rows="5" cols="30" readonly>
I am a read-only textarea.
</textarea>
<textarea name="textarea" rows="5" cols="30" disabled>
I am a disabled textarea.
</textarea>
```

```css
textarea {
  display: block;
  resize: horizontal;
  max-width: 500px;
}
```

#### نتیجه

## خلاصه فنی
```

| ویژگی | مقدار |
|---|---|
| [دسته‌بندی محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) (Content categories) | [محتوای جریانی](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) (flow content)، [محتوای عبارتی](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) (phrasing content)، [محتوای تعاملی](/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content) (interactive content)، و یک عنصر مرتبط با فرم (form-associated) که [listed](/en-US/docs/Web/HTML/Guides/Content_categories#listed)، [labelable](/en-US/docs/Web/HTML/Guides/Content_categories#labelable)، [resettable](/en-US/docs/Web/HTML/Guides/Content_categories#resettable) و [submittable](/en-US/docs/Web/HTML/Guides/Content_categories#submittable) است. |
| محتوای مجاز (Permitted content) | متن (Text) |
| حذف تگ (Tag omission) | هیچ؛ هم تگ شروع و هم تگ پایان الزامی هستند. |
| والدین مجاز (Permitted parents) | هر عنصری که [محتوای عبارتی](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) (phrasing content) را بپذیرد. |
| نقش ARIA ضمنی (Implicit ARIA role) | `[textbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)` |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | هیچ `role` ای مجاز نیست |
| رابط DOM (DOM interface) | `HTMLTextAreaElement` |

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

سایر عناصر مرتبط با فرم:

- `<form>`
- `<button>`
- `<datalist>`
- `<legend>`
- `<label>`
- `<select>`
- `<optgroup>`
- `<option>`
- `<input>`
- `<fieldset>`
- `<output>`
- `<progress>`
- `<meter>`