---
title: "<input type=\"reset\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/reset"
translated_by: "n8n + AI"
---

عناصر `<input>` از نوع **`reset`** به صورت دکمه نمایش داده می‌شوند و یک event handler پیش‌فرض برای رویداد {{domxref("Element/click_event", "click")}} دارند که تمام ورودی‌های فرم را به مقادیر اولیه‌شان بازنشانی (reset) می‌کند.

> [!NOTE]
> معمولاً بهتر است از قرار دادن دکمه‌های بازنشانی در فرم‌ها خودداری کنید. این دکمه‌ها به ندرت مفید هستند و بیشتر باعث می‌شوند کاربرانی که به‌اشتباه روی آن‌ها کلیک می‌کنند (اغلب هنگام تلاش برای کلیک روی [دکمه ارسال](/en-US/docs/Web/HTML/Reference/Elements/input/submit)) ناامید شوند.

## مقدار (Value)

ویژگی [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) یک عنصر `<input type="reset">` شامل یک رشته است که به عنوان برچسب دکمه استفاده می‌شود و یک {{glossary("accessible description", "توضیح دسترس‌پذیر")}} برای دکمه فراهم می‌کند. دکمه‌هایی مانند `reset` در غیر این صورت مقدار دیگری ندارند.

### تنظیم ویژگی value

```html
<input type="reset" value="Reset the form" />
```

### حذف ویژگی value

اگر `value` را مشخص نکنید، دکمه‌ای با برچسب پیش‌فرض (معمولاً "Reset" اما بسته به {{Glossary("user agent", "مرورگر")}} متفاوت است) دریافت می‌کنید:

```html
<input type="reset" />
```

## استفاده از دکمه‌های بازنشانی

دکمه‌های `<input type="reset">` برای بازنشانی فرم‌ها استفاده می‌شوند. اگر می‌خواهید یک دکمه سفارشی ایجاد کنید و رفتار آن را با JavaScript سفارشی‌سازی کنید، باید از [`<input type="button">`](/en-US/docs/Web/HTML/Reference/Elements/input/button) یا بهتر از آن، از عنصر {{htmlelement("button")}} استفاده کنید.

### یک دکمه بازنشانی ساده

ابتدا یک دکمه بازنشانی ساده می‌سازیم:

```html
<form>
  <div>
    <label for="example">متن نمونه وارد کنید</label>
    <input id="example" type="text" />
  </div>
  <div>
    <input type="reset" value="بازنشانی فرم" />
  </div>
</form>
```

می‌توانید مقداری متن در فیلد متنی وارد کنید و سپس دکمه بازنشانی را فشار دهید.

### افزودن میان‌بر صفحه‌کلید برای بازنشانی

برای افزودن میان‌بر صفحه‌کلید به یک دکمه بازنشانی — درست مانند هر {{HTMLElement("input")}} دیگری که منطقی باشد — از ویژگی سراسری [`accesskey`](/en-US/docs/Web/HTML/Reference/Global_attributes/accesskey) استفاده می‌کنید.

در این مثال، <kbd>r</kbd> به عنوان کلید دسترسی مشخص شده است (باید <kbd>r</kbd> را به همراه کلیدهای اصلاح‌کننده خاص مرورگر/سیستم‌عامل خود فشار دهید؛ برای لیست مفیدی از این کلیدها به [`accesskey`](/en-US/docs/Web/HTML/Reference/Global_attributes/accesskey) مراجعه کنید).

```html
<form>
  <div>
    <label for="example">متن نمونه وارد کنید</label>
    <input id="example" type="text" />
  </div>
  <div>
    <input type="reset" value="بازنشانی فرم" accesskey="r" />
  </div>
</form>
```

مشکل مثال بالا این است که کاربر راهی برای دانستن کلید دسترسی (access key) ندارد! این مسئله به‌ویژه زمانی جدی‌تر می‌شود که modifierها معمولاً غیراستاندارد هستند تا از تداخل جلوگیری کنند. هنگام ساخت یک وب‌سایت، حتماً این اطلاعات را به‌گونه‌ای ارائه دهید که با طراحی سایت تداخل نداشته باشد (مثلاً با ارائه یک لینک قابل دسترسی که به اطلاعات مربوط به کلیدهای دسترسی سایت اشاره می‌کند). افزودن tooltip به دکمه (با استفاده از attribute [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title)) نیز می‌تواند کمک کند، اگرچه راه‌حل کاملی برای دسترسی‌پذیری نیست.

### غیرفعال کردن و فعال کردن دکمه reset

برای غیرفعال کردن دکمه reset، attribute [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/input#disabled) را روی آن تنظیم کنید، مانند زیر:

```html
<input type="reset" value="Disabled" disabled />
```

می‌توانید دکمه‌ها را در زمان اجرا با تنظیم `disabled` به `true` یا `false` فعال یا غیرفعال کنید؛ در JavaScript این کار به صورت `btn.disabled = true` یا `btn.disabled = false` انجام می‌شود.

> [!NOTE]
> برای ایده‌های بیشتر درباره فعال و غیرفعال کردن دکمه‌ها، صفحه [`<input type="button">`](/en-US/docs/Web/HTML/Reference/Elements/input/button#disabling_and_enabling_a_button) را ببینید.

## اعتبارسنجی

دکمه‌ها در اعتبارسنجی محدودیت (constraint validation) شرکت نمی‌کنند؛ زیرا مقدار واقعی برای محدود شدن ندارند.

## مثال‌ها

در بالا مثال‌های پایه‌ای آورده‌ایم. واقعاً چیز بیشتری برای گفتن درباره دکمه‌های reset وجود ندارد.

## خلاصه فنی

| ویژگی | توضیحات |
| --- | --- |
| **Value** | یک رشته که به عنوان برچسب دکمه استفاده می‌شود |
| **Events** | `click` |
| **ویژگی‌های رایج پشتیبانی‌شده** | [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#type) و [`value`](/en-US/docs/Web/HTML/Reference/Elements/input#value) |
| **IDL attributes** | `value` |
| **DOM interface** | `HTMLInputElement` |
| **نقش ARIA ضمنی** | [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) |

## مشخصات

(مشخصات - حذف شده)

## سازگاری با مرورگر

(سازگاری با مرورگر - حذف شده)

## همچنین ببینید

- `<input>` و رابط `HTMLInputElement` که آن را پیاده‌سازی می‌کند.
- [فرم‌ها و دکمه‌ها](/en-US/docs/Learn_web_development/Extensions/Forms/Basic_native_form_controls#actual_buttons)
- [فرم‌های HTML](/en-US/docs/Learn_web_development/Extensions/Forms)
- عنصر `<button>`