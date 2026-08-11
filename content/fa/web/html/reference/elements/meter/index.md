---
title: "<meter> HTML meter element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meter"
translated_by: "n8n + AI"
---

المان `<meter>` در HTML، یک مقدار عددی (scalar) را در یک بازهٔ مشخص یا یک مقدار کسری (fractional) نمایش می‌دهد.

## ویژگی‌ها (Attributes)

این المان شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `value`
  - : مقدار عددی فعلی. این مقدار باید بین حداقل و حداکثر (ویژگی‌های `min` و `max`) باشد، اگر آن‌ها مشخص شده باشند. اگر مشخص نشده یا نادرست باشد، مقدار `0` است. اگر مشخص شده باشد اما در بازه‌ای که توسط `min` و `max` تعیین شده نباشد، مقدار معادل نزدیک‌ترین حد بازه خواهد بود.

    > [!NOTE]
    > مگر اینکه مقدار `value` بین `0` و `1` (شامل این دو) باشد، باید با استفاده از `min` و `max` یک بازه تعریف کنید تا مقدار `value` درون آن قرار گیرد.

- [`min`](/en-US/docs/Web/HTML/Reference/Attributes/min)
  - : کران پایین عددی بازه‌ی اندازه‌گیری. اگر مشخص شده باشد، باید از مقدار حداکثر (`max`) کوچک‌تر باشد. اگر مشخص نشود، مقدار پیش‌فرض `0` است.
- [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)
  - : کران بالای عددی بازه‌ی اندازه‌گیری. اگر مشخص شده باشد، باید از مقدار حداقل (`min`) بزرگ‌تر باشد. اگر مشخص نشود، مقدار پیش‌فرض `1` است.
- `low`
  - : کران بالای عددی بخش پایینی بازه. این مقدار باید از `min` بزرگ‌تر باشد و همچنین از `high` و `max` (در صورت مشخص بودن) کوچک‌تر باشد. اگر مشخص نشود یا از `min` کوچک‌تر باشد، `low` برابر با `min` در نظر گرفته می‌شود.
- `high`
  - : کران پایین عددی بخش بالایی بازه. این مقدار باید از `max` کوچک‌تر باشد و همچنین از `low` و `min` (در صورت مشخص بودن) بزرگ‌تر باشد. اگر مشخص نشود یا از `max` بزرگ‌تر باشد، `high` برابر با `max` در نظر گرفته می‌شود.
- `optimum`
  - : مقدار عددی بهینه را مشخص می‌کند. باید درون بازه‌ای که توسط `min` و `max` تعریف شده است قرار گیرد. وقتی همراه با `low` و `high` استفاده می‌شود، مشخص می‌کند کدام بخش از بازه ترجیح داده می‌شود. مثلاً اگر بین `min` و `low` باشد، بخش پایینی ترجیح داده می‌شود. مرورگر ممکن است نوار meter را بسته به اینکه مقدار کمتر یا مساوی `optimum` باشد، به رنگ متفاوتی نمایش دهد.

| ویژگی | مقدار |
| --- | --- |
| [دسته‌بندی محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، labelable content، palpable content |
| محتوای مجاز | [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، اما هیچ عنصر `<meter>` نباید در میان فرزندان آن باشد. |
| حذف تگ | هیچ؛ هم تگ آغازین و هم تگ پایانی الزامی هستند. |
| والدهای مجاز | هر عنصری که [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد. |
| نقش ضمنی ARIA | [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents) |
| نقش‌های مجاز ARIA | هیچ `role` ای مجاز نیست. |
| DOM interface | `HTMLMeterElement` |

## جستارهای وابسته

- [ایجاد کنترل‌های فرم عمودی](/en-US/docs/Web/CSS/Guides/Writing_modes/Vertical_controls)
- `<progress>`
- `::-webkit-meter-bar`، `::-webkit-meter-inner-element`، `::-webkit-meter-even-less-good-value`، `::-webkit-meter-optimum-value`، `::-webkit-meter-suboptimum-value`: شبه‌المان‌های غیراستاندارد