---
title: <head> HTML document metadata (header) element
source: https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/head
translated_by: n8n + AI
---

# \<head> HTML document metadata (header) element

المان **`<head>`** در HTML شامل اطلاعات قابل‌خواندن توسط ماشین (\{{glossary("metadata")\}}) درباره سند است، مانند [عنوان](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/title/)، [اسکریپت‌ها](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/script/) و [شیوه‌نامه‌ها](../../../../../../../en-US/docs/Web/HTML/Reference/Elements/style/). در یک سند HTML فقط یک المان `<head>` می‌تواند وجود داشته باشد.

> **نکته:**\
> `<head>` عمدتاً اطلاعاتی را برای پردازش ماشینی نگه می‌دارد، نه برای خوانایی انسان. برای اطلاعات قابل مشاهده توسط انسان، مانند عنوان‌های سطح بالا و نویسندگان ذکر شده، به المان \{{HTMLElement("header")\}} مراجعه کنید.

### ویژگی‌ها (Attributes)

این المان شامل [ویژگی‌های سراسری](../../../../../../../en-US/docs/Web/HTML/Reference/Global_attributes/) است.

* `profile` \{{deprecated\_inline\}}
  * : \{{glossary("URI")\}} یک یا چند پروفایل metadata که با فضای خالی (\{{Glossary("whitespace")\}}) از هم جدا شده‌اند.

### مثال

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Document title</title>
  </head>
</html>
```

### خلاصه فنی

| [دسته‌بندی محتوا](../../../../../../../en-US/docs/Web/HTML/Guides/Content_categories/) | هیچکدام.                                                                                                                                                                                                                                                                                                                                                                                                                      |
| -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| محتوای مجاز                                                                            | <p>اگر سند یک سند {{HTMLElement("iframe")}} با <a href="../../../../../../../en-US/docs/Web/HTML/Reference/Elements/iframe/#srcdoc"><code>srcdoc</code></a> باشد، یا اگر اطلاعات عنوان از یک پروتکل سطح بالاتر (مانند موضوع خط در ایمیل HTML) در دسترس باشد، صفر یا چند المان از محتوای metadata.</p><p>در غیر این صورت، یک یا چند المان از محتوای metadata که دقیقاً یکی از آن‌ها یک المان {{HTMLElement("title")}} است.</p> |
| حذف تگ                                                                                 | <p>اگر اولین چیز داخل المان `` یک المان باشد، تگ شروع می‌تواند حذف شود.<br>اگر اولین چیز بعد از المان `` یک کاراکتر فاصله یا کامنت نباشد، تگ پایان می‌تواند حذف شود.</p>                                                                                                                                                                                                                                                      |
| والدین مجاز                                                                            | یک المان \{{HTMLElement("html")\}} به عنوان اولین فرزند.                                                                                                                                                                                                                                                                                                                                                                      |
| نقش ARIA ضمنی                                                                          | [بدون نقش متناظر](https://w3c.github.io/html-aria/#dfn-no-corresponding-role)                                                                                                                                                                                                                                                                                                                                                 |
| نقش‌های ARIA مجاز                                                                      | هیچ `role` مجاز نیست                                                                                                                                                                                                                                                                                                                                                                                                          |
| رابط DOM                                                                               | \{{domxref("HTMLHeadElement")\}}                                                                                                                                                                                                                                                                                                                                                                                              |

### مشخصات

\{{Specifications\}}

### سازگاری با مرورگرها

\{{Compat\}}

### همچنین ببینید

* المان‌هایی که می‌توانند داخل `<head>` استفاده شوند:
  * \{{HTMLElement("title")\}}
  * \{{HTMLElement("base")\}}
  * \{{HTMLElement("link")\}}
  * \{{HTMLElement("style")\}}
  * \{{HTMLElement("meta")\}}
  * \{{HTMLElement("script")\}}
  * \{{HTMLElement("noscript")\}}
  * \{{HTMLElement("template")\}}
