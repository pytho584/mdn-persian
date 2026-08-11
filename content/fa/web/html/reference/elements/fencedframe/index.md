---
title: "<fencedframe> HTML fenced frame element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/fencedframe"
translated_by: "n8n + AI"
---

# عنصر `<fencedframe>` (فریم حصاردار) HTML

عنصر **`<fencedframe>`** در [HTML](/en-US/docs/Web/HTML) یک {{Glossary("browsing context")}} تودرتو را نمایش می‌دهد که صفحه HTML دیگری را درون صفحه جاری جاسازی می‌کند. `<fencedframe>` از نظر شکل و عملکرد شباهت زیادی به عنصر {{htmlelement("iframe")}} دارد، با این تفاوت‌ها:

- ارتباط بین محتوای `<fencedframe>` و سایت میزبان محدود شده است.
- `<fencedframe>` می‌تواند به داده‌های بین‌سایتی (cross-site) دسترسی داشته باشد، اما تنها در شرایط بسیار مشخص و کنترل‌شده‌ای که حریم خصوصی کاربر را حفظ می‌کند.
- `<fencedframe>` از طریق اسکریپت‌نویسی معمولی (مثلاً خواندن یا تنظیم URL منبع) قابل دستکاری یا دسترسی به داده‌هایش نیست. محتوای `<fencedframe>` فقط از طریق [APIهای خاص](/en-US/docs/Web/API/Fenced_frame_API#use_cases) قابل جاسازی است.
- `<fencedframe>` نمی‌تواند به DOM context میزبان دسترسی داشته باشد و context میزبان نیز نمی‌تواند به DOM `<fencedframe>` دسترسی پیدا کند.

عنصر `<fencedframe>` نوعی `<iframe>` با قابلیت‌های حریم خصوصی بیشتر و بومی است. این عنصر نارسایی‌های `<iframe>` مانند وابستگی به کوکی‌های شخص ثالث و سایر ریسک‌های حریم خصوصی را برطرف می‌کند. برای جزئیات بیشتر به [Fenced frame API](/en-US/docs/Web/API/Fenced_frame_API) مراجعه کنید.

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- `allow`
  - : یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) برای `<fencedframe>` مشخص می‌کند که بر اساس مبدأ درخواست، چه قابلیت‌هایی در دسترس `<fencedframe>` قرار می‌گیرد. برای اطلاع از اینکه کدام ویژگی‌ها را می‌توان از طریق یک policy تنظیم‌شده روی fenced frame کنترل کرد، به [Permissions policies available to fenced frames](#permissions_policies_available_to_fenced_frames) مراجعه کنید.

- `height`
  - : یک عدد صحیح بدون واحد که ارتفاع fenced frame را بر حسب پیکسل CSS نشان می‌دهد. مقدار پیش‌فرض `150` است.

- `width`
  - : یک عدد صحیح بدون واحد که عرض fenced frame را بر حسب پیکسل CSS نشان می‌دهد. مقدار پیش‌فرض `300` است.

## Permissions policies موجود برای fenced frame

دسترسی‌هایی که از context سطح بالا به یک fenced frame واگذار می‌شوند تا ویژگی‌ها را مجاز یا غیرمجاز کنند، می‌توانند به عنوان یک کانال ارتباطی مورد استفاده قرار گیرند و بنابراین تهدیدی برای حریم خصوصی محسوب می‌شوند. در نتیجه، ویژگی‌های استاندارد وب که قابلیت کنترل آن‌ها از طریق [Permissions Policy](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy) وجود دارد (مانند [`camera`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/camera) یا [`geolocation`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/geolocation)) **در داخل fenced frame در دسترس نیستند**.

تنها ویژگی‌هایی که می‌توانند توسط یک policy در داخل fenced frame فعال شوند، ویژگی‌های خاصی هستند که برای استفاده درون fenced frame طراحی شده‌اند:

- [Protected Audience API](https://privacysandbox.google.com/private-advertising/protected-audience)
  - `attribution-reporting`
  - `private-aggregation`
  - `shared-storage`
  - `shared-storage-select-url`
- [Shared Storage API](/en-US/docs/Web/API/Shared_Storage_API)
  - `attribution-reporting`
  - `private-aggregation`
  - `shared-storage`
  - `shared-storage-select-url`

در حال حاضر این ویژگی‌ها همیشه در داخل fenced frame فعال هستند. در آینده، می‌توان با استفاده از ویژگی `allow` در `<fencedframe>` کنترل کرد که کدام‌یک فعال باشند. مسدود کردن ویژگی‌های privacy sandbox به این روش، بارگیری fenced frame را نیز مسدود می‌کند – در این صورت هیچ کانال ارتباطی وجود نخواهد داشت.

## تمرکز در مرزهای fenced frame

توانایی حرکت فوکوس فعال سند از مرزهای fenced frame (یعنی از یک عنصر خارج از fenced frame به داخل آن یا برعکس) محدود است. اقدامات کاربر مانند کلیک یا Tab می‌توانند این کار را انجام دهند، زیرا خطر انگشت‌نگاری (fingerprinting) وجود ندارد.

اما تلاش برای عبور از مرز از طریق فراخوانی API مانند `HTMLElement.focus()` ممنوع است – یک اسکریپت مخرب می‌تواند از مجموعه‌ای از این فراخوانی‌ها برای نشت اطلاعات استنباطی در سراسر مرز استفاده کند.

## موقعیت‌یابی و مقیاس‌بندی

از آنجایی که `<fencedframe>` یک replaced element است، می‌توان موقعیت سند تعبیه‌شده درون جعبه‌اش را با استفاده از ویژگی {{cssxref("object-position")}} تنظیم کرد.

> [!NOTE]
> ویژگی {{cssxref("object-fit")}} روی عناصر `<fencedframe>` تأثیری ندارد.

اندازهٔ محتوای تعبیه‌شده می‌تواند توسط ویژگی‌های داخلی `contentWidth` و `contentHeight` در شی `config` مربوط به `<fencedframe>` تنظیم شود (شی `config` از نوع `HTMLFencedFrameElement.config` است). در چنین مواردی، تغییر `width` یا `height` عنصر `<fencedframe>` اندازهٔ ظرف تعبیه‌شده را در صفحه تغییر می‌دهد، اما سند داخل ظرف به صورت بصری مقیاس‌بندی می‌شود تا در آن جا بگیرد. عرض و ارتفاع گزارش‌شدهٔ سند تعبیه‌شده (یعنی `Window.innerWidth` و `Window.innerHeight`) بدون تغییر باقی می‌مانند.

## دسترسی‌پذیری

افرادی که با فناوری‌های کمکی مانند صفحه‌خوان (screen reader) مرور می‌کنند، می‌توانند از ویژگی `title` روی یک `<fencedframe>` برای برچسب‌گذاری محتوای آن استفاده کنند. مقدار `title` باید به طور مختصر محتوای تعبیه‌شده را توصیف کند:

```html
<fencedframe
  title="Advertisement for new Log. From Blammo!"
  width="640"
  height="320"></fencedframe>
```

بدون این عنوان، آنها باید به داخل `<fencedframe>` بروند تا بفهمند محتوای تعبیه‌شده چیست. این تغییر بافت (context shift) می‌تواند گیج‌کننده و زمان‌بر باشد، به‌ویژه برای صفحاتی که چندین `<fencedframe>` دارند و/یا اگر محتوای تعبیه‌شده شامل محتوای تعاملی مانند ویدیو یا صدا باشد.

## مثال‌ها

برای تعیین محتوایی که در یک `<fencedframe>` نمایش داده می‌شود، یک API استفاده‌کننده (مانند [Protected Audience](https://privacysandbox.google.com/private-advertising/protected-audience) یا [Shared Storage](https://privacysandbox.google.com/private-advertising/shared-storage)) یک شی `FencedFrameConfig` تولید می‌کند که سپس به عنوان مقدار ویژگی `config` عنصر `<fencedframe>` تنظیم می‌شود.

مثال زیر یک `FencedFrameConfig` از یک حراجی تبلیغاتی API Protected Audience دریافت می‌کند که سپس برای نمایش تبلیغ برنده در یک `<fencedframe>` استفاده می‌شود:

```html
<fencedframe width="640" height="320"></fencedframe>
```

```js
const frameConfig = await navigator.runAdAuction({
  // … پیکربندی حراجی
  resolveToConfig: true,
});

const frame = document.querySelector("fencedframe");
frame.config = frameConfig;
```

> [!NOTE]
> برای دریافت یک شی `FencedFrameConfig` باید `resolveToConfig: true` به فراخوانی `runAdAuction()` ارسال شود. اگر تنظیم نشود، `Promise` حاصل به یک URN تبدیل می‌شود که فقط در یک `<iframe>` قابل استفاده است.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتویات جریانی (Flow content)</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتویات عبارتی (Phrasing content)</a>،
        محتوای جاسازی‌شده (embedded content)، محتوای تعاملی (interactive content)، محتوای قابل لمس (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتویات مجاز</th>
      <td>هیچ.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچکدام؛ هم تگ شروع و هم تگ پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>هر عنصری که محتوای جاسازی‌شده بپذیرد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role"><code>application</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role"><code>document</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role"><code>img</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLFencedFrameElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات فنی

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [مستندات Fenced Frame API](/en-US/docs/Web/API/Fenced_frame_API)
- [Fenced frames](https://privacysandbox.google.com/private-advertising/fenced-frame) در privacysandbox.google.com
- [The Privacy Sandbox](https://privacysandbox.google.com/) در privacysandbox.google.com