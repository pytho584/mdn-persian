---
title: "<head> HTML document metadata (header) element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/head"
translated_by: "n8n + AI"
---

المان **`<head>`** در HTML شامل اطلاعات قابل‌خواندن توسط ماشین ({{glossary("metadata")}}) درباره سند است، مانند [عنوان](/en-US/docs/Web/HTML/Reference/Elements/title)، [اسکریپت‌ها](/en-US/docs/Web/HTML/Reference/Elements/script) و [شیوه‌نامه‌ها](/en-US/docs/Web/HTML/Reference/Elements/style). در یک سند HTML فقط یک المان `<head>` می‌تواند وجود داشته باشد.

> **نکته:**  
> `<head>` عمدتاً اطلاعاتی را برای پردازش ماشینی نگه می‌دارد، نه برای خوانایی انسان. برای اطلاعات قابل مشاهده توسط انسان، مانند عنوان‌های سطح بالا و نویسندگان ذکر شده، به المان {{HTMLElement("header")}} مراجعه کنید.

## ویژگی‌ها (Attributes)

این المان شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `profile` {{deprecated_inline}}
  - : {{glossary("URI")}} یک یا چند پروفایل metadata که با فضای خالی ({{Glossary("whitespace")}}) از هم جدا شده‌اند.

## مثال

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

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>هیچکدام.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <p>
          اگر سند یک سند {{HTMLElement("iframe")}} با <a href="/en-US/docs/Web/HTML/Reference/Elements/iframe#srcdoc"><code>srcdoc</code></a> باشد، یا اگر اطلاعات عنوان از یک پروتکل سطح بالاتر (مانند موضوع خط در ایمیل HTML) در دسترس باشد، صفر یا چند المان از محتوای metadata.
        </p>
        <p>
          در غیر این صورت، یک یا چند المان از محتوای metadata که دقیقاً یکی از آن‌ها یک المان {{HTMLElement("title")}} است.
        </p>
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        اگر اولین چیز داخل المان `<head>` یک المان باشد، تگ شروع می‌تواند حذف شود.<br />اگر اولین چیز بعد از المان `<head>` یک کاراکتر فاصله یا کامنت نباشد، تگ پایان می‌تواند حذف شود.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>یک المان {{HTMLElement("html")}} به عنوان اولین فرزند.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">بدون نقش متناظر</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLHeadElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- المان‌هایی که می‌توانند داخل `<head>` استفاده شوند:
  - {{HTMLElement("title")}}
  - {{HTMLElement("base")}}
  - {{HTMLElement("link")}}
  - {{HTMLElement("style")}}
  - {{HTMLElement("meta")}}
  - {{HTMLElement("script")}}
  - {{HTMLElement("noscript")}}
  - {{HTMLElement("template")}}