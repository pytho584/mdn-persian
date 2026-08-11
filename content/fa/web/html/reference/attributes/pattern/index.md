---
title: "pattern HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/pattern"
translated_by: "n8n + AI"
---

**ویژگی `pattern`** یک عبارت باقاعده (regular expression) را مشخص می‌کند که مقدار کنترل فرم باید با آن مطابقت داشته باشد. اگر مقدار غیر `null` با محدودیت‌های تعیین‌شده توسط `pattern` همخوانی نداشته باشد، خاصیت فقط‌خواندنی `patternMismatch` از شیء {{domxref('ValidityState')}} برابر `true` خواهد شد.

## مرور کلی

ویژگی `pattern` برای انواع ورودی {{HTMLElement("input/text", "text")}}، {{HTMLElement("input/tel", "tel")}}، {{HTMLElement("input/email", "email")}}، {{HTMLElement("input/url", "url")}}، {{HTMLElement("input/password", "password")}} و {{HTMLElement("input/search", "search")}} قابل استفاده است.

وقتی `pattern` مشخص شود، یک عبارت باقاعده است که [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) ورودی باید با آن مطابقت کامل داشته باشد تا مقدار بتواند از [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) عبور کند. این عبارت باید یک عبارت باقاعدهٔ معتبر جاوااسکریپت باشد، مطابق با نوع {{jsxref("RegExp")}} و مطابق مستندات [راهنمای عبارات باقاعده](/en-US/docs/Web/JavaScript/Guide/Regular_expressions).

عبارت باقاعدهٔ `pattern` با پرچم [`'v'`](/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_class#v-mode_character_class) کامپایل می‌شود. این کار باعث می‌شود عبارت باقاعده [unicode-aware](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/unicode#unicode-aware_mode) شود و نحوهٔ تفسیر کلاس‌های کاراکتری را تغییر دهد. این امکان عملیات اشتراک و تفاضل کلاس‌های کاراکتری را فراهم می‌کند و علاوه بر `]` و `\`، کاراکترهای زیر نیز در صورت نمایش به عنوان کاراکتر واقعی باید با بک‌اسلش `\` escape شوند: `(`, `)`, `[`, `{`, `}`, `/`, `-`, `|`. قبل از اواسط ۲۰۲۳ از پرچم `'u'` استفاده می‌شد؛ اگر کد قدیمی را به‌روزرسانی می‌کنید، به مرجع [`unicodeSets`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/unicodeSets) مراجعه کنید.

عبارت باقاعدهٔ `pattern` باید با کل `value` ورودی مطابقت داشته باشد، نه یک زیررشته - انگار که `^(?:` در ابتدای الگو و `)$` در انتهای آن قرار دارد.

هیچ اسلش جلویی (forward slash) نباید دور متن الگو قرار گیرد. اگر مقدار ویژگی وجود نداشته باشد، رشتهٔ خالی باشد یا نامعتبر باشد، هیچ عبارت باقاعده‌ای اعمال نمی‌شود.

برخی از انواع ورودی که از ویژگی `pattern` پشتیبانی می‌کنند، به ویژه {{HTMLElement("input/email", "email")}} و {{HTMLElement("input/url", "url")}}، دارای نحو (syntax) مقدار مورد انتظاری هستند که باید با آن مطابقت داشته باشد. اگر ویژگی `pattern` وجود نداشته باشد و مقدار با نحو مورد انتظار برای آن نوع مقدار همخوانی نداشته باشد، خاصیت فقط‌خواندنی `typeMismatch` از شیء {{domxref('ValidityState')}} برابر `true` خواهد شد.

### اعتبارسنجی محدودیت‌ها

اگر مقدار ورودی رشتهٔ خالی نباشد و با کل عبارت باقاعده مطابقت نداشته باشد، یک نقض محدودیت رخ می‌دهد که با `true` بودن خاصیت `patternMismatch` از شیء {{domxref('ValidityState')}} گزارش می‌شود.

> **نکته:** اگر ویژگی `pattern` بدون مقدار مشخص شود، مقدار آن به طور ضمنی رشتهٔ خالی است. بنابراین، هر مقدار **غیر خالی** برای ورودی منجر به نقض محدودیت خواهد شد.

### ملاحظات کاربردپذیری و دسترس‌پذیری

وقتی از `pattern` استفاده می‌کنید، توضیحی از الگو را در متن قابل مشاهده در نزدیکی کنترل قرار دهید. همچنین یک attribute به نام [`title`](/en-US/docs/Web/HTML/Reference/Elements/input#title) اضافه کنید که توصیف الگو را ارائه دهد. user agent ممکن است از محتوای `title` در زمان اعتبارسنجی محدودیت‌ها استفاده کند تا به کاربر بگوید الگو مطابقت ندارد. برخی مرورگرها tooltip حاوی محتوای `title` نمایش می‌دهند که کاربردپذیری را برای کاربران بینا بهبود می‌بخشد. علاوه بر این، فناوری کمکی ممکن است هنگام دریافت فوکوس توسط کنترل، `title` را با صدای بلند بخواند، اما نباید برای دسترس‌پذیری به آن تکیه کرد.

تکیه صرف بر attribute به نام `title` برای نمایش بصری محتوای متنی توصیه نمی‌شود، زیرا بسیاری از user agent ها این attribute را به شکلی قابل دسترس در معرض دید قرار نمی‌دهند. اگرچه برخی مرورگرها وقتی روی عنصری که `title` دارد هاور می‌کنند tooltip نشان می‌دهند، این کار کاربرانی را که فقط با صفحه‌کلید یا لمس کار می‌کنند از دست می‌دهد. این یکی از چندین دلیل است که باید اطلاعاتی در اختیار کاربران بگذارید تا نحوه پر کردن کنترل برای مطابقت با الزامات را بدانند.

اگرچه از `title` ها در برخی مرورگرها برای پر کردن پیام خطا استفاده می‌شود، اما چون مرورگرها گاهی `title` را به صورت متن در حالت هاور نمایش می‌دهند، بنابراین در موقعیت‌های غیر خطا هم ظاهر می‌شود؛ پس مراقب باشید عنوان‌ها را طوری نوشته نکنید که انگار خطایی رخ داده است.

## مثال‌ها

### مطابقت با شماره تلفن

با توجه به کد زیر:

```html
<p>
  <label>
    Enter your phone number in the format (123) - 456 - 7890 (<input
      name="tel1"
      type="tel"
      pattern="[0-9]{3}"
      placeholder="###"
      aria-label="3-digit area code"
      size="2" />) -
    <input
      name="tel2"
      type="tel"
      pattern="[0-9]{3}"
      placeholder="###"
      aria-label="3-digit prefix"
      size="2" />
    -
    <input
      name="tel3"
      type="tel"
      pattern="[0-9]{4}"
      placeholder="####"
      aria-label="4-digit number"
      size="3" />
  </label>
</p>
```

در اینجا سه بخش برای یک شماره تلفن آمریکای شمالی داریم. یک label ضمنی هر سه بخش شماره تلفن را در بر می‌گیرد و طبق attribute های `pattern` که روی هر بخش تنظیم شده، به ترتیب انتظار ۳ رقم، ۳ رقم و ۴ رقم را دارد.

اگر مقدارها خیلی بلند یا خیلی کوتاه باشند، یا شامل کاراکترهایی غیر از رقم باشند، مقدار `patternMismatch` برابر `true` خواهد بود. وقتی این مقدار `true` باشد، عنصر با شبه‌کلاس CSS `:invalid` مطابقت می‌کند.

```css
input:invalid {
  border: red solid 3px;
}
```

اگر به جای آن از attribute های [`minlength`](/en-US/docs/Web/HTML/Reference/Attributes/minlength) و [`maxlength`](/en-US/docs/Web/HTML/Reference/Attributes/maxlength) استفاده می‌کردیم، ممکن بود `validityState.tooLong` یا `validityState.tooShort` برابر `true` شوند.

### تعیین یک الگو

می‌توانید از attribute [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) برای指定 یک عبارت باقاعده (regular expression) استفاده کنید که مقدار واردشده باید با آن مطابقت داشته باشد تا معتبر در نظر گرفته شود (برای آشنایی سریع با استفاده از عبارت‌های باقاعده در اعتبارسنجی ورودی‌ها، [Validating against a regular expression](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation#validating_against_a_regular_expression) را ببینید).

مثال زیر مقدار را به ۴ تا ۸ نویسه محدود می‌کند و الزام می‌کند که فقط شامل حروف کوچک باشد.

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
      pattern="[a-z]{4,8}"
      title="4 to 8 lowercase letters" />
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
```

```css
input:valid + span::after {
  position: absolute;
  content: "✓";
  padding-left: 5px;
}
```

خروجی به این صورت است:

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- [Constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- [Forms: Data form validation](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [Regular Expressions](/en-US/docs/Web/JavaScript/Guide/Regular_expressions)