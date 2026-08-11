---
title: "<selectedcontent> HTML selected option display element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/selectedcontent"
translated_by: "n8n + AI"
---

عنصر **`<selectedcontent>`** در HTML داخل یک عنصر [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) استفاده می‌شود تا محتوای گزینهٔ انتخاب‌شده (selected option) را در اولین فرزند `<button>` خود نمایش دهد. این کار به شما امکان می‌دهد که تمام بخش‌های یک `<select>` را استایل کنید؛ به این قابلیت «selectهای قابل سفارشی‌سازی» (customizable selects) می‌گویند.

## ویژگی‌ها

این عنصر شامل [ویژگی‌های سراسری (global attributes)](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## توضیحات

شما از `<selectedcontent>` به عنوان تنها فرزند یک عنصر `<button>` استفاده می‌کنید. این `<button>` باید اولین فرزند `<select>` باشد. هر عنصر `<option>` که تنها فرزند معتبر دیگر `<select>` است، باید بعد از جفت `<button>` و `<selectedcontent>` بیاید.

```html
<select>
  <button>
    <selectedcontent></selectedcontent>
  </button>
  <option></option>
  ...
</select>
```

### نحوهٔ کار `<selectedcontent>` در پشت صحنه

عنصر `<selectedcontent>` حاوی یک کپی (clone) از محتوای گزینه‌ای است که در حال حاضر انتخاب شده است. مرورگر این کپی را با استفاده از متد `cloneNode()` ایجاد می‌کند. وقتی گزینهٔ انتخاب‌شده تغییر می‌کند (مثلاً در رویداد `change`)، محتوای `<selectedcontent>` با یک کپی از گزینهٔ جدید جایگزین می‌شود. آگاهی از این رفتار مهم است، به‌ویژه وقتی با محتوای پویا کار می‌کنید.

> **هشدار:**  
> از آنجایی که مرورگر `<selectedcontent>` را فقط زمانی به‌روزرسانی می‌کند که گزینهٔ انتخاب‌شده تغییر کند، هر تغییر پویایی که به محتوای گزینهٔ انتخاب‌شده بعد از رندر اولیهٔ `<select>` اعمال کنید، در `<selectedcontent>` کپی نخواهد شد. شما باید `<selectedcontent>` را به صورت دستی به‌روزرسانی کنید. اگر از فریم‌ورک‌های محبوب front-end JavaScript استفاده می‌کنید که عناصر `<option>` را بعد از رندر اولیه به صورت پویا تغییر می‌دهند، مراقب باشید؛ نتیجه ممکن است با آنچه در `<selectedcontent>` انتظار دارید مطابقت نداشته باشد.

### غیرفعال بودن (inertness) `<selectedcontent>`

به طور پیش‌فرض، هر `<button>` داخل یک `<select>` [غیرفعال (inert)](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/inert) است. در نتیجه، تمام محتوای داخل آن دکمه، از جمله `<selectedcontent>`، نیز غیرفعال است. این یعنی کاربران نمی‌توانند با محتوای داخل `<selectedcontent>` تعامل کنند یا آن را فوکوس کنند.

### استایل‌دهی به محتوای گزینهٔ انتخاب‌شده با CSS

می‌توانید محتوای عنصر `<option>` که در حال حاضر انتخاب شده را هدف قرار دهید و نحوهٔ نمایش آن را در دکمهٔ select استایل کنید. استایل‌دهی به دکمه تأثیری بر ظاهر محتوای `<option>` که کپی شده ندارد. این به شما امکان می‌دهد که ظاهر گزینهٔ انتخاب‌شده را در دکمه به صورت جداگانه از نحوهٔ نمایش آن در لیست کشویی سفارشی کنید.

برای مثال، عناصر `<option>` شما ممکن است شامل آیکون‌ها، تصاویر یا حتی ویدیوهایی باشند که در داخل لیست کشویی زیبا نمایش داده می‌شوند، اما ممکن است باعث افزایش اندازه دکمهٔ select، ظاهر نامرتب و تأثیر روی چیدمان اطراف شوند. با هدف قرار دادن محتوای داخل `<selectedcontent>` می‌توانید عناصری مانند تصاویر را در دکمه مخفی کنید، بدون اینکه روی نحوهٔ نمایش آن‌ها در لیست کشویی تأثیر بگذارید، همانطور که در قطعه کد زیر نشان داده شده است:

```css
selectedcontent img {
  display: none;
}
```

> **نکته:**  
> اگر عناصر `<button>` و `<selectedcontent>` داخل `<select>` قرار نگیرند، مرورگر به طور ضمنی یک دکمه برای نمایش محتوای گزینهٔ انتخاب‌شده ایجاد می‌کند. این دکمهٔ پیش‌فرض (fallback) را نمی‌توان با CSS با استفاده از انتخابگرهای `button` یا `selectedcontent` هدف قرار داد.

## مثال‌ها

### استایل‌دهی به select با استفاده از `<selectedcontent>`

در این مثال، یک `<select>` با استفاده از `<selectedcontent>` برای نمایش محتوای گزینهٔ انتخاب‌شده و یک `<button>` برای باز کردن لیست کشویی ایجاد می‌کنیم. گزینه‌ها شامل یک آیکون و متن هستند. آیکون در دکمه مخفی می‌شود اما در لیست کشویی نمایش داده می‌شود.

```html
<select>
  <button>
    <selectedcontent></selectedcontent>
  </button>
  <option value="home">🏠 خانه</option>
  <option value="work">💼 محل کار</option>
  <option value="school">🎓 مدرسه</option>
</select>
```

```css
/* استایل کلی دکمه */
select button {
  padding: 5px 10px;
  border: 1px solid #ccc;
  background: #f9f9f9;
  cursor: pointer;
}

/* مخفی کردن آیکون در دکمه */
selectedcontent img {
  display: none;
}
```

در اینجا، آیکون‌ها (🏠, 💼, 🎓) به صورت emoji هستند، اما اگر تصویر بودند، مخفی می‌شدند. می‌توانید این استایل‌ها را برای نیازهای خاص خود تنظیم کنید.

برای مشاهدهٔ یک مثال کامل از عنصر `<selectedcontent>`، به راهنمای [عناصر select قابل شخصی‌سازی](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select) مراجعه کنید.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا (Content categories)</a>
      </th>
      <td>هیچ</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>بازتاب‌دهندهٔ محتوای عنصر <code>&lt;option&gt;</code> انتخاب‌شده است.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هم تگ شروع و هم تگ پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>یک عنصر <code>&lt;button&gt;</code> که فرزند اول یک عنصر <code>&lt;select&gt;</code> باشد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ضمنی ARIA</th>
      <td>هیچ</td>
    </tr>
    <tr>
      <th scope="row">نقش‌های مجاز ARIA</th>
      <td>هیچ</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLSelectedContentElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- عنصر `<select>`
- عنصر `<option>`
- عنصر `<optgroup>`
- [عناصر select قابل شخصی‌سازی](/en-US/docs/Learn_web_development/Extensions/Forms/Customizable_select)