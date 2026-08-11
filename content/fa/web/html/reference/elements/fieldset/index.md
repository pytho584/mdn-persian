---
title: "<fieldset> HTML field set element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/fieldset"
translated_by: "n8n + AI"
---

# `<fieldset>` - عنصر گروه‌بندی فیلد در HTML

المان **`<fieldset>`** در [HTML](/en-US/docs/Web/HTML) برای گروه‌بندی چندین کنترل و برچسب (المان {{HTMLElement("label")}}) درون یک فرم وب استفاده می‌شود.

```html interactive-example
<form>
  <fieldset>
    <legend>Choose your favorite monster</legend>

    <input type="radio" id="kraken" name="monster" value="K" />
    <label for="kraken">Kraken</label><br />

    <input type="radio" id="sasquatch" name="monster" value="S" />
    <label for="sasquatch">Sasquatch</label><br />

    <input type="radio" id="mothman" name="monster" value="M" />
    <label for="mothman">Mothman</label>
  </fieldset>
</form>
```

```css interactive-example
legend {
  background-color: black;
  color: white;
  padding: 3px 6px;
}

input {
  margin: 0.4rem;
}
```

همانطور که در مثال بالا دیده می‌شود، `<fieldset>` گروه‌بندی بخشی از فرم HTML را فراهم می‌کند و یک المان {{htmlelement("legend")}} درون آن به عنوان عنوان `<fieldset>` عمل می‌کند. این المان ویژگی‌های کمی دارد که مهم‌ترین آن‌ها `form` و `disabled` هستند. ویژگی `form` می‌تواند `id` یک {{htmlelement("form")}} در همان صفحه را بگیرد تا `<fieldset>` بخشی از آن فرم باشد، حتی اگر داخل آن نباشد. ویژگی `disabled` هم به شما اجازه می‌دهد تا `<fieldset>` و تمام محتویاتش را یک‌جا غیرفعال کنید.

## ویژگی‌ها

این المان شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
  - : اگر این ویژگی بولین تنظیم شود، تمام کنترل‌های فرمی که از فرزندان `<fieldset>` هستند، غیرفعال می‌شوند؛ یعنی قابل ویرایش نیستند و همراه {{htmlelement("form")}} ارسال نمی‌شوند. همچنین هیچ رویداد تعاملی مانند کلیک ماوس یا رویدادهای مرتبط با فوکوس دریافت نمی‌کنند. مرورگرها به طور پیش‌فرض این کنترل‌ها را خاکستری نمایش می‌دهند. توجه کنید که المان‌های فرم داخل {{HTMLElement("legend")}} غیرفعال نمی‌شوند.
- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)
  - : این ویژگی مقدار ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) المان {{HTMLElement("form")}}ای را می‌گیرد که می‌خواهید `<fieldset>` بخشی از آن باشد، حتی اگر داخل آن فرم نباشد. توجه داشته باشید که استفاده از این ویژگی می‌تواند گیج‌کننده باشد — اگر می‌خواهید المان‌های {{HTMLElement("input")}} داخل `<fieldset>` با فرم مرتبط شوند، باید ویژگی `form` را مستقیماً روی آن عناصر قرار دهید. می‌توانید با جاوااسکریپت و استفاده از [HTMLFormElement.elements](/en-US/docs/Web/API/HTMLFormElement/elements) بررسی کنید که کدام عناصر با یک فرم مرتبط هستند.
- `name`
  - : نام مرتبط با گروه.

> **نکته:** عنوان مربوط به `<fieldset>` توسط اولین المان {{HTMLElement("legend")}} که داخل آن قرار گرفته است مشخص می‌شود.

## استایل‌دهی با CSS

برای `<fieldset>` ملاحظات خاصی در استایل‌دهی وجود دارد.

به طور پیش‌فرض، مقدار `display` آن `block` است و یک [بافت قالب‌بندی بلوکی](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) ایجاد می‌کند. اگر `<fieldset>` با مقدار `display` در سطح خطی (inline-level) استایل داده شود، مانند `inline-block` رفتار می‌کند، در غیر این صورت مانند `block`. به طور پیش‌فرض، یک حاشیه `groove` به ضخامت `2px` دور محتوا و کمی padding پیش‌فرض وجود دارد. این المان به طور پیش‌فرض `min-inline-size: min-content` دارد.

اگر یک {{htmlelement("legend")}} وجود داشته باشد، روی حاشیه `block-start` قرار می‌گیرد. `<legend>` اندازه‌اش به محتوا جمع می‌شود و همچنین یک بافت قالب‌بندی ایجاد می‌کند. مقدار `display` آن به حالت بلوکی تبدیل می‌شود (مثلاً `display: inline` مانند `block` رفتار می‌کند).

یک جعبهٔ ناشناس (anonymous box) محتویات `<fieldset>` را در خود نگه می‌دارد و برخی ویژگی‌ها را از `<fieldset>` به ارث می‌برد. اگر `<fieldset>` با `display: grid` یا `display: inline-grid` استایل‌دهی شده باشد، آن جعبهٔ ناشناس یک بافتار قالب گرید (grid formatting context) خواهد بود. اگر `<fieldset>` با `display: flex` یا `display: inline-flex` استایل‌دهی شده باشد، آن جعبهٔ ناشناس یک بافتار قالب فلکس (flex formatting context) خواهد بود. در غیر این صورت، یک بافتار قالب بلوکی (block formatting context) ایجاد می‌کند.

شما آزادید که `<fieldset>` و `<legend>` را هر طور که برای طراحی صفحه‌تان مناسب است استایل دهید.

## نمونه‌ها

### `<fieldset>` پایه

این مثال شامل یک `<fieldset>` با یک `<legend>` است و یک کنترل درون آن قرار دارد.

```html
<form action="#">
  <fieldset>
    <legend>Do you agree?</legend>
    <input type="checkbox" id="chbx" name="agree" value="Yes!" />
    <label for="chbx">I agree</label>
  </fieldset>
</form>
```

#### نتیجه

### `<fieldset>` غیرفعال

این مثال یک `<fieldset>` غیرفعال را با دو کنترل درون آن نشان می‌دهد. توجه کنید که هر دو کنترل به دلیل قرار گرفتن داخل یک `<fieldset>` غیرفعال، غیرفعال شده‌اند.

```html
<form action="#">
  <fieldset disabled>
    <legend>Disabled login fieldset</legend>
    <div>
      <label for="name">Name: </label>
      <input type="text" id="name" value="Chris" />
    </div>
    <div>
      <label for="pwd">Archetype: </label>
      <input type="password" id="pwd" value="Wookie" />
    </div>
  </fieldset>
</form>
```

#### نتیجه

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا (Content categories)</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی (Flow content)</a>،
        ریشهٔ بخش‌بندی (sectioning root)،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#listed">فهرست‌شده (listed)</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content">عنصر مرتبط با فرم (form-associated element)</a>،
        محتوای قابل لمس (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        یک عنصر اختیاری <code>&lt;legend&gt;</code> و سپس محتوای جریانی.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a>
        را می‌پذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"><code>group</code></a></td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role"><code>radiogroup</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLFieldSetElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

- عنصر `<legend>`
- عنصر `<input>`
- عنصر `<label>`
- عنصر `<form>`