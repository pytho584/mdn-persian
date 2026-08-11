---
title: "<samp> HTML sample output element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/samp"
translated_by: "n8n + AI"
---

عنصر `<samp>` HTML برای نمایش خروجی نمونه (یا نقل‌قول‌شده) از یک برنامه‌ی کامپیوتری به کار می‌رود. محتوای آن معمولاً با فونت تک‌فاصله (monospaced) پیش‌فرض مرورگر (مانند Courier یا Lucida Console) نمایش داده می‌شود.

```html interactive-example
<p>I was trying to boot my computer, but I got this hilarious message:</p>

<p>
  <samp>Keyboard not found <br />Press F1 to continue</samp>
</p>
```

```css interactive-example
samp {
  font-weight: bold;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

می‌توانید با یک قانون CSS، فونت پیش‌فرض مرورگر را برای عنصر `<samp>` تغییر دهید؛ اما ممکن است تنظیمات مرورگر بر CSS شما اولویت داشته باشد.

کد CSS برای تغییر فونت پیش‌فرض به این شکل است:

```css
samp {
  font-family: "Courier";
}
```

> [!NOTE]
> اگر به عنصری نیاز دارید که خروجی تولیدشده توسط کد JavaScript سایت یا اپلیکیشنتان را نمایش دهد، بهتر است از عنصر `<output>` استفاده کنید.

## مثال‌ها

### مثال ساده

در این مثال، یک پاراگراف شامل نمونه‌ای از خروجی یک برنامه است.

```html
<p>
  When the process is complete, the utility will output the text
  <samp>Scan complete. Found <em>N</em> results.</samp> You can then proceed to
  the next step.
</p>
```

#### نتیجه

### خروجی نمونه شامل ورودی کاربر

می‌توانید عنصر `<kbd>` را درون یک بلوک `<samp>` قرار دهید تا مثالی از خروجی همراه با متنی که کاربر وارد کرده است ارائه دهید. برای مثال، متنی که یک نشست ترمینال لینوکس (یا مک) را نشان می‌دهد:

#### HTML

```html
<pre>
<samp><span class="prompt">mike@interwebz:~$</span> <kbd>md5 -s "Hello world"</kbd>
MD5 ("Hello world") = 3e25960a79dbc69b674cd4ec67a72c62

<span class="prompt">mike@interwebz:~$</span> <span class="cursor">█</span></samp></pre>
```

توجه کنید که از `<span>` برای شخصی‌سازی ظاهر بخش‌هایی از متن نمونه مانند پرامپت شل (shell prompt) و مکان‌نما (cursor) استفاده شده است. همچنین `<kbd>` نشان‌دهنده‌ی دستوری است که کاربر در پرامپت تایپ کرده است.

#### CSS

CSS مورد نظر برای رسیدن به ظاهر بالا:

```css
.prompt {
  color: #bb0000;
}

samp > kbd {
  font-weight: bold;
}

.cursor {
  color: #0000bb;
}
```

این کد به پرامپت و مکان‌نما رنگ‌های ملایمی می‌دهد و ورودی صفحه‌کلید را درون متن نمونه پررنگ می‌کند.

#### نتیجه

خروجی نهایی به این شکل خواهد بود:

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌بندی محتوا</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ؛ هم تگ شروع و هم تگ پایانی اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        > را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ضمنی ARIA</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role"
            >generic</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های مجاز ARIA</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- عناصر مرتبط: `kbd`، `code`، `pre`
- عنصر `output`: ظرفی برای خروجی تولیدشده توسط اسکریپت