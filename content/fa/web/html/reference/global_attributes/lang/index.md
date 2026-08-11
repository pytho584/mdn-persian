---
title: "lang HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/lang"
translated_by: "n8n + AI"
---

**`lang`** یک **global attribute** است که زبان یک element را مشخص می‌کند: زبانی که در elementهای غیرقابل ویرایش نوشته شده، یا زبانی که کاربر باید در elementهای قابل ویرایش بنویسد. این attribute شامل یک **BCP 47 language tag** (برچسب زبان BCP 47) است.

> [!NOTE]
> اگر مقدار `lang` رشتهٔ خالی باشد، زبان به‌صورت صریح «ناشناخته» در نظر گرفته می‌شود. بنابراین توصیه می‌شود همیشه مقدار مناسبی برای این attribute تعیین کنید.

```html interactive-example
<p>This paragraph is English, but the language is not specifically defined.</p>

<p lang="en-GB">This paragraph is defined as British English.</p>

<p lang="fr">Ce paragraphe est défini en français.</p>
```

```css interactive-example
p::before {
  padding-right: 5px;
}

[lang="en-GB"]::before {
  content: "(In British English) ";
}

[lang="fr"]::before {
  content: "(In French) ";
}
```

اگر مقدار attribute رشتهٔ خالی (`lang=""`) باشد، زبان به‌صورت _unknown (ناشناخته)_ تنظیم می‌شود و اگر language tag مطابق BCP47 معتبر نباشد، مقدار آن _invalid (نامعتبر)_ خواهد بود.

حتی اگر attribute `lang` تنظیم شده باشد، ممکن است مورد توجه قرار نگیرد، زیرا attribute `xml:lang` اولویت بالاتری دارد.

برای شبه‌کلاس CSS `:lang`، دو نام زبان نامعتبر اگر نام‌هایشان متفاوت باشد، متفاوت در نظر گرفته می‌شوند. به همین ترتیب، در حالی که `:lang(es)` با هر دو `lang="es-ES"` و `lang="es-419"` مطابقت دارد، `:lang(xyzzy)` با `lang="xyzzy-Zorp!"` مطابقت _نمی‌کند_.

## نگرانی‌های دسترس‌پذیری

معیار موفقیت WCAG 3.1.1 **الزام می‌کند** که زبان صفحه به روشی مشخص شود که «به‌صورت برنامه‌ریزی‌شده قابل تعیین» باشد (یعنی از طریق attribute **`lang`**).

معیار موفقیت WCAG 3.1.2 نیز الزام می‌کند که در صفحاتی که **بخش‌هایی** به زبان‌های مختلف دارند، زبان آن بخش‌ها نیز مشخص شود. باز هم attribute **`lang`** مکانیزم درست برای این کار است.

هدف اصلی این الزامات، امکان‌پذیر کردن تلفظ صحیح برای فناوری‌های کمکی مانند screen readerهاست.

برای مثال، منوی زبان در همین سایت (MDN) برای هر گزینه، یک attribute **`lang`** دارد.

```markdown
## ارث‌بری

اگر یک عنصر (element) ویژگی `lang` نداشته باشد، مقدار `lang` تنظیم‌شده روی [گره والد (parent node)](/en-US/docs/Glossary/Node/DOM) خود را به ارث می‌برد؛ و آن گره والد نیز ممکن است مقدار را از والد خودش به ارث ببرد و همین روند ادامه پیدا می‌کند.

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- همه [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- [`Content-Language` HTTP Header](/en-US/docs/Web/HTTP/Reference/Headers/Content-Language)
- ویژگی HTML [`translate`](/en-US/docs/Web/HTML/Reference/Global_attributes/translate)
```