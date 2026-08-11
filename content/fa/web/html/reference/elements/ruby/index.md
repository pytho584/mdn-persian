---
title: "<ruby> HTML ruby annotation element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/ruby"
translated_by: "n8n + AI"
---

عنصر HTML `<ruby>` برای نمایش حاشیه‌نویسی‌های کوچک در بالا، پایین یا کنار متن اصلی به کار می‌رود. معمولاً از آن برای نشان‌دادن تلفظ نویسه‌های شرق آسیا استفاده می‌شود، اما می‌توان برای حاشیه‌نویسی سایر متون هم از آن استفاده کرد (هرچند کاربرد کمتری دارد).

واژهٔ *ruby* در اصل [یک واحد اندازه‌گیری در حروف‌چینی](https://en.wikipedia.org/wiki/Agate_(typography)) بوده و به کوچک‌ترین اندازه‌ای اشاره دارد که متن روی کاغذ روزنامه خوانا باقی می‌ماند.

## ویژگی‌ها

این عنصر فقط [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) را می‌پذیرد.

## مثال‌ها

### مثال ۱: یک نویسه

```html
<ruby>
  漢 <rp>(</rp><rt>Kan</rt><rp>)</rp> 字 <rp>(</rp><rt>ji</rt><rp>)</rp>
</ruby>
```

### مثال ۲: یک واژه

```html
<ruby> 明日 <rp>(</rp><rt>Ashita</rt><rp>)</rp> </ruby>
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا (Content categories)</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>، محتوای قابل لمس (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (Permitted content)</th>
      <td>
        یک یا چند گروه که هر کدام از دو بخش تشکیل شده است:
        <ol>
          <li>متن پایه که می‌تواند یکی از موارد زیر باشد:
            <ul>
              <li><a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>، اما بدون عناصر <code>&lt;ruby&gt;</code> و بدون فرزند <code>&lt;ruby&gt;</code>، یا</li>
              <li>یک عنصر <code>&lt;ruby&gt;</code> که خودش فرزند <code>&lt;ruby&gt;</code> نداشته باشد.</li>
            </ul>
          </li>
          <li>حاشیه‌نویسی متن پایه که می‌تواند یکی از موارد زیر باشد:
            <ul>
              <li>یک یا چند عنصر {{HTMLElement("rt")}}، یا</li>
              <li>یک عنصر {{HTMLElement("rp")}} و به دنبال آن یک یا چند عنصر {{HTMLElement("rt")}} که هر کدام با یک عنصر {{HTMLElement("rp")}} بسته می‌شوند (یعنی <code>rp, rt, rp, rt, ..., rp</code>).</li>
            </ul>
          </li>
        </ol>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (Tag omission)</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (Permitted parents)</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM interface)</th>
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- [عنصر `<rt>`](/en-US/docs/Web/HTML/Reference/Elements/rt)
- [عنصر `<rp>`](/en-US/docs/Web/HTML/Reference/Elements/rp)

- عنصر [`<rt>`](/en-US/docs/Web/HTML/Element/rt): برای نمایش متن روبی (تلفظ یا ترجمهٔ نویسه‌های آسیای شرقی) داخل یک annotation روبی به کار می‌رود.
- عنصر [`<rp>`](/en-US/docs/Web/HTML/Element/rp): پرانتزهای جایگزین را برای مرورگرهایی که از annotation روبی پشتیبانی نمی‌کنند فراهم می‌کند.
- ویژگی CSS [`ruby-overhang`](/en-US/docs/Web/CSS/ruby-overhang): نحوهٔ سرریز شدن متن روبی روی متن مجاور را کنترل می‌کند.
- مقدار `full-size-kana` برای ویژگی [`text-transform`](/en-US/docs/Web/CSS/text-transform): نویسه‌های کوچک کانا (kana) را به اندازهٔ تمام‌عرض تبدیل می‌کند.
- ماژول [CSS ruby layout](/en-US/docs/Web/CSS/Guides/Ruby_layout): چیدمان روبی را در CSS تعریف می‌کند.