---
title: "<i> HTML idiomatic text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/i"
translated_by: "n8n + AI"
---

# عنصر متن اصطلاحی `<i>` در HTML

عنصر **`<i>`** [HTML](/en-US/docs/Web/HTML) بخشی از متن را نشان می‌دهد که به دلایلی از متن عادی جدا می‌شود؛ مانند متن‌های اصطلاحی، اصطلاحات فنی، نام‌های طبقه‌بندی زیستی و موارد دیگر. در گذشته این عنصر با حروف ایتالیک نمایش داده می‌شد و همین موضوع منشأ نام‌گذاری `<i>` است.

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (Global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

- از عنصر `<i>` برای متنی استفاده کنید که به دلایل خوانایی از نثر عادی جدا می‌شود. این متن معمولاً معنای معنایی متفاوتی با متن اطراف دارد. موارد استفاده از `<i>` شامل این‌هاست:
  - لحن یا حالت جایگزین
  - نام‌های طبقه‌بندی زیستی (مانند جنس و گونه‌ی "_Homo sapiens_")
  - اصطلاحات ایدئوماتیک از زبان دیگر (مانند "_et cetera_")؛ این موارد باید ویژگی [`lang`](/en-US/docs/Web/HTML/Reference/Global_attributes/lang) را برای شناسایی زبان داشته باشند.
  - اصطلاحات فنی
  - نویسه‌گردانی‌ها (transliteration)
  - افکار درونی (مثل: "او با خودش فکر کرد، _این نویسنده اصلاً درباره چه چیزی حرف می‌زند؟_")
  - نام کشتی‌ها یا سفینه‌ها در نوشتارهای غربی (مثل: "آنها در اسکله به دنبال _Empress of the Galaxy_، کشتی‌ای که به آن منصوب شده بودند، گشتند.")

- در نسخه‌های قدیمی‌تر مشخصات HTML، عنصر `<i>` صرفاً یک عنصر نمایشی بود که متن را به صورت ایتالیک نشان می‌داد، مانند `<b>` که متن را ضخیم نشان می‌داد. این دیگر درست نیست؛ این تگ‌ها اکنون معنای معنایی را تعریف می‌کنند، نه ظاهر تایپوگرافی را. مرورگر معمولاً محتوای `<i>` را هنوز با حروف ایتالیک نمایش می‌دهد، اما طبق تعریف دیگر الزامی به این کار ندارد. برای نمایش متن به صورت ایتالیک، نویسندگان باید از ویژگی CSS `font-style` استفاده کنند.

- مطمئن شوید که متن مورد نظر واقعاً با عنصر دیگری مناسب‌تر نشان داده نمی‌شود.
  - از `<em>` برای تأکید (stress emphasis) استفاده کنید.
  - از `<strong>` برای اهمیت، جدیت یا فوریت استفاده کنید.
  - از `<mark>` برای نشان دادن مرتبط بودن استفاده کنید.
  - از `<cite>` برای نام یک اثر مانند کتاب، نمایشنامه یا آهنگ استفاده کنید.
  - از `<dfn>` برای تعریف یک اصطلاح استفاده کنید.

## مثال‌ها

این مثال نحوه استفاده از عنصر `<i>` برای علامت‌گذاری متنی به زبان دیگر را نشان می‌دهد.

```html
<p>
  The Latin phrase <i lang="la">Veni, vidi, vici</i> is often mentioned in
  music, art, and literature.
</p>
```

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >, محتوای محسوس (palpable content).
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
        >
        را بپذیرد.
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

- `<em>`
- سایر عناصر مورب: `<var>`، `<dfn>`، `<cite>`، `<address>`