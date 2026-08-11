---
title: "CSS anchor positioning"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Anchor_positioning"
translated_by: "n8n + AI"
---

ماژول **CSS anchor positioning** قابلیت‌هایی را تعریف می‌کند که به کمک آن‌ها می‌توانید المان‌ها را به یکدیگر متصل کنید. برخی المان‌ها به عنوان **المان‌های anchor** تعریف می‌شوند؛ سپس **المان‌های anchor-positioned** می‌توانند با توجه به اندازه و موقعیت المان‌های anchor که به آن‌ها متصل شده‌اند، اندازه و موقعیت بگیرند.

علاوه بر این، این مشخصات سازوکارهایی را فقط با CSS ارائه می‌دهد که با آن‌ها می‌توانید:

- مجموعه‌ای از موقعیت‌های جایگزین برای یک المان anchor تعیین کنید؛ اگر موقعیت رندر پیش‌فرض باعث شود که المان از containing block خود سرریز کند یا خارج از صفحه رندر شود، مرورگر تلاش می‌کند المان anchor را در موقعیت‌های جایگزین رندر کند.
- شرایطی را اعلام کنید که بر اساس آن‌ها، المان‌های anchor-positioned در مواقعی که اتصال آن‌ها به المان‌های anchor مناسب نیست، پنهان شوند.

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

### At-rule‌ها و توصیفگرها

- `@position-try`

### توابع

- [`anchor()`](/en-US/docs/Web/CSS/Reference/Values/anchor)
- [`anchor-size()`](/en-US/docs/Web/CSS/Reference/Values/anchor-size)

### انواع داده و مقدارها

- [`anchor-center`](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using#centering_on_the_anchor_using_anchor-center)
- [`<anchor-side>`](/en-US/docs/Web/CSS/Reference/Values/anchor#anchor-side)
- [`<anchor-size>`](/en-US/docs/Web/CSS/Reference/Values/anchor-size#anchor-size)
- [`<position-area>`](/en-US/docs/Web/CSS/Reference/Values/position-area_value)
- [`<try-size>`](/en-US/docs/Web/CSS/Reference/Properties/position-try-order#try-size)
- [`<try-tactic>`](/en-US/docs/Web/CSS/Reference/Properties/position-try-fallbacks#try-tactic)

### ویژگی‌های HTML

- [`anchor`](/en-US/docs/Web/HTML/Reference/Global_attributes/anchor) (غیراستاندارد)

### رابط‌ها

- `CSSPositionTryDescriptors`
- `CSSPositionTryRule`
- `HTMLElement.anchorElement` (غیراستاندارد)

## راهنماها

- [Using CSS anchor positioning](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Using)
  - : راهنمای مقدماتی برای مفاهیم اساسی موقعیت‌دهی anchor؛ از جمله ارتباط برقرار کردن، موقعیت‌دهی و اندازه‌دهی المان‌ها نسبت به anchor آن‌ها.

- [Fallback options and conditional hiding for overflow](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Try_options_hiding)
  - : راهنمایی درباره سازوکارهایی که CSS anchor positioning برای جلوگیری از سرریز شدن المان‌های anchor-positioned از عناصر شامل‌کننده یا viewport ارائه می‌دهد؛ از جمله گزینه‌های fallback موقعیت و مخفی کردن شرطی المان‌ها.

- [Using anchored container queries](/en-US/docs/Web/CSS/Guides/Anchor_positioning/Anchored_container_queries)
  - : توضیح می‌دهد که چگونه از container queries متصل به anchor استفاده کنید تا استایل‌ها را به‌صورت شرطی روی المان‌های anchor-positioned اعمال کنید، بسته به اینکه کدام گزینه‌های fallback موقعیت روی آن‌ها فعال است.

## مفاهیم مرتبط

- [خواص و مقادیر منطقی CSS](/en-US/docs/Web/CSS/Guides/Logical_properties_and_values) ماژول:
  - `inset-block-start`
  - `inset-block-end`
  - `inset-inline-start`
  - `inset-inline-end`
  - `inset-block`
  - `inset-inline`
  - `inset` (shorthand)
  - `inline-size`
  - `min-block-size`
  - `min-inline-size`
  - `block-size`
  - `max-block-size`
  - `max-inline-size`
  - `margin-block`
  - `margin-block-end`
  - `margin-block-start`
  - `margin-inline`
  - `margin-inline-end`
  - `margin-inline-start`
  - [Inset properties](/en-US/docs/Glossary/Inset_properties) — اصطلاح واژه‌نامه
- [چیدمان موقعیت‌دار CSS](/en-US/docs/Web/CSS/Guides/Positioned_layout) ماژول:
  - `top`
  - `left`
  - `bottom`
  - `right`
- [مدل جعبه CSS](/en-US/docs/Web/CSS/Guides/Box_model) ماژول:
  - `width`
  - `height`
  - `min-width`
  - `min-height`
  - `max-width`
  - `max-height`
  - `margin`
  - `margin-bottom`
  - `margin-left`
  - `margin-right`
  - `margin-top`
- [تراز جعبه CSS](/en-US/docs/Web/CSS/Guides/Box_alignment) ماژول:
  - `align-items`
  - `align-self`
  - `justify-items`
  - `justify-self`
  - `place-items`
  - `place-self`

## همچنین ببینید

- ماژول [لنگر انداختن اسکرول CSS](/en-US/docs/Web/CSS/Guides/Scroll_anchoring)
- [یادگیری: موقعیت‌دهی CSS](/en-US/docs/Learn_web_development/Core/CSS_layout/Positioning)
- ماژول [خواص و مقادیر منطقی CSS](/en-US/docs/Web/CSS/Guides/Logical_properties_and_values)
- [یادگیری: اندازه‌دهی عناصر در CSS](/en-US/docs/Learn_web_development/Core/Styling_basics/Sizing)