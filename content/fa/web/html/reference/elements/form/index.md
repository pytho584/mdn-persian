---
title: "<form> HTML form element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/form"
translated_by: "n8n + AI"
---

عنصر `<form>` در HTML، بخشی از سند را نشان می‌دهد که شامل کنترل‌های تعاملی برای ارسال اطلاعات است.

```html interactive-example
<form action="" method="get" class="form-example">
  <div class="form-example">
    <label for="name">Enter your name: </label>
    <input type="text" name="name" id="name" required />
  </div>
  <div class="form-example">
    <label for="email">Enter your email: </label>
    <input type="email" name="email" id="email" required />
  </div>
  <div class="form-example">
    <input type="submit" value="Subscribe!" />
  </div>
</form>
```

```css interactive-example
form.form-example {
  display: table;
}

div.form-example {
  display: table-row;
}

label,
input {
  display: table-cell;
  margin-bottom: 10px;
}

label {
  padding-right: 10px;
}
```

می‌توان از pseudo-classهای CSS مانند `:valid` و `:invalid` برای استایل‌دهی به یک عنصر `<form>` بر اساس معتبر بودن عناصر داخل آن استفاده کرد.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `accept` {{deprecated_inline}}
  - : لیستی از [نوع‌های محتوایی (content types)](/en-US/docs/Web/SVG/Guides/Content_type) که سرور می‌پذیرد، با کاما از هم جدا شده‌اند.

    > [!NOTE]
    > **این ویژگی منسوخ شده است و نباید استفاده شود.** در عوض، از ویژگی [`accept`](/en-US/docs/Web/HTML/Reference/Elements/input#accept) روی عناصر `<input type=file>` استفاده کنید.

- `accept-charset`
  - : {{Glossary("character encoding")}} (رمزگذاری کاراکتر) مورد پذیرش سرور.
    مشخصات فقط یک مقدار `"UTF-8"` (بدون حساسیت به بزرگی/کوچکی حروف) را مجاز می‌داند که نشان‌دهندهٔ فراگیر بودن این رمزگذاری است (در گذشته، چندین رمزگذاری کاراکتر می‌توانست به صورت لیست جدا شده با کاما یا فاصله مشخص شود).

- `autocapitalize`
  - : مشخص می‌کند که آیا متن ورودی به طور خودکار بزرگ‌نویسی می‌شود یا خیر، و اگر بله، به چه صورت. برای اطلاعات بیشتر، صفحهٔ ویژگی سراسری [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize) را ببینید.

- [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
  - : نشان می‌دهد که آیا مرورگر می‌تواند به طور پیش‌فرض مقادیر عناصر ورودی را به صورت خودکار تکمیل کند. ویژگی‌های `autocomplete` روی عناصر فرم، مقدار تعیین‌شده روی `<form>` را بازنویسی می‌کنند. مقادیر ممکن:
    - `off`: مرورگر ممکن است ورودی‌ها را به صورت خودکار تکمیل نکند. (مرورگرها معمولاً این مقدار را برای فرم‌های ورود به سیستم نادیده می‌گیرند؛ به [مدیریت تکمیل خودکار برای فیلدهای ورود](/en-US/docs/Web/Security/Practical_implementation_guides/Turning_off_form_autocompletion#managing_autofill_for_login_fields) مراجعه کنید.)
    - `on`: مرورگر ممکن است ورودی‌ها را به صورت خودکار تکمیل کند.

- `name`
  - : نام فرم. مقدار نباید رشتهٔ خالی باشد و در میان عناصر `form` موجود در مجموعه‌ای که فرم در آن قرار دارد (در صورت وجود)، باید یکتا باشد. این نام به یک property از اشیاء `Window`، `Document` و `document.forms` تبدیل می‌شود که به عنصر فرم ارجاع می‌دهد.

- [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel)
  - : کنترل می‌کند که فرم چه حاشیه‌نویسی‌ها (annotations) و چه نوع پیوندهایی ایجاد کند. حاشیه‌نویسی‌ها شامل [`external`](/en-US/docs/Web/HTML/Reference/Attributes/rel#external)، [`nofollow`](/en-US/docs/Web/HTML/Reference/Attributes/rel#nofollow)، [`opener`](/en-US/docs/Web/HTML/Reference/Attributes/rel#opener)، [`noopener`](/en-US/docs/Web/HTML/Reference/Attributes/rel#noopener) و [`noreferrer`](/en-US/docs/Web/HTML/Reference/Attributes/rel#noreferrer) هستند. نوع پیوندها شامل [`help`](/en-US/docs/Web/HTML/Reference/Attributes/rel#help)، [`prev`](/en-US/docs/Web/HTML/Reference/Attributes/rel#prev)، [`next`](/en-US/docs/Web/HTML/Reference/Attributes/rel#next)، [`search`](/en-US/docs/Web/HTML/Reference/Attributes/rel#search) و [`license`](/en-US/docs/Web/HTML/Reference/Attributes/rel#license) می‌شود. مقدار [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) فهرستی از این مقادیر شمارشی است که با فاصله از هم جدا شده‌اند.

### ویژگی‌های ارسال فرم

ویژگی‌های زیر رفتار فرم را هنگام ارسال کنترل می‌کنند.

- `action`
  - : نشانی URL که پردازش ارسال فرم را انجام می‌دهد. این مقدار می‌تواند با ویژگی [`formaction`](/en-US/docs/Web/HTML/Reference/Elements/button#formaction) روی یک عنصر `<button>`، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) بازنویسی شود. وقتی `method="dialog"` تنظیم شده باشد، این ویژگی نادیده گرفته می‌شود.

- `enctype`
  - : اگر مقدار ویژگی `method` برابر `post` باشد، `enctype` نوع [MIME](https://en.wikipedia.org/wiki/Mime_type) ارسال فرم است. مقادیر ممکن:
    - `application/x-www-form-urlencoded`: مقدار پیش‌فرض.
    - `multipart/form-data`: اگر فرم شامل عناصر `<input>` با `type=file` باشد، از این مقدار استفاده کنید.
    - `text/plain`: برای اهداف اشکال‌زدایی مفید است.

    این مقدار می‌تواند با ویژگی‌های [`formenctype`](/en-US/docs/Web/HTML/Reference/Elements/button#formenctype) روی عناصر `<button>`، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) بازنویسی شود.

- `method`
  - : متد [HTTP](/en-US/docs/Web/HTTP) که فرم با آن ارسال می‌شود.
    تنها متدها/مقادیر مجاز (به‌صورت case-insensitive) عبارتند از:
    - `post`: متد `POST`؛ داده‌های فرم به‌عنوان [بدنهٔ درخواست](/en-US/docs/Web/API/Request/body) ارسال می‌شوند.
    - `get` (پیش‌فرض): متد `GET`؛ داده‌های فرم با یک جداکنندهٔ `?` به URL مشخص‌شده در `action` اضافه می‌شوند. این متد را زمانی استفاده کنید که فرم [اثر جانبی ندارد](/en-US/docs/Glossary/Idempotent).
    - `dialog`: وقتی فرم داخل یک `<dialog>` است، دیالوگ را می‌بندد و هنگام ارسال، رویداد `submit` را فعال می‌کند، بدون اینکه داده‌ای ارسال یا فرم پاک شود.

    این مقدار توسط ویژگی‌های [`formmethod`](/en-US/docs/Web/HTML/Reference/Elements/button#formmethod) روی عناصر `<button>`، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) بازنویسی می‌شود.

- `novalidate`
  - این ویژگی بولی (Boolean) مشخص می‌کند که فرم در زمان ارسال اعتبارسنجی نشود. اگر این ویژگی تنظیم نشده باشد (و بنابراین فرم اعتبارسنجی **می‌شود**)، می‌توان با استفاده از ویژگی [`formnovalidate`](/en-US/docs/Web/HTML/Reference/Elements/button#formnovalidate) روی یک عنصر {{HTMLElement("button")}}، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) که متعلق به فرم است، این رفتار را نادیده گرفت.

- `target`
  - : مشخص می‌کند پاسخ پس از ارسال فرم در کجا نمایش داده شود. این یک نام/کلیدواژه برای یک _browsing context_ (زمینه مرور) است (مثلاً تب، پنجره یا iframe). کلیدواژه‌های زیر معانی خاصی دارند:
    - `_self` (پیش‌فرض): بارگیری در همان browsing context فعلی.
    - `_blank`: بارگیری در یک browsing context جدید بدون نام. این رفتار مشابه تنظیم [`rel="noopener"`](#rel) است که [`window.opener`](/en-US/docs/Web/API/Window/opener) را تنظیم نمی‌کند.
    - `_parent`: بارگیری در browsing context والد (والد) فعلی. اگر والد وجود نداشته باشد، مانند `_self` عمل می‌کند.
    - `_top`: بارگیری در بالاترین سطح browsing context (یعنی browsing context‌ای که جد (ancestor) فعلی است و والد ندارد). اگر والد وجود نداشته باشد، مانند `_self` عمل می‌کند.
    - `_unfencedTop`: پاسخ فرم داخل یک [fenced frame](/en-US/docs/Web/API/Fenced_frame_API) توکار را در فریم بالاترین سطح بارگیری می‌کند (یعنی از ریشه fenced frame عبور می‌کند، بر خلاف سایر مقصدهای رزرو شده). فقط در داخل fenced frames در دسترس است.

    این مقدار می‌تواند با استفاده از ویژگی [`formtarget`](/en-US/docs/Web/HTML/Reference/Elements/button#formtarget) روی یک عنصر {{HTMLElement("button")}}، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) نادیده گرفته شود.

## مثال (Examples)

```html
<!-- Form which will send a GET request to the current URL -->
<form method="get">
  <label>
    Name:
    <input name="submitted-name" autocomplete="name" />
  </label>
  <button>Save</button>
</form>

<!-- Form which will send a POST request to the current URL -->
<form method="post">
  <label>
    Name:
    <input name="submitted-name" autocomplete="name" />
  </label>
  <button>Save</button>
</form>

<!-- Form with fieldset, legend, and label -->
<form method="post">
  <fieldset>
    <legend>Do you agree to the terms?</legend>
    <label><input type="radio" name="radio" value="yes" /> Yes</label>
    <label><input type="radio" name="radio" value="no" /> No</label>
  </fieldset>
</form>
```

| ویژگی | مقدار |
|-------|-------|
| [Content categories](/en-US/docs/Web/HTML/Guides/Content_categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content), [palpable content](/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) |
| Permitted content | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، اما شامل عنصر `<form>` نباشد |
| Tag omission | هیچکدام، هر دو تگ شروع و پایان اجباری هستند |
| Permitted parents | هر عنصری که [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد |
| Implicit ARIA role | نقش ARIA ضمنی: [`form`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role) |
| Permitted ARIA roles | نقش‌های ARIA مجاز: [`search`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role), [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role) یا [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) |
| DOM interface | `HTMLFormElement` |

## See also

- [HTML forms guide](/en-US/docs/Learn_web_development/Extensions/Forms)
- Other elements used when creating forms: `<button>`, `<datalist>`, `<fieldset>`, `<input>`, `<label>`, `<legend>`, `<meter>`, `<optgroup>`, `<option>`, `<output>`, `<progress>`, `<select>`, `<textarea>`
- Getting a list of the elements in the form: `HTMLFormElement.elements`
- [ARIA: Form role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role)
- [ARIA: Search role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)