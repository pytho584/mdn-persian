---
title: "Robust"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Robust"
translated_by: "n8n + AI"
---

---
title: Robust
slug: Web/Accessibility/Guides/Understanding_WCAG/Robust
page-type: guide
sidebar: accessibilitysidebar
---

این مقاله توصیه‌های عملی در مورد نحوه نوشتن محتوای وب خود به گونه‌ای ارائه می‌دهد که با معیارهای موفقیت ذکر شده در اصل **Robust** از دستورالعمل‌های دسترسی به محتوای وب (WCAG) 2.0 و 2.1 مطابقت داشته باشد. اصل Robust بیان می‌کند که محتوا باید به اندازه کافی محکم باشد تا بتواند توسط طیف گسترده‌ای از عامل‌های کاربری، از جمله فناوری‌های کمکی، به طور قابل اعتماد تفسیر شود. این امر معمولاً با پیروی از استانداردهای وب و [آزمایش دقیق](/en-US/docs/Learn_web_development/Extensions/Testing) قابل دستیابی است.

> [!NOTE]
> برای خواندن تعاریف W3C برای اصل Robust و رهنمودها و معیارهای موفقیت آن، به [اصل 4: Robust — محتوا باید به اندازه کافی محکم باشد تا بتواند توسط طیف گسترده‌ای از عامل‌های کاربری، از جمله فناوری‌های کمکی، به طور قابل اعتماد تفسیر شود.](https://w3c.github.io/wcag/guidelines/22/#robust) مراجعه کنید.

## رهنمود 4.1 — سازگار: سازگاری را با عامل‌های کاربری فعلی و آینده، از جمله فناوری‌های کمکی، به حداکثر برسانید

این رهنمود بر سازگار کردن هرچه بیشتر محتوا، نه تنها با عامل‌های کاربری فعلی (مانند مرورگرها)، بلکه با عامل‌های کاربری آینده نیز تمرکز دارد.

<table class="standard-table">
  <thead>
    <tr>
      <th scope="col">معیار موفقیت</th>
      <th scope="col">نحوه مطابقت با معیار</th>
      <th scope="col">منبع عملی</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4.1.1 تجزیه (A)</td>
      <td>
        <p>
          محتوا باید به خوبی ساختارمند باشد تا بتواند با موفقیت توسط مرورگرها و سایر عامل‌های کاربری مانند صفحه‌خوان‌ها تجزیه شود.
        </p>
        <p>
          برای گذراندن این معیار، اطمینان حاصل کنید که HTML شما تا حد امکان معتبر است. از
          <a href="https://validator.w3.org/">اعتبارسنج W3C</a> برای اعتبارسنجی نشانه‌گذاری خود استفاده کنید.
        </p>
      </td>
      <td>
        برای راهنمای عملی به
        <a href="/en-US/docs/Learn_web_development/Core/Structuring_content/Debugging_HTML"
          >اشکال‌زدایی HTML</a
        >
        مراجعه کنید.
      </td>
    </tr>
    <tr>
      <td>4.1.2 نام، نقش، مقدار (A)</td>
      <td>
        <p>
          نام و نقش اجزای رابط کاربری (مانند ورودی‌های فرم، دکمه‌ها، پیوندها و غیره) باید به صورت برنامه‌ای قابل تعیین باشد.
        </p>
        <p>
          هنگام استفاده از عناصر معنایی به درستی برای هدف مورد نظرشان، این معیار باید به طور خودکار پاس شود. هنگام اسکریپت‌نویسی اجزای سفارشی، باید از نقش‌های WAI-ARIA و سایر ویژگی‌ها استفاده کنید تا مطمئن شوید کنترل‌های شما به درستی تفسیر شده و قابل استفاده هستند، به عنوان مثال، نه تنها توسط کاربران بینا با موس، بلکه توسط کاربران صفحه‌خوان، کاربران فقط با صفحه‌کلید و غیره.
        </p>
      </td>
      <td>
        به
        <a href="/en-US/docs/Learn_web_development/Core/Accessibility/HTML"
          >HTML: پایه خوبی برای دسترسی</a
        >
        و
        <a href="/en-US/docs/Learn_web_development/Core/Accessibility/WAI-ARIA_basics"
          >مقدمات WAI-ARIA</a
        >
        مراجعه کنید.
      </td>
    </tr>
    <tr>
      <td>
        4.1.3 پیام‌های وضعیت (AA)
      </td>
      <td>
        <p>
          کاربران فناوری‌های کمکی از پیام‌های وضعیت جدید اضافه شده به صفحه مطلع می‌شوند.
        </p>
      </td>
      <td>
        <a
          href="https://www.w3.org/WAI/WCAG21/Understanding/status-messages.html"
          >درک پیام‌های وضعیت</a
        >
      </td>
    </tr>
  </tbody>
</table>

> [!NOTE]
> همچنین توضیحات WCAG را برای [رهنمود 4.1: سازگار: سازگاری را با عامل‌های کاربری فعلی و آینده، از جمله فناوری‌های کمکی، به حداکثر برسانید.](https://w3c.github.io/wcag/guidelines/22/#compatible) ببینید.

## همچنین ببینید

- [WCAG](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG)
  1. [قابل درک](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable)
  2. [قابل اجرا](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable)
  3. [قابل فهم](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Understandable)
  4. Robust