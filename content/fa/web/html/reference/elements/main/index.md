---
title: "<main> HTML main element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/main"
translated_by: "n8n + AI"
---

عنصر **`<main>`** در HTML نمایانگر محتوای اصلی داخل {{HTMLElement("body")}} یک سند است. بخش محتوای اصلی شامل مطالبی می‌شود که مستقیماً به موضوع مرکزی سند یا عملکرد اصلی یک اپلیکیشن مربوط است یا آن را بسط می‌دهد.

{{InteractiveExample("HTML Demo: &lt;main&gt;", "tabbed-shorter")}}

```html interactive-example
<header>Gecko facts</header>

<main>
  <p>
    Geckos are a group of usually small, usually nocturnal lizards. They are
    found on every continent except Antarctica.
  </p>

  <p>
    Many species of gecko have adhesive toe pads which enable them to climb
    walls and even windows.
  </p>
</main>
```

```css interactive-example
header {
  font:
    bold 7vw "Arial",
    sans-serif;
}
```

یک سند نباید بیش از یک عنصر `<main>` داشته باشد، مگر آن‌هایی که ویژگی [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden) روی آن‌ها تنظیم شده باشد.

## ویژگی‌ها

این عنصر فقط [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) را شامل می‌شود.

## نکات استفاده

محتوای عنصر `<main>` باید منحصر به همان سند باشد. محتوایی که در مجموعه‌ای از اسناد یا بخش‌های سند تکرار می‌شود، مانند نوار کناری، لینک‌های ناوبری، اطلاعات کپی‌رایت، لوگوی سایت و فرم‌های جستجو، نباید در این عنصر قرار گیرد — مگر اینکه فرم جستجو عملکرد اصلی صفحه باشد.

`<main>` در طرح کلی (outline) سند نقشی ندارد؛ یعنی برخلاف عناصری مثل {{HTMLElement("body")}} یا عناصر heading مثل {{HTMLElement("Heading_Elements", "h2")}}، `<main>` روی مفهوم ساختار صفحه از نظر {{glossary("DOM", "DOM")}} تأثیر نمی‌گذارد. این عنصر صرفاً جنبهٔ اطلاعاتی دارد.

## دسترسی‌پذیری

### نشانهٔ (Landmark) اصلی

عنصر `<main>` به‌مثابهٔ نقش `main landmark` عمل می‌کند. [نشانه‌ها](/en-US/docs/Web/Accessibility/ARIA/Guides/Techniques#landmark_roles) به فناوری‌های کمکی کمک می‌کنند تا بخش‌های بزرگ سند را سریع شناسایی کرده و به آن‌ها بروند. بهتر است از `<main>` به جای `role="main"` استفاده کنید، مگر اینکه نگرانی از [پشتیبانی مرورگرهای قدیمی](#browser_compatibility) وجود داشته باشد.

### پرش از ناوبری (Skip Navigation)

پرش از ناوبری که به آن "skipnav" هم می‌گویند، تکنیکی است که به کاربر فناوری کمکی اجازه می‌دهد سریع از بخش‌های بزرگ محتوای تکراری (منوی اصلی، بنرهای اطلاعاتی و...) عبور کند و به محتوای اصلی صفحه برسد.

با افزودن یک [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) به عنصر `<main>`، می‌توان از آن به‌عنوان هدف لینک پرش از ناوبری استفاده کرد.

```html
<body>
  <a href="#main-content">پرش به محتوای اصلی</a>

  <!-- ناوبری و محتوای هدر -->

  <main id="main-content">
    <!-- محتوای اصلی صفحه -->
  </main>
</body>
```

- [لینک‌های "Skip Navigation" در WebAIM](https://webaim.org/techniques/skipnav/)

### حالت مطالعه (Reader Mode)

حالت مطالعه در مرورگرها برای تبدیل محتوا به نمای خواندن اختصاصی، به دنبال وجود عنصر `<main>` و همچنین [عناصر heading](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) و [بخش‌بندی محتوا](/en-US/docs/Web/HTML/Reference/Elements#content_sectioning) می‌گردد.

- [ساخت وب‌سایت برای Safari Reader Mode و سایر اپ‌های مطالعه](https://medium.com/@mandy.michael/building-websites-for-safari-reader-mode-and-other-reading-apps-1562913c86c9)

## مثال‌ها

```html
<!-- سایر محتوا -->

<main>
  <h1>سیب‌ها</h1>
  <p>سیب میوهٔ دانه‌دار درخت سیب است.</p>

  <article>
    <h2>رد دلیشز</h2>
    <p>
      این سیب‌های قرمز روشن رایج‌ترین نوعی هستند که در بسیاری از سوپرمارکت‌ها یافت می‌شوند.
    </p>
    <p>…</p>
    <p>…</p>
  </article>
</main>
```

## مثال

### Result

## خلاصه فنی

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
        >, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted content</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Tag omission</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">Permitted parents</th>
      <td>
        هر جایی که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        >
        مورد انتظار است، اما فقط در صورتی که یک
        <a
          href="https://html.spec.whatwg.org/multipage/grouping-content.html#hierarchically-correct-main-element"
          >عنصر <code>main</code> از نظر سلسله‌مراتبی صحیح</a
        > باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role"
            >main</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">DOM interface</th>
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- عناصر ساختاری پایه: {{HTMLElement("html")}}، {{HTMLElement("head")}}، {{HTMLElement("body")}}
- عناصر مرتبط با بخش‌بندی: {{HTMLElement("article")}}، {{HTMLElement("aside")}}، {{HTMLElement("footer")}}، {{HTMLElement("header")}} یا {{HTMLElement("nav")}}
- [نقش ARIA: main](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role)