---
title: "contenteditable HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable"
translated_by: "n8n + AI"
---

ویژگی سراسری `contenteditable` یک ویژگی شمارشی (enumerated) است که مشخص می‌کند کاربر می‌تواند محتوای عنصر را ویرایش کند یا نه. اگر قابل ویرایش باشد، مرورگر ویجت عنصر را طوری تغییر می‌دهد که ویرایش امکان‌پذیر شود.

## مقدار

ویژگی باید یکی از مقادیر زیر را بگیرد:

- `true` یا یک _رشتهٔ خالی_ — یعنی عنصر قابل ویرایش است.
- `false` — یعنی عنصر قابل ویرایش نیست.
- `plaintext-only` — یعنی فقط متن خام عنصر قابل ویرایش است، اما قالب‌بندی rich text غیرفعال است.

اگر ویژگی بدون مقدار داده شود، مثلاً `<label contenteditable>Example Label</label>`، مقدار آن به‌عنوان یک رشتهٔ خالی در نظر گرفته می‌شود.

اگر این ویژگی وجود نداشته باشد یا مقدارش نامعتبر باشد، مقدار آن از عنصر والد _به ارث می‌رسد_؛ بنابراین اگر عنصر والد قابل ویرایش باشد، این عنصر هم قابل ویرایش خواهد بود.

توجه کن که اگرچه مقادیر مجاز شامل `true` و `false` هستند، این ویژگی یک ویژگی _شمارشی_ است، نه _بولی_.

می‌توانی با استفاده از ویژگی CSS {{cssxref("caret-color")}} رنگ caret (محل درج متن) را تعیین کنی.

عناصری که با استفاده از `contenteditable` قابل ویرایش و در نتیجه تعاملی می‌شوند، قابلیت focus شدن دارند. آن‌ها در ناوبری متوالی صفحه‌کلید (sequential keyboard navigation) شرکت می‌کنند. اما عناصری که ویژگی `contenteditable` دارند و درون عناصر `contenteditable` دیگری تودرتو شده‌اند، به طور پیش‌فرض به ترتیب tabbing اضافه نمی‌شوند. می‌توانی با تعیین مقدار `tabindex` (مثلاً `tabindex="0"`) این عناصر تودرتو را به ترتیب ناوبری صفحه‌کلید اضافه کنی.

اگر محتوا درون یک عنصر با `contenteditable="true"` چسبانده (paste) شود، تمام قالب‌بندی‌های آن حفظ می‌شود. اگر محتوا درون یک عنصر با `contenteditable="plaintext-only"` چسبانده شود، همهٔ قالب‌بندی‌ها حذف می‌شود.

## مثال‌ها

### چسباندن محتوا درون contenteditable

این مثال دو عنصر {{HTMLElement("div")}} با `contenteditable` دارد: اولی با مقدار `true` و دومی با مقدار `plaintext-only`. محتوای زیر را کپی کن و درون هر `div` بچسبان تا تفاوت آن‌ها را ببینی.

#### HTML

```html hidden
<h2>محتوا برای کپی کردن</h2>
<p class="instructions">
  تمام متن بلوک زیر را کپی کرده و درون هر یک از بلوک‌های contenteditable
  بچسبانید تا نتایج را مقایسه کنید.
</p>
<section class="copying">
  <div class="copy">
    <p>
      این یک پاراگراف شامل <strong>پررنگ</strong>، <em>ایتالیک</em>، و متن
      <span class="red">قرمز</span> است و به دنبال آن یک لیست مرتب شده می‌آید:
    </p>
    <ol>
      <li>مرحله یک</li>
      <li>مرحله دو</li>
      <li>مرحله سه</li>
    </ol>
  </div>
</section>
```

```html
<h2>ناحیه‌های چسباندن</h2>
<section class="pasting">
  <div class="wrapper">
    <h3>contenteditable="true"</h3>
    <div contenteditable="true"></div>
  </div>
  <div class="wrapper">
    <h3>contenteditable="plaintext-only"</h3>
    <div contenteditable="plaintext-only"></div>
  </div>
</section>
```

```css hidden
h2 {
  margin-bottom: 0;
}
.copying {
  font-family: "Georgia", serif;
  margin: 1rem;
  padding: 1rem;
  border: solid black 1px;
}
.red {
  color: red;
}
.pasting {
  display: flex;
  flex-direction: row;
  gap: 1rem;
  width: 100%;
  .wrapper {
    flex: 1 1;
    margin: 0;
    padding: 0;
  }
  h3 {
    font-family: monospace;
  }
  [contenteditable] {
    min-height: 3rem;
    border: solid 1px;
    padding: 0.5rem;
    background-color: whitesmoke;
  }
  [contenteditable="true"] {
    caret-color: blue;
  }
  [contenteditable="plaintext-only"] {
    caret-color: red;
  }
}
```

## همچنین ببینید

- همهٔ [ویژگی‌های سراسری](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes)
- `HTMLElement.contentEditable` و `HTMLElement.isContentEditable`
- ویژگی CSS `caret-color`
- [رویداد `input` در `HTMLElement`](https://developer.mozilla.org/en-US/docs/Web/API/Element/input_event)