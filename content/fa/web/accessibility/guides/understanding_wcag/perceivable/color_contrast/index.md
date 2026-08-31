---
title: "Color contrast"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable/Color_contrast"
translated_by: "n8n + AI"
---

---
title: Color contrast
slug: Web/Accessibility/Guides/Understanding_WCAG/Perceivable/Color_contrast
page-type: guide
sidebar: accessibilitysidebar
---

[کنتراست رنگ](https://w3c.github.io/wcag/guidelines/22/#dfn-contrast-ratio) بین زمینه و محتوای پیش‌زمینه (که معمولاً متن است) باید به اندازه‌ای زیاد باشد که خوانایی تضمین شود.

هنگام طراحی رابط‌های خوانا برای توانایی‌های مختلف بینایی، دستورالعمل‌های WCAG نسبت‌های کنتراست زیر را توصیه می‌کنند:

| نوع محتوا                                                                 | حداقل نسبت (رتبه AA) | نسبت بهبودیافته (رتبه AAA) |
| ------------------------------------------------------------------------------- | ------------------------- | --------------------------- |
| متن بدنه                                                                       | 4.5 : 1                   | 7 : 1                       |
| متن بزرگ (120-150% بزرگ‌تر از متن بدنه)                               | 3 : 1                     | 4.5 : 1                     |
| اجزای رابط کاربری فعال و اشیاء گرافیکی مانند آیکون‌ها و نمودارها | 3 : 1                     | تعریف نشده                 |

این نسبت‌ها برای متن‌های «تصادفی» مانند کنترل‌های غیرفعال، لوگوها یا متن‌های صرفاً تزئینی اعمال نمی‌شوند.

برای اطلاعات بیشتر، بخش [راه‌حل](#solution) را ببینید.

داشتن کنتراست رنگ خوب در سایت شما به همه کاربران کمک می‌کند، اما به ویژه برای کاربران با انواع خاصی از کوررنگی و سایر شرایط مشابه که کنتراست پایینی را تجربه می‌کنند و در تشخیص رنگ‌های مشابه مشکل دارند، مفید است. این به دلیل آن است که آنها نواحی روشن و تاریک را به راحتی افرادی که چنین شرایطی ندارند نمی‌بینند و در نتیجه در دیدن لبه‌ها، حاشیه‌ها و سایر جزئیات مشکل دارند.

داشتن طراحی جذاب در وب‌سایت شما خوب است، اما اگر کاربران نتوانند محتوای شما را بخوانند، طراحی بی‌ارزش است.

## مثال‌ها

بیایید نگاهی به برخی کدهای HTML و CSS بیندازیم:

```html
<div class="good">Good contrast</div>
<div class="bad">Bad contrast</div>
```

```css
div {
  /* General div styles here */
}

.good {
  background-color: #5a80a9;
}

.bad {
  background-color: #400064;
}
```

هر دو قطعه متن رنگ پیش‌فرض سیاه خود را دارند.

### کنتراست خوب

`<div>` «خوب» دارای پس‌زمینه آبی نئونی است که خواندن متن را آسان می‌کند:

```html
<div class="good">Good contrast</div>
```

```css
div {
  font-family: sans-serif;
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  width: 250px;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 4px 4px 4px black;
}

.good {
  background-color: #5a80a9;
}
```

{{EmbedLiveSample('Good_Contrast', '100%', '100')}}

### کنتراست بد

از طرف دیگر، `<div>` «بد» دارای پس‌زمینه بنفش بسیار تیره است که خواندن متن را بسیار دشوارتر می‌کند:

```html
<div class="bad">Bad contrast</div>
```

```css
div {
  font-family: sans-serif;
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  width: 250px;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 4px 4px 4px black;
}

.bad {
  background-color: #400064;
}
```

{{EmbedLiveSample('Bad_Contrast', '100%', '100')}}

## راه‌حل

هنگام انتخاب طرح رنگ برای وب‌سایت خود، رنگ‌های پیش‌زمینه و پس‌زمینه‌ای را انتخاب کنید که کنتراست خوبی دارند. کنتراست رنگ را تا حد امکان در محدودیت‌های طراحی خود خوب کنید - ایده‌آل این است که به رتبه AAA برسید (به 1.4.6 در زیر مراجعه کنید)، اما حداقل رتبه AA را برآورده کنید (به 1.4.3 در زیر مراجعه کنید).

اگر محتوای غیرمتنی مانند ویدیو یا انیمیشن را شامل می‌شوید، باید از 1.4.11 پیروی کنید (دوباره، به زیر مراجعه کنید).

برای بررسی کنتراست خود هنگام انتخاب رنگ، از ابزاری مانند [بررسی‌کننده کنتراست رنگ](https://webaim.org/resources/contrastchecker/) متعلق به WebAIM استفاده کنید.

همچنین می‌توانید کنتراست رنگ را به‌طور لحظه‌ای با استفاده از ابزارهای توسعه‌دهنده Firefox بررسی کنید — راهنمای [بازرس دسترسی](https://firefox-source-docs.mozilla.org/devtools-user/accessibility_inspector/index.html) و به ویژه بخش [بررسی مشکلات دسترسی](https://firefox-source-docs.mozilla.org/devtools-user/accessibility_inspector/index.html#check-for-accessibility-issues) را ببینید. سعی کنید از آن روی مثال‌های زنده در بخش توضیحات استفاده کنید.

## معیارهای موفقیت مرتبط WCAG

- [1.4.3 حداقل کنتراست (AA)](https://w3c.github.io/wcag/guidelines/22/#contrast-minimum)
  - : کنتراست رنگ بین پس‌زمینه و محتوای پیش‌زمینه باید در حداقل سطح باشد تا خوانایی تضمین شود:
    - متن و پس‌زمینه آن باید نسبت کنتراست حداقل 4.5:1 داشته باشند.
    - متن عنوان (یا فقط بزرگ‌تر) باید نسبت حداقل 3:1 داشته باشد. متن بزرگ به عنوان حداقل 18pt یا 14pt پررنگ تعریف می‌شود.

- [1.4.6 کنتراست بهبودیافته (AAA)](https://w3c.github.io/wcag/guidelines/22/#contrast-enhanced)
  - : این معیار از معیار 1.4.3 پیروی می‌کند و بر آن بنا می‌شود.
    - متن و پس‌زمینه آن باید نسبت کنتراست حداقل 7:1 داشته باشند.
    - متن عنوان (یا فقط بزرگ‌تر) باید نسبت حداقل 4.5:1 داشته باشد.

- [1.4.11 کنتراست غیرمتن (AA)](https://w3c.github.io/wcag/guidelines/22/#non-text-contrast)
  - : باید حداقل نسبت کنتراست رنگ 3 به 1 برای اجزای رابط کاربری و اشیاء گرافیکی وجود داشته باشد.

## همچنین ببینید

- [رنگ و کنتراست رنگ](/en-US/docs/Learn_web_development/Core/Accessibility/CSS_and_JavaScript#color_and_color_contrast)
- [برچسب‌های چندگانه](/en-US/docs/Learn_web_development/Extensions/Forms/How_to_structure_a_web_form#multiple_labels)
- [درک کنتراست غیرمتن](https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html)