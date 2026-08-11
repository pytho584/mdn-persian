---
title: "<meta name=\"referrer\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/meta/name/referrer"
translated_by: "n8n + AI"
---

# مقدار `referrer` برای ویژگی `name` در `<meta>`

مقدار **`referrer`** برای ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/meta/name) عنصر `<meta>`، هدر HTTP `Referer` درخواست‌هایی که از سند ارسال می‌شوند را کنترل می‌کند. وقتی این مقدار مشخص شده باشد، referrer را با یک مقدار کلیدواژه‌ای در ویژگی `content` درون همان `<meta>` تعریف می‌کنید.

برای مثال، `<meta>` زیر، origin سند را به‌عنوان referrer ارسال می‌کند:

```html
<meta name="referrer" content="origin" />
```

> [!WARNING]
> درج پویای `<meta name="referrer">` (با `document.write()` یا `appendChild()`) باعث می‌شود رفتار referrer غیرقابل پیش‌بینی شود. وقتی چند سیاست متناقض تعریف شده باشند، سیاست `no-referrer` اعمال می‌شود.

## نکات استفاده

یک `<meta name="referrer">` ویژگی‌های اضافی زیر را دارد:

- [`content`](/en-US/docs/Web/HTML/Reference/Elements/meta#content)
  - : referrer سند را تعیین می‌کند. این ویژگی باید حتماً تعریف شود. یکی از مقادیر زیر را می‌پذیرد:
    - `no-referrer`
      - : هیچ هدر HTTP `Referer` ارسال نمی‌کند.
    - `origin`
      - : فقط origin سند را ارسال می‌کند.
    - `no-referrer-when-downgrade`
      - : وقتی مقصد حداقل به اندازه صفحه فعلی امن باشد (HTTP(S)→HTTPS)، URL کامل را ارسال می‌کند؛ اما وقتی امنیت کمتری داشته باشد (HTTPS→HTTP)، هیچ referrer ای ارسال نمی‌کند. این رفتار پیش‌فرض است.
    - `origin-when-cross-origin`
      - : برای درخواست‌های same-origin، URL کامل (بدون پارامترها) را ارسال می‌کند؛ اما در سایر موارد فقط origin را می‌فرستد.
    - `same-origin`
      - : برای درخواست‌های same-origin، URL کامل (بدون پارامترها) را ارسال می‌کند. درخواست‌های cross-origin هیچ هدر referrer ندارند.
    - `strict-origin`
      - : وقتی مقصد حداقل به اندازه صفحه فعلی امن باشد (HTTP(S)→HTTPS)، origin را ارسال می‌کند؛ اما وقتی امنیت کمتری داشته باشد (HTTPS→HTTP)، هیچ referrer ای ارسال نمی‌کند.
    - `strict-origin-when-cross-origin`
      - : برای درخواست‌های same-origin، URL کامل (بدون پارامترها) را ارسال می‌کند. وقتی مقصد حداقل به اندازه صفحه فعلی امن باشد (HTTP(S)→HTTPS)، origin را ارسال می‌کند. در غیر این صورت، هیچ referrer ای ارسال نمی‌کند.
    - `unsafe-URL`
      - : برای درخواست‌های same-origin یا cross-origin، URL کامل (بدون پارامترها) را ارسال می‌کند.

## مثال‌ها

### حذف referrer از درخواست‌ها

`<meta>` زیر مشخص می‌کند که سند نباید هدر `Referer` را همراه با درخواست‌های HTTP خود ارسال کند:

```html
<meta name="referrer" content="no-referrer" />
```

## همچنین ببینید

- هدر HTTP `Referer`