---
title: "lang HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/lang"
translated_by: "n8n + AI"
---

**`lang`** یک [global attribute](/en-US/docs/Web/HTML/Reference/Global_attributes) است که زبان یک element را مشخص می‌کند: زبانی که elementهای غیرقابل ویرایش با آن نوشته شده‌اند، یا زبانی که کاربر باید در elementهای قابل ویرایش بنویسد. مقدار این attribute یک BCP 47 language tag است.

> [!NOTE]
> اگر مقدار `lang` برابر با رشتهٔ خالی باشد، زبان به‌صراحت ناشناخته است؛ بنابراین توصیه می‌شود برای این attribute همیشه مقدار مناسبی تعیین کنید.

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

اگر مقدار attribute رشتهٔ خالی باشد (`lang=""`)، زبان به صورت _ناشناخته_ در نظر گرفته می‌شود؛ اگر language tag مطابق BCP47 معتبر نباشد، به صورت _نامعتبر_ در نظر گرفته می‌شود.

حتی اگر `lang` تنظیم شده باشد، ممکن است مورد توجه قرار نگیرد، چون attribute مربوط به `xml:lang` اولویت دارد.

برای شبه‌کلاس CSS یعنی `:lang`، دو نام زبان نامعتبر اگر نام‌هایشان متفاوت باشد، متفاوت تلقی می‌شوند. پس در حالی که `:lang(es)` با هر دو `lang="es-ES"` و `lang="es-419"` مطابقت دارد، `:lang(xyzzy)` با `lang="xyzzy-Zorp!"` مطابقت _نخواهد_ داشت.

## دسترس‌پذیری

معیار موفقیت WCAG 3.1.1 **الزام می‌کند** که زبان صفحه به شکلی مشخص شود که «به‌صورت برنامه‌ای قابل تعیین» باشد (یعنی از طریق attribute **`lang`**).

معیار موفقیت WCAG 3.1.2 نیز الزام می‌کند که در صفحه‌هایی که **بخش‌هایی** به زبان‌های مختلف دارند، زبان آن بخش‌ها نیز مشخص شود. باز هم، attribute **`lang`** سازوکار درست برای این کار است.

هدف اصلی این الزامات این است که فناوری‌های کمکی مانند صفحه‌خوان‌ها (screen reader) بتوانند تلفظ درست را اعمال کنند.

برای مثال، منوی زبان در همین سایت (MDN) برای هر گزینه یک attribute **`lang`** دارد.

```html
<div class="dropdown-container language-menu">
  <button
    id="header-language-menu"
    type="button"
    class="dropdown-menu-label"
    aria-haspopup="true"
    aria-owns="language-menu"
    aria-label="Current language is English. Choose your preferred language.">
    English
    <span class="dropdown-arrow-down" aria-hidden="true">▼</span>
  </button>
  <ul
    id="language-menu"
    class="dropdown-menu-items right show"
    aria-expanded="true"
    role="menu">
    <li role="menuitem">
      <a
        href="/ca/docs/Web/HTML/Reference/Global_attributes/lang"
        title="Catalan">
        <bdi lang="ca">Català</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/de/docs/Web/HTML/Reference/Global_attributes/lang"
        title="German">
        <bdi lang="de">Deutsch</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/es/docs/Web/HTML/Reference/Global_attributes/lang"
        title="Spanish">
        <bdi lang="es">Español</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/fr/docs/Web/HTML/Reference/Global_attributes/lang"
        title="French">
        <bdi lang="fr">Français</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/ja/docs/Web/HTML/Reference/Global_attributes/lang"
        title="Japanese">
        <bdi lang="ja">日本語</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/ko/docs/Web/HTML/Reference/Global_attributes/lang"
        title="Korean">
        <bdi lang="ko">한국어</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/pt-BR/docs/Web/HTML/Reference/Global_attributes/lang"
        title="Portuguese (Brazilian)">
        <bdi lang="pt-BR">Português (do&nbsp;Brasil)</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/ru/docs/Web/HTML/Reference/Global_attributes/lang"
        title="Russian">
        <bdi lang="ru">Русский</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/uk/docs/Web/HTML/Reference/Global_attributes/lang"
        title="Ukrainian">
        <bdi lang="uk">Українська</bdi>
      </a>
    </li>
    <li role="menuitem">
      <a
        href="/zh-CN/docs/Web/HTML/Reference/Global_attributes/lang"
        title="Chinese (Simplified)">
        <bdi lang="zh-Hans">中文 (简体)</bdi>
      </a>
    </li>
    <li>
      <a
        href="/en-US/docs/Web/HTML/Reference/Global_attributes/lang"
        rel="nofollow"
        id="translations-add">
        Add a translation
      </a>
    </li>
  </ul>
</div>

## ارث‌بری

اگر یک element فاقد attribute ی `lang` باشد، مقدار `lang` را از [parent node](/en-US/docs/Glossary/Node/DOM) خود به ارث می‌برد. خود parent node نیز ممکن است این مقدار را از والد خود به ارث برده باشد و این روند به همین ترتیب ادامه می‌یابد.

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- All [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).
- [`Content-Language` HTTP Header](/en-US/docs/Web/HTTP/Reference/Headers/Content-Language)
- HTML [`translate`](/en-US/docs/Web/HTML/Reference/Global_attributes/translate) attribute
```