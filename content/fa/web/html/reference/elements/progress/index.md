---
title: "<progress> HTML progress indicator element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/progress"
translated_by: "n8n + AI"
---

عنصر `<progress>` در HTML، نشانگری برای نمایش میزان پیشرفت انجام یک کار است؛ معمولاً به شکل نوار پیشرفت (progress bar) نمایش داده میشود.

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- [`max`](/en-US/docs/Web/HTML/Reference/Attributes/max)
  - این ویژگی مشخص می‌کند که کار موردنظر در عنصر `progress` به چه میزان تلاش نیاز دارد. اگر `max` وجود داشته باشد، باید مقداری بزرگ‌تر از `0` و یک عدد اعشاری معتبر باشد. مقدار پیش‌فرض `1` است.
- `value`
  - این ویژگی مشخص می‌کند چه مقدار از کار تکمیل شده است. مقدار آن باید یک عدد اعشاری معتبر بین `0` و `max` باشد، یا اگر از `max` استفاده نشده باشد، بین `0` و `1`. اگر ویژگی `value` وجود نداشته باشد، نوار پیشرفت نامعین (indeterminate) است؛ یعنی فعالیتی در حال انجام است بدون اینکه مشخص باشد چقدر طول می‌کشد.

> [!NOTE]
> برخلاف عنصر `<meter>`، حداقل مقدار همیشه `0` است و ویژگی `min` برای عنصر `<progress>` مجاز نیست.

> [!NOTE]
> شبه‌کلاس `:indeterminate` را می‌توان برای تطبیق با نوارهای پیشرفت نامعین استفاده کرد. برای تغییر نوار پیشرفت به حالت نامعین پس از مقداردهی، باید ویژگی `value` را با `element.removeAttribute('value')` حذف کنید.

## دسترس‌پذیری

### برچسب‌گذاری

در بیشتر موارد باید هنگام استفاده از `<progress>` یک برچسب قابل‌دسترس (accessible label) فراهم کنید. اگرچه می‌توانید مانند هر عنصر دیگری با `role="progressbar"` از ویژگی‌های استاندارد برچسب‌گذاری ARIA یعنی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) یا [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده کنید، در `<progress>` می‌توانید به‌جای آن از عنصر `<label>` هم استفاده کنید.

> [!NOTE]
> متنی که بین تگ‌های عنصر قرار می‌گیرد برچسب قابل‌دسترس محسوب نمی‌شود و فقط به‌عنوان جایگزین (fallback) برای مرورگرهای قدیمی که این عنصر را پشتیبانی نمی‌کنند توصیه می‌شود.

#### مثال‌ها

```html
<label>
  Uploading Document: <progress value="70" max="100">70 %</progress>
</label>

<!-- OR -->
<br />

<label for="progress-bar">Uploading Document</label>
<progress id="progress-bar" value="70" max="100">70 %</progress>
```

#### نتیجه

### توصیف یک ناحیه خاص

اگر عنصر `<progress>` پیشرفت بارگذاری بخشی از صفحه را توصیف می‌کند، از [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) برای اشاره به وضعیت استفاده کنید و [`aria-busy="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy) را روی بخشی که در حال به‌روزرسانی است قرار دهید؛ سپس وقتی بارگذاری تمام شد، ویژگی `aria-busy` را حذف کنید.

#### مثال‌ها

```html
<div aria-busy="true" aria-describedby="progress-bar">
  <!-- content is for this region is loading -->
</div>

<!-- ... -->

<progress id="progress-bar" aria-label="Content loading…"></progress>
```

#### نتیجه

## مثال‌ها

```html
<progress value="70" max="100">70 %</progress>
```

### نتیجه

## خلاصه فنی

| ویژگی | توضیحات |
|-------|----------|
| [دسته‌بندی محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، labelable content، [Palpable content](/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) |
| محتوای مجاز | [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) ولی نباید هیچ عنصر `<progress>` در میان فرزندان آن وجود داشته باشد. |
| حذف تگ | هیچکدام؛ هر دو تگ شروع و پایان اجباری هستند. |
| والدین مجاز | هر عنصری که [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد. |
| نقش ARIA ضمنی | [`progressbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/progressbar_role) |
| نقش‌های ARIA مجاز | هیچ نقشی مجاز نیست |
| رابط DOM | [`HTMLProgressElement`](/en-US/docs/Web/API/HTMLProgressElement) |

## همچنین ببینید

- [ایجاد کنترل‌های فرم عمودی](/en-US/docs/Web/CSS/Guides/Writing_modes/Vertical_controls)
- `<meter>`
- `:indeterminate`
- `-moz-orient`
- `::-moz-progress-bar`
- `::-webkit-progress-bar`
- `::-webkit-progress-value`
- `::-webkit-progress-inner-element`