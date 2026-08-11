---
title: "<optgroup> HTML option group element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/optgroup"
translated_by: "n8n + AI"
---

عنصر `<optgroup>` در [HTML](/en-US/docs/Web/HTML) گروه‌بندی گزینه‌ها را درون یک عنصر `<select>` ایجاد می‌کند.

در [عنصرهای `<select>` قابل شخصی‌سازی](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select)، عنصر `<legend>` به عنوان فرزند `<optgroup>` مجاز است تا برچسبی فراهم کند که هدف‌گیری و استایل‌دهی به آن آسان باشد. این کار جایگزین هر متنی می‌شود که در ویژگی `label` عنصر `<optgroup>` تنظیم شده است و همان معناشناسی را دارد.

```html interactive-example
<label for="dino-select">Choose a dinosaur:</label>
<select id="dino-select">
  <optgroup label="Theropods">
    <option>Tyrannosaurus</option>
    <option>Velociraptor</option>
    <option>Deinonychus</option>
  </optgroup>
  <optgroup label="Sauropods">
    <option>Diplodocus</option>
    <option>Saltasaurus</option>
    <option>Apatosaurus</option>
  </optgroup>
</select>
```

```css interactive-example
label {
  display: block;
  margin-bottom: 10px;
}
```

> [!NOTE]
> عنصرهای `<optgroup>` را نمی‌توان تودرتو قرار داد.

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- [`disabled`](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
  - : اگر این Boolean attribute تنظیم شود، هیچ‌کدام از آیتم‌های این گروه گزینه قابل انتخاب نیستند. معمولاً مرورگرها چنین کنترلی را خاکستری می‌کنند و این کنترل هیچ رویداد مرورگری مانند کلیک ماوس یا رویدادهای مرتبط با فوکوس را دریافت نمی‌کند.
- `label`
  - : نام گروه گزینه‌ها است که مرورگر می‌تواند هنگام برچسب‌گذاری گزینه‌ها در رابط کاربری از آن استفاده کند. اگر این عنصر استفاده شود، این attribute الزامی است.

## مثال‌ها

```html
<select>
  <optgroup label="Group 1">
    <option>Option 1.1</option>
  </optgroup>
  <optgroup label="Group 2">
    <option>Option 2.1</option>
    <option>Option 2.2</option>
  </optgroup>
  <optgroup label="Group 3" disabled>
    <option>Option 3.1</option>
    <option>Option 3.2</option>
    <option>Option 3.3</option>
  </optgroup>
</select>
```

### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا</th>
      <td>هیچ.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>صفر یا چند عنصر <code>&lt;option&gt;</code>. در عنصرهای <code>select</code> قابل شخصی‌سازی، عنصر <code>&lt;legend&gt;</code> به عنوان فرزند <code>&lt;optgroup&gt;</code> مجاز است.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>تگ شروع الزامی است. اگر بلافاصله بعد از این عنصر، عنصر <code>&lt;optgroup&gt;</code> دیگری بیاید، یا اگر عنصر والد محتوای بیشتری نداشته باشد، تگ پایانی اختیاری است.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>یک عنصر <code>&lt;select&gt;</code>.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"><code>group</code></a></td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLOptGroupElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- سایر عناصر مرتبط با فرم: `form`، `legend`، `label`، `button`، `select`، `datalist`، `option`، `fieldset`، `textarea`، `input`، `output`، `progress` و `meter`.
- [عناصر select قابل تنظیم](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select)