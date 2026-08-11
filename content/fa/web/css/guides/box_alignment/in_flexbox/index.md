---
title: "Box alignment in flexbox"
source: "https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Box_alignment/In_flexbox"
translated_by: "n8n + AI"
---

ماژول [box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment) نحوهٔ عملکرد ترازبندی را در روش‌های مختلف چیدمان توضیح می‌دهد. در این راهنما، کارکرد box alignment را در بستر [flexbox](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Basic_concepts) بررسی می‌کنیم. از آنجا که هدف این راهنما پرداختن به ویژگی‌های خاص flexbox و box alignment است، بهتر است آن را همراه با [مرور box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview) بخوانید؛ راهنمایی که ویژگی‌های مشترک box alignment را در روش‌های مختلف چیدمان پوشش می‌دهد.

## مثال پایه

در این مثال flexbox، سه آیتم فلکس روی محور اصلی با `justify-content` و روی محور عرضی با `align-items` تراز شده‌اند. آیتم اول با تنظیم `align-self` روی `center`، مقدار `align-items` تعیین‌شده برای کل گروه را لغو می‌کند.

```css hidden live-sample___gap live-sample___flex-align-items live-sample___auto-margins
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

```html live-sample___flex-align-items
<div class="box">
  <div>One</div>
  <div>Two</div>
  <div>Three <br />has <br />extra <br />text</div>
</div>
```

```css live-sample___flex-align-items
.box {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  border: 2px dotted rgb(96 139 168);
}

.box :first-child {
  align-self: center;
}
```

## محورها و flex-direction

Flexbox به حالت نگارش سند احترام می‌گذارد؛ بنابراین اگر با زبان انگلیسی کار می‌کنید و `justify-content` را روی `flex-end` تنظیم کنید، آیتم‌ها به انتهای ظرف فلکس (flex container) تراز می‌شوند. اگر `flex-direction` روی `row` باشد، این تراز در جهت inline انجام می‌شود.

اما در flexbox می‌توانید محور اصلی را با تنظیم `flex-direction: column` تغییر دهید. در این حالت، `justify-content` آیتم‌ها را در جهت block تراز می‌کند. بنابراین ساده‌ترین راه این است که در flexbox به این شکل به محور اصلی و محور عرضی فکر کنید:

- محور اصلی = جهتی که `flex-direction` تعیین می‌کند = تراز کردن با `justify-content`
- محور عرضی = عمود بر محور اصلی = تراز کردن با `align-content`، `align-self`/`align-items`

### تراز محور اصلی

- `justify-content`

### تراز محور عرضی

- `align-self`
- `align-items`
- `align-content`

### در flexbox ویژگی justify-self وجود ندارد

در محور اصلی، flexbox با آیتم‌های فلکس به‌عنوان یک گروه رفتار می‌کند. فضای لازم برای چیدمان آیتم‌ها محاسبه می‌شود و فضای باقی‌مانده برای توزیع در دسترس است. ویژگی `justify-content` نحوهٔ استفاده از این فضای باقی‌مانده را کنترل می‌کند. اگر `justify-content: flex-end` تنظیم کنید، فضای اضافه قبل از آیتم‌ها قرار می‌گیرد؛ با `justify-content: space-around`، فضا در دو سمت هر آیتم در آن بُعد توزیع می‌شود؛ و به همین ترتیب.

این یعنی ویژگی `justify-self` در flexbox معنایی ندارد، چون همیشه با جابه‌جایی کل گروه آیتم‌ها سروکار داریم.

در محور عرضی، `align-self` معنادار است؛ چون احتمالاً فضای اضافی در آن بُعد از ظرف فلکس وجود دارد و می‌توان یک آیتمِ واحد را به ابتدا یا انتهای آن حرکت داد.

## تراز و حاشیه‌های خودکار

در flexbox یک مورد استفاده‌ی خاص وجود دارد که ممکن است فکر کنیم به property ای مثل `justify-self` نیاز داریم: وقتی می‌خواهیم مجموعه‌ای از آیتم‌های flex را از هم جدا کنیم؛ مثلاً برای ساختن یک الگوی ناوبری تقسیم‌شده (split navigation). در این حالت می‌توانیم از `margin` با مقدار `auto` استفاده کنیم. یک `margin` با مقدار `auto` تمام فضای موجود را در آن جهت جذب می‌کند. این همان کاری است که هنگام وسط‌چین کردن یک بلوک با `margin: auto` انجام می‌شود. اگر margin چپ و راست را `auto` بگذاریم، هر دو طرف بلوک سعی می‌کنند همه‌ی فضای خالی را پر کنند و در نتیجه بلوک به مرکز رانده می‌شود.

اگر روی یکی از آیتم‌های یک مجموعه آیتم‌های flex که همگی در ابتدای محور (start) قرار گرفته‌اند، `margin: auto` بگذاریم، می‌توانیم یک ناوبری تقسیم‌شده ایجاد کنیم. این روش با flexbox و property های alignment به خوبی کار می‌کند. به محض اینکه فضای خالی برای margin خودکار باقی نماند، آن آیتم دقیقاً مثل بقیه‌ی آیتم‌های flex رفتار می‌کند و برای جا شدن در فضای موجود کوچک می‌شود.

```html live-sample___auto-margins
<div class="box">
  <div>One</div>
  <div>Two</div>
  <div>Three</div>
  <div class="push">Four</div>
  <div>Five</div>
</div>
```

```css live-sample___auto-margins
.box {
  display: flex;
  border: 2px dotted rgb(96 139 168);
}
.push {
  margin-left: auto;
}
```

## property های `gap`

- `row-gap`
- `column-gap`
- `gap`

### ایجاد فاصله‌های با اندازه ثابت بین آیتم‌ها

در محور اصلی (main axis)، property ای به نام `column-gap` بین آیتم‌های مجاور فاصله‌هایی با اندازه ثابت ایجاد می‌کند.

در محور عرضی (cross axis)، property ای به نام `row-gap` بین خطوط مجاور flex فاصله ایجاد می‌کند. برای اینکه این فاصله‌گذاری مؤثر باشد، باید `flex-wrap` نیز روی `wrap` تنظیم شده باشد.

```html live-sample___gap
<div class="box">
  <div>One</div>
  <div>Two</div>
  <div>Three</div>
  <div>Four</div>
  <div>Five</div>
  <div>Six</div>
</div>
```

```css live-sample___gap
.box {
  width: 450px;
  display: flex;
  flex-wrap: wrap;
  row-gap: 10px;
  column-gap: 2em;
  border: 2px dotted rgb(96 139 168);
}

.box > * {
  flex: 1;
}
```

## همچنین ببینید

- [CSS box alignment](/en-US/docs/Web/CSS/Guides/Box_alignment) module
- [Box alignment overview](/en-US/docs/Web/CSS/Guides/Box_alignment/Overview)
- [Box alignment in CSS grid layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_grid_layout)
- [Box alignment in multiple-column layout](/en-US/docs/Web/CSS/Guides/Box_alignment/In_multi-column_layout)
- [Box alignment for block, absolutely positioned, and table layouts](/en-US/docs/Web/CSS/Guides/Box_alignment/In_block_abspos_tables)
- [Aligning items in flex container](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Aligning_items)
- Cross axis
- Main axis