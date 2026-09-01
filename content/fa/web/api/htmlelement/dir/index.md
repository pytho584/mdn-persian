```markdown
---
title: "HTMLElement: dir property"
short-title: dir
slug: Web/API/HTMLElement/dir
page-type: web-api-instance-property
browser-compat: api.HTMLElement.dir
---

{{ApiRef("HTML DOM")}}

ویژگی **`HTMLElement.dir`** جهت نوشتار متنِ محتوای عنصر فعلی را مشخص می‌کند. این ویژگی، بازتابی از ویژگی [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir) عنصر است.

توجه داشته باشید که اگر ویژگی `dir` تنظیم نشده باشد، خودِ عنصر ممکن است جهت را از والد خود به ارث ببرد؛ با این حال، این جهتِ به‌ارث‌برده‌شده در مقدار این ویژگی بازتاب داده نمی‌شود.

جهت نوشتار متن یک عنصر، جهتی است که متن در آن حرکت می‌کند (برای پشتیبانی از سیستم‌های زبانی مختلف). زبان‌های عربی و عبری نمونه‌های رایج زبان‌هایی هستند که از جهت RTL (راست‌به‌چپ) استفاده می‌کنند.

## مقدار

یکی از موارد زیر:

- `"ltr"`
  - : جهت نوشتار از چپ به راست.
- `"rtl"`
  - : جهت نوشتار از راست به چپ.
- `"auto"`
  - : جهت عنصر باید بر اساس محتوای داخل عنصر تعیین شود.
- `""`
  - : مقدار پیش‌فرض؛ جهت‌دهی از عنصر والد به ارث برده می‌شود.

## مثال

```js
const para = document.getElementById("para1");
para.dir = "rtl";
// تغییر جهت متن در پاراگرافی با شناسه "para1"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("document.dir")}}
- ویژگی سراسری [`dir`](/en-US/docs/Web/HTML/Reference/Global_attributes/dir) در HTML
- ویژگی CSS {{cssxref("direction")}}
- شبه‌کلاس CSS {{cssxref(":dir")}}
```