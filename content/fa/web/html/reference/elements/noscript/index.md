---
title: <noscript> HTML noscript element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/noscript
translated_by: n8n + AI
---

# \<noscript> HTML noscript element

عنصر `<noscript>` یک بخش از HTML را مشخص می‌کند که اگر نوع اسکریپت در صفحه پشتیبانی نشود، یا اسکریپت‌نویسی در مرورگر غیرفعال باشد، درج می‌شود.

### ویژگی‌ها (Attributes)

این عنصر فقط [ویژگی‌های سراسری (global attributes)](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) را شامل می‌شود.

### مثال

```html
<noscript>
  <!-- لینک به فایل خارجی -->
  <a href="https://www.mozilla.org/">External Link</a>
</noscript>
<p>Rocks!</p>
```

#### خروجی با اسکریپت فعال

Rocks!

#### خروجی با اسکریپت غیرفعال

[External Link](https://www.mozilla.org/)

Rocks!

### نکات استفاده

عنصر `<noscript>` فرزندان خود را بسته به فعال یا غیرفعال بودن اسکریپت به صورت متفاوتی نمایش می‌دهد:

* اگر اسکریپت غیرفعال باشد، عنصر `<noscript>` فرزندان خود را به عنوان [محتوای HTML](../../../../../../../en-US/docs/Web/API/HTMLElement/) نمایش می‌دهد.
* اگر اسکریپت فعال باشد، عنصر `<noscript>` فرزندان خود را به عنوان [متن (Text)](../../../../../../../en-US/docs/Web/API/Text/) نمایش می‌دهد.

### خلاصه فنی

| [دسته‌بندی محتوا (Content categories)](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | [Metadata content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#metadata_content)، [Flow content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#flow_content)، [Phrasing content](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/#phrasing_content). |
| ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| محتوای مجاز (Permitted content)                                                                             | <p>وقتی اسکریپت غیرفعال است و عنصر درون `` قرار دارد: به هر ترتیبی، صفر یا چند عنصر ``، صفر یا چند عنصر `</p><h3>Browser compatibility</h3>                                                                                                                                                                           |
