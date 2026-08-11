---
title: "<rtc> HTML ruby text container element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/rtc"
translated_by: "n8n + AI"
---

عنصر `<rtc>` (که اکنون منسوخ شده) در HTML برای نگهداری حاشیه‌نویسی‌های معنایی نویسه‌هایی به کار می‌رود که در یک ruby از عناصر `<rb>` درون عنصر `<ruby>` قرار می‌گیرند. عناصر `<rb>` می‌توانند هم تلفظ (`<rt>`) و هم حاشیه‌نویسی معنایی (`<rtc>`) داشته باشند.

```html interactive-example
<ruby lang="zh-Hant">
  <rbc>
    <rb>馬</rb><rp>(</rp><rt>mǎ</rt><rp>)</rp>
    <rb>來</rb><rp>(</rp><rt>lái</rt><rp>)</rp>
    <rb>西</rb><rp>(</rp><rt>xī</rt><rp>)</rp>
    <rb>亞</rb><rp>(</rp><rt>yà</rt><rp>)</rp>
  </rbc>
  <rtc lang="en">
    <rp>(</rp><rt>Malaysia</rt><rp>)</rp>
  </rtc>
</ruby>
```

```css interactive-example
ruby {
  font-size: 2em;
  ruby-position: under;
}

rtc {
  ruby-position: over;
}
```

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

## مثال‌ها

```html
<div class="info">
  <ruby>
    <rbc>
      <rb>旧</rb><rt>jiù</rt> <rb>金</rb><rt>jīn</rt> <rb>山</rb><rt>shān</rt>
    </rbc>
    <rtc>San Francisco</rtc>
  </ruby>
</div>
```

```css hidden
.info {
  padding-top: 10px;
  font-size: 36px;
}
```

### نتیجه

## خلاصه فنی

| دسته‌های محتوا | هیچ‌کدام. |
| --- | --- |
| محتوای مجاز | [محتوای عبارتی (Phrasing content)](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) یا عناصر `<rt>`. |
| حذف تگ | تگ پایانی را می‌توان حذف کرد اگر بلافاصله پس از آن یک تگ آغازین `<rb>`، `<rtc>` یا `<rt>` بیاید، یا اگر تگ پایانی والد باشد. |
| والدین مجاز | یک عنصر `<ruby>`. |
| نقش‌های ARIA مجاز | هر نقشی |
| رابط DOM | `HTMLElement` |

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- {{HTMLElement("ruby")}}
- {{HTMLElement("rp")}}
- {{HTMLElement("rb")}}
- {{HTMLElement("rt")}}
- [ماژول چیدمان ruby در CSS](/en-US/docs/Web/CSS/Guides/Ruby_layout)