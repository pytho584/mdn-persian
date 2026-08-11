---
title: "Box alignment in multi-column layout"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_alignment/In_multi-column_layout"
translated_by: "n8n + AI"
---

ماژول [box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment) نحوه‌ی کار ترازبندی را در روش‌های مختلف چیدمان توضیح می‌دهد؛ در این راهنما به box alignment در بستر [چیدمان چندستونه (multi-column layout)](/en-US/docs/Web/CSS/Guides/Multicol_layout) می‌پردازیم. چون این راهنما نکات مخصوصِ این دو ماژول را پوشش می‌دهد، بهتر است آن را همراه با [مرور کلی box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview) بخوانید که ویژگی‌های مشترک box alignment را در روش‌های چیدمان مختلف شرح می‌دهد.

در [چیدمان چندستونه](/en-US/docs/Web/CSS/Guides/Multicol_layout/Basic_concepts)، alignment container همان جعبه محتوای multicol container است و alignment subject همان جعبه ستون است. ویژگی‌هایی که روی چیدمان چندستونه اعمال می‌شوند در ادامه فهرست شده‌اند.

## align-content و justify-content

ویژگی `align-content` در block axis و `justify-content` در inline axis اعمال می‌شود. هر فضای اضافه‌ای که از توزیع فضا بین ستون‌ها به‌وجود می‌آید، به فاصله‌ی بین ستون‌ها اضافه می‌شود و باعث می‌شود این فاصله از مقدار مشخص‌شده توسط `column-gap` (یا خلاصه‌نویسی `gap`) بزرگ‌تر شود.

اگر برای `justify-content` مقداری غیر از `normal` یا `stretch` استفاده کنید، جعبه‌های ستون با `column-width` تعیین‌شده روی ظرف چندستونه نمایش داده می‌شوند و فضای باقی‌مانده بر اساس مقدار `justify-content` توزیع می‌شود.

## column-gap

ویژگی `column-gap` ابتدا در استاندارد چیدمان چندستونه تعریف شد و بعداً با ویژگی‌های gap سایر روش‌های چیدمان در box alignment یکپارچه شد. در حالی که سایر روش‌های چیدمان مقدار اولیه `column-gap` را `0` در نظر می‌گیرند، چیدمان چندستونه آن را `1em` می‌داند؛ زیرا معمولاً بین ستون‌ها فاصله می‌خواهید.

## همچنین ببینید

- ماژول [box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment)
- [مرور کلی box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview)
- [box alignment در flexbox](/en-US/docs/Web/CSS/Guides/Box_alignment/In_flexbox)
- [box alignment در چیدمان grid](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
- [box alignment برای چیدمان‌های block، absolutely positioned و table](/en-US/docs/Web/CSS/Guides/Box_alignment/In_block_abspos_tables)