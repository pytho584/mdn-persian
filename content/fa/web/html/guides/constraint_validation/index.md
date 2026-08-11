---
title: "Using HTML form validation and the Constraint Validation API"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Constraint_validation"
translated_by: "n8n + AI"
---

```markdown
ایجاد فرم‌های وب همیشه کار پیچیده‌ای بوده است. هرچند نوشتن خود فرم ساده است، بررسی اینکه هر فیلد مقدار معتبر و سازگار دارد سخت‌تر است و اطلاع‌رسانی به کاربر درباره مشکل می‌تواند سردردآور باشد. HTML5 سازوکارهای جدیدی برای فرم‌ها معرفی کرد: انواع معنایی جدید برای عنصر `input` و اعتبارسنجی مبتنی بر قیود (_constraint validation_) برای آسان‌کردن بررسی محتوای فرم در سمت کلاینت. محدودیت‌های پایه و معمول را می‌توان بدون نیاز به جاوااسکریپت با تنظیم attributeهای جدید بررسی کرد؛ محدودیت‌های پیچیده‌تر را می‌توان با استفاده از Constraint Validation API آزمود.

برای آشنایی مقدماتی با این مفاهیم، همراه با مثال، به [آموزش اعتبارسنجی فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation) مراجعه کنید.

> **توجه:** اعتبارسنجی قیود HTML نیاز به اعتبارسنجی در سمت سرور را از بین نمی‌برد. حتی اگر درخواست‌های فرم نامعتبر بسیار کمتری انتظار می‌رود، هنوز هم می‌توان به روش‌های مختلف درخواست‌های نامعتبر ارسال کرد:
>
> - با تغییر HTML از طریق ابزار توسعه‌دهنده مرورگر.
> - با ساخت دستی یک درخواست HTTP بدون استفاده از فرم.
> - با نوشتن برنامه‌نویسی‌شده محتوا در فرم (برخی اعتبارسنجی‌های قیود _فقط_ برای ورودی کاربر اجرا می‌شوند، نه اگر مقدار فیلد فرم را با جاوااسکریپت تنظیم کنید).
>
> بنابراین، همیشه باید داده‌های فرم را در سمت سرور، مطابق با آنچه در سمت کلاینت انجام شده، اعتبارسنجی کنید.

## محدودیت‌های ذاتی و پایه

در HTML، محدودیت‌های پایه به دو روش تعریف می‌شوند:

- با انتخاب مناسب‌ترین مقدار از نظر معنایی برای attribute نوع (`type`) عنصر `input`؛ به عنوان مثال انتخاب نوع `email` به طور خودکار محدودیتی ایجاد می‌کند که بررسی می‌کند مقدار یک آدرس ایمیل معتبر است.
- با تنظیم مقادیر روی attributeهای مرتبط با اعتبارسنجی، به طوری که محدودیت‌های پایه بدون نیاز به جاوااسکریپت توصیف شوند.

### انواع معنایی input

محدودیت‌های ذاتی برای attribute نوع (`type`) عبارت‌اند از:

| نوع input | توضیح محدودیت | نقض مرتبط |
| --- | --- | --- |
| [`<input type="URL">`](/en-US/docs/Web/HTML/Reference/Elements/input/url) | مقدار باید یک [URL](/en-US/docs/Learn_web_development/Howto/Web_mechanics/What_is_a_URL) مطلق باشد، همانطور که در [URL Living Standard](https://url.spec.whatwg.org/) تعریف شده است. | نقض محدودیت **[TypeMismatch](/en-US/docs/Web/API/ValidityState/typeMismatch)** |
| [`<input type="email">`](/en-US/docs/Web/HTML/Reference/Elements/input/email) | مقدار باید یک آدرس ایمیل از نظر نحوی معتبر باشد، که عموماً قالب `username@hostname.tld` دارد اما می‌تواند محلی نیز باشد مانند `username@hostname`. | نقض محدودیت **[TypeMismatch](/en-US/docs/Web/API/ValidityState/typeMismatch)** |
```

برای `input` از نوع `email`، اگر attribute [`multiple`](/en-US/docs/Web/HTML/Reference/Elements/input#multiple) تنظیم شود، می‌توان چندین مقدار را به صورت فهرست جدا شده با کاما مشخص کرد. اگر هر یک از مقادیر موجود در فهرست با شرط ذکر شده در اینجا مطابقت نداشته باشد، نقض محدودیت **Type mismatch** (عدم تطابق نوع) رخ می‌دهد.

توجه داشته باشید که بیشتر انواع `input` محدودیت ذاتی ندارند؛ زیرا برخی از اعتبارسنجی محدودیت (constraint validation) مستثنی هستند یا دارای یک الگوریتم sanitization هستند که مقادیر نادرست را به یک مقدار پیش‌فرض صحیح تبدیل می‌کند.

### ویژگی‌های مرتبط با اعتبارسنجی

علاوه بر attribute `type` که در بالا توضیح داده شد، ویژگی‌های زیر برای توصیف محدودیت‌های پایه استفاده می‌شوند:

<table class="standard-table">
  <thead>
    <tr>
      <th scope="col">Attribute</th>
      <th scope="col">انواع input های پشتیبانی‌کننده از این attribute</th>
      <th scope="col">مقادیر ممکن</th>
      <th scope="col">توضیح محدودیت</th>
      <th scope="col">نقض مرتبط</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <code><a href="/en-US/docs/Web/HTML/Reference/Attributes/pattern">pattern</a></code>
      </td>
      <td>
        <code>text</code>، <code>search</code>، <code>url</code>،
        <code>tel</code>، <code>email</code>، <code>password</code>
      </td>
      <td>
        یک <a href="/en-US/docs/Web/JavaScript/Guide/Regular_expressions">عبارت باقاعده جاوااسکریپت</a>
        (با فلگ‌های <code>global</code>، <code>ignoreCase</code> و
        <code>multiline</code> غیرفعال)
      </td>
      <td>مقدار باید با الگو (pattern) مطابقت داشته باشد.</td>
      <td>
        نقض محدودیت
        <a href="/en-US/docs/Web/API/ValidityState/patternMismatch"><strong><code>patternMismatch</code></strong></a>
      </td>
    </tr>
    <tr>
      <td rowspan="3">
        <code><a href="/en-US/docs/Web/HTML/Reference/Attributes/min">min</a></code>
      </td>
      <td><code>range</code>، <code>number</code></td>
      <td>یک عدد معتبر</td>
      <td rowspan="3">مقدار باید بزرگ‌تر یا مساوی min باشد.</td>
      <td rowspan="3">
        نقض محدودیت
        <strong><code><a href="/en-US/docs/Web/API/ValidityState/rangeUnderflow">rangeUnderflow</a></code></strong>
      </td>
    </tr>
    <tr>
      <td><code>date</code>، <code>month</code>، <code>week</code></td>
      <td>یک تاریخ معتبر</td>
    </tr>
    <tr>
      <td><code>datetime-local</code>، <code>time</code></td>
      <td>یک تاریخ و زمان معتبر</td>
    </tr>
    <tr>
      <td rowspan="3">
        <code><a href="/en-US/docs/Web/HTML/Reference/Attributes/max">max</a></code>
      </td>
      <td><code>range</code>، <code>number</code></td>
      <td>یک عدد معتبر</td>
      <td rowspan="3">مقدار باید کوچک‌تر یا مساوی max باشد.</td>
      <td rowspan="3">
        نقض محدودیت
        <strong><code><a href="/en-US/docs/Web/API/ValidityState/rangeOverflow">rangeOverflow</a></code></strong>
      </td>
    </tr>
    <tr>
      <td><code>date</code>، <code>month</code>، <code>week</code></td>
      <td>یک تاریخ معتبر</td>
    </tr>
    <tr>
      <td><code>datetime-local</code>، <code>time</code></td>
      <td>یک تاریخ و زمان معتبر</td>
    </tr>
    <tr>
      <td>
        <code><a href="/en-US/docs/Web/HTML/Reference/Attributes/required">required</a></code>
      </td>
      <td>
        <code>text</code>، <code>search</code>، <code>url</code>،
        <code>tel</code>، <code>email</code>، <code>password</code>،
        <code>date</code>، <code>datetime-local</code>،
        <code>month</code>، <code>week</code>، <code>time</code>،
        <code>number</code>، <code>checkbox</code>، <code>radio</code>،
        <code>file</code>؛ همچنین روی المان‌های <code>select</code> و
        <code>textarea</code>
      </td>
      <td>
        هیچ؛ چون یک attribute از نوع Boolean است: وجودش به معنای
        <em>true</em> و نبودش به معنای <em>false</em> است.
      </td>
      <td>در صورت تنظیم، باید مقداری وجود داشته باشد.</td>
      <td>
        نقض محدودیت
        <strong><code><a href="/en-US/docs/Web/API/ValidityState/valueMissing">valueMissing</a></code></strong>
      </td>
    </tr>
    <tr>
      <td rowspan="5">
        <code><a href="/en-US/docs/Web/HTML/Reference/Attributes/step">step</a></code>
      </td>
      <td><code>date</code></td>
      <td>یک عدد صحیح بر حسب روز</td>
      <td rowspan="5">
        مگر اینکه step روی مقدار <code>any</code> تنظیم شده باشد، مقدار باید
        <strong>min</strong> + مضربی صحیح از step باشد.
      </td>
      <td rowspan="5">
        نقض محدودیت
        <strong><code><a href="/en-US/docs/Web/API/ValidityState/stepMismatch">stepMismatch</a></code></strong>
      </td>
    </tr>
    <tr>
      <td><code>month</code></td>
      <td>یک عدد صحیح بر حسب ماه</td>
    </tr>
    <tr>
      <td><code>week</code></td>
      <td>یک عدد صحیح بر حسب هفته</td>
    </tr>
    <tr>
      <td><code>datetime-local</code>، <code>time</code></td>
      <td>یک عدد صحیح بر حسب ثانیه</td>
    </tr>
    <tr>
      <td><code>range</code>، <code>number</code></td>
      <td>یک عدد صحیح</td>
    </tr>
    <tr>
      <td>
        <code><a href="/en-US/docs/Web/HTML/Reference/Attributes/minlength">minlength</a></code>
      </td>
      <td>
        <code>text</code>، <code>search</code>، <code>url</code>،
        <code>tel</code>، <code>email</code>، <code>password</code>؛ همچنین روی
        المان <code>textarea</code>
      </td>
      <td>یک طول به صورت عدد صحیح</td>
      <td>
        تعداد کاراکترها (code point ها) در صورت غیرخالی بودن، نباید کمتر از مقدار این
        attribute باشد. در <code>textarea</code>، همه خطوط جدید به یک کاراکتر واحد
        نرمال‌سازی می‌شوند (نه به صورت جفت CRLF).
      </td>
      <td>
        نقض محدودیت
        <strong><code><a href="/en-US/docs/Web/API/ValidityState/tooShort">tooShort</a></code></strong>
      </td>
    </tr>
    <tr>
      <td>
        <code><a href="/en-US/docs/Web/HTML/Reference/Attributes/maxlength">maxlength</a></code>
      </td>
      <td>
        <code>text</code>، <code>search</code>، <code>url</code>،
        <code>tel</code>، <code>email</code>، <code>password</code>؛ همچنین روی
        المان <code>textarea</code>
      </td>
      <td>یک طول به صورت عدد صحیح</td>
      <td>
        تعداد کاراکترها (code point ها) نباید از مقدار این attribute بیشتر شود.
      </td>
      <td>
        نقض محدودیت
        <strong><code><a href="/en-US/docs/Web/API/ValidityState/tooLong">tooLong</a></code></strong>
      </td>
    </tr>
  </tbody>
</table>

## فرآیند اعتبارسنجی محدودیت‌ها (Constraint Validation)

اعتبارسنجی محدودیت‌ها از طریق Constraint Validation API انجام می‌شود؛ یا روی یک عنصر فرم به‌تنهایی، یا در سطح فرم روی خود عنصر `<form>`. این اعتبارسنجی به روش‌های زیر صورت می‌گیرد:

- با فراخوانی متد `checkValidity()` یا `reportValidity()` روی یک DOM interface مرتبط با فرم (مانند [`HTMLInputElement`](/en-US/docs/Web/API/HTMLInputElement)، [`HTMLSelectElement`](/en-US/docs/Web/API/HTMLSelectElement)، [`HTMLButtonElement`](/en-US/docs/Web/API/HTMLButtonElement)، [`HTMLOutputElement`](/en-US/docs/Web/API/HTMLOutputElement) یا [`HTMLTextAreaElement`](/en-US/docs/Web/API/HTMLTextAreaElement)). این کار فقط محدودیت‌های همان عنصر را بررسی می‌کند و به اسکریپت اجازه می‌دهد اطلاعات را دریافت کند. متد `checkValidity()` یک مقدار Boolean برمی‌گرداند که نشان می‌دهد آیا مقدار عنصر از محدودیت‌هایش عبور می‌کند یا نه. (این کار معمولاً توسط user-agent انجام می‌شود تا مشخص کند کدام یک از شبه‌کلاس‌های CSS یعنی {{ Cssxref(":valid") }} یا {{ Cssxref(":invalid") }} اعمال شود.) در مقابل، متد `reportValidity()` هرگونه خطای اعتبارسنجی را به کاربر گزارش می‌دهد.
- با فراخوانی متد `checkValidity()` یا `reportValidity()` روی interface [`HTMLFormElement`](/en-US/docs/Web/API/HTMLFormElement).
- با ارسال خود فرم (submitting).

فراخوانی `checkValidity()` را اعتبارسنجی _ایستای_ محدودیت‌ها می‌گویند، در حالی که فراخوانی `reportValidity()` یا ارسال فرم، اعتبارسنجی _تعاملی_ محدودیت‌ها محسوب می‌شود.

> **توجه:**
>
> - اگر ویژگی [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) روی عنصر `<form>` تنظیم شده باشد، اعتبارسنجی تعاملی محدودیت‌ها انجام نمی‌شود.
> - فراخوانی متد `submit()` روی interface [`HTMLFormElement`](/en-US/docs/Web/API/HTMLFormElement) باعث فعال شدن اعتبارسنجی محدودیت‌ها نمی‌شود. به عبارت دیگر، این متد داده‌های فرم را حتی اگر محدودیت‌ها را رعایت نکنند به سرور ارسال می‌کند. به جای آن از متد `click()` روی یک دکمه submit استفاده کنید.
> - محدودیت‌های `minlength` و `maxlength` فقط روی ورودی کاربر بررسی می‌شوند. اگر مقدار به صورت برنامه‌نویسی (programmatically) تنظیم شود، حتی با فراخوانی `checkValidity()` یا `reportValidity()` این محدودیت‌ها بررسی نمی‌شوند.

## محدودیت‌های پیچیده با استفاده از Constraint Validation API

با استفاده از JavaScript و Constraint API می‌توان محدودیت‌های پیچیده‌تری را پیاده‌سازی کرد، مثلاً محدودیت‌هایی که چندین فیلد را ترکیب می‌کنند یا محاسبات پیچیده دارند.

ایده اصلی این است که روی یک رویداد از فیلد فرم (مثل **onchange**) کد JavaScript را فعال کنید تا بررسی کند آیا محدودیت نقض شده است یا نه، و سپس از متد `field.setCustomValidity()` برای تنظیم نتیجه اعتبارسنجی استفاده کنید: یک رشته خالی یعنی محدودیت رعایت شده است، و هر رشته دیگری یعنی خطایی وجود دارد و این رشته به عنوان پیام خطا به کاربر نمایش داده می‌شود.

### محدودیت ترکیبی چند فیلد: اعتبارسنجی کد پستی

فرمت کد پستی از کشوری به کشور دیگر متفاوت است. بسیاری از کشورها یک پیشوند اختیاری با کد کشور دارند (مثل `D-` در آلمان، `F-` در فرانسه و `CH-` در سوئیس). برخی کشورها فقط تعداد ثابتی رقم در کد پستی استفاده می‌کنند، در حالی که کشورهایی مثل بریتانیا فرمت‌های پیچیده‌تری دارند که در موقعیت‌های خاصی حروف را هم قبول می‌کنند.

> **توجه:**
> این یک کتابخانه جامع برای اعتبارسنجی کد پستی نیست، بلکه صرفاً نمایشی از مفاهیم کلیدی است.

به عنوان مثال، یک اسکریپت برای بررسی اعتبارسنجی محدودیت‌ها در یک فرم اضافه می‌کنیم:

```html
<form>
  <label for="postal-code">Postal Code: </label>
  <input type="text" id="postal-code" />
  <label for="country">Country: </label>
  <select id="country">
    <option value="ch">Switzerland</option>
    <option value="fr">France</option>
    <option value="de">Germany</option>
    <option value="nl">The Netherlands</option>
  </select>
  <input type="submit" value="Validate" />
</form>
```

این کد فرم زیر را نمایش می‌دهد:

ابتدا تابعی می‌نویسیم که خودِ محدودیت را بررسی می‌کند:

```js
const countrySelect = document.getElementById("country");
const postalCodeField = document.getElementById("postal-code");

function checkPostalCode() {
  // برای هر کشور، الگوی مورد نیاز کد پستی را مشخص می‌کند
  const constraints = {
    ch: [
      "^(CH-)?\\d{4}$",
      "کد پستی سوئیس باید دقیقاً ۴ رقم باشد: مثلاً CH-1950 یا 1950",
    ],
    fr: [
      "^(F-)?\\d{5}$",
      "کد پستی فرانسه باید دقیقاً ۵ رقم باشد: مثلاً F-75012 یا 75012",
    ],
    de: [
      "^(D-)?\\d{5}$",
      "کد پستی آلمان باید دقیقاً ۵ رقم باشد: مثلاً D-12345 یا 12345",
    ],
    nl: [
      "^(NL-)?\\d{4}\\s*([A-RT-Z][A-Z]|S[BCE-RT-Z])$",
      "کد پستی هلند باید دقیقاً ۴ رقم و سپس ۲ حرف (به جز SA, SD و SS) باشد",
    ],
  };

  // شناسه‌ی کشور را بخوان
  const country = countrySelect.value;

  // بررسی‌کننده‌ی محدودیت را بساز
  const constraint = new RegExp(constraints[country][0], "");
  console.log(constraint);

  // آن را بررسی کن!
  if (constraint.test(postalCodeField.value)) {
    // کد پستی مطابق محدودیت است؛ با Constraint API به مرورگر اطلاع می‌دهیم
    postalCodeField.setCustomValidity("");
  } else {
    // کد پستی مطابق محدودیت نیست؛ با Constraint API پیام خطا می‌فرستیم
    postalCodeField.setCustomValidity(constraints[country][1]);
  }
}
```

سپس تابع را به رویداد `change` عنصر `<select>` و رویداد `input` عنصر `<input>` متصل می‌کنیم:

```js
countrySelect.addEventListener("change", checkPostalCode);
postalCodeField.addEventListener("input", checkPostalCode);
```

### محدود کردن حجم فایل قبل از آپلود

یکی دیگر از محدودیت‌های رایج، محدود کردن حجم فایل برای آپلود است. بررسی این موضوع در سمت کلاینت و پیش از ارسال فایل به سرور، نیاز به ترکیب Constraint Validation API (به‌ویژه متد `field.setCustomValidity()`) با یک API جاوااسکریپت دیگر، یعنی File API دارد.

بخش HTML:

```html
<label for="fs">فایلی کوچک‌تر از 75 کیلوبایت انتخاب کنید: </label>
<input type="file" id="fs" />
```

جاوااسکریپت فایل انتخاب‌شده را می‌خواند، با استفاده از متد `File.size()` اندازه آن را به‌دست می‌آورد، با محدودیت (ثابت) مقایسه می‌کند و در صورت نقض محدودیت، با Constraint API به مرورگر اطلاع می‌دهد:

```js
const fs = document.getElementById("fs");

function checkFileSize() {
  const files = fs.files;

  // اگر حداقل یک فایل انتخاب شده باشد
  if (files.length > 0) {
    if (files[0].size > 75 * 1000) {
      // بررسی محدودیت
      fs.setCustomValidity("فایل انتخاب‌شده نباید بزرگ‌تر از 75 کیلوبایت باشد");
      fs.reportValidity();
      return;
    }
  }
  // عدم وجود نقض محدودیت سفارشی
  fs.setCustomValidity("");
}
```

در نهایت، متد را به رویداد مناسب متصل می‌کنیم:

```js
fs.addEventListener("change", checkFileSize);
```

## سبک‌دهی بصری اعتبارسنجی محدودیت‌ها

علاوه بر تعیین محدودیت‌ها، توسعه‌دهندگان می‌خواهند نحوه نمایش پیام‌ها به کاربران و سبک‌دهی آن‌ها را کنترل کنند.

### کنترل ظاهر عناصر

ظاهر عناصر را می‌توان با استفاده از pseudo-classهای CSS کنترل کرد.

#### شبه‌کلاس‌های :required و :optional

شبه‌کلاس‌های `:required` و `:optional` به شما امکان می‌دهند انتخاب‌گرهایی بنویسید که عناصر فرم دارای ویژگی `required` یا فاقد آن را مطابقت دهند.

#### شبه‌کلاس :placeholder-shown

به مستندات `:placeholder-shown` مراجعه کنید.

#### شبه‌کلاس‌های :valid و :invalid

شبه‌کلاس‌های `:valid` و `:invalid` (از نوع [pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Selectors/Pseudo-classes)) برای نمایش عناصر `<input>` استفاده می‌شوند که محتوای آن‌ها به‌ترتیب بر اساس تنظیمات نوع input معتبر یا نامعتبر است. این کلاس‌ها به شما امکان می‌دهند عناصر معتبر یا نامعتبر فرم را طوری استایل دهید که تشخیص عناصر درست یا نادرست قالب‌بندی‌شده آسان‌تر شود.

### کنترل متن نقض محدودیت (constraint violation)

موارد زیر به کنترل متن نقض محدودیت کمک می‌کنند:

- متد `setCustomValidity(message)` روی عناصر زیر:
  - {{HTMLElement("fieldset")}}. توجه: تنظیم پیام اعتبارسنجی سفارشی روی عناصر `fieldset` در بیشتر مرورگرها از ارسال فرم جلوگیری نمی‌کند.
  - {{HTMLElement("input")}}
  - {{HTMLElement("output")}}
  - {{HTMLElement("select")}}
  - دکمه‌های ارسال (که با یک عنصر `<button>` با نوع `submit` یا یک عنصر `input` با نوع `submit` ساخته می‌شوند. انواع دیگر دکمه‌ها در اعتبارسنجی محدودیت شرکت نمی‌کنند.)
  - {{HTMLElement("textarea")}}

- رابط [`ValidityState`](/en-US/docs/Web/API/ValidityState) شیء بازگشتی از property `validity` عناصر بالا را توصیف می‌کند. این رابط روش‌های مختلفی را نشان می‌دهد که یک مقدار واردشده می‌تواند نامعتبر باشد. این روش‌ها با هم کمک می‌کنند توضیح دهند که چرا یک مقدار در صورت نامعتبر بودن، اعتبارسنجی را رد می‌کند.