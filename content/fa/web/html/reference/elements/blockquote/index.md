---
title: "<blockquote> HTML block quotation element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/blockquote"
translated_by: "n8n + AI"
---

عنصر `<blockquote>` در HTML نشان می‌دهد که متن داخل آن، یک نقل‌قول طولانی است. معمولاً این نقل‌قول به صورت بصری با تورفتگی (indentation) نمایش داده می‌شود (برای تغییر آن، بخش [یادداشت‌های استفاده](#usage-notes) را ببینید). می‌توانید URL منبع نقل‌قول را با attribute به نام `cite` مشخص کنید و یک نمایش متنی از منبع را با عنصر {{HTMLElement("cite")}} ارائه دهید.

## Attributes

این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) نیز می‌شود.

- `cite`
  - : یک URL که سند یا پیام منبعِ اطلاعاتِ نقل‌شده را مشخص می‌کند. این attribute برای اشاره به اطلاعاتی است که زمینه یا مرجع نقل‌قول را توضیح می‌دهد.

## یادداشت‌های استفاده

طبق مشخصات، در صورت وجود هرگونه ارجاع برای نقل‌قول، باید خارج از عنصر `<blockquote>` قرار گیرد.

برای تغییر تورفتگی متن نقل‌قول‌شده، از خواص {{Glossary("CSS")}} مانند {{cssxref("margin-left")}} و/یا {{cssxref("margin-right")}} یا property کوتاه‌شده {{cssxref("margin")}} استفاده کنید.

برای نقل‌قول‌های کوتاه‌تر به صورت inline (نه در یک بلوک جداگانه)، از عنصر {{HTMLElement("q")}} (Quotation) استفاده کنید.

## مثال‌ها

این مثال استفاده از عنصر `<blockquote>` را برای نقل‌قول از {{RFC(1149)}}، _A Standard for the Transmission of IP Datagrams on Avian Carriers_ نشان می‌دهد.

```html
<blockquote cite="https://datatracker.ietf.org/doc/html/rfc1149">
  <p>
    Avian carriers can provide high delay, low throughput, and low altitude
    service. The connection topology is limited to a single point-to-point path
    for each carrier, used with standard carriers, but many carriers can be used
    without significant interference with each other, outside early spring. This
    is because of the 3D ether space available to the carriers, in contrast to
    the 1D ether used by IEEE802.3. The carriers have an intrinsic collision
    avoidance system, which increases availability.
  </p>
</blockquote>
```

### نتیجه

## خلاصه فنی

| مشخصه | مقدار |
|------|-------|
| [Content categories](/en-US/docs/Web/HTML/Reference/Content_categories) | Flow content, sectioning root, palpable content. |
| Permitted content | Flow content. |
| Tag omission | هیچ، تگ شروع و پایان هر دو الزامی هستند. |
| Permitted parents | هر عنصری که flow content را بپذیرد. |
| Implicit ARIA role | [`blockquote`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles) |
| Permitted ARIA roles | هر role |
| DOM interface | [`HTMLQuoteElement`](/en-US/docs/Web/API/HTMLQuoteElement) |

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌های محتوا</a>
      </th>
      <td>
        محتوای جریانی (Flow content)، ریشهٔ بخش‌بندی (Sectioning root)، محتوای محسوس (Palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ تگ شروع و تگ پایان هر دو الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a> را می‌پذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">blockquote</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>HTMLQuoteElement</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری با مرورگر

## همچنین ببینید

- عنصر `<q>` برای نقل‌قول‌های درون‌خطی.
- عنصر `<cite>` برای استناد به منبع.
- [عنصر blockquote](https://heydonworks.com/article/the-blockquote-element/) از heydonworks.com (۲۰۲۴)