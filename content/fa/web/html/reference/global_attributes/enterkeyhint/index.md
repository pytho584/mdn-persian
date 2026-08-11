---
title: "enterkeyhint HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/enterkeyhint"
translated_by: "n8n + AI"
---

**`enterkeyhint`** یک [ویژگی سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) از نوع [enumerated](/en-US/docs/Glossary/Enumerated) است که مشخص می‌کند چه برچسب (یا آیکنی) برای کلید Enter در صفحه‌کلید مجازی نمایش داده شود.

```html interactive-example
<input enterkeyhint="go" />

<p contenteditable enterkeyhint="go">https://example.org</p>
```

## توضیحات

کنترل‌های فرم (فرم کنترل‌ها) مانند المان‌های [`<textarea>`](/en-US/docs/Web/HTML/Reference/Elements/textarea) یا [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input)، یا المان‌هایی که از [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) استفاده می‌کنند، می‌توانند ویژگی [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode) را مشخص کنند تا تعیین شود از چه نوع صفحه‌کلید مجازی استفاده شود. برای بهبود بیشتر تجربه کاربر، می‌توان کلید Enter را به‌صورت دقیق‌تری سفارشی کرد؛ با ارائه ویژگی `enterkeyhint` مشخص می‌شود که کلید Enter چگونه برچسب‌گذاری شود (یا چه آیکنی نمایش داده شود). کلید Enter معمولاً نشان‌دهنده عملی است که کاربر باید بعدی انجام دهد؛ اقدامات رایج عبارت‌اند از: ارسال متن، درج خط جدید یا جستجو.

اگر ویژگی `enterkeyhint` ارائه نشود، عامل کاربر (user agent) ممکن است از اطلاعات زمینه‌ای موجود در ویژگی‌های [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode)، [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#input_types) یا [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) استفاده کند تا برچسب (یا آیکن) مناسبی برای کلید Enter نمایش دهد.

## مقدار

ویژگی `enterkeyhint` یک ویژگی از نوع [enumerated](/en-US/docs/Glossary/Enumerated) است و فقط مقادیر زیر را می‌پذیرد:

<table class="no-markdown">
  <thead>
    <tr>
      <th>مقدار</th>
      <th>توضیحات</th>
      <th>نمونه برچسب (بسته به عامل کاربر و زبان کاربر)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>enterkeyhint="enter"</code></td>
      <td>معمولاً درج یک خط جدید.</td>
      <td><kbd>return</kbd>, <kbd>↵</kbd></td>
    </tr>
    <tr>
      <td><code>enterkeyhint="done"</code></td>
      <td>معمولاً به این معنی است که ورودی دیگری وجود ندارد و ویرایشگر روش ورودی (IME) بسته می‌شود.</td>
      <td><kbd>done</kbd>, <kbd>✅</kbd></td>
    </tr>
    <tr>
      <td><code>enterkeyhint="go"</code></td>
      <td>معمولاً کاربر را به مقصد متنی که تایپ کرده هدایت می‌کند.</td>
      <td><kbd>go</kbd>, <kbd>🡢</kbd></td>
    </tr>
    <tr>
      <td><code>enterkeyhint="next"</code></td>
      <td>معمولاً کاربر را به فیلد بعدی که متن می‌پذیرد می‌برد.</td>
      <td><kbd>next</kbd>, <kbd>⇥</kbd></td>
    </tr>
    <tr>
      <td><code>enterkeyhint="previous"</code></td>
      <td>معمولاً کاربر را به فیلد قبلی که متن می‌پذیرد می‌برد.</td>
      <td><kbd>return</kbd>, <kbd>⇤</kbd></td>
    </tr>
    <tr>
      <td><code>enterkeyhint="search"</code></td>
      <td>معمولاً کاربر را به نتایج جستجوی متنی که تایپ کرده می‌برد.</td>
      <td><kbd>search</kbd>, <kbd>🔍</kbd></td>
    </tr>
    <tr>
      <td><code>enterkeyhint="send"</code></td>
      <td>معمولاً متن را به مقصد موردنظر می‌رساند.</td>
      <td><kbd>send</kbd></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- [`HTMLElement.enterKeyHint`](/en-US/docs/Web/API/HTMLElement/enterKeyHint) property که این attribute را منعکس می‌کند
- [`inputmode`](/en-US/docs/Web/HTML/Reference/Global_attributes/inputmode) attribute سراسری
- [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) attribute سراسری
- [`type`](/en-US/docs/Web/HTML/Reference/Elements/input#input_types) و
  [`pattern`](/en-US/docs/Web/HTML/Reference/Elements/input#pattern) attributeهایی روی عناصر
  [`<input>`](/en-US/docs/Web/HTML/Reference/Elements/input)