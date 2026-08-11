---
title: "<label> HTML label element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/label"
translated_by: "n8n + AI"
---

# المان `<label>`

المان `<label>` در HTML نمایانگر یک برچسب (caption) برای یک آیتم در رابط کاربری است.

```html interactive-example
<div class="preference">
  <label for="cheese">I like cheese.</label>
  <input type="checkbox" name="cheese" id="cheese" />
</div>

<div class="preference">
  <label for="peas">I like peas.</label>
  <input type="checkbox" name="peas" id="peas" />
</div>
```

```css interactive-example
.preference {
  display: flex;
  justify-content: space-between;
  width: 60%;
  margin: 0.5rem;
}
```

## ویژگی‌ها

این المان شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- [`for`](/en-US/docs/Web/HTML/Reference/Attributes/for)
  - : مقدار این ویژگی، `id` کنترل فرم قابل برچسب‌گذاری (labelable) در همان سند است و `<label>` را به آن کنترل فرم [مرتبط می‌کند](#associating_a_label_with_a_form_control). توجه کنید که خاصیت بازتابی جاوااسکریپتی آن `htmlFor` است.

## نکات استفاده

### ارتباط دادن یک label با یک form control

اولین المانی در سند که ویژگی `id` آن با مقدار ویژگی `for` مطابقت داشته باشد، _کنترل برچسب‌خورده_ (labeled control) برای این المان `label` است — اگر آن المان واقعاً یک [المان قابل برچسب‌گذاری](/en-US/docs/Web/HTML/Guides/Content_categories#labelable) باشد. اگر _چنین_ عنصری قابل برچسب‌گذاری نباشد، ویژگی `for` هیچ اثری ندارد. اگر عناصر دیگری نیز در ادامه سند با آن مقدار `id` وجود داشته باشند، در نظر گرفته نمی‌شوند.

چند المان `<label>` می‌توانند با داشتن مقدار `for` یکسان، با همان کنترل فرم مرتبط شوند و در نتیجه آن کنترل فرم چند برچسب خواهد داشت.

ارتباط یک `<label>` با یک کنترل فرم، مانند `<input>` یا `<textarea>`، مزیت‌های مهمی دارد:

- متن برچسب فقط به‌صورت بصری با ورودی متن مربوطه مرتبط نیست؛ بلکه به‌صورت برنامه‌نویسی نیز با آن مرتبط است. یعنی برای مثال، screen reader وقتی کاربر روی ورودی فرم فوکوس دارد، برچسب را می‌خواند و در نتیجه درک اینکه چه داده‌هایی باید وارد شود برای کاربر فناوری کمکی آسان‌تر می‌شود.
- وقتی کاربر روی برچسب کلیک می‌کند یا آن را لمس می‌کند، مرورگر فوکوس را به ورودی مرتبط منتقل می‌کند (رویداد حاصل برای ورودی نیز صادر می‌شود). این ناحیه کلیک بزرگ‌تر برای فوکوس کردن ورودی، به هر کسی که می‌خواهد آن را فعال کند مزیت می‌دهد — از جمله کسانی که از دستگاه‌های صفحه لمسی استفاده می‌کنند.

دو روش برای مرتبط کردن `<label>` با یک کنترل فرم وجود دارد که معمولاً به آنها _ارتباط صریح_ (explicit) و _ارتباط ضمنی_ (implicit) گفته می‌شود.

برای ارتباط صریح بین یک المان `<label>` و یک المان `<input>`، ابتدا باید ویژگی `id` را به المان `<input>` اضافه کنید. سپس ویژگی `for` را به المان `<label>` اضافه کنید، به طوری که مقدار `for` با `id` در المان `<input>` یکسان باشد.

```html
<label for="peas">I like peas.</label>
<input type="checkbox" name="peas" id="peas" />
```

از طرف دیگر، می‌توانید `<input>` را مستقیماً داخل `<label>` قرار دهید؛ در این صورت ویژگی‌های `for` و `id` لازم نیستند، زیرا ارتباط به‌صورت ضمنی برقرار می‌شود:

```html
<label>
  I like peas.
  <input type="checkbox" name="peas" />
</label>
```

> [!NOTE]
> یک المان `<label>` می‌تواند هم ویژگی `for` داشته باشد و هم یک کنترل داخلی، تا زمانی که ویژگی `for` به همان کنترل داخلی اشاره کند.

این دو روش معادل هستند، اما چند نکته وجود دارد:

اگرچه ترکیب‌های رایج مرورگر و screen reader از implicit association پشتیبانی می‌کنند، اما همه فناوری‌های کمکی این کار را نمی‌کنند.

بسته به طراحی شما، نوع association ممکن است روی قابلیت استایل‌دهی تأثیر بگذارد. قرار دادن `<label>` و کنترل فرم به صورت خواهر (sibling) به جای والد-فرزندی باعث می‌شود که آن‌ها جعبه‌های مجزای مجاور باشند و امکان چیدمان سفارشی‌تر مانند هم‌تراز کردن با روش‌های grid یا flex را فراهم کند.

ارتباط صریح (explicit association) نیاز دارد که کنترل فرم یک `id` داشته باشد که باید در کل سند یکتا باشد. این کار مخصوصاً در برنامه‌های کامپوننتی سخت است. فریمورک‌ها اغلب راه‌حل‌های خود را ارائه می‌دهند، مثل [`useId()`](https://react.dev/reference/react/useId) در React، اما همچنان برای درست کار کردن به هماهنگی اضافی نیاز دارد.

به طور کلی، توصیه می‌کنیم از explicit association با attribute `for` استفاده کنید تا سازگاری با ابزارهای خارجی و فناوری‌های کمکی تضمین شود. در واقع، می‌توانید همزمان عنصر را nesting کنید و هم `id`/`for` را ارائه دهید تا حداکثر سازگاری را داشته باشید.

کنترل فرمی که یک label آن را برچسب‌گذاری می‌کند، _labeled control_ (کنترل برچسب‌گذاری‌شده) عنصر label نامیده می‌شود. چندین label می‌توانند با یک کنترل فرم مرتبط شوند:

```html
<label for="username">Enter your username:</label>
<input id="username" name="username" type="text" />
<label for="username">Forgot your username?</label>
```

عناصری که می‌توانند با یک `<label>` مرتبط شوند عبارتند از `<button>`، `<input>` (به جز `type="hidden"`)، `<meter>`، `<output>`، `<progress>`، `<select>` و `<textarea>`.

## دسترسی‌پذیری

### محتوای تعاملی (Interactive content)

به غیر از کنترل فرمی که به صورت implicit با label مرتبط شده، عناصر تعاملی دیگری مثل anchor یا دکمه را داخل `<label>` قرار ندهید. این کار باعث می‌شود کاربر نتواند به راحتی ورودی فرم مرتبط با label را فعال کند.

**❌ نادرست:**

```html example-bad
<label for="tac">
  <input id="tac" type="checkbox" name="terms-and-conditions" />
  I agree to the <a href="terms-and-conditions.html">Terms and Conditions</a>
</label>
```

**✅ درست:**

```html example-good
<p>
  <a href="terms-and-conditions.html">Read our Terms and Conditions</a>
</p>
<label for="tac">
  <input id="tac" type="checkbox" name="terms-and-conditions" />
  I agree to the Terms and Conditions
</label>
```

> [!نکته]
> خوب است که هرگونه زمینه لازم، مثل لینک به شرایط و ضوابط، قبل از کنترل فرم قرار داده شود تا کاربر بتواند قبل از تعامل با کنترل، آن را بخواند.

### عنوان‌ها (Headings)

قرار دادن [عناصر heading](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) درون `<label>` با بسیاری از فناوری‌های کمکی تداخل دارد، زیرا headingها معمولاً به عنوان [یک راهنمای ناوبری](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements#navigation) استفاده می‌شوند. اگر نیاز است متن label به صورت بصری تغییر کند، از کلاس‌های CSS روی خود عنصر `<label>` استفاده کنید.

اگر یک فرم یا بخشی از آن نیاز به عنوان دارد، از عنصر `<legend>` درون `<fieldset>` استفاده کنید.

**❌ نادرست:**

```html example-bad
<label for="your-name">
  <h3>Your name</h3>
  <input id="your-name" name="your-name" type="text" />
</label>
```

**✅ درست:**

```html example-good
<label class="large-label" for="your-name">
  Your name
  <input id="your-name" name="your-name" type="text" />
</label>
```

### دکمه‌ها (Buttons)

یک عنصر `<input>` با `type="button"` و یک `value` معتبر نیازی به label ندارد. این کار ممکن است نحوه تفسیر ورودی دکمه توسط فناوری کمکی را مختل کند. همین مورد برای عنصر `<button>` نیز صدق می‌کند.

## مثال‌ها

### تعریف یک label ضمنی

```html
<label>Click me <input type="text" /></label>
```

### تعریف label صریح با attribute «for»

برای اتصال صریح یک `<label>` به عنصر کنترلی، از attribute «for» استفاده می‌شود. مقدار این attribute باید با مقدار `id` عنصر کنترلی یکسان باشد:

```html
<label for="username">Click me to focus on the input field</label>
<input type="text" id="username" />
```

## خلاصه فنی

| | |
|---|---|
| **دسته‌های محتوا** | [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، [interactive content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content)، [form-associated element](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content)، palpable content |
| **محتوای مجاز** | [Phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)؛ اما هیچ عنصر فرزندِ `label` مجاز نیست. هیچ عنصر [labelable](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#labelable) دیگری به‌جز کنترلِ برچسب‌خورده هم مجاز نیست. |
| **حذف تگ** | هیچ‌کدام؛ تگ شروع و پایان هر دو الزامی هستند. |
| **والدهای مجاز** | هر عنصری که [phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد. |
| **نقش ARIA ضمنی** | [هیچ نقش متناظری وجود ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| **نقش‌های ARIA مجاز** | هیچ `role` مجاز نیست |
| **رابط DOM** | `HTMLLabelElement` |

## مشخصات

جدول مشخصات این عنصر به‌صورت خودکار از منابع رسمی پر می‌شود.

## سازگاری مرورگرها

جدول سازگاری مرورگرهای این عنصر به‌صورت خودکار نمایش داده می‌شود.