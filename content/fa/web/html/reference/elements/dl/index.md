---
title: "<dl> HTML description list element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dl"
translated_by: "n8n + AI"
---

عنصر `<dl>` - لیست توضیحات HTML

عنصر **`<dl>`** در [HTML](/fa/docs/Web/HTML) یک لیست توضیحات (description list) را نمایش می‌دهد. این عنصر شامل گروه‌هایی از عبارت‌ها (که با عنصر {{HTMLElement("dt")}} مشخص می‌شوند) و توضیحات مربوط به آن‌ها (که با عنصر {{HTMLElement("dd")}} ارائه می‌شوند) است. کاربردهای رایج این عنصر شامل ایجاد واژه‌نامه (glossary) یا نمایش داده‌های فراداده (metadata) به صورت یک لیست از جفت‌های کلید-مقدار است.

```html interactive-example
<p>Cryptids of Cornwall:</p>

<dl>
  <dt>Beast of Bodmin</dt>
  <dd>A large feline inhabiting Bodmin Moor.</dd>

  <dt>Morgawr</dt>
  <dd>A sea serpent.</dd>

  <dt>Owlman</dt>
  <dd>A giant owl-like creature.</dd>
</dl>
```

```css interactive-example
p,
dt {
  font-weight: bold;
}

dl,
dd {
  font-size: 0.9rem;
}

dd {
  margin-bottom: 1em;
}
```

## ویژگی‌ها (Attributes)

این عنصر همچنین [ویژگی‌های سراسری (global attributes)](/fa/docs/Web/HTML/Reference/Global_attributes) را می‌پذیرد.

- `compact` {{Deprecated_inline}}
  - : این ویژگی بولی (Boolean) نشان می‌دهد که لیست باید به صورت فشرده نمایش داده شود. تفسیر این ویژگی به مرورگر بستگی دارد. به جای آن از [CSS](/fa/docs/Web/CSS) استفاده کنید: برای ایجاد اثری مشابه ویژگی `compact`، می‌توان از ویژگی CSS {{cssxref("line-height")}} با مقدار `80%` استفاده کرد.

## دسترسی‌پذیری (Accessibility)

هر صفحه‌خوان (screen reader) محتوای `<dl>` را به صورت متفاوتی نمایش می‌دهد، از جمله تعداد کل، بافت عبارت‌ها/تعاریف و روش‌های پیمایش. این تفاوت‌ها لزوماً باگ محسوب نمی‌شوند.  
از iOS 14 به بعد، VoiceOver هنگام پیمایش با مکان‌نمای مجازی (virtual cursor، نه از طریق دستور خواندن همه) اعلام می‌کند که محتوای `<dl>` یک لیست است. VoiceOver از دستورات پیمایش لیست با `<dl>` پشتیبانی نمی‌کند. در استفاده از نقش‌های ARIA `term` و `definition` برای ساختار `<dl>` احتیاط کنید، زیرا VoiceOver (در macOS و iOS) نحوه اعلام آن‌ها را تغییر می‌دهد.

- [VoiceOver on iOS 14 Supports Description Lists](https://adrianroselli.com/2020/09/voiceover-on-ios-14-supports-description-lists.html)
- [Brief Note on Description List Support](https://adrianroselli.com/2022/12/brief-note-on-description-list-support.html)

## مثال‌ها

### یک عبارت و یک توضیح

```html
<dl>
  <dt>Firefox</dt>
  <dd>
    A free, open source, cross-platform, graphical web browser developed by the
    Mozilla Corporation and hundreds of volunteers.
  </dd>

  <!-- Other terms and descriptions -->
</dl>
```

### چند عبارت، یک توضیح

```html
<dl>
  <dt>Firefox</dt>
  <dt>Mozilla Firefox</dt>
  <dt>Fx</dt>
  <dd>
    A free, open source, cross-platform, graphical web browser developed by the
    Mozilla Corporation and hundreds of volunteers.
  </dd>

  <!-- Other terms and descriptions -->
</dl>
```

### یک عبارت، چند توضیح

```html
<dl>
  <dt>Firefox</dt>
  <dd>
    A free, open source, cross-platform, graphical web browser developed by the
    Mozilla Corporation and hundreds of volunteers.
  </dd>
  <dd>
    The Red Panda also known as the Lesser Panda, Wah, Bear Cat or Firefox, is a
    mostly herbivorous mammal, slightly larger than a domestic cat (60 cm long).
  </dd>

  <!-- Other terms and descriptions -->
</dl>
```

### چند عبارت و چند توضیح

همچنین می‌توان با ترکیب مثال‌های بالا، چند عبارت را با چند توضیح متناظر تعریف کرد.

### فراداده (Metadata)

لیست‌های توضیحات برای نمایش فراداده به صورت جفت‌های کلید-مقدار مفید هستند.

```html
<dl>
  <dt>Name</dt>
  <dd>Godzilla</dd>
  <dt>Born</dt>
  <dd>1952</dd>
  <dt>Birthplace</dt>
  <dd>Japan</dd>
  <dt>Color</dt>
  <dd>Green</dd>
</dl>
```

### نکته

بهتر است جداکننده‌ی کلید-مقدار را در CSS تعریف کنید، مثلاً:

```css
dt::after {
  content: ": ";
}
```

### بسته‌بندی گروه‌های نام-مقدار در عنصرهای `div`

HTML به شما اجازه می‌دهد هر گروه نام-مقدار را داخل یک عنصر `<div>` درون یک `<dl>` قرار دهید. این کار می‌تواند هنگام استفاده از [microdata](/en-US/docs/Web/HTML/Guides/Microdata) یا وقتی [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) روی کل گروه اعمال می‌شود، یا برای اهداف استایل‌دهی مفید باشد.

```html
<dl>
  <div>
    <dt>Name</dt>
    <dd>Godzilla</dd>
  </div>
  <div>
    <dt>Born</dt>
    <dd>1952</dd>
  </div>
  <div>
    <dt>Birthplace</dt>
    <dd>Japan</dd>
  </div>
  <div>
    <dt>Color</dt>
    <dd>Green</dd>
  </div>
</dl>
```

## یادداشت‌ها

از این عنصر (و نیز عنصرهای `<ul>`) صرفاً برای ایجاد تورفتگی در صفحه استفاده نکنید. اگرچه این کار عملاً درست کار می‌کند، اما شیوه‌ای نادرست است و معنای فهرست‌های توصیفی را مبهم می‌کند.

برای تغییر تورفتگی یک عبارت توصیفی، از ویژگی [CSS](/en-US/docs/Web/CSS) [margin](/en-US/docs/Web/CSS/margin) استفاده کنید.

## خلاصه‌ی فنی

| مشخصه | مقدار |
| --- | --- |
| دسته‌بندی محتوا | محتوای جریانی (Flow content)؛ و اگر فرزندان `<dl>` شامل یک گروه نام-مقدار باشند، محتوای محسوس (palpable content) نیز هست. |
| محتوای مجاز | یا: صفر یا چند گروه که هر کدام شامل یک یا چند `<dt>` و به دنبال آن یک یا چند `<dd>` هستند، به‌صورت اختیاری با عناصر `<script>` و `<template>` درآمیخته. یا: (در WHATWG HTML و W3C HTML 5.2 به بعد) یک یا چند `<div>`، به‌صورت اختیاری با عناصر `<script>` و `<template>` درآمیخته. |
| حذف تگ | هیچ‌کدام؛ هر دو تگ شروع و پایان اجباری هستند. |
| والدین مجاز | هر عنصری که محتوای جریانی (Flow content) را می‌پذیرد. |
| نقش ARIA ضمنی | [نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)، [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)، [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)، [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) |
| رابط DOM | `HTMLDListElement` |

## همچنین ببینید

- [`dt`](/en-US/docs/Web/HTML/Element/dt)
- [`dd`](/en-US/docs/Web/HTML/Element/dd)