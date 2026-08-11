---
title: "<option> HTML option element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/option"
translated_by: "n8n + AI"
---

عنصر `<option>` در HTML برای تعریف یک گزینه درون یک `<select>`، `<optgroup>` یا `<datalist>` استفاده می‌شود. بنابراین `<option>` می‌تواند آیتم‌های منو در پنجره‌های بازشو و سایر لیست‌های آیتم‌ها در یک سند HTML را نمایش دهد.

مثال تعاملی

```html interactive-example
<label for="pet-select">Choose a pet:</label>

<select id="pet-select">
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

## Attributes

این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) نیز می‌شود.

- `disabled`
  - : اگر این Boolean attribute تنظیم شده باشد، این گزینه قابل انتخاب نیست. معمولاً مرورگرها چنین کنترلی را به صورت خاکستری نشان می‌دهند و هیچ رویداد مرورگری مانند کلیک ماوس یا فوکس دریافت نمی‌کند. اگر این attribute تنظیم نشده باشد، عنصر همچنان ممکن است غیرفعال شود اگر یکی از اجدادش یک `<optgroup>` غیرفعال باشد.
- `label`
  - : این attribute متنی برای برچسبی است که معنی گزینه را نشان می‌دهد. اگر attribute `label` تعریف نشده باشد، مقدار آن برابر با محتوای متنی عنصر خواهد بود.
- `selected`
  - : اگر وجود داشته باشد، این Boolean attribute نشان می‌دهد که گزینه به صورت پیش‌فرض انتخاب شده است. اگر عنصر `<option>` فرزند یک `<select>` باشد که attribute `multiple` آن تنظیم نشده است، فقط یک `<option>` از آن `<select>` می‌تواند attribute `selected` را داشته باشد.
- `value`
  - : محتوای این attribute مقداری است که در صورت انتخاب شدن این گزینه، همراه با فرم ارسال می‌شود. اگر این attribute حذف شود، مقدار از محتوای متنی عنصر option گرفته می‌شود.

## Styling with CSS

استایل‌دهی به عناصر `<option>` از نظر تاریخی بسیار محدود بوده است. [Customizable select elements](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select) ویژگی‌های جدیدتری را توضیح می‌دهد که امکان شخصی‌سازی کامل آن‌ها را مانند هر عنصر معمولی DOM فراهم می‌کند.

### Legacy option styling

در مرورگرهایی که از ویژگی‌های مدرن شخصی‌سازی پشتیبانی نمی‌کنند (یا در پروژه‌های قدیمی که نمی‌توان از آن‌ها استفاده کرد)، استایل‌های موجود برای عناصر `<option>` به مرورگر و سیستم‌عامل بستگی دارد. بسته به سیستم‌عامل، `font-size` `<select>` والد در Firefox و Chromium رعایت می‌شود. Chromium ممکن است علاوه بر این اجازه تنظیم `color`، `background-color`، `font-family`، `font-variant` و `text-align` را بدهد.

جزئیات بیشتر درباره استایل‌دهی قدیمی `<option>` را می‌توانید در [our guide to advanced form styling](/en-US/docs/Learn_web_development/Extensions/Forms/Advanced_form_styling) پیدا کنید.

## Examples

برای مثال‌ها به `<select>` مراجعه کنید.

```markdown
| [دسته‌بندی محتوا (Content categories)](/en-US/docs/Web/HTML/Guides/Content_categories) | هیچ‌کدام. |
| محتوای مجاز (Permitted content) | در عناصر سنتی `<select>`، فقط محتوای متنی مجاز است، و احتمالاً شامل کاراکترهای escape شده (مانند `&eacute;`) نیز هست. در [عناصر select قابل تنظیم](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select)، عناصر `<option>` می‌توانند هر محتوای دلخواهی داشته باشند. |
| حذف تگ (Tag omission) | تگ شروع اجباری است. تگ پایان اختیاری است اگر این عنصر بلافاصله بعد از یک عنصر `<option>` دیگر یا یک `<optgroup>` بیاید، یا اگر عنصر والد محتوای دیگری نداشته باشد. |
| والدهای مجاز (Permitted parents) | یک عنصر `<select>`، `<optgroup>` یا `<datalist>`. |
| نقش ARIA ضمنی (Implicit ARIA role) | [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role) |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | هیچ `role` مجاز نیست. |
| رابط DOM (DOM interface) | [`HTMLOptionElement`](/en-US/docs/Web/API/HTMLOptionElement) |

## مشخصات

## سازگاری با مرورگر

## جستارهای وابسته

- سایر عناصر مرتبط با فرم: [`<form>`](/en-US/docs/Web/HTML/Element/form)، [`<legend>`](/en-US/docs/Web/HTML/Element/legend)، [`<label>`](/en-US/docs/Web/HTML/Element/label)، [`<button>`](/en-US/docs/Web/HTML/Element/button)، [`<select>`](/en-US/docs/Web/HTML/Element/select)، [`<datalist>`](/en-US/docs/Web/HTML/Element/datalist)، [`<optgroup>`](/en-US/docs/Web/HTML/Element/optgroup)، [`<fieldset>`](/en-US/docs/Web/HTML/Element/fieldset)، [`<textarea>`](/en-US/docs/Web/HTML/Element/textarea)، [`<input>`](/en-US/docs/Web/HTML/Element/input)، [`<output>`](/en-US/docs/Web/HTML/Element/output)، [`<progress>`](/en-US/docs/Web/HTML/Element/progress)، [`<meter>`](/en-US/docs/Web/HTML/Element/meter).
- [عناصر select قابل تنظیم](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select)
```