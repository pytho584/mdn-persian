---
title: "<figure> HTML figure with optional caption element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/figure"
translated_by: "n8n + AI"
---

عنصر `<figure>` در HTML، یک محتوای خودکفا را نمایش می‌دهد که می‌تواند یک توضیح اختیاری (caption) همراه داشته باشد. این توضیح با استفاده از عنصر `<figcaption>` مشخص می‌شود. خود figure، caption و محتوایش به‌عنوان یک واحد واحد در نظر گرفته می‌شوند.

```html
<figure>
  <img
    src="/shared-assets/images/examples/elephant.jpg"
    alt="Elephant at sunset" />
  <figcaption>An elephant at sunset</figcaption>
</figure>
```

```css
figure {
  border: thin silver solid;
  display: flex;
  flex-flow: column;
  padding: 5px;
  max-width: 220px;
  margin: auto;
}

img {
  max-width: 220px;
  max-height: 150px;
}

figcaption {
  background-color: #222222;
  color: white;
  font: italic smaller sans-serif;
  padding: 3px;
  text-align: center;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

- معمولاً `<figure>` برای تصویر، نمودار، دیاگرام، قطعه کد و موارد مشابه به کار می‌رود که در جریان اصلی سند به آن اشاره می‌شود، اما می‌توان آن را بدون تأثیر بر جریان اصلی به بخش دیگری از سند یا ضمیمه منتقل کرد.
- برای اضافه کردن caption به `<figure>`، یک عنصر `<figcaption>` داخل آن قرار دهید (به‌عنوان فرزند اول یا آخر). اولین `<figcaption>` که درون figure پیدا شود به‌عنوان caption آن در نظر گرفته می‌شود.
- `<figcaption>` نام دسترسی‌پذیر (accessible name) را برای `<figure>` والد فراهم می‌کند.

## مثال‌ها

### تصاویر

```html
<!-- فقط یک تصویر -->
<figure>
  <img src="favicon-192x192.png" alt="The beautiful MDN logo." />
</figure>

<!-- تصویر با caption -->
<figure>
  <img src="favicon-192x192.png" alt="The beautiful MDN logo." />
  <figcaption>MDN Logo</figcaption>
</figure>
```

### قطعه کد

```html
<figure>
  <figcaption>Get browser details using <code>navigator</code>.</figcaption>
  <pre>
function NavigatorExample() {
  let txt = `Browser CodeName: ${navigator.appCodeName};\n`;
  txt += `Browser Name: ${navigator.appName};\n`;
  txt += `Browser Version: ${navigator.appVersion};\n`;
  txt += `Cookies Enabled: ${navigator.cookieEnabled};\n`;
  txt += `Platform: ${navigator.platform};\n`;
  txt += `User-agent header: ${navigator.userAgent};`;
  console.log("NavigatorExample", txt);
}
  </pre>
</figure>
```

### نقل‌قول‌ها

```html
<figure>
  <figcaption><b>Edsger Dijkstra:</b></figcaption>
  <blockquote>
    If debugging is the process of removing software bugs, then programming must
    be the process of putting them in.
  </blockquote>
</figure>
```

### شعر

```html
<figure>
  <p>
    Bid me discourse, I will enchant thine ear,<br />
    Or like a fairy trip upon the green,<br />
    Or, like a nymph, with long dishevelled hair,<br />
    Dance on the sands, and yet no footing seen:<br />
    Love is a spirit all compact of fire,<br />
    Not gross to sink, but light, and will aspire.<br />
  </p>
  <figcaption><cite>Venus and Adonis</cite>, by William Shakespeare</figcaption>
</figure>
```

<figure> عنصری است که محتوای مستقل مانند تصاویر، نمودارها، کدها و غیره را همراه با یک توضیح اختیاری (عنصر <figcaption>) گروه‌بندی می‌کند. جدول زیر مشخصات این عنصر را نشان می‌دهد.

| ویژگی | توضیح |
|-------|-------|
| [دسته‌بندی محتوا](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories) | [محتواهای جریانی](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [محتواهای قابل لمس](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) |
| محتوای مجاز | یک عنصر `<figcaption>` و سپس [محتواهای جریانی](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)؛ یا محتواهای جریانی و سپس یک `<figcaption>`؛ یا فقط محتواهای جریانی |
| حذف تگ | هیچکدام – هر دو تگ شروع و پایان اجباری هستند |
| والد مجاز | هر عنصری که [محتواهای جریانی](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را می‌پذیرد |
| نقش ARIA ضمنی | [figure](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/figure_role) |
| نقش‌های ARIA مجاز | اگر فرزند `figcaption` نداشته باشد: [هر نقشی](https://w3c.github.io/html-aria/#dfn-any-role)؛ در غیر این صورت هیچ نقشی مجاز نیست |
| رابط DOM | `HTMLElement` |

## مشخصات

## سازگاری مرورگرها

## همچنین ببینید

- عنصر [`<figcaption>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/figcaption)