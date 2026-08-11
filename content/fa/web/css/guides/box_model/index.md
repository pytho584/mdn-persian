---
title: "CSS box model"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model"
translated_by: "n8n + AI"
---

ماژول **box model** در CSS ویژگی‌های `margin` و `padding` را تعریف می‌کند. این ویژگی‌ها به‌همراه [height](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_sizing)، [width](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_sizing) و [ویژگی‌های border](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders)، [مدل جعبهٔ CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model/Introduction) را می‌سازند.

هر عنصر قابل مشاهده در یک صفحه وب، یک جعبه است که طبق مدل قالب‌بندی بصری (visual formatting model) چیده می‌شود. ویژگی‌های CSS اندازه، موقعیت و سطح انباشتگی (stacking level) آن‌ها را تعیین می‌کنند؛ همچنین ویژگی‌های box model (و برخی دیگر) اندازهٔ بیرونی (extrinsic size) هر جعبه و فضای اطراف آن را مشخص می‌کنند.

هر جعبه یک ناحیهٔ محتوای مستطیلی دارد که هر متن، تصویر و محتوای دیگری در آن نمایش داده می‌شود. محتوا ممکن است از یک یا چند طرف با `padding`، `border` و `margin` احاطه شود. `padding` دور محتوا، `border` دور `padding` و `margin` بیرون از `border` قرار می‌گیرد. box model توصیف می‌کند که این بخش‌ها — محتوا، `padding`، `border` و `margin` — چگونه با هم کار می‌کنند تا جعبه‌ای که CSS نمایش می‌دهد ساخته شود.

![اجزای مدل جعبه CSS](boxmodel.png)

ماژول box model ویژگی‌های فیزیکی (یا «نسبت به صفحه») مانند `margin-top` و `padding-top` را تعریف می‌کند. ویژگی‌های هم‌جهت با جریان متن (flow-relative) مانند `margin-block-start` و `margin-inline-start` که به جهت متن مرتبط‌اند، در [Logical Properties and Values](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Logical_properties_and_values) تعریف شده‌اند. ماژول box model توسط [ماژول box sizing در CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_sizing) گسترش می‌یابد؛ این ماژول مقدار «اندازهٔ ذاتی» (intrinsic size) را معرفی می‌کند و اجازه می‌دهد برای عناصری که حداقل در یک بعد اندازهٔ خودکار دارند، «نسبت تصویر» (aspect ratio) تعریف شود.

## مرجع

### ویژگی‌ها

- [`margin`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin) (shorthand)
- [`margin-bottom`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-bottom)
- [`margin-left`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-left)
- [`margin-right`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-right)
- [`margin-top`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-top)
- [`margin-trim`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-trim)
- [`padding`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) (shorthand)
- [`padding-bottom`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding-bottom)
- [`padding-left`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding-left)
- [`padding-right`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding-right)
- [`padding-top`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding-top)

### انواع داده

- [`box-edge`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-edge)
  - [`<visual-box>`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-edge#visual-box)
  - [`<layout-box>`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-edge#layout-box)
  - [`<paint-box>`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-edge#paint-box)
  - [`<coord-box>`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-edge#coord-box)
  - [`<geometry-box>`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-edge#geometry-box)

## راهنماها

- [مقدمه‌ای بر مدل جعبه CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model/Introduction)
  - : یکی از مفاهیم بنیادی CSS یعنی box model را توضیح می‌دهد. این مدل تعیین می‌کند که CSS چگونه عناصر را، شامل نواحی محتوا، `padding`، `border` و `margin`، چیدمان می‌کند.

- [آشنایی با همگرایی حاشیه‌ها (margin collapsing)](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_model/Margin_collapsing)
  - : گاهی دو حاشیه (margin) مجاور به یک حاشیه ادغام می‌شوند. این مقاله قوانینی را که مشخص می‌کنند این اتفاق چه زمانی و چرا رخ می‌دهد، و همچنین نحوه کنترل آن را تشریح می‌کند.

- [مدل قالب‌بندی بصری (visual formatting model)](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Display/Visual_formatting_model)
  - : مدل قالب‌بندی بصری را توضیح می‌دهد.

## مفاهیم مرتبط

- ماژول [CSS backgrounds and borders](/en-US/docs/Web/CSS/Guides/Backgrounds_and_borders) (پس‌زمینه و حاشیه‌های CSS)
  - `border-width` (خلاصه‌نویس)
  - `border-bottom-width`
  - `border-left-width`
  - `border-right-width`
  - `border-top-width`
- ماژول [CSS logical properties](/en-US/docs/Web/CSS/Guides/Logical_properties_and_values) (ویژگی‌های منطقی)
  - `block-size`
  - `inline-size`
  - `max-block-size`
  - `max-inline-size`
  - `min-block-size`
  - `min-inline-size`
  - `margin-block`
  - `margin-block-end`
  - `margin-block-start`
  - `margin-inline`
  - `margin-inline-end`
  - `margin-inline-start`
  - `padding-block`
  - `padding-block-end`
  - `padding-block-start`
  - `padding-inline`
  - `padding-inline-end`
  - `padding-inline-start`
  - `border-block`
  - `border-block-end`
  - `border-block-end-width`
  - `border-block-start`
  - `border-block-start-width`
  - `border-block-style`
  - `border-block-width`
  - `border-inline`
  - `border-inline-end`
  - `border-inline-end-width`
  - `border-inline-start`
  - `border-inline-start-width`
  - `border-inline-width`
- ماژول [CSS box sizing](/en-US/docs/Web/CSS/Guides/Box_sizing) (اندازه‌گیری جعبه)
  - `aspect-ratio`
  - `box-sizing`
  - `contain-intrinsic-block-size`
  - `contain-intrinsic-height`
  - `contain-intrinsic-inline-size`
  - `contain-intrinsic-size`
  - `contain-intrinsic-width`
  - `height`
  - `max-height`
  - `max-width`
  - `min-height`
  - `min-width`
  - `width`
- ماژول [CSS overflow](/en-US/docs/Web/CSS/Guides/Overflow) (سرریز)
  - `overflow` (خلاصه‌نویس)
  - `overflow-block`
  - `overflow-clip-margin`
  - `overflow-inline`
  - `overflow-x`
  - `overflow-y`
  - `text-overflow`

## مشخصات

{{Specifications}}

## همچنین ببینید

- ماژول [CSS display](/en-US/docs/Web/CSS/Guides/Display) (نمایش)
- ماژول [CSS flex layout](/en-US/docs/Web/CSS/Guides/Flexible_box_layout) (چیدمان فلکس)
- ماژول [CSS grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout) (چیدمان گرید)
- ماژول [CSS table](/en-US/docs/Web/CSS/Guides/Table) (جدول)
- ماژول [CSS positioned layout](/en-US/docs/Web/CSS/Guides/Positioned_layout) (چیدمان موقعیت‌یافته)
- ماژول [CSS fragmentation](/en-US/docs/Web/CSS/Guides/Fragmentation) (تکه‌تکه‌سازی)
- [Understanding aspect ratios](/en-US/docs/Web/CSS/Guides/Box_sizing/Aspect_ratios) (درک نسبت‌های ابعاد)