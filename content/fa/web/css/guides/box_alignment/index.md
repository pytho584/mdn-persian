---
title: "CSS box alignment"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_alignment"
translated_by: "n8n + AI"
---

ماژول **CSS box alignment** ویژگی‌های CSS مرتبط با تراز کردن جعبه‌ها درون ظرف‌هایشان را مشخص می‌کند. این ماژول، تراز کردن را برای مدل‌های مختلف چیدمان جعبه در CSS از جمله block layout، table layout، flexible box layout (flexbox) و grid layout تعریف می‌کند و یک روش تراز یکسان در سراسر CSS ایجاد می‌کند.

این ماژول اصطلاحات تراز را شرح می‌دهد و امکان استفاده از ویژگی‌های تراز را در چندین ماژول چیدمان فراهم می‌کند، نه اینکه فقط محدود به یک روش چیدمان خاص باشد.

تراز کردن با writing modes مرتبط است؛ به این معنا که وقتی یک آیتم را تراز می‌کنیم، به ابعاد فیزیکی بالا، راست، پایین و چپ توجه نمی‌کنیم. در عوض، تراز را بر اساس start و end آن بُعد خاصی که با آن کار می‌کنیم توصیف می‌کنیم. این کار تضمین می‌کند که تراز کردن بدون توجه به writing mode سند، به یک شکل عمل می‌کند.

تراز کردن متن و محتوای inline-level به ترتیب در [ماژول CSS text](/en-US/docs/Web/CSS/Guides/Text) و [ماژول CSS inline](/en-US/docs/Web/CSS/Guides/Inline_layout) تعریف شده است.

## مرجع

### ویژگی‌های CSS

- `align-content`
- `align-items`
- `align-self`
- `justify-content`
- `justify-items`
- `justify-self`
- `place-content`
- `place-items`
- `place-self`

### انواع داده

- `baseline-position`
- `content-distribution`
- `content-position`
- `overflow-position`
- `self-position`

### اصطلاحات و تعاریف

- Alignment container
- Alignment subject
- [Baseline alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview#baseline_alignment)
- [Distributed alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview#distributed_alignment)
- Fallback alignment
- [Positional alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview#positional_alignment)

## راهنماها

- [مرور کلی box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview)
  - : مروری بر مفاهیم کلی موجود در ماژول box alignment CSS.

- [Box alignment در flexbox](/en-US/docs/Web/CSS/Guides/Box_alignment/In_flexbox)
  - : نحوه عملکرد box alignment در زمینه flexbox.

- [Box alignment در CSS grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
  - : نحوه عملکرد box alignment در زمینه grid layout.

- [Box alignment در چیدمان چندستونه](/en-US/docs/Web/CSS/Guides/Box_alignment/In_multi-column_layout)
  - : نحوه عملکرد box alignment در زمینه multi-column layout.

- [Box alignment برای block layout، absolutely positioned و table layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_block_abspos_tables)
  - : نحوه عملکرد box alignment در زمینه block layout، شامل عناصر float شده، position داده شده و table.

## مفاهیم مرتبط

- `alignment-baseline`
- `dominant-baseline`
- `scroll-snap-align`
- ویژگی SVG `dominant-baseline` (SVG attribute)
- Cross axis
- Main axis

[ماژول CSS gaps](/en-US/docs/Web/CSS/Guides/Gaps)

- `column-gap`
- `gap`
- `row-gap`

## مشخصات

(مشخصات حذف شده است)

## همچنین ببینید

- [Basic concepts of flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts)
- [Aligning items in a flex container](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Aligning_items)
- [Box alignment in grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
- [ماژول CSS display](/en-US/docs/Web/CSS/Guides/Display)
- [ماژول CSS flexible box layout](/en-US/docs/Web/CSS/Guides/Flexible_box_layout)
- [ماژول CSS grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout)