---
title: "CSS anchor positioning"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Anchor_positioning"
translated_by: "n8n + AI"
---

# CSS anchor positioning

ماژول **CSS anchor positioning** امکاناتی را فراهم می‌کند که به شما اجازه می‌دهد عناصر را به یکدیگر متصل کنید. برخی عناصر به عنوان **anchor elements** (عناصر لنگر) تعریف می‌شوند؛ **anchor-positioned elements** (عناصر دارای موقعیت‌دهی لنگر) می‌توانند اندازه و موقعیت‌شان بر اساس اندازه و مکان عناصر لنگر مربوطه تنظیم شود.

علاوه بر این، این مشخصات مکانیزم‌های صرفاً CSS ارائه می‌دهد برای:

- تعیین مجموعه‌ای از موقعیت‌های جایگزین برای یک عنصر لنگرشده؛ وقتی موقعیت پیش‌فرض رندر باعث سرریز شدن از بلاک شامل‌کننده یا خارج از صفحه شود، مرورگر تلاش می‌کند عنصر را در موقعیت‌های جایگزین رندر کند.
- اعلام شرایطی که در آن عناصر دارای موقعیت‌دهی لنگر باید مخفی شوند، در موقعیت‌هایی که اتصال آن‌ها به عناصر لنگر مناسب نیست.

## مرجع

### ویژگی‌ها

- `anchor-scope`
- `anchor-name`
- `position-anchor`
- `position-area`
- `position-try-fallbacks`
- `position-try-order`
- `position-try` (shorthand)
- `position-visibility`

### At-rules و توصیفگرها

- `@position-try`

### توابع

- [`anchor()`](/en-US/docs/Web/CSS/Reference/Values/anchor)
- [`anchor-size()`](/en-US/docs/Web/CSS/Reference/Values/anchor-size)

### انواع داده و مقادیر

- [`anchor-center`](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using#centering_on_the_anchor_using_anchor-center)
- [`<anchor-side>`](/en-US/docs/Web/CSS/Reference/Values/anchor#anchor-side)
- [`<anchor-size>`](/en-US/docs/Web/CSS/Reference/Values/anchor-size#anchor-size)
- [`<position-area>`](/en-US/docs/Web/CSS/Reference/Values/position-area_value)
- [`<try-size>`](/en-US/docs/Web/CSS/Reference/Properties/position-try-order#try-size)
- [`<try-tactic>`](/en-US/docs/Web/CSS/Reference/Properties/position-try-fallbacks#try-tactic)

### ویژگی‌های HTML

- [`anchor`](/en-US/docs/Web/HTML/Reference/Global_attributes/anchor)

### رابط‌ها

- `CSSPositionTryDescriptors`
- `CSSPositionTryRule`
- `HTMLElement.anchorElement`

## راهنماها

- [استفاده از CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using)
  - : راهنمای مقدماتی برای مفاهیم اساسی موقعیت‌یابی لنگر، شامل ارتباط دادن، موقعیت‌دهی و تنظیم اندازه عناصر نسبت به لنگرشان.

- [گزینه‌های جایگزین و پنهان‌سازی شرطی برای سرریز](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding)
  - : راهنمایی برای مکانیزم‌هایی که CSS anchor positioning برای جلوگیری از سرریز شدن عناصر دارای موقعیت‌دهی لنگر از عناصر شامل‌کننده یا viewport فراهم می‌کند، شامل گزینه‌های جایگزین position-try و پنهان‌سازی شرطی عناصر.

- [استفاده از container queries لنگرشده](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Anchored_container_queries)
  - : توضیح می‌دهد که چگونه از container queries لنگرشده برای اعمال شرطی استایل‌ها به عناصر دارای موقعیت‌دهی لنگر استفاده کنید، بسته به اینکه کدام گزینه‌های جایگزین position-try روی آن‌ها فعال هستند.

## مفاهیم مرتبط

- ماژول [CSS logical properties and values](/en-US/docs/Web/CSS/Guides/Logical_properties_and_values):
  - [inset-block-start](/en-US/docs/Web/CSS/inset-block-start)
  - [inset-block-end](/en-US/docs/Web/CSS/inset-block-end)
  - [inset-inline-start](/en-US/docs/Web/CSS/inset-inline-start)
  - [inset-inline-end](/en-US/docs/Web/CSS/inset-inline-end)
  - [inset-block](/en-US/docs/Web/CSS/inset-block)
  - [inset-inline](/en-US/docs/Web/CSS/inset-inline)
  - [inset](/en-US/docs/Web/CSS/inset) (shorthand)
  - [inline-size](/en-US/docs/Web/CSS/inline-size)
  - [min-block-size](/en-US/docs/Web/CSS/min-block-size)
  - [min-inline-size](/en-US/docs/Web/CSS/min-inline-size)
  - [block-size](/en-US/docs/Web/CSS/block-size)
  - [max-block-size](/en-US/docs/Web/CSS/max-block-size)
  - [max-inline-size](/en-US/docs/Web/CSS/max-inline-size)
  - [margin-block](/en-US/docs/Web/CSS/margin-block)
  - [margin-block-end](/en-US/docs/Web/CSS/margin-block-end)
  - [margin-block-start](/en-US/docs/Web/CSS/margin-block-start)
  - [margin-inline](/en-US/docs/Web/CSS/margin-inline)
  - [margin-inline-end](/en-US/docs/Web/CSS/margin-inline-end)
  - [margin-inline-start](/en-US/docs/Web/CSS/margin-inline-start)
  - [Inset properties](/en-US/docs/Glossary/Inset_properties) — مدخل واژه‌نامه

- ماژول [CSS positioned layout](/en-US/docs/Web/CSS/Guides/Positioned_layout):
  - [top](/en-US/docs/Web/CSS/top)
  - [left](/en-US/docs/Web/CSS/left)
  - [bottom](/en-US/docs/Web/CSS/bottom)
  - [right](/en-US/docs/Web/CSS/right)

- ماژول [CSS box model](/en-US/docs/Web/CSS/Guides/Box_model):
  - [width](/en-US/docs/Web/CSS/width)
  - [height](/en-US/docs/Web/CSS/height)
  - [min-width](/en-US/docs/Web/CSS/min-width)
  - [min-height](/en-US/docs/Web/CSS/min-height)
  - [max-width](/en-US/docs/Web/CSS/max-width)
  - [max-height](/en-US/docs/Web/CSS/max-height)
  - [margin](/en-US/docs/Web/CSS/margin)
  - [margin-bottom](/en-US/docs/Web/CSS/margin-bottom)
  - [margin-left](/en-US/docs/Web/CSS/margin-left)
  - [margin-right](/en-US/docs/Web/CSS/margin-right)
  - [margin-top](/en-US/docs/Web/CSS/margin-top)

- ماژول [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment):
  - [align-items](/en-US/docs/Web/CSS/align-items)
  - [align-self](/en-US/docs/Web/CSS/align-self)
  - [justify-items](/en-US/docs/Web/CSS/justify-items)
  - [justify-self](/en-US/docs/Web/CSS/justify-self)
  - [place-items](/en-US/docs/Web/CSS/place-items)
  - [place-self](/en-US/docs/Web/CSS/place-self)

## مشخصات

## همچنین ببینید

- ماژول [CSS scroll anchoring](/en-US/docs/Web/CSS/Guides/Scroll_anchoring)
- [آموزش: CSS positioning](/en-US/docs/Learn_web_development/Core/CSS_layout/Positioning)
- ماژول [CSS logical properties and values](/en-US/docs/Web/CSS/Guides/Logical_properties_and_values)
- [آموزش: تعیین اندازه المان‌ها در CSS](/en-US/docs/Learn_web_development/Core/Styling_basics/Sizing)