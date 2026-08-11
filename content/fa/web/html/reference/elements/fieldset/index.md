---
title: "<fieldset> HTML field set element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/fieldset"
translated_by: "n8n + AI"
---

عنصر HTML `<fieldset>` برای گروه‌بندی چندین کنترل فرم و برچسب‌های مربوط به آن‌ها ({{HTMLElement("label")}}) درون یک فرم وب استفاده می‌شود.

```html interactive-example
<form>
  <fieldset>
    <legend>هیولای مورد علاقه‌ات را انتخاب کن</legend>

    <input type="radio" id="kraken" name="monster" value="K" />
    <label for="kraken">کِرِیکِن</label><br />

    <input type="radio" id="sasquatch" name="monster" value="S" />
    <label for="sasquatch">ساسکواچ</label><br />

    <input type="radio" id="mothman" name="monster" value="M" />
    <label for="mothman">ماثمن</label>
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

همانطور که مثال بالا نشان می‌دهد، عنصر `<fieldset>` یک گروه‌بندی برای بخشی از فرم HTML ایجاد می‌کند و یک عنصر {{htmlelement("legend")}} تودرتو عنوان این گروه را مشخص می‌کند. این عنصر ویژگی‌های کمی دارد که مهم‌ترین آن‌ها عبارتند از:

- `form`: می‌تواند `id` یک {{htmlelement("form")}} در همان صفحه را بگیرد. به این ترتیب می‌توانید `<fieldset>` را حتی اگر درون آن فرم نباشد، بخشی از آن فرم کنید.
- `disabled`: با این ویژگی می‌توانید یک‌باره کل `<fieldset>` و تمام محتویاتش را غیرفعال کنید.

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
  - : اگر این ویژگی Boolean تنظیم شود، همه کنترل‌های فرمی که فرزند `<fieldset>` هستند غیرفعال می‌شوند. یعنی قابل ویرایش نیستند و همراه با {{htmlelement("form")}} ارسال نمی‌شوند. همچنین رویدادهای مرورگر مانند کلیک ماوس یا رویدادهای مرتبط با focus را دریافت نمی‌کنند. مرورگرها معمولاً این کنترل‌ها را به صورت خاکستری نشان می‌دهند. توجه داشته باشید که عناصر فرم درون {{HTMLElement("legend")}} غیرفعال نمی‌شوند.
- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)
  - : این ویژگی مقدار [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یک عنصر {{HTMLElement("form")}} را می‌گیرد که می‌خواهید `<fieldset>` بخشی از آن باشد، حتی اگر درون فرم نباشد. توجه کنید که استفاده از این ویژگی می‌تواند گیج‌کننده باشد — اگر می‌خواهید عناصر {{HTMLElement("input")}} داخل `<fieldset>` با فرم مرتبط شوند، باید ویژگی `form` را مستقیماً روی آن عناصر اعمال کنید. با استفاده از JavaScript و {{domxref("HTMLFormElement.elements")}} می‌توانید بررسی کنید کدام عناصر با یک فرم مرتبط هستند.
- `name`
  - : نام مرتبط با گروه.

> [!NOTE]
> عنوان گروه (`fieldset`) توسط اولین عنصر {{HTMLElement("legend")}} که درون آن قرار می‌گیرد مشخص می‌شود.

## استایل‌دهی با CSS

برخی نکات خاص برای استایل‌دهی `<fieldset>` وجود دارد.

مقدار پیش‌فرض {{cssxref("display")}} آن `block` است و یک [بافتار قالب‌بندی بلوکی (block formatting context)](/en-US/docs/Web/CSS/Guides/Display/Block_formatting_context) ایجاد می‌کند. اگر به `<fieldset>` یک مقدار `display` در سطح inline بدهید، مانند `inline-block` رفتار می‌کند، در غیر این صورت مانند `block` رفتار می‌کند. به طور پیش‌فرض یک حاشیه `groove` به ضخامت `2px` دور محتویات وجود دارد و کمی padding پیش‌فرض اعمال می‌شود. این عنصر به طور پیش‌فرض دارای {{cssxref("min-inline-size", "min-inline-size: min-content")}} است.

اگر یک {{htmlelement("legend")}} وجود داشته باشد، روی حاشیه `block-start` قرار می‌گیرد. `<legend>` متناسب با محتوا جمع می‌شود (shrink-wrap) و یک بافتار قالب‌بندی نیز ایجاد می‌کند. مقدار `display` آن به `block` تبدیل می‌شود (مثلاً `display: inline` مانند `block` رفتار می‌کند).

یک جعبهٔ ناشناس (anonymous box) وجود خواهد داشت که محتوای داخل `<fieldset>` را در خود نگه می‌دارد و برخی ویژگی‌ها را از `<fieldset>` به ارث می‌برد. اگر `<fieldset>` با `display: grid` یا `display: inline-grid` استایل‌دهی شده باشد، آن جعبهٔ ناشناس یک زمینهٔ قالب‌بندی گرید (grid formatting context) خواهد بود. اگر `<fieldset>` با `display: flex` یا `display: inline-flex` استایل‌دهی شده باشد، جعبهٔ ناشناس یک زمینهٔ قالب‌بندی فلکس (flex formatting context) خواهد بود. در غیر این صورت، یک زمینهٔ قالب‌بندی بلوک (block formatting context) ایجاد می‌کند.

شما می‌توانید `<fieldset>` و `<legend>` را به هر شکلی که با طراحی صفحه‌تان هماهنگ است استایل دهید.

## نمونه‌ها

### فیلدست پایه

این مثال شامل یک `<fieldset>` به همراه `<legend>` و یک کنترل درون آن است.

```html
<form action="#">
  <fieldset>
    <legend>Do you agree?</legend>
    <input type="checkbox" id="chbx" name="agree" value="Yes!" />
    <label for="chbx">I agree</label>
  </fieldset>
</form>
```

### فیلدست غیرفعال (disabled)

این مثال یک `<fieldset>` غیرفعال را با دو کنترل درون آن نشان می‌دهد. توجه کنید که هر دو کنترل به دلیل قرار گرفتن درون یک `<fieldset>` غیرفعال، غیرفعال شده‌اند.

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

## خلاصهٔ فنی

| ویژگی               | توضیحات                                                                                                                                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| دسته‌بندی محتوا     | [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، ریشهٔ بخش‌بندی (sectioning root)، [listed](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#listed)، عنصر [مرتبط با فرم](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content)، محتوای قابل لمس (palpable content). |
| محتوای مجاز         | یک عنصر اختیاری `<legend>` و سپس محتوای جریانی (flow content).                                                                                                                                                          |
| حذف تگ              | هیچکدام؛ هر دو تگ شروع و پایان اجباری هستند.                                                                                                                                                                           |
| والدین مجاز         | هر عنصری که [محتوای جریانی](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد.                                                                                       |
| نقش ARIA ضمنی       | `group`                                                                                                                                                                                                               |
| نقش‌های ARIA مجاز   | `radiogroup`، `presentation`، `none`                                                                                                                                                                                  |
| رابط DOM            | `HTMLFieldSetElement`                                                                                                                                                                                                   |

## مشخصات

(مشخصات استاندارد — در این مستند آورده نشده است)

## سازگاری با مرورگرها

(جدول سازگاری — در این مستند آورده نشده است)

## همچنین ببینید

- عنصر `<legend>`
- عنصر `<input>`
- عنصر `<label>`
- عنصر `<form>`