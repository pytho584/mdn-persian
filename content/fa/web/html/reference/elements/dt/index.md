---
title: "<dt> HTML description term element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dt"
translated_by: "n8n + AI"
---

```markdown
عنصر **`<dt>`** (term description) در HTML برای مشخص کردن یک اصطلاح در یک لیست توضیحی یا تعریفی به کار می‌رود. این عنصر حتماً باید داخل یک عنصر {{HTMLElement("dl")}} استفاده شود. معمولاً بعد از `<dt>` یک عنصر {{HTMLElement("dd")}} می‌آید؛ اما اگر چندین `<dt>` پشت‌سر هم بیایند، نشان‌دهندهٔ چند اصطلاح است که همگی توسط اولین {{HTMLElement("dd")}} بعدی تعریف می‌شوند.

عنصر بعدی {{HTMLElement("dd")}} (جزئیات توضیح) تعریف یا متن مرتبط با اصطلاحی که با `<dt>` مشخص شده را ارائه می‌دهد.

```html interactive-example
<p>Please use the following paint colors for the new house:</p>

<dl>
  <dt>Denim (semigloss finish)</dt>
  <dd>Ceiling</dd>

  <dt>Denim (eggshell finish)</dt>
  <dt>Evening Sky (eggshell finish)</dt>
  <dd>Layered on the walls</dd>
</dl>
```

```css interactive-example
p,
dl {
  font:
    1rem "Fira Sans",
    sans-serif;
}

dl > dt {
  font-weight: normal;
  font-style: oblique;
}

dd {
  margin-bottom: 1rem;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## مثال‌ها

برای مشاهدهٔ مثال‌ها، به [مثال‌های ارائه‌شده برای عنصر `<dl>`](/en-US/docs/Web/HTML/Reference/Elements/dl#examples) مراجعه کنید.

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا (Content categories)</th>
      <td>هیچ‌کدام.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (Permitted content)</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتوای جریانی (Flow content)</a
        >، اما بدون هیچ فرزند از نوع {{HTMLElement("header")}}،
        {{HTMLElement("footer")}}، محتوای بخش‌بندی یا محتوای عنوان.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (Tag omission)</th>
      <td>
        تگ شروع اجباری است. تگ پایان ممکن است حذف شود اگر این عنصر بلافاصله با یک عنصر دیگر <code>&lt;dt&gt;</code> یا یک {{HTMLElement("dd")}} دنبال شود، یا اگر محتوای دیگری در عنصر والد وجود نداشته باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (Permitted parents)</th>
      <td>
        یک {{HTMLElement("dl")}} یا (در HTML {{Glossary("WHATWG")}}،
        HTML 5.2 {{Glossary("W3C")}} و بعد از آن) یک
        {{HTMLElement("div")}} که فرزند یک {{HTMLElement("dl")}} باشد.<br />این عنصر می‌تواند قبل از یک {{HTMLElement("dd")}} یا یک عنصر دیگر <code>&lt;dt&gt;</code> استفاده شود.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >نقش متناظری ندارد</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role"
            >listitem</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM interface)</th>
      <td>
        {{domxref("HTMLElement")}} تا نسخهٔ Gecko 1.9.2 (Firefox 4)
        به‌طور کامل، فایرفاکس از رابط {{domxref("HTMLSpanElement")}} برای این عنصر استفاده می‌کرد.
      </td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- {{HTMLElement("dl")}}
- {{HTMLElement("dd")}}
```