---
title: "ARIA: aria-colspan attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colspan"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-colspan attribute"
short-title: aria-colspan
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-colspan
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-colspan
sidebar: accessibilitysidebar
---

ویژگی `aria-colspan` تعداد ستون‌هایی را که یک سلول (cell) یا گریدسل (gridcell) درون یک [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)، [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) پوشش می‌دهد، تعریف می‌کند.

## توضیحات

این ویژگی برای [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)‌ها و [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)‌هایی در نظر گرفته شده است که در یک {{HTMLElement('table')}} بومی HTML قرار ندارند. مقدار ویژگی `aria-colspan` تعریف می‌کند که یک سلول منفرد در یک [`table`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/table_role)، [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) یا [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) ARIA چند ستون را پوشش می‌دهد.

در HTML، عناصر {{HTMLElement('th')}} و {{HTMLElement('td')}} دارای ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#attributes) هستند. هنگام استفاده از {{HTMLElement('table')}} معنایی، از ویژگی بومی `colspan` همان‌طور که طراحی شده استفاده کنید. این ویژگی ARIA برای سلول‌ها و گریدسل‌هایی در نظر گرفته شده است که در جدول بومی قرار ندارند و اگر روی سلولی در یک {{HTMLElement('table')}} استفاده شود، نادیده گرفته می‌شود.

> [!NOTE]
> اولین قانون استفاده از ARIA این است: اگر می‌توانید از یک ویژگی بومی استفاده کنید که معنا و رفتار مورد نیاز شما از قبل در آن تعبیه شده است، به‌جای تغییر کاربری یک عنصر و **افزودن** نقش، حالت یا ویژگی ARIA برای قابل‌دسترس کردن آن، این کار را انجام دهید. تا حد امکان از عناصر HTML جدول، از جمله {{HTMLElement('td')}} و {{HTMLElement('th')}} با ویژگی `colspan` به‌جای عناصر غیر معنایی با نقش‌ها و ویژگی‌های ARIA استفاده کنید.

مقدار `aria-colspan` باید یک عدد صحیح مثبت باشد. مقدار پیش‌فرض یا مفروض گستره یک سلول، ۱ است. مطمئن شوید که مقدار درج‌شده باعث هم‌پوشانی سلول یا گریدسل با سلول یا گریدسل بعدی در همان ردیف نمی‌شود و باعث نمی‌شود سلول از جدول، گرید یا درخت‌گریدِ حاوی آن خارج شود.

## مثال

در ادامه نمونه‌ای از بخشی از یک صفحه گسترده امتیازات لیگ مسابقات بولینگ آورده شده است. هر بازی شامل ۱۰ فریم است و هر فریم ۳ امتیاز را پوشش می‌دهد: دو توپ و مجموع فعلی. دهمین (و آخرین) فریم در هر بازی ۴ ستون را پوشش می‌دهد، در صورتی که کسی تمام توپ‌ها را استرایک بزند.

```html
<div role="grid" aria-rowcount="27">
  aria-label="Bowling League Scores"
  <div role="rowgroup">
    <div role="row" aria-rowindex="1">
      <!--
            aria-rowspan and aria-colspan provide
            assistive technologies with the correct data cell header information
            when header cells span more than one row or column.
          -->

      <span role="columnheader" aria-rowspan="2">Team</span>
      <span role="columnheader" aria-colspan="2">Player</span>
      <span role="columnheader" aria-colspan="31">Game 1 Frames</span>
      <span role="columnheader" aria-colspan="31">Game 2 Frames</span>
      <span role="columnheader" aria-colspan="31">Game 3 Frames</span>
      <span role="columnheader" aria-rowspan="2">Total</span>
    </div>
    <div role="row" aria-rowindex="2">
      <span role="columnheader">Last Name</span>
      <span role="columnheader">First Name</span>
      <span role="columnheader" aria-colspan="3">1</span>
      <span role="columnheader" aria-colspan="3">2</span>
      <span role="columnheader" aria-colspan="3">3</span>
      <span role="columnheader" aria-colspan="3">4</span>
      <span role="columnheader" aria-colspan="3">5</span>
      <span role="columnheader" aria-colspan="3">6</span>
      <span role="columnheader" aria-colspan="3">7</span>
      <span role="columnheader" aria-colspan="3">8</span>
      <span role="columnheader" aria-colspan="3">9</span>
      <span role="columnheader" aria-colspan="4">10</span>
      <span role="columnheader" aria-colspan="3">1</span>
      <span role="columnheader" aria-colspan="3">2</span>
      <span role="columnheader" aria-colspan="3">3</span>
      <span role="columnheader" aria-colspan="3">4</span>
      <span role="columnheader" aria-colspan="3">5</span>
      <span role="columnheader" aria-colspan="3">6</span>
      <span role="columnheader" aria-colspan="3">7</span>
      <span role="columnheader" aria-colspan="3">8</span>
      <span role="columnheader" aria-colspan="3">9</span>
      <span role="columnheader" aria-colspan="4">10</span>
      <span role="columnheader" aria-colspan="3">1</span>
      <span role="columnheader" aria-colspan="3">2</span>
      <span role="columnheader" aria-colspan="3">3</span>
      <span role="columnheader" aria-colspan="3">4</span>
      <span role="columnheader" aria-colspan="3">5</span>
      <span role="columnheader" aria-colspan="3">6</span>
      <span role="columnheader" aria-colspan="3">7</span>
      <span role="columnheader" aria-colspan="3">8</span>
      <span role="columnheader" aria-colspan="3">9</span>
      <span role="columnheader" aria-colspan="4">10</span>
    </div>
  </div>
  <div role="rowgroup">
    <div role="row" aria-rowindex="10">
      <span role="rowheader" aria-rowspan="3">The Mighty Quokkas</span>
      <span role="cell">Henderson</span>
      <span role="cell">Alice</span>
      <span role="cell">7</span>
      <span role="cell">/</span>
      <span role="cell">20</span>
      <span role="cell" aria-colspan="2">X</span>
      <span role="cell">39</span>
      <span role="cell">9</span>
      <span role="cell">-</span>
      <span role="cell">48</span>
      <span role="cell" aria-colspan="2">X</span>
      <span role="cell">76</span>
      <span role="cell" aria-colspan="2">X</span>
      <span role="cell">96</span>
      <span role="cell">8</span>
      <span role="cell">/</span>
      <span role="cell">113</span>
      <span role="cell">7</span>
      <span role="cell">-</span>
      <span role="cell">120</span>
      <span role="cell" aria-colspan="2">X</span>
      <span role="cell">146</span>
      <span role="cell" aria-colspan="2">X</span>
      <span role="cell">166</span>
      <span role="cell">6</span>
      <span role="cell">/</span>
      <span role="cell">X</span>
      <span role="cell">186</span>
      <span role="cell">7</span>
      <span role="cell">2</span>
      <span role="cell">9</span>
      <span role="cell">6</span>
      <span role="cell">-</span>
      <span role="cell">15</span>
      <span role="cell" aria-colspan="2">X</span>
      <span role="cell">35</span>
      <span role="cell">7</span>
      <span role="cell">/</span>
      …
    </div>
    <div role="row" aria-rowindex="11">
      <span role="cell">McPherson</span>
      <span role="cell">Leslie</span>
      <span role="cell">9</span>
      <span role="cell">-</span>
      <span role="cell">9</span>
      <span role="cell">8</span>
      <span role="cell">1</span>
      <span role="cell">18</span>
      …
    </div>
  </div>
</div>
```

اگر از {{HTMLElement('table')}} و عناصر جدول معنایی استفاده می‌کردیم، نشانه‌گذاری ما خلاصه‌تر بود و به‌طور پیش‌فرض قابل‌دسترس بود.

## مقادیر

- `<integer>`
  - : عددی صحیح بزرگ‌تر یا مساوی مقدار پیش‌فرض ۱ که تعداد ستون‌های تحت پوشش سلول را تعریف می‌کند. مقدار باید کمتر از مقداری باشد که باعث هم‌پوشانی سلول با سلول بعدی در همان ردیف می‌شود.

## رابط‌های مرتبط

- {{domxref("Element.ariaColSpan")}}
  - : ویژگی [`ariaColSpan`](/en-US/docs/Web/API/Element/ariaColSpan) که بخشی از رابط هر عنصر است، مقدار ویژگی `aria-colspan` را بازتاب می‌دهد؛ ویژگی‌ای که تعداد ستون‌های پوشش‌داده‌شده توسط یک سلول یا گریدسل درون یک جدول، گرید یا درخت‌گرید را تعریف می‌کند.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

- [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)

در نقش‌های زیر به ارث می‌رسد:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- ویژگی [`colspan`](/en-US/docs/Web/HTML/Reference/Elements/td#attributes) برای عناصر {{HTMLElement('th')}} و {{HTMLElement('td')}}
- ویژگی [`aria-colindex`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-colindex)
- ویژگی [`aria-rowspan`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-rowspan)
- نقش [`cell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/cell_role)
- نقش [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- نقش [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)