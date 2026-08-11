---
title: "Box alignment in grid layout"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout"
translated_by: "n8n + AI"
---

ماژول [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment) نحوه‌ی ترازبندی را در روش‌های مختلف چیدمان توضیح می‌دهد. در این صفحه، بررسی می‌کنیم که box alignment در بسترِ [CSS grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout) چطور کار می‌کند.

این راهنما به ویژگی‌های مختصِ Grid layout و Box Alignment می‌پردازد؛ پس بهتر است آن را همراه با [مرور box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview) بخوانید که ویژگی‌های مشترک ترازبندی را در روش‌های مختلف چیدمان پوشش می‌دهد.

## مثال ابتدایی

در این مثال که از [grid layout](/en-US/docs/Web/CSS/Guides/Grid_layout/Basic_concepts) استفاده شده، بعد از چیدن trackهای با عرض ثابت روی inline axis، فضای اضافی در {{glossary("grid container")}} باقی می‌ماند. این فضا با {{cssxref("justify-content")}} توزیع می‌شود. در block axis، ترازبندی ایتم‌ها درون ناحیه‌های grid با {{cssxref("align-items")}} کنترل می‌شود. ایتم اول مقدار `align-items` که روی گروه تنظیم شده را با {{cssxref("align-self")}} روی `center` بازنویسی می‌کند.

```html live-sample___grid-align-items
<div class="box">
  <div>One</div>
  <div>Two</div>
  <div>Three <br />has <br />extra <br />text</div>
  <div>Four</div>
  <div>Five</div>
  <div>Six</div>
</div>
```

```css hidden live-sample___grid-align-items
body {
  font-family: sans-serif;
}
.box > * {
  padding: 20px;
  border: 2px solid rgb(96 139 168);
  border-radius: 5px;
  background-color: rgb(96 139 168 / 0.2);
}
```

```css live-sample___grid-align-items
.box {
  display: grid;
  grid-template-columns: 120px 120px 120px;
  align-items: start;
  justify-content: space-between;
  border: 2px dotted rgb(96 139 168);
}

.box :first-child {
  align-self: center;
}
```

{{EmbedLiveSample("grid-align-items", , 200)}}

## محورهای Grid

Grid یک روش چیدمان دوبعدی است؛ بنابراین همیشه دو محور برای ترازبندی ایتم‌ها داریم و به همه‌ی ویژگی‌های box alignment دسترسی داریم تا این کار را انجام دهیم.

**Inline axis** محوری است که با جهت نوشتن کلمات در یک جمله هماهنگ است. مثلاً در زبان‌های افقی مثل انگلیسی یا عربی، این محور به صورت افقی حرکت می‌کند. اگر writing mode عمودی باشد، inline axis هم عمودی می‌شود.

![محورهای inline افقی هستند.](inline_axis.png)

برای ترازبندی در امتداد inline axis از ویژگی‌هایی استفاده می‌کنیم که با `justify-` شروع می‌شوند: {{cssxref("justify-content")}}، {{cssxref("justify-items")}} و {{cssxref("justify-self")}}.

**Block axis** عمود بر inline axis است و همان جهتی است که بلوک‌ها در صفحه چیده می‌شوند؛ مثلاً پاراگراف‌های انگلیسی یکی زیر دیگری به صورت عمودی قرار می‌گیرند. این بعدِ block است.

برای ترازبندی در امتداد block axis از ویژگی‌هایی استفاده می‌کنیم که با `align-` شروع می‌شوند: {{cssxref("align-content")}}، {{cssxref("align-items")}} و {{cssxref("align-self")}}.

![محورهای block عمودی هستند.](block_axis.png)

## ترازبندی ایتم (Self alignment)

این ویژگی‌ها به ترازبندی ایتم درون ناحیه‌ی grid که در آن قرار گرفته می‌پردازند:

- {{cssxref("justify-self")}}
- {{cssxref("align-self")}}
- {{cssxref("place-self")}}
- {{cssxref("justify-items")}}
- {{cssxref("align-items")}}
- {{cssxref("place-items")}}

ویژگی‌های `*-items` یعنی `align-items` و `justify-items` روی grid container اعمال می‌شوند و ترازبندی همه‌ی ایتم‌های grid را به عنوان یک گروه تنظیم می‌کنند. در مقابل، ویژگی‌های `*-self` یعنی `align-self` و `justify-self` روی خود ایتم‌ها تنظیم می‌شوند. یعنی می‌توانید ابتدا ترازبندی را برای همه‌ی ایتم‌ها تعیین کنید و بعد اگر ایتم خاصی به تراز متفاوتی نیاز داشت، با اعمال `align-self` یا `justify-self` روی قوانین مربوط به همان ایتم، مقدار پیش‌فرض را بازنویسی کنید.

مقدار اولیه برای `align-items` و `justify-items` برابر با `stretch` است و مقدار اولیه برای `align-self` و `justify-self` برابر با `auto` است؛ بنابراین آیتم در کل ناحیه grid کشیده می‌شود. استثنای این قانون زمانی است که آیتم دارای نسبت ابعاد (aspect ratio) ذاتی باشد، مثلاً یک تصویر. در این حالت، آیتم در هر دو بعد به `start` تراز می‌شود تا تصویر تحریف نشود.

## تراز محتوا

این ویژگی‌ها به تراز کردن trackهای grid زمانی که فضای اضافی برای توزیع وجود دارد می‌پردازند:

- `justify-content`
- `align-content`
- `place-content`

این سناریو زمانی رخ می‌دهد که مجموع عرض trackهای تعریف‌شده کمتر از عرض کل grid container باشد.

## فاصله (Gap) و ویژگی‌های قدیمی grid-gap

این ویژگی‌ها فاصله بین آیتم‌های grid را در داخل یک grid container تعریف می‌کنند:

- `row-gap`
- `column-gap`
- `gap`

مشخصات grid در ابتدا شامل تعریف ویژگی‌های `grid-row-gap`، `grid-column-gap` و `grid-gap` بود. این ویژگی‌ها بعداً به مشخصات Box Alignment منتقل شدند و به `row-gap`، `column-gap` و `gap` تغییر نام دادند. این کار استفاده از آن‌ها را در سایر روش‌های چیدمان که فاصله بین آیتم‌ها معنا دارد ممکن می‌سازد.

## جستارهای وابسته

- ماژول [Box alignment در CSS](/en-US/docs/Web/CSS/Guides/Box_alignment)
- [مرور کلی Box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview)
- [Box alignment در Flexbox](/en-US/docs/Web/CSS/Guides/Box_alignment/In_flexbox)
- [Box alignment در چیدمان چندستونه](/en-US/docs/Web/CSS/Guides/Box_alignment/In_multi-column_layout)
- [Box alignment برای چیدمان block، absolutely positioned و جدول](/en-US/docs/Web/CSS/Guides/Box_alignment/In_block_abspos_tables)
- [تراز کردن آیتم‌ها در چیدمان CSS Grid](/en-US/docs/Web/CSS/Guides/Grid_layout/Box_alignment)