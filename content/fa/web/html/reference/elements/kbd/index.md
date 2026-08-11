---
title: "<kbd> HTML keyboard input element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/kbd"
translated_by: "n8n + AI"
---

```markdown
عنصر **`<kbd>`** [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML) یک بازهٔ متنی درون‌خطی را نشان می‌دهد که ورودی متنی کاربر را مشخص می‌کند؛ خواه از صفحه‌کلید، ورودی صوتی یا هر وسیلهٔ ورود متن دیگر. طبق قرارداد، user agent (عامل کاربر) به طور پیش‌فرض محتوای یک عنصر `<kbd>` را با فونت monospace خودش نمایش می‌دهد، هرچند استاندارد HTML این الزام را ندارد.

`<kbd>` را می‌توان به روش‌های مختلف با عنصر {{HTMLElement("samp")}} (خروجی نمونه) تودرتو کرد تا انواع ورودی یا خروجی را بر اساس نشانه‌های بصری نمایش دهد.

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های global (سراسری)](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

## نکات استفاده

می‌توان از عناصر دیگر در کنار `<kbd>` برای نمایش سناریوهای خاص‌تر استفاده کرد:

- قرار دادن یک `<kbd>` درون `<kbd>` دیگر، یک کلید واقعی یا واحد ورودی دیگر را به عنوان بخشی از یک ورودی بزرگ‌تر نشان می‌دهد. در ادامه، بخش [نمایش کلیدهای فشرده درون یک ورودی](#representing_keystrokes_within_an_input) را ببینید.
- قرار دادن یک `<kbd>` درون یک {{HTMLElement("samp")}}، ورودی‌ای را نشان می‌دهد که توسط سیستم به کاربر بازتاب شده است. برای مثال، بخش [ورودی بازتاب‌شده](#echoed_input) را ببینید.
- از طرف دیگر، قرار دادن یک `<samp>` درون یک `<kbd>`، ورودی‌ای را نشان می‌دهد که بر اساس متنی ارائه‌شده توسط سیستم است، مانند نام منوها و آیتم‌های منو، یا نام دکمه‌های نمایش‌داده‌شده روی صفحه. مثال زیر در بخش [نمایش گزینه‌های ورودی روی صفحه](#representing_onscreen_input_options) را ببینید.

> [!NOTE]
> می‌توانید یک استایل سفارشی برای override کردن انتخاب فونت پیش‌فرض مرورگر برای عنصر `<kbd>` تعریف کنید، هرچند ممکن است تنظیمات کاربر اولویت را داشته باشد.

## مثال‌ها

### مثال ساده

```html
<p>
  Use the command <kbd>help my-command</kbd> to view documentation for the
  command "my-command".
</p>
```

### نمایش کلیدهای فشرده درون یک ورودی

برای توصیف یک ورودی که از چند کلید تشکیل شده است، می‌توانید چند عنصر `<kbd>` را تودرتو کنید: یک `<kbd>` بیرونی که کل ورودی را نشان می‌دهد و هر کلید یا جزء ورودی درون `<kbd>` خودش قرار می‌گیرد.

#### بدون استایل

ابتدا ببینیم این کار در HTML ساده چگونه به نظر می‌رسد.

##### HTML

```html
<p>
  You can also create a new document using the
  <kbd><kbd>Ctrl</kbd>+<kbd>N</kbd></kbd> keyboard shortcut.
</p>
```

این کد، کل دنباله کلیدها را در یک `<kbd>` بیرونی می‌پیچد و سپس هر کلید را درون `<kbd>` خودش قرار می‌دهد تا اجزای دنباله مشخص شوند.

> [!NOTE]
> نیازی به انجام این همه تودرتوسازی نیست؛ می‌توانید با حذف `<kbd>` بیرونی، آن را ساده‌تر کنید. به عبارت دیگر، ساده‌سازی به `<kbd>Ctrl</kbd>+<kbd>N</kbd>` کاملاً معتبر است.
> با این حال، بسته به استایل‌شیت شما، ممکن است این نوع تودرتوسازی مفید باشد.

##### خروجی

خروجی بدون استایل‌شیت به این شکل است:

#### با استایل سفارشی

با افزودن کمی CSS، می‌توانیم آن را خواناتر کنیم.

##### CSS

یک selector جدید برای عناصر `<kbd>` تودرتو اضافه می‌کنیم، `kbd>kbd`، که هنگام نمایش کلیدهای صفحه‌کلید اعمال می‌شود:

```css
kbd {
  background-color: #eeeeee;
  border-radius: 3px;
  border: 1px solid #b4b4b4;
  box-shadow:
    0 1px 1px rgb(0 0 0 / 0.2),
    0 2px 0 0 rgb(255 255 255 / 0.7) inset;
  color: #333333;
  display: inline-block;
  font-size: 0.85em;
  font-weight: bold;
  line-height: 1;
  padding: 2px 4px;
  white-space: nowrap;
}
```

##### HTML

```html
<p>
  You can also create a new document using the
  <kbd><kbd>Ctrl</kbd>+<kbd>N</kbd></kbd> keyboard shortcut.
</p>
```

##### خروجی

خروجی با استایل سفارشی به این شکل است:

### ورودی بازتاب‌شده

با قرار دادن یک عنصر `<kbd>` درون یک عنصر {{HTMLElement("samp")}}، می‌توانید ورودی‌ای را نشان دهید که توسط سیستم به کاربر بازتاب شده است. برای مثال، کدی که یک دستور تکراری را بازتاب می‌دهد:

```html
<p>
  If you want to repeat the last command, use the
  <samp><kbd>!!</kbd></samp> command.
</p>
```

### نمایش گزینه‌های ورودی روی صفحه

با قرار دادن یک عنصر {{HTMLElement("samp")}} درون یک `<kbd>`، می‌توانید ورودی‌ای را نشان دهید که بر اساس متنی است که روی صفحه نمایش داده می‌شود، مانند نام منوها یا دکمه‌ها. برای مثال، می‌توانید از این روش برای نمایش نحوه انتخاب یک گزینه از منو استفاده کنید:

```html
<p>
  You can select the text in the input field using
  <kbd><samp>Edit</samp>→<samp>Select All</samp></kbd>.
</p>
```

```css
kbd > kbd {
  border-radius: 3px;
  padding: 1px 2px 0;
  border: 1px solid black;
}
```

##### HTML

سپس HTML را به‌روز می‌کنیم تا از این کلاس روی کلیدهای خروجی استفاده کند:

```html
<p>
  You can also create a new document by pressing the
  <kbd><kbd>Ctrl</kbd>+<kbd>N</kbd></kbd> shortcut.
</p>
```

##### نتیجه

نتیجه دقیقاً همان چیزی است که می‌خواهیم.

### ورودی منعکس‌شده

قرار دادن یک `<kbd>` درون یک `<samp>` نشان‌دهنده ورودی‌ای است که توسط سیستم به کاربر بازگردانده شده است.

```html
<p>
  If a syntax error occurs, the tool will output the initial command you typed
  for your review:
</p>
<blockquote>
  <samp><kbd>custom-git ad my-new-file.cpp</kbd></samp>
</blockquote>
```

#### نتیجه

### نمایش گزینه‌های ورودی روی صفحه

قرار دادن یک `<samp>` درون یک `<kbd>` نشان‌دهنده ورودی‌ای است که بر اساس متنی ارائه‌شده توسط سیستم (مانند نام منوها و آیتم‌های منو، یا نام دکمه‌های نمایش‌داده‌شده روی صفحه) انتخاب می‌شود.

مثلاً می‌توانید نحوه انتخاب گزینه «New Document» در منوی «File» را با HTML زیر توضیح دهید:

```html-nolint
<p>
  To create a new file, choose the <kbd><kbd><samp>File</samp></kbd>
  ⇒<kbd><samp>New Document</samp></kbd></kbd> menu option.
</p>

<p>
  Don't forget to click the <kbd><samp>OK</samp></kbd> button to confirm once
  you've entered the name of the new file.
</p>
```

در اینجا تودرتویی جالبی داریم. برای توضیح گزینه منو، کل ورودی درون یک `<kbd>` محصور شده است. سپس داخل آن، هم نام منو و هم نام آیتم منو درون `<kbd>` و `<samp>` قرار گرفته‌اند تا نشان دهند ورودی از یک ویجت روی صفحه انتخاب شده است.

#### نتیجه

## خلاصه فنی

| ویژگی | مقدار |
|-------|-------|
| [دسته‌بندی محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | [محتوای جریانی (Flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [محتوای عبارتی (Phrasing content)](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، محتوای قابل لمس. |
| محتوای مجاز | [محتوای عبارتی (Phrasing content)](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content). |
| حذف برچسب | هیچکدام، هر دو برچسب شروع و پایان اجباری هستند. |
| والدین مجاز | هر عنصری که [محتوای عبارتی (Phrasing content)](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد. |
| نقش ضمنی ARIA | [نقش متناظری وجود ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | هر کدام |
| رابط DOM | `HTMLElement` |

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- {{htmlelement("code")}}