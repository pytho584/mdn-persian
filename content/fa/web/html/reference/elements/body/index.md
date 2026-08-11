---
title: "<body> HTML document body element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/body"
translated_by: "n8n + AI"
---

## ویژگی‌ها

عنصر `<body>` در [HTML](/en-US/docs/Web/HTML)، محتوای یک سند HTML را نمایش می‌دهد. در هر سند فقط یک عنصر `<body>` می‌تواند وجود داشته باشد.

این عنصر شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes)، ویژگی‌های رویداد و ویژگی‌های منسوخ است:

### ویژگی‌های رویداد

> [!NOTE]
> هر یک از نام ویژگی‌های رویداد زیر به رویداد معادل خود در رابط `Window` متصل است. برای گوش دادن به این رویدادها می‌توانید از [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) استفاده کنید، به‌جای اینکه ویژگی `oneventname` را به عنصر `<body>` اضافه کنید.

- [`onafterprint`](/en-US/docs/Web/API/Window/afterprint_event)
  - : تابعی که بعد از چاپ سند توسط کاربر صدا زده می‌شود.
- [`onbeforeprint`](/en-US/docs/Web/API/Window/beforeprint_event)
  - : تابعی که وقتی کاربر درخواست چاپ سند می‌دهد صدا زده می‌شود.
- [`onbeforeunload`](/en-US/docs/Web/API/Window/beforeunload_event)
  - : تابعی که وقتی سند در آستانه unload قرار دارد صدا زده می‌شود.
- [`onblur`](/en-US/docs/Web/API/Window/blur_event)
  - : تابعی که وقتی سند فوکوس را از دست می‌دهد صدا زده می‌شود.
- [`onerror`](/en-US/docs/Web/API/Window/error_event)
  - : تابعی که وقتی سند به‌درستی بارگذاری نمی‌شود صدا زده می‌شود.
- [`onfocus`](/en-US/docs/Web/API/Window/focus_event)
  - : تابعی که وقتی سند فوکوس می‌گیرد صدا زده می‌شود.
- [`onhashchange`](/en-US/docs/Web/API/Window/hashchange_event)
  - : تابعی که وقتی بخش شناسهٔ قطعه (fragment identifier) از آدرس فعلی سند — که با کاراکتر `#` شروع می‌شود — تغییر کند، صدا زده می‌شود.
- [`onlanguagechange`](/en-US/docs/Web/API/Window/languagechange_event)
  - : تابعی که وقتی زبان‌های ترجیحی کاربر تغییر می‌کند صدا زده می‌شود.
- [`onload`](/en-US/docs/Web/API/Window/load_event)
  - : تابعی که وقتی بارگذاری سند تمام می‌شود صدا زده می‌شود.
- [`onmessage`](/en-US/docs/Web/API/Window/message_event)
  - : تابعی که وقتی سند پیامی دریافت می‌کند صدا زده می‌شود.
- [`onmessageerror`](/en-US/docs/Web/API/Window/messageerror_event)
  - : تابعی که وقتی سند پیامی دریافت می‌کند که امکان deserialize کردن آن وجود ندارد صدا زده می‌شود.
- [`onoffline`](/en-US/docs/Web/API/Window/offline_event)
  - : تابعی که وقتی ارتباط شبکه از کار بیفتد صدا زده می‌شود.
- [`ononline`](/en-US/docs/Web/API/Window/online_event)
  - : تابعی که وقتی ارتباط شبکه برقرار می‌شود صدا زده می‌شود.
- [`onpageswap`](/en-US/docs/Web/API/Window/pageswap_event)
  - : تابعی که وقتی بین اسناد ناوبری می‌کنید و سند قبلی در آستانه unload قرار دارد، صدا زده می‌شود.
- [`onpagehide`](/en-US/docs/Web/API/Window/pagehide_event)
  - : تابعی که وقتی مرورگر صفحهٔ فعلی را در فرایند نمایش صفحه‌ای دیگر از تاریخچهٔ نشست مخفی می‌کند صدا زده می‌شود.
- [`onpagereveal`](/en-US/docs/Web/API/Window/pagereveal_event)
  - : تابعی که وقتی یک سند برای اولین بار رندر می‌شود صدا زده می‌شود؛ چه هنگام بارگذاری سند جدید از شبکه، چه هنگام فعال‌سازی یک سند.
- [`onpageshow`](/en-US/docs/Web/API/Window/pageshow_event)
  - : تابعی که وقتی مرورگر سند پنجره را به دلیل ناوبری نمایش می‌دهد صدا زده می‌شود.
- [`onpopstate`](/en-US/docs/Web/API/Window/popstate_event)
  - : تابعی که وقتی کاربر در تاریخچهٔ نشست ناوبری می‌کند صدا زده می‌شود.
- [`onresize`](/en-US/docs/Web/API/Window/resize_event)
  - : تابعی که وقتی اندازهٔ سند تغییر می‌کند صدا زده می‌شود.
- [`onrejectionhandled`](/en-US/docs/Web/API/Window/rejectionhandled_event)
  - : تابعی که وقتی یک Promise جاوااسکریپت با تأخیر مدیریت می‌شود صدا زده می‌شود.
- [`onstorage`](/en-US/docs/Web/API/Window/storage_event)
  - : تابعی که وقتی ناحیهٔ ذخیره‌سازی (storage) تغییر می‌کند صدا زده می‌شود.
- [`onunhandledrejection`](/en-US/docs/Web/API/Window/unhandledrejection_event)
  - : تابعی که وقتی یک Promise در جاوااسکریپت که هیچ هندلری برای rejection ندارد، رد (reject) می‌شود صدا زده می‌شود.
- [`onunload`](/en-US/docs/Web/API/Window/unload_event)
  - : تابعی که وقتی سند در حال خروج است صدا زده می‌شود.

### ویژگی‌های منسوخ‌شده

> [!WARNING]
> از این ویژگی‌های منسوخ‌شده استفاده نکنید؛ به‌جای آن‌ها از جایگزین‌های CSS که در کنار هر ویژگی ذکر شده استفاده کنید.

- `alink`
  - : رنگ متن ابرپیوندها هنگام انتخاب. به‌جای آن از خاصیت CSS `color` همراه با شبه‌کلاس‌های `:active` و `:focus` استفاده کنید.
- `background`
  - : آدرس (URI) یک تصویر برای استفاده به‌عنوان پس‌زمینه. به‌جای آن از خاصیت CSS `background-image` استفاده کنید.
- `bgcolor`
  - : رنگ پس‌زمینهٔ سند. به‌جای آن از خاصیت CSS `background-color` استفاده کنید.
- `bottommargin`
  - : نادیده گرفته می‌شود.
- `leftmargin`
  - : حاشیهٔ چپ و راست بدنه. به‌جای آن از خاصیت‌های CSS `margin-left` و `margin-right` (یا خاصیت منطقی `margin-inline`) استفاده کنید.
- `link`
  - : رنگ متن ابرپیوندهای بازدید نشده. به‌جای آن از خاصیت CSS `color` همراه با شبه‌کلاس `:link` استفاده کنید.
- `rightmargin`
  - : نادیده گرفته می‌شود.
- `text`
  - : رنگ پیش‌زمینهٔ متن. به‌جای آن از خاصیت CSS `color` استفاده کنید.
- `topmargin`
  - : حاشیهٔ بالا و پایین بدنه. به‌جای آن از خاصیت‌های CSS `margin-top` و `margin-bottom` (یا خاصیت منطقی `margin-block`) استفاده کنید.
- `vlink`
  - : رنگ متن ابرپیوندهای بازدید شده. به‌جای آن از خاصیت CSS `color` همراه با شبه‌کلاس `:visited` استفاده کنید.

## مثال‌ها

```html
<html lang="en">
  <head>
    <title>Document title</title>
  </head>
  <body>
    <p>
      The <code>&lt;body&gt;</code> HTML element represents the content of an
      HTML document. There can be only one <code>&lt;body&gt;</code> element in
      a document.
    </p>
  </body>
</html>
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا</th>
      <td>هیچ.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        اگر اولین چیزی که داخل تگ شروع قرار دارد یک فاصله، کامنت، عنصر
        <code>&lt;script&gt;</code> یا عنصر <code>&lt;style&gt;</code> نباشد،
        می‌توان تگ شروع را حذف کرد. همچنین اگر عنصر <code>&lt;body&gt;</code>
        محتوا داشته باشد یا تگ شروع داشته باشد و بلافاصله بعد از آن کامنت نیامده
        باشد، می‌توان تگ پایانی را حذف کرد.
      </td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>
        باید دومین عنصر از عنصر <code>&lt;html&gt;</code> باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ضمنی ARIA</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role"
            >generic</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های مجاز ARIA</th>
      <td>هیچ <code>role</code> ای مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>
        <code>HTMLBodyElement</code>
        <ul>
          <li>
            عنصر <code>&lt;body&gt;</code> رابط
            <code>HTMLBodyElement</code> را در اختیار قرار می‌دهد.
          </li>
          <li>
            می‌توانید از طریق خاصیت <code>document.body</code> به عنصر
            <code>&lt;body&gt;</code> دسترسی پیدا کنید.
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

- `<html>`
- `<head>`
- [مرور کلی مدیریت رویداد](/en-US/docs/Web/API/Document_Object_Model/Events#registering_event_handlers)