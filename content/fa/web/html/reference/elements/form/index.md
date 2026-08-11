---
title: "<form> HTML form element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/form"
translated_by: "n8n + AI"
---

عنصر `<form>` در HTML، بخشی از سند را نشان می‌دهد که شامل کنترل‌های تعاملی برای ارسال اطلاعات است.

```html interactive-example
<form action="" method="get" class="form-example">
  <div class="form-example">
    <label for="name">نام خود را وارد کنید: </label>
    <input type="text" name="name" id="name" required />
  </div>
  <div class="form-example">
    <label for="email">ایمیل خود را وارد کنید: </label>
    <input type="email" name="email" id="email" required />
  </div>
  <div class="form-example">
    <input type="submit" value="عضویت!" />
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

می‌توان از کلاس‌های شبه (`pseudo-classes`) CSS مانند `:valid` و `:invalid` برای استایل‌دهی به عنصر `<form>` بر اساس اعتبار عناصر داخل فرم استفاده کرد.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `accept` {{deprecated_inline}}
  - : فهرستی از [انواع محتوا (content types)](/en-US/docs/Web/SVG/Guides/Content_type) که سرور می‌پذیرد، که با کاما از هم جدا شده‌اند.

    > [!NOTE]
    > **این ویژگی منسوخ شده است و نباید استفاده شود.** به جای آن، از ویژگی [`accept`](/en-US/docs/Web/HTML/Reference/Elements/input#accept) روی عناصر `<input type=file>` استفاده کنید.

- `accept-charset`
  - : [رمزگذاری کاراکتر (character encoding)](/en-US/docs/Glossary/Character_encoding) که سرور می‌پذیرد. مشخصات فقط مقدار `"UTF-8"` را بدون در نظر گرفتن حروف بزرگ و کوچک مجاز می‌داند؛ این نشان‌دهنده فراگیر بودن این رمزگذاری است (در گذشته می‌توانست چندین رمزگذاری به صورت فهرست جدا شده با کاما یا فاصله مشخص شود).

- `autocapitalize`
  - : مشخص می‌کند که آیا متن ورودی به طور خودکار بزرگ شود یا نه و اگر بله، به چه صورت. برای اطلاعات بیشتر به صفحه ویژگی سراسری [`autocapitalize`](/en-US/docs/Web/HTML/Reference/Global_attributes/autocapitalize) مراجعه کنید.

- [`autocomplete`](/en-US/docs/Web/HTML/Reference/Attributes/autocomplete)
  - : نشان می‌دهد که آیا مرورگر می‌تواند به طور پیش‌فرض مقادیر عناصر ورودی را به صورت خودکار تکمیل کند. ویژگی‌های `autocomplete` روی عناصر فرم، این ویژگی را روی `<form>` لغو می‌کنند. مقادیر ممکن:
    - `off`: مرورگر ممکن است ورودی‌ها را به صورت خودکار تکمیل نکند. (مرورگرها معمولاً این مقدار را برای فرم‌های ورود نادیده می‌گیرند؛ به [مدیریت تکمیل خودکار برای فیلدهای ورود](/en-US/docs/Web/Security/Practical_implementation_guides/Turning_off_form_autocompletion#managing_autofill_for_login_fields) مراجعه کنید.)
    - `on`: مرورگر ممکن است ورودی‌ها را به صورت خودکار تکمیل کند.

- `name`
  - : نام فرم. مقدار نباید رشته خالی باشد و در میان عناصر `form` موجود در مجموعه فرم‌ها (در صورت وجود) باید یکتا باشد. این نام به یک ویژگی از اشیاء `Window`، `Document` و `document.forms` تبدیل می‌شود که به عنصر فرم ارجاع می‌دهد.

- [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel)
  - : حاشیه‌نویسی‌ها (annotations) و نوع لینک‌هایی که فرم ایجاد می‌کند را کنترل می‌کند. حاشیه‌نویسی‌ها شامل [`external`](/en-US/docs/Web/HTML/Reference/Attributes/rel#external)، [`nofollow`](/en-US/docs/Web/HTML/Reference/Attributes/rel#nofollow)، [`opener`](/en-US/docs/Web/HTML/Reference/Attributes/rel#opener)، [`noopener`](/en-US/docs/Web/HTML/Reference/Attributes/rel#noopener) و [`noreferrer`](/en-US/docs/Web/HTML/Reference/Attributes/rel#noreferrer) هستند. نوع لینک‌ها نیز شامل [`help`](/en-US/docs/Web/HTML/Reference/Attributes/rel#help)، [`prev`](/en-US/docs/Web/HTML/Reference/Attributes/rel#prev)، [`next`](/en-US/docs/Web/HTML/Reference/Attributes/rel#next)، [`search`](/en-US/docs/Web/HTML/Reference/Attributes/rel#search) و [`license`](/en-US/docs/Web/HTML/Reference/Attributes/rel#license) می‌شود. مقدار `rel` یک لیست جدا شده با فاصله از این مقادیر شمارشی است.

### ویژگی‌های مربوط به ارسال فرم

ویژگی‌های زیر رفتار حین ارسال فرم را کنترل می‌کنند.

- `action`
  - : آدرس URLای که داده‌های فرم را پردازش می‌کند. این مقدار می‌تواند توسط ویژگی [`formaction`](/en-US/docs/Web/HTML/Reference/Elements/button#formaction) روی عنصر {{HTMLElement("button")}}، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) بازنویسی شود. اگر `method="dialog"` تنظیم شده باشد، این ویژگی نادیده گرفته می‌شود.
- `enctype`
  - : اگر مقدار ویژگی `method` برابر با `post` باشد، `enctype` نوع [MIME](https://en.wikipedia.org/wiki/Mime_type) داده‌های ارسالی فرم است. مقادیر ممکن:
    - `application/x-www-form-urlencoded`: مقدار پیش‌فرض.
    - `multipart/form-data`: اگر فرم شامل عناصر {{HTMLElement("input")}} با `type=file` باشد، از این مقدار استفاده کنید.
    - `text/plain`: برای اهداف اشکال‌زدایی مناسب است.

    این مقدار می‌تواند توسط ویژگی‌های [`formenctype`](/en-US/docs/Web/HTML/Reference/Elements/button#formenctype) روی عناصر {{HTMLElement("button")}}، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) بازنویسی شود.

- `method`
  - : روش [HTTP](/en-US/docs/Web/HTTP) برای ارسال فرم. تنها روش‌ها/مقادیر مجاز (بدون حساسیت به حروف بزرگ و کوچک) عبارتند از:
    - `post`: روش {{HTTPMethod("POST")}}؛ داده‌های فرم به عنوان [بدنه درخواست](/en-US/docs/Web/API/Request/body) ارسال می‌شوند.
    - `get` (پیش‌فرض): روش {{HTTPMethod("GET")}}؛ داده‌های فرم به آدرس `action` با جداکننده `?` اضافه می‌شوند. زمانی از این روش استفاده کنید که فرم [عوارض جانبی ندارد](/en-US/docs/Glossary/Idempotent).
    - `dialog`: وقتی فرم داخل یک {{HTMLElement("dialog")}} قرار دارد، دیالوگ را می‌بندد و باعث می‌شود رویداد `submit` در هنگام ارسال فعال شود، بدون اینکه داده‌ای ارسال کند یا فرم را پاک کند.

    این مقدار توسط ویژگی‌های [`formmethod`](/en-US/docs/Web/HTML/Reference/Elements/button#formmethod) روی عناصر {{HTMLElement("button")}}، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) بازنویسی می‌شود.

- `novalidate`
  - : این ویژگی بولین مشخص می‌کند که فرم هنگام ارسال نباید اعتبارسنجی شود. اگر این ویژگی تنظیم نشده باشد (و در نتیجه فرم **_اعتبارسنجی می‌شود_**)، می‌توان آن را با ویژگی [`formnovalidate`](/en-US/docs/Web/HTML/Reference/Elements/button#formnovalidate) روی یک عنصر [`<button>`](/en-US/docs/Web/HTML/Reference/Elements/button)، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) متعلق به فرم نادیده گرفت.

- `target`
  - : مشخص می‌کند که پاسخ پس از ارسال فرم در کجا نمایش داده شود. این مقدار یک نام/کلیدواژه برای یک _browsing context_ است (مثلاً تب، پنجره یا iframe). کلیدواژه‌های زیر معانی ویژه‌ای دارند:
    - `_self` (پیش‌فرض): در همان browsing context فعلی بارگذاری شود.
    - `_blank`: در یک browsing context جدید بدون نام بارگذاری شود. این رفتار مشابه تنظیم [`rel="noopener"`](#rel) است که [`window.opener`](/en-US/docs/Web/API/Window/opener) را تنظیم نمی‌کند.
    - `_parent`: در browsing context والدِ بافت فعلی بارگذاری شود. اگر والدی نباشد، مانند `_self` عمل می‌کند.
    - `_top`: در browsing context سطح بالا (یعنی بافتی که جدِ بافت فعلی است و والدی ندارد) بارگذاری شود. اگر والدی نباشد، مانند `_self` عمل می‌کند.
    - `_unfencedTop`: پاسخ یک فرم را از داخل یک [fenced frame](/en-US/docs/Web/API/Fenced_frame_API) تعبیه‌شده در قاب سطح بالا بارگذاری می‌کند (یعنی فراتر از ریشهٔ fenced frame می‌رود، برخلاف سایر مقصدهای رزروشده). فقط در داخل fenced frame ها در دسترس است.

    این مقدار می‌تواند با ویژگی [`formtarget`](/en-US/docs/Web/HTML/Reference/Elements/button#formtarget) روی یک عنصر [`<button>`](/en-US/docs/Web/HTML/Reference/Elements/button)، [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) یا [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image) نادیده گرفته شود.

## مثال‌ها

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

### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content">palpable content</a>
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>، اما بدون عنصر <code>&lt;form&gt;</code>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">flow content</a> را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA پیش‌فرض</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role">form</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role">search</a></code>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>
        یا <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td><code>HTMLFormElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات (Specifications)

مشخصات مربوط به این عنصر در مرورگرهای مختلف قابل مشاهده است.

## سازگاری با مرورگرها (Browser compatibility)

اطلاعات سازگاری این عنصر با مرورگرهای مختلف در جدول‌های مربوطه موجود است.

## همچنین ببینید

- [راهنمای فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)
- سایر عناصر مورد استفاده در ساخت فرم‌ها: <code>&lt;button&gt;</code>، <code>&lt;datalist&gt;</code>، <code>&lt;fieldset&gt;</code>، <code>&lt;input&gt;</code>، <code>&lt;label&gt;</code>، <code>&lt;legend&gt;</code>، <code>&lt;meter&gt;</code>، <code>&lt;optgroup&gt;</code>، <code>&lt;option&gt;</code>، <code>&lt;output&gt;</code>، <code>&lt;progress&gt;</code>، <code>&lt;select&gt;</code>، <code>&lt;textarea&gt;</code>
- دریافت لیست عناصر داخل فرم: <code>HTMLFormElement.elements</code>
- [نقش ARIA: Form](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role)
- [نقش ARIA: Search](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)